---
date: 2023-10-07
tags:
  - macOS
  - automation
---
This uses [[Running scripts in the background using launchd|launchd]] and [[fswatch]] to help with [[Self-Hosting Obsidian Notes]].

Launchd:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>com.yourname.quartzsync</string>
    <key>ProgramArguments</key>
    <array>
      <string>/Users/yourusername/sync_script.zsh</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>StandardOutPath</key>
    <string>/path/to/your/stdout.log</string>
    <key>StandardErrorPath</key>
    <string>/path/to/your/stderr.log</string>
  </dict>
</plist>

```

Script:

```zsh
#!/usr/bin/env zsh

# Source nvm
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

# Log file path
log_file="/path/to/your/log_file.log"

# Directory to watch
quartz_dir="/path/to/quartz/folder/"

# Initialize variables
cooldown=300  # Cooldown period in seconds (5 minutes)
last_sync=0  # Timestamp of the last sync

# Watch the specified folder for changes
fswatch -o "$quartz_dir"content | while read f; do
  current_time=$(date +%s)  # Get the current time in seconds since the Unix epoch
  
  # Check if enough time has passed since the last sync
  if (( current_time - last_sync >= cooldown )); then
    # Use the default version of Node
    nvm use default
    
    # Clear the log file
    echo "" > $log_file
    
    # Navigate to the specific folder and execute the command
    cd /path/to/specific/directory
    npx quartz sync
    
    # Update the last sync time
    last_sync=$current_time
    
    # Log the sync
    echo "[$(date)] - Sync complete." >> $log_file
    
    # Display a notification
    osascript -e 'display notification "Sync complete" with title "Quartz Sync"'
  else
    echo "[$(date)] - Cooldown. Skipping sync." >> $log_file
  fi
done

```