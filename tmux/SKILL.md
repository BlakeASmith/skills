---
name: tmux-operating
description: Manage and interact with tmux sessions, windows, and panes. Use when the user wants to list, view, or control tmux environments.
---

# Tmux Skill

Instructions for AI agents to interact with tmux sessions, windows, and panes.

## List Sessions
List all active tmux sessions.
```bash
tmux ls
```

## List Windows and Panes
List all panes across all sessions with their session name, window index, and pane index.
```bash
tmux list-panes -a -F "#S:#I.#P #{pane_id} #{pane_current_command}"
```
- `#S`: Session name
- `#I`: Window index
- `#P`: Pane index
- `#{pane_id}`: Unique pane ID (prefixed with %, e.g., %0)
- `#{pane_current_command}`: Command currently running in the pane

## Read Pane Content
Capture and print the content of a specific pane using its ID.
```bash
tmux capture-pane -pt %<id>
```
Example for pane %0:
```bash
tmux capture-pane -pt %0
```

## Run Command in Pane
Send a command to a specific pane.
```bash
tmux send-keys -t %<id> "ls -la" C-m
```
- `C-m`: Represents the Enter key.

## Creating New Sessions and Windows
Create a new detached session.
```bash
tmux new-session -d -s <session_name>
```

Create a new window in a specific session.
```bash
tmux new-window -d -t <session_name> -n <window_name>
```

## Manipulating Panes
Split a pane horizontally or vertically.
```bash
# Vertical split (panes side-by-side)
tmux split-window -h -t %<id>
# Horizontal split (panes top-to-bottom)
tmux split-window -v -t %<id>
```

## Resizing Panes
Resize a pane in a specific direction by a given number of cells.
```bash
# Directions: U (Up), D (Down), L (Left), R (Right)
tmux resize-pane -t %<id> -U 5   # Up by 5
tmux resize-pane -t %<id> -D 10  # Down by 10
tmux resize-pane -t %<id> -L 2   # Left by 2
tmux resize-pane -t %<id> -R 20  # Right by 20
```

## Deleting Sessions and Panes
Kill a session.
```bash
tmux kill-session -t <session_name>
```

Kill a specific pane.
```bash
tmux kill-pane -t %<id>
```
