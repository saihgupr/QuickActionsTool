# Quick Actions Tool for macOS

A simple AppleScript tool to configure macOS Quick Actions (Automator workflows) with proper file type associations and optionally move them from the Quick Actions submenu to the main context menu.

## Features

- 📁 **Easy File Selection** - Browse and select any `.workflow` file from anywhere on your system
- 🎯 **File Type Configuration** - Set which file types your Quick Action should work with
- 🚀 **Context Menu Integration** - Optionally move Quick Actions from the submenu to the main right-click menu
- 🔧 **No Command Line Required** - Simple dialog-based interface

## Supported File Types

The tool supports configuring Quick Actions for:

- Folders
- All Files
- Text Files
- Images
- PDFs
- URLs
- Audio Files
- Video Files
- Applications (.app)
- Documents
- Archives (.zip, .tar, etc.)
- Source Code
- Shell Scripts
- Disk Images (.dmg)

## Installation

1. Open **Script Editor** (found in `/Applications/Utilities/`)
2. Copy the AppleScript code into a new script
3. Save it as an **Application**:
   - File → Save
   - File Format: **Application**
   - Save it anywhere you like (e.g., Applications folder)

## Usage

1. **Run the application** you just created
2. **Select a Quick Action** - Browse to your `.workflow` file (usually in `~/Library/Services/`)
3. **Choose a file type** - Select what kind of files this Quick Action should work with
4. **Optional: Move to context menu** - Choose whether to move it from Quick Actions submenu to main menu

### Example Use Cases

- Make a Quick Action that only appears on folders
- Create an action specifically for `.app` files
- Configure an action to work only with images
- Move frequently-used actions out of the Quick Actions submenu for faster access

## How It Works

The script modifies two key properties in the Quick Action's `Info.plist`:

1. **`NSSendFileTypes`** - Defines which file types the action accepts (using UTI - Uniform Type Identifiers)
2. **`NSIconName`** - Removing this moves the action from Quick Actions submenu to main context menu

This is based on [Erik Johnson's solution](https://apple.stackexchange.com/questions/445872/is-it-possible-to-move-quick-action-from-the-separate-tab-directly-to-context-me/453044#453044) for context menu placement.

## Requirements

- macOS 10.10 (Yosemite) or later
- Quick Actions/Automator workflows (`.workflow` files)

## Notes

- After running the script, you may need to **log out and back in** or run `killall Finder` in Terminal for changes to take effect
- The script defaults to browsing `~/Library/Services/` but can select workflows from anywhere
- You can run the script multiple times to reconfigure the same Quick Action

## Troubleshooting

**Changes not appearing?**
- Try running `killall Finder` in Terminal
- Log out and back in
- Restart your Mac

**Quick Action not showing up?**
- Make sure you're right-clicking on the correct file type
- Check that the Quick Action is enabled in System Settings → Extensions → Finder

## Technical Details

### Uniform Type Identifiers (UTIs) Used

| File Type | UTI |
|-----------|-----|
| Folders | `public.folder` |
| Files | `public.data` |
| Text Files | `public.text` |
| Images | `public.image` |
| PDFs | `com.adobe.pdf` |
| URLs | `public.url` |
| Audio | `public.audio` |
| Video | `public.movie` |
| Applications | `com.apple.application-bundle` |
| Documents | `public.content` |
| Archives | `public.archive` |
| Source Code | `public.source-code` |
| Shell Scripts | `public.shell-script` |
| Disk Images | `com.apple.disk-image` |

## Contributing

Feel free to submit issues or pull requests if you'd like to:
- Add more file type options
- Improve the user interface
- Fix bugs
- Add new features

## License

MIT License - feel free to use and modify as needed.

## Credits

- Context menu placement technique based on [Erik Johnson's Stack Exchange answer](https://apple.stackexchange.com/questions/445872/is-it-possible-to-move-quick-action-from-the-separate-tab-directly-to-context-me/453044#453044)

## Changelog

### Version 1.0
- Initial release
- File type configuration support
- Optional context menu placement
- Support for 14 common file types
