---
date: 2023-10-07
tags:
  - macOS
  - linux
  - automation
---
`fswatch` is a command-line utility that monitors changes in the file system. It's particularly handy when you're working on code or other files and you want to trigger some action whenever a change occurs. For example, you might use `fswatch` to automatically compile code, sync files, or reload a web page whenever you save a file.
### How It Works

You generally specify a directory (or directories) for `fswatch` to watch. Then, you can define a command that will run every time a change is detected in those directories. `fswatch` supports multiple file events like create, update, and delete.
### Example Usage

Here's a basic example to give you an idea of how you might use it:

```bash
fswatch -o /path/to/watch | xargs -n1 -I{} ./your-command.sh
```

- `fswatch -o /path/to/watch`: Tells `fswatch` to monitor changes in `/path/to/watch`.
- `xargs -n1 -I{} ./your-command.sh`: Runs `./your-command.sh` each time a change is detected.
### Installation

Installing `fswatch` might differ depending on your operating system. If you're on a Mac, it's as simple as running:

```bash
brew install fswatch
```

For Linux, you might use a package manager like `apt`:

```bash
sudo apt-get install fswatch
```