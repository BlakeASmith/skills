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
