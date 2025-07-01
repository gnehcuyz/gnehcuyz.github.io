---
title: Tmux for remote development
date: 2025-06-30
draft: False
summary: Keep your scripts running even after disconnection by using tmux on remote servers.
tags: [Tools]
---

# **What is `tmux`?**
`tmux` (Terminal Multiplexer) is a powerful terminal tool that lets you:
- Run multiple shell sessions in a single terminal window.
- Keep processes running even after SSH disconnection.
- Reattach to sessions from anywhere.

If you’re running **long scripts or model training on a server**, `tmux` protects your work by keeping it alive when your network fails.

---

# **Basic Workflow (Step-by-Step)**

## Start a tmux session
```bash
tmux new -s session_name
```

## Run the script like usual
```bash
python run.py
# or
bash attack_local.sh
```

## Detach safely (but keep it running)
Press:
```text
Ctrl + b, then d
```

## Reattach later
```bash
tmux attach -t session_name
```

## List all sessions
```bash
tmux ls
```

## Kill a session when done
```bash
tmux kill-session -t session_name
```

---

# **What Happens if I Don’t Use `tmux`?**

If you start a job in a normal SSH session and the session drops:
- Your training job is killed
- No way to resume it
- You may lose logs and progress

So for long or important tasks: **Always use tmux**

---

# **Common tmux Shortcuts**

| Action                  | Shortcut                 |
| ----------------------- | ------------------------ |
| Detach from tmux        | Ctrl + b, then d         |
| Create new window       | Ctrl + b, then c         |
| Next/Previous window    | Ctrl + b, then n / p     |
| Split pane (horizontal) | Ctrl + b, then "         |
| Split pane (vertical)   | Ctrl + b, then %         |
| Move between panes      | Ctrl + b, then arrow key |
| Kill pane/window        | Ctrl + b, then x         |
| Rename window           | Ctrl + b, then ,         |


---

# Resources
- [tmux Cheat Sheet](https://tmuxcheatsheet.com)

