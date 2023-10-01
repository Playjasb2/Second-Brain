---
date: 2023-09-30
---
Control-B % - to create a new pane
Control-B <directional keys> - to switch panes
Control-B " - to create a new horizontal pane
Control-B c - to create a new window
Control-B <num> - to switch to window <num>
Control-B , - to rename a window

Control-B d - to detach a session
tmux ls - to view sessions running in the background
tmux attach -t <target> - attach to <target> session
tmux rename-session -t <target> <name> - Rename session <target> with <name>
tmux new -s <name> - create a new session named <name>
tmux kill-session -t <target> - kill session named <target>

exit - to exit and close a pane