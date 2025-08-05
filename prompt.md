I want to set up macOS notifications so you can alert me when you need permission or finish working. Please help me configure Claude Code with notification capabilities.

Please follow these steps in order:

## Step 1: Verify macOS Environment
First, confirm we're on macOS by running `uname -s` to ensure this setup will work.

## Step 2: Install Required Tools
1. **Check if Homebrew is installed**: Run `which brew` to see if Homebrew exists
2. **Install Homebrew if needed**: If brew is missing, install it with:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
3. **Install terminal-notifier**: Run `brew install terminal-notifier`
4. **Verify installation**: Run `which terminal-notifier` to confirm it's installed

## Step 3: Locate Claude Code Settings
Find the Claude Code settings file at `~/.claude/settings.json`. If it doesn't exist, create it.

## Step 4: Configure Notification Hooks
Add this exact JSON configuration to the settings.json file. If the file already has content, merge this "hooks" section into the existing JSON:

```json
{
  "hooks": {
    "Notification": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "terminal-notifier -title 'Claude Code' -message '🔔 Claude needs permission' -sound 'Glass'"
          }
        ]
      }
    ],
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "terminal-notifier -title 'Claude Code' -message '✅ Claude finished working' -sound 'Funk'"
          }
        ]
      }
    ]
  }
}
```

## Step 5: Verify Configuration
1. **Check JSON syntax**: Ensure the settings.json file has valid JSON formatting
2. **Confirm file location**: The file should be at `~/.claude/settings.json`

## Step 6: Activate the Configuration
Exit the current Claude Code session and restart with `claude -c` to load the new configuration.

## Step 7: Test Notifications
Test both notification types:
1. **Test permission notification**: Trigger a situation where Claude needs permission
2. **Test completion notification**: Let Claude finish a task to see the completion notification
3. **Manual test**: Run the terminal-notifier commands directly to verify they work:
   ```bash
   terminal-notifier -title 'Claude Code' -message '🔔 Claude needs permission' -sound 'Glass'
   terminal-notifier -title 'Claude Code' -message '✅ Claude finished working' -sound 'Funk'
   ```

## Troubleshooting
- If notifications don't appear, check System Preferences > Notifications > terminal-notifier
- If settings.json has syntax errors, validate the JSON formatting
- If hooks don't trigger, restart Claude Code with `claude -c`

The goal is simple notifications so users can give you tasks and step away, knowing you'll alert them when you need something or when you're done.
