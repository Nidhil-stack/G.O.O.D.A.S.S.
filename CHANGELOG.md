# Changelog

## Version 0.1.1

### ✨ New Features

#### Tab Autocomplete Support
- **Settings Menu**: Added tab completion for SSH private key path selection with full filesystem navigation
- **Host Management**: Added tab completion for removing hosts with `user@host` format support
- **User Management**: Added tab completion for user email selection in all user management operations
- **Key Access Management**: Added tab completion for removing access entries in the deepest layer of user key access management

### 🔧 Improvements

#### Code Refactoring
- **New `autocomplete.py` module**: Centralized tab-completion functionality with:
  - Path completion for filesystem navigation
  - List-based completion for predefined options
  - Multi-word completion support (e.g., `remove user@host`)
  - Windows compatibility (graceful fallback when readline is unavailable)

- **New `utils.py` module**: Extracted utility functions from cli.py:
  - `signal_handler` - Graceful Ctrl+C handling
  - `exit_gracefully` - Clean temporary file removal on exit
  - `generate_ssh_keypair` - SSH keypair generation

- **New `settingsManager.py` module**: Extracted settings management from cli.py:
  - `settings_cli` - Main settings menu
  - `edit_ssh_private_key_path` - Edit SSH key path with tab completion
  - `edit_verbosity` - Edit verbosity level
  - `edit_max_threads_per_host` - Edit concurrent thread limit

- **Updated `keyManager.py`**: Added `non_interactive_fix_keys()` function

- **Slimmed `cli.py`**: Reduced from ~470 lines to ~190 lines through modularization

### 📝 Usage Notes

#### Autocomplete
- Press `Tab` to cycle through available completions when prompted
- Autocomplete for hosts and key access is only available for **removal** operations (not adding new entries)
- Path completion supports `~` expansion and directory navigation

### 🔄 Compatibility
- Autocomplete requires the `readline` module (included by default on Linux/macOS)
- On Windows, the application gracefully falls back to standard input without completion
