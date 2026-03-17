# pyenv

一个 Python 开发环境配置脚本，自动设置完整的现代化编码环境。

## 功能特性

- ⚙️ 自动配置 Ruff（代码格式化和检查）
- 📝 自动配置 Pyright（类型检查）
- 💻 自动配置 VS Code/Windsurf 设置
- 🐍 从项目自动检测 Python 版本
- 🎯 一键设置开发环境
- 🔧 适用于任何 Python 项目（uv、pip、poetry 等）

## 安装

1. 下载脚本：
```bash
curl -O https://raw.githubusercontent.com/yourusername/pydev/main/pydev
```

2. 添加执行权限：
```bash
chmod +x pydev
```

3. 移动到系统路径（可选）：
```bash
mv pydev ~/.local/bin/
```

## 使用方法

### 基本用法

```bash
# 配置当前目录
pydev

# 配置指定项目目录
pydev /path/to/my-project

# 显示帮助
pydev --help
```

### 典型工作流程

```bash
# 1. 创建新项目（使用 uv、pip、poetry 等）
uv init my-project
cd my-project

# 2. 配置开发环境
pydev

# 3. 开始编码！
```

## 自动配置的内容

### 1. VS Code/Windsurf 配置 (`.vscode/settings.json`)
- 配置 Python 虚拟环境路径
- 启用保存时格式化
- 设置 Ruff 为默认格式化工具
- 配置保存时自动整理导入和修复问题

### 2. Pyright 配置 (`pyrightconfig.json`)
- 从项目自动检测 Python 版本
- 标准类型检查模式
- 优化的错误报告配置

### 3. Ruff 配置 (追加到 `pyproject.toml`)
- 代码行长度限制：88 字符
- 目标 Python 版本：自动检测
- 全面的代码检查规则
- 自动修复所有可修复的问题

## 示例

创建一个名为 `my-app` 的项目：

```bash
uv-init my-app
cd my-app
```

这将创建：
- 完整的 Python 项目结构
- 配置好的开发环境
- 可以直接开始编码的环境

## 依赖要求

- [uv](https://github.com/astral-sh/uv): Python 包管理工具
- Python 3.8+（推荐 3.11+）

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

## 贡献

欢迎提交 Issue 和 Pull Request！

## 为什么选择这个脚本？

标准的 `uv init` 只创建基本的项目结构，这个脚本在此基础上：

1. **开箱即用**：无需手动配置开发环境
2. **最佳实践**：预设了现代 Python 开发的最佳配置
3. **工具集成**：完美集成 VS Code、Ruff、Pyright
4. **灵活配置**：支持不同类型的项目和 Python 版本

让您专注于编码，而不是环境配置！

---

**Language:** 中文 | [English](README.md)
