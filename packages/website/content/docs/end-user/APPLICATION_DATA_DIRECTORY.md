# Application Data Directory

The per-user application data directory is located in the following directory:

- `%APPDATA%\mytext` on Windows
- `$XDG_CONFIG_HOME/mytext` or `~/.config/mytext` on Linux
- `~/Library/Application Support/mytext` on macOS

When [portable mode](PORTABLE.md) is enabled, the directory location is either the `--user-data-dir` parameter or `mytext-user-data` directory.
