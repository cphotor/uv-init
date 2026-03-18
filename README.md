# pye

**Version:** 1.1.7  
**Language:** English | [中文](README.zh.md)

A Python development environment configuration script that automatically sets up a complete coding environment with modern tooling.

## Features

- ⚙️ Automatic Ruff configuration (code formatting and linting)
- 📝 Automatic Pyright configuration (type checking)
- 💻 Automatic VS Code/Windsurf settings
- 🔄 Smart configuration updates (no duplicates)
- 🐍 Auto-detect Python version from project
- 🎯 One-click development environment setup
- 🔧 Compatible with any Python project structure
- 📜 Automatic `.gitignore` configuration with comprehensive Python development patterns

-**Recommended**: This script is designed to work seamlessly with [uv](https://github.com/astral-sh/uv), a modern Python package manager. While it supports any Python project structure, using uv provides the best experience for project initialization, dependency management, and virtual environment handling.
+**Note**: This script requires [uv](https://github.com/astral-sh/uv) to be installed, as it uses `uv venv` to create virtual environments. uv is a modern Python package manager that provides excellent project management capabilities.

## Installation

1. Download the script:
```bash
curl -O https://raw.githubusercontent.com/cphotor/pye/main/pye
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
# 1. Create a new project
uv init my-project
cd my-project

# 2. Configure development environment (auto-creates venv and installs toolchain)
pye

# 3. Start coding!
```

**Note**: 
- Use `uv run <script.py>` to run Python scripts directly in the virtual environment
- Use `uv add <package-name>` to add third-party dependencies when needed (e.g., `uv add requests`)

## Automatic Configurations

### 1. VS Code/Windsurf Configuration (`.vscode/settings.json`)
- Python formatting with Ruff
- Enable format on save
- Configure auto-organize imports and fix issues on save
- Configure auto-delay save: Automatically saves files after 1 second of modification (`files.autoSave: afterDelay`, `files.autoSaveDelay: 1000`)

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

### 6. `.gitignore` Configuration
- Auto-create or update `.gitignore` with comprehensive Python development patterns:
  - `.ruff_cache/` - Ruff cache directory
  - `.vscode/` user-specific files only (`settings.json.user`, `workspace.xml`, `*.lock`)
  - Python development artifacts (`__pycache__/`, `*.pyc`, `build/`, `dist/`, etc.)
  - Virtual environments (`.venv/`, `venv/`, `ENV/`, etc.)
  - Test and coverage caches (`.pytest_cache/`, `.coverage`, `htmlcov/`, etc.)
- Smart merge: preserves existing custom entries, only adds missing patterns
- Project-friendly: keeps `.vscode/settings.json` and `.vscode/extensions.json` under version control

## Python Version Detection

The script automatically detects Python version from:

1. `pyproject.toml` → `requires-python` field
2. `.python-version` file
3. `uv python list` (active version)
4. Falls back to `3.13` if detection fails

## Requirements

- Python 3.8+ (3.11+ recommended)
- Bash shell environment (built-in on macOS/Linux)
-**Required**: [uv](https://github.com/astral-sh/uv) - Modern Python package manager (used for virtual environment creation and project management)