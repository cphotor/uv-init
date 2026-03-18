# pye

**Version:** 1.1.1  
**Language:** English | [中文](README.zh.md)

A Python development environment configuration script that automatically sets up a complete coding environment with modern tooling.

## Features

- ⚙️ Automatic Ruff configuration (code formatting and linting)
- 📝 Automatic Pyright configuration (type checking)
- 💻 Automatic VS Code/Windsurf settings
-  Smart configuration updates (no duplicates)
-  Auto-detect Python version from project
- 🎯 One-click development environment setup
- 🔧 Works with any Python project (uv, pip, poetry, etc.)

**Recommended**: This script is designed to work seamlessly with [uv](https://github.com/astral-sh/uv), a modern Python package manager. While it supports any Python project structure, using uv provides the best experience for project initialization, dependency management, and virtual environment handling.

## Installation

1. Download the script:
```bash
curl -O https://raw.githubusercontent.com/yourusername/pye/main/pye
```

2. Make it executable:
```bash
chmod +x pye
```

3. Move to system path (optional):
```bash
mv pye ~/.local/bin/
```

## Usage

### Basic Usage

```bash
# Configure current directory
pye

# Configure specific project directory
pye /path/to/my-project

# Configure code line length (default: 88, PEP 8 standard)
# Recommended values:
#   --pep8     : 88 characters (PEP 8 standard, default)
#   --github   : 100 characters (GitHub standard)
#   --wide     : 120 characters (wide screen mode)
pye --pep8
pye --github
pye --wide

# Combine options
pye --github /path/to/my-project

# Show help
pye -H

# Show version
pye -V
```

### Typical Workflow

```bash
# 1. Create a new project (using uv, pip, poetry, etc.)
uv init my-project
cd my-project

# 2. Configure development environment
pye

# 3. Create virtual environment
uv venv

# 4. Activate environment
source .venv/bin/activate

# 5. Install dependencies
uv add .  # or uv add <package-name>, or use 'uv sync' to install configured dependencies

# 6. Start coding!
```

## Automatic Configurations

### 1. VS Code/Windsurf Configuration (`.vscode/settings.json`)
- Python formatting with Ruff
- Enable format on save
- Configure auto-organize imports and fix issues on save

### 2. VS Code/Windsurf Extensions (`.vscode/extensions.json`)
- Auto-recommend Python extension (auto-selects Pylance/Pyright)
- Auto-recommend Ruff extension for formatting

### 3. Pyright Configuration (`pyrightconfig.json`)
- Auto-detect Python version from project
- Standard type checking mode
- Optimized error reporting configuration

### 4. Ruff Configuration (appended to `pyproject.toml`)
- Code line length limit: **88 characters** (configurable with `--pep8`, `--github`, `--wide`)
  - `--pep8`: 88 characters (PEP 8 standard, default)
  - `--github`: 100 characters (GitHub standard)
  - `--wide`: 120 characters (wide screen mode)
- Target Python version: auto-detect
- Comprehensive code checking rules
- Auto-fix all fixable issues

### 5. VS Code/Windsurf Environment Settings (in `pyproject.toml`)
- Virtual environment search paths
- Terminal auto-activation
- Shell startup activation for better Copilot support

## Python Version Detection

The script automatically detects Python version from:

1. `pyproject.toml` → `requires-python` field
2. `.python-version` file
3. `uv python list` (active version)
4. Falls back to `3.13` if detection fails

## Requirements

- Python 3.8+ (3.11+ recommended)
- Bash shell environment (built-in on macOS/Linux)
- Optional: [uv](https://github.com/astral-sh/uv) - Recommended Python project manager

## VS Code Plugins

**For VS Code users**, we recommend installing these plugins:
- **Ruff**: `charliermarsh.ruff`
- **Pylance**: `ms-python.vscode-pylance`

**For Windsurf users**, we recommend:
- **Ruff**: `charliermarsh.ruff`
- **Windsurf Pyright**: (built-in, but check for updates to get the latest features)

## License

MIT License - see [LICENSE](LICENSE) file for details

## Contributing

Issues and Pull Requests are welcome!

## Why choose this script?

Setting up a Python development environment manually can be time-consuming. This script:

1. **Saves time**: No manual configuration needed
2. **Smart updates**: Detects and updates existing configurations without creating duplicates
3. **Best practices**: Pre-configured with modern Python development standards
4. **Tool integration**: Perfect integration with VS Code/Windsurf, Ruff, Pyright
5. **Universal**: Works with any Python project setup
6. **Idempotent**: Safe to run multiple times - always ensures correct configuration

Focus on coding, not environment configuration!
