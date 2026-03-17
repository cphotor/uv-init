# pye

**Language:** English | [中文](README.zh.md)

A Python development environment configuration script that automatically sets up a complete coding environment with modern tooling.

## Features

- ⚙️ Automatic Ruff configuration (code formatting and linting)
- 📝 Automatic Pyright configuration (type checking)
- 💻 Automatic VS Code/Windsurf settings
- 🐍 Auto-detect Python version from project
- 🎯 One-click development environment setup
- 🔧 Works with any Python project (uv, pip, poetry, etc.)

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

# Show help
pye --help
```

### Typical Workflow

```bash
# 1. Create a new project (using uv, pip, poetry, etc.)
uv init my-project
cd my-project

# 2. Configure development environment
pye

# 3. Start coding!
```

## Automatic Configurations

### 1. VS Code/Windsurf Configuration (`.vscode/settings.json`)
- Configure Python virtual environment path
- Enable format on save
- Set Ruff as default formatter
- Configure auto-organize imports and fix issues on save

### 2. Pyright Configuration (`pyrightconfig.json`)
- Auto-detect Python version from project
- Standard type checking mode
- Optimized error reporting configuration

### 3. Ruff Configuration (appended to `pyproject.toml`)
- Code line length limit: 88 characters
- Target Python version: auto-detect
- Comprehensive code checking rules
- Auto-fix all fixable issues

## Python Version Detection

The script automatically detects Python version from:

1. `pyproject.toml` → `requires-python` field
2. `.python-version` file
3. `uv python list` (active version)
4. Falls back to `3.13` if detection fails

## Requirements

- Python 3.8+ (3.11+ recommended)
- A Python project with `pyproject.toml`

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
2. **Best practices**: Pre-configured with modern Python development standards
3. **Tool integration**: Perfect integration with VS Code/Windsurf, Ruff, Pyright
4. **Universal**: Works with any Python project setup

Focus on coding, not environment configuration!
