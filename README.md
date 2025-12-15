# Ask Continue - Windsurf对话持续工具

AI对话持续工具：智能提示词增强（结合上下文和内存记忆）、**队列模式连续对话**、账号管理无感切号、重置机器码、内置MCP服务器、音效提醒、跨平台支持。

👤免费一天试用授权码：AAA6-5V5J-J7H4-SXHA-9XGW-L3SA、AAA6-A2L2-PP39-2M9G-MNBZ-VP2A

## 功能特性

### 🎯 核心功能
- 🔄 **对话持续管理** - 自动询问用户是否继续对话，避免任务中断
- 📋 **队列模式（连续对话）** - 高效批量任务执行
  - 进入队列模式后保持MCP连接，无需重复调用工具
  - 支持任务队列：AI执行中可预添加多个任务
  - 智能调度：AI空闲时直接发送，执行中自动排队
  - 队列管理：支持删除、调整优先级
  - 面板可隐藏到状态栏，随时恢复
- 📝 **智能提示词增强** - 结合上下文和内存记忆，优化用户指令
  - 支持自定义角色模板（开发工程师、架构师、测试工程师等）
  - 自动检索历史记忆和项目上下文
  - 生成更精准、可执行的提示词
- 👤 **账号管理** - Windsurf账号无感切号
  - 支持添加、删除、批量导入账号
  - 密码加密存储，跨平台同步
  - 一键切换账号，无需手动登录
- 🔔 **音效提醒** - 对话框弹出时播放提示音
  - 8种预设音效可选
  - 支持启用/禁用
- 🔄 **重置机器码** - 一键重置设备标识
  - 重置 Windsurf 配置文件中的机器码
  - 支持重置 Windows 注册表 MachineGuid（需管理员权限）

### 🛠️ 技术特性
- 🖼️ 支持上传图片（截图粘贴、文件选择）
- 🖥️ 内置 MCP 服务器（HTTP + stdio 双模式）
- 🌍 跨平台支持（Windows、Linux、macOS）

## 系统要求

### Windows
- Node.js 18+（用于 MCP stdio 模式）

### Linux
- Node.js 18+
- 对话框工具（至少安装其中一个）：
  - `zenity`（GNOME 桌面，推荐）
  - `kdialog`（KDE 桌面）
  - `yad`（通用）

#### Linux 依赖安装

**Ubuntu/Debian:**
```bash
# 安装 Node.js
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# 安装对话框工具（选择一个）
sudo apt-get install -y zenity  # GNOME
# 或
sudo apt-get install -y kdialog  # KDE
```

**CentOS/RHEL/Fedora:**
```bash
# 安装 Node.js
curl -fsSL https://rpm.nodesource.com/setup_20.x | sudo bash -
sudo yum install -y nodejs

# 安装对话框工具
sudo yum install -y zenity
```

**Arch Linux:**
```bash
sudo pacman -S nodejs npm zenity
```

### macOS
- Node.js 18+
- 可选：`zenity`（通过 Homebrew 安装）

## 安装

1. 从 VSCode 扩展市场安装，或手动安装 `.vsix` 文件
2. 重启 VSCode/Cursor/Windsurf

## 配置 MCP

### 方法一：自动配置（推荐）
1. 点击侧边栏的 "Ask Continue" 图标
2. 点击 "🔧 配置 MCP" 按钮
3. 选择要配置的 AI 工具

### 方法二：手动配置

**Windsurf** (`~/.codeium/windsurf/mcp_config.json`):
```json
{
  "mcpServers": {
    "ask_continue": {
      "command": "node",
      "args": ["/path/to/extension/mcp-server.js"]
    }
  }
}
```

**Cursor** (`.cursor/mcp.json`):
```json
{
  "mcpServers": {
    "ask_continue": {
      "command": "node",
      "args": ["/path/to/extension/mcp-server.js"]
    }
  }
}
```

## 故障排除

### Linux: "node: executable file not found in $PATH"

确保 Node.js 正确安装并在 PATH 中：
```bash
# 检查 node 是否可用
which node
node --version

# 如果 node 不在 PATH 中，添加到 ~/.bashrc 或 ~/.profile
export PATH=$PATH:/path/to/node/bin
```

### Linux: 对话框不显示

确保安装了 zenity 或 kdialog：
```bash
# 检查
which zenity || which kdialog

# 安装
sudo apt-get install zenity  # Debian/Ubuntu
```

