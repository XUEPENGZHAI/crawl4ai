# Crawl4ai VSCode 配置说明

## 开发环境要求

- **Python**: 3.12.10
- **包管理器**: uv (推荐) 或 conda
- **VSCode 扩展**: 见 `extensions.json`

## 快速开始

### 使用 uv (推荐)

```bash
# 安装 uv (如果尚未安装)
pip install uv

# 安装 Python 3.12.10
uv python install 3.12.10

# 创建虚拟环境
uv venv --python 3.12.10

# 激活虚拟环境
# Windows:
.venv\Scripts\activate
# Linux/macOS:
source .venv/bin/activate

# 同步依赖
uv sync
```

### 使用 conda (备选)

```bash
# 创建 conda 环境
conda create -n crawl4ai -c conda-forge python=3.12.10

# 激活环境
conda activate crawl4ai

# 安装依赖
pip install -r requirements.txt
```

如果使用 conda，需要修改 `.vscode/settings.json` 中的解释器路径：

```json
// 注释掉 uv 路径
// "python.defaultInterpreterPath": "${workspaceFolder}/.venv/Scripts/python.exe",

// 取消注释 conda 路径并修改为你的实际路径
"python.defaultInterpreterPath": "C:/Users/YOUR_USERNAME/anaconda3/envs/crawl4ai/python.exe",
```

## VSCode 配置说明

### 已启用功能

- ✅ 自动格式化 (Black, line-length=100)
- ✅ 代码检查 (Flake8, mypy)
- ✅ 自动导入排序
- ✅ 测试支持 (pytest)
- ✅ 保存时格式化
- ✅ 智能代码补全 (Pylance)

### 推荐扩展

打开 VSCode 后，会自动提示安装推荐扩展。主要包括：

- Python (ms-python.python)
- Pylance (ms-python.vscode-pylance)
- Black Formatter (ms-python.black-formatter)
- Flake8 (ms-python.flake8)
- mypy (ms-python.mypy-type-checker)

## 常见问题

### 1. 解释器未找到

按 `Ctrl+Shift+P` (Windows) 或 `Cmd+Shift+P` (macOS)，输入 "Python: Select Interpreter"，选择正确的虚拟环境。

### 2. 格式化不工作

确保已安装 Black Formatter 扩展，并在虚拟环境中安装了 black：

```bash
pip install black
```

### 3. Linting 不工作

确保已安装 Flake8 和 mypy：

```bash
pip install flake8 mypy
```

## 项目结构

```
crawl4ai/
├── .venv/              # uv 虚拟环境
├── .vscode/            # VSCode 配置 (团队共享)
├── crawl4ai/           # 主要源代码
├── tests/              # 测试文件
├── pyproject.toml      # 项目配置
├── requirements.txt    # 依赖列表
└── uv.lock            # uv 锁文件
```

## 开发工作流

1. 激活虚拟环境
2. 在 VSCode 中打开项目
3. 编写代码（自动格式化和检查）
4. 运行测试：`pytest tests/`
5. 提交代码

---

**最后更新**: 2025-11-20
