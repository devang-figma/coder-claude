# coder-claude — One-command Claude Code on a Coder box

## Setup (one-time)

```bash
mkdir -p ~/bin
curl -fsSL https://raw.githubusercontent.com/devang-figma/coder-claude/main/coder-claude -o ~/bin/coder-claude
chmod +x ~/bin/coder-claude

# Make sure ~/bin is in your PATH (add to ~/.zshrc if not already)
export PATH="$HOME/bin:$PATH"

# Make sure you're logged into Coder
coder login https://coder.figdev.systems
```

## Usage

```bash
coder-claude my-workspace              # start claude on an existing workspace
coder-claude my-new-box us-east-1      # create a new workspace in a specific region
```

## What it does

1. Creates or starts the workspace (handles outdated templates automatically)
2. Waits for the devcontainer agent to be ready
3. Pre-configures Claude Code (skips onboarding prompts, sets model to opus)
4. Drops you into a tmux session running `claude --dangerously-skip-permissions`

## Tips

- Detach from tmux: `Ctrl-b d` (Claude keeps running in the background)
- Re-attach later: just run `coder-claude my-workspace` again
- When Claude exits, you get a shell in the same tmux session
- Default region is `us-west-2`
