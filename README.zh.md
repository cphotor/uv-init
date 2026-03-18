# pye

**版本：** 1.1.8  
**语言:** 中文 | [English](README.md)

一个 Python 开发环境配置脚本，自动设置完整的现代化编码环境。

## 功能特性

- ⚙️ 自动配置 Ruff（代码格式化和检查）
- 📝 自动配置 Pyright（类型检查）
- 💻 自动配置 VS Code/Windsurf 设置
- 🔄 智能配置更新（无重复）
- 🐍 从项目自动检测 Python 版本
- 🎯 一键设置开发环境
- 🔧 兼容任何 Python项目结构
- 📜 自动配置 `.gitignore`，包含全面的 Python 开发忽略模式

**注意**: 本脚本需要安装 [uv](https://github.com/astral-sh/uv)，因为它使用 `uv venv` 来创建虚拟环境。uv 是一个现代化的 Python 包管理器，提供出色的项目管理能力。

## 安装

1. 下载脚本：
```bash
curl -O https://raw.githubusercontent.com/cphotor/pye/main/pye
```

2. 添加执行权限：
```bash
chmod +x pye
```

3. 移动到系统路径（可选）：
```bash
mv pye ~/.local/bin/
```

## 使用方法

### 基本用法

```bash
# 配置当前目录
pye

# 配置指定项目目录
pye /path/to/my-project

# 配置代码行长度（默认：88，PEP 8 标准）
# 推荐值：
#   --pep8     : 88 字符（PEP 8 标准，默认）
#   --github   : 100 字符（GitHub 标准）
#   --wide     : 120 字符（宽屏模式）
pye --pep8
pye --github
pye --wide

# 组合使用选项
pye --github /path/to/my-project

# 显示帮助
pye -H

# 显示版本
pye -V
```

### 典型工作流程

```bash
# 1. 创建新项目
uv init my-project
cd my-project

# 2. 配置开发环境（自动创建虚拟环境、安装工具链）
pye

# 3. 开始编码！
```

**提示**: 
- 使用 `uv run <script.py>` 可以直接在虚拟环境中运行 Python 脚本
- 需要添加第三方依赖时，使用 `uv add <package-name>`（如 `uv add requests`）

## 自动配置的内容

### 1. VS Code/Windsurf 配置 (`.vscode/settings.json`)
- Python 格式化配置（使用 Ruff）
- 启用保存时格式化
- 配置保存时自动整理导入和修复问题
- 配置自动延时保存：修改后 1 秒自动保存文件（`files.autoSave: afterDelay`, `files.autoSaveDelay: 1000`）

### 2. VS Code/Windsurf 扩展 (`.vscode/extensions.json`)
- 自动推荐 Python 扩展（自动选择 Pylance/Pyright）
- 自动推荐 Ruff 扩展用于格式化

### 3. Pyright 配置 (`pyrightconfig.json`)
- 从项目自动检测 Python 版本
- 标准类型检查模式
- 优化的错误报告配置

### 4. Ruff 配置 (追加到 `pyproject.toml`)
- 代码行长度限制：**88 字符**（可通过 `--pep8`、`--github`、`--wide` 参数自定义）
  - `--pep8`: 88 字符（PEP 8 标准，默认）
  - `--github`: 100 字符（GitHub 标准）
  - `--wide`: 120 字符（宽屏模式）
- 目标 Python 版本：自动检测
- 全面的代码检查规则
- 自动修复所有可修复的问题

### 5. VS Code/Windsurf 环境设置 (在 `pyproject.toml` 中)
- 虚拟环境搜索路径
- 终端自动激活
- Shell 启动激活以获得更好的 Copilot 支持

### 6. `.gitignore` 配置
- 自动创建或更新 `.gitignore`，包含全面的 Python 开发忽略模式：
  - `.ruff_cache/` - Ruff 缓存目录
  - `.vscode/` 仅用户特定文件（`settings.json.user`、`workspace.xml`、`*.lock`）
  - Python 开发产物（`__pycache__/`、`*.pyc`、`build/`、`dist/` 等）
  - 虚拟环境（`.venv/`、`venv/`、`ENV/` 等）
  - 测试和覆盖率缓存（`.pytest_cache/`、`.coverage`、`htmlcov/` 等）
- 智能合并：保留现有的自定义条目，仅添加缺失的模式
- 项目友好：保持 `.vscode/settings.json` 和 `.vscode/extensions.json` 纳入版本控制

## 系统要求

- Python 3.8+（推荐 3.11+）
- Bash shell 环境（macOS/Linux 自带）
-**必需**: [uv](https://github.com/astral-sh/uv) - 现代化 Python 包管理器（用于创建虚拟环境和管理项目）

## VS Code 插件

**VS Code 用户**推荐安装以下插件：
- **Ruff**: `charliermarsh.ruff`
- **Pylance**: `ms-python.vscode-pylance`

**Windsurf 用户**推荐安装：
- **Ruff**: `charliermarsh.ruff`
- **Windsurf Pyright**: (内置，但建议检查更新以获得最新功能)

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

## 贡献

欢迎提交 Issue 和 Pull Request！

## 为什么选择这个脚本？

手动设置 Python 开发环境可能很耗时。这个脚本：

1. **节省时间**：无需手动配置
2. **智能更新**：检测并更新现有配置，不会创建重复内容
3. **最佳实践**：预设了现代 Python 开发的最佳配置
4. **工具集成**：完美集成 VS Code/Windsurf、Ruff、Pyright
5. **通用性**：适用于任何 Python 项目设置
6. **幂等性**：可以安全地多次运行 - 始终确保配置正确

让您专注于编码，而不是环境配置！
