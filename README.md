# Claude Code Notifier Setup

This repository provides a ready-to-use prompt that configures Claude Code with macOS notifications, so you can step away from your computer while Claude works and get notified when intervention is needed or tasks are complete.

## What This Does

Sets up two types of notifications:
- **Permission notifications** (=): When Claude needs your permission to proceed
- **Completion notifications** (): When Claude finishes working on a task

## How to Use

1. **Copy the prompt URL**: Copy this GitHub raw URL:
   ```
   https://raw.githubusercontent.com/[username]/claude-code-notifier-setup/main/prompt.md
   ```

2. **Use with Claude Code**: In your Claude Code terminal, reference the prompt:
   ```bash
   claude @https://raw.githubusercontent.com/[username]/claude-code-notifier-setup/main/prompt.md
   ```

3. **Follow Claude's guidance**: Claude will walk you through:
   - Installing terminal-notifier via Homebrew
   - Configuring the notification hooks
   - Testing the setup

4. **Restart Claude Code**: After setup, restart with `claude -c` to activate notifications

## Expected Outcome

Once configured, you'll receive:
- Sound and visual notifications when Claude needs permission
- Sound and visual notifications when Claude completes tasks
- Ability to multitask while Claude works on complex tasks

## Requirements

- macOS (required for terminal-notifier)
- Homebrew (will be installed if needed)
- Claude Code CLI

## Troubleshooting

- **No notifications appearing**: Check System Preferences ’ Notifications ’ terminal-notifier
- **Permission issues**: Ensure terminal-notifier has notification permissions
- **Hooks not working**: Restart Claude Code with `claude -c`

## Manual Testing

Test notifications directly:
```bash
terminal-notifier -title 'Claude Code' -message '= Test notification' -sound 'Glass'
```

Perfect for developers who want to stay productive while Claude handles longer tasks in the background.