---
tags:
  - macOS
---
On macOS you can schedule scripts to run in the background using launchd. This differs from cronjob in the sense that it could call the script when it resumes from sleep or a shutdown.

Sample script to get started:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>com.yourname.quartzsync</string>
  <key>ProgramArguments</key>
  <array>
    <string>/Users/yourusername/path/to/script.zsh</string>
  </array>
  <key>StartCalendarInterval</key>
  <dict>
    <key>Minute</key>
    <integer>0</integer>
  </dict>
  <key>RunAtLoad</key>
  <true/>
</dict>
</plist>

```

Then assuming it's placed in `~/Library/LaunchAgents/`, you can load the job into launchd:

```
launchctl load ~/Library/LaunchAgents/com.yourname.quartzsync.plist
```

To unload it, do:

```
launchctl unload ~/Library/LaunchAgents/com.yourname.quartzsync.plist
```