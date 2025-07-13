# Claude Switcher

简单易用的Claude配置管理工具 - 让你轻松在不同环境下使用Claude

## 🌟 特性

- 🚀 **一键启动** - 运行 `claude-switcher` 即可开始使用
- 📋 **配置管理** - 创建和管理多个Claude配置
- 🔄 **快速切换** - 自动记住上次使用的配置，按回车快速启动  
- 🌍 **IP检查** - 启动前自动检查出口IP地址
- 🔒 **安全存储** - 配置文件权限保护
- 🎯 **默认选项** - 所有菜单支持默认选项，按回车选择最常用操作
- 💡 **灵活配置** - 支持空Token配置，便于创建模板和测试

## 📦 安装

### 一键安装
```bash
curl -sSL https://raw.githubusercontent.com/fiftyk/claude-switcher/main/install.sh | bash
```

### 手动安装
```bash
# 下载脚本
curl -L https://raw.githubusercontent.com/fiftyk/claude-switcher/main/claude-switcher.sh -o claude-switcher.sh

# 设置权限并安装
chmod +x claude-switcher.sh
sudo mv claude-switcher.sh /usr/local/bin/claude-switcher
```

## 🚀 使用方法

### 启动程序
```bash
claude-switcher
```

### 操作流程

1. **首次运行** - 会显示配置选择界面
2. **快速启动** - 再次运行时显示上次使用的配置，按回车即可快速启动  
3. **配置管理** - 选择已有配置后可以启动、编辑或删除，按回车默认启动
4. **创建配置** - 按提示依次输入配置信息，所有字段都可留空
5. **一键启动** - 所有菜单都支持默认选项，直接按回车选择最常用操作

### 交互界面示例

#### 快速启动（再次运行时）
```
=== 快速启动 ===
  上次使用: "我的工作配置"

  1 继续使用"我的工作配置"
  2 选择其他配置
  3 退出

请选择 [1-3] (默认: 1):   # 直接按回车启动
```

#### 首次运行/选择其他配置
```
=== 可用配置 ===
  1 使用"anyrouter配置"
  2 使用"代理配置"  
  3 创建新配置
  4 退出

请选择配置 [1-4]:
```

#### 配置操作
```
=== 配置: anyrouter配置 ===
ℹ 配置概要:
  Base URL: https://anyrouter.top
  Auth Token: sk-ant***
  代理: 未设置

选择操作:
  1 启动 Claude
  2 查看/编辑配置
  3 删除此配置
  4 返回主菜单
  5 退出

请选择 [1-5] (默认: 1):   # 直接按回车启动
```

## 📝 配置文件格式

配置文件使用简单的 Shell 变量格式：

```bash
# Claude Switcher 配置文件
NAME="我的anyrouter配置"
ANTHROPIC_AUTH_TOKEN="sk-ant-xxxx"
ANTHROPIC_BASE_URL="https://anyrouter.top"
http_proxy="http://127.0.0.1:7890"
https_proxy="http://127.0.0.1:7890"
```

## 🔧 创建配置流程

运行程序后选择"创建新配置"，然后按提示输入：

1. **配置名称** - 给配置起个名字，如 "work", "home"
2. **ANTHROPIC_BASE_URL** - API端点，留空使用默认
3. **ANTHROPIC_AUTH_TOKEN** - 你的Claude认证Token，可留空后续编辑
4. **代理设置** - 代理地址，留空不使用代理

**说明：所有字段都可以留空，方便创建配置模板或占位配置。**

## 🌍 常用配置示例

### anyrouter配置
- **Base URL**: `https://anyrouter.top`
- **Token**: 你的anyrouter token
- **代理**: 留空

### 代理配置  
- **Base URL**: 留空(使用默认)
- **Token**: 你的官方Claude token
- **代理**: `http://127.0.0.1:7890`

### 直连配置
- **Base URL**: 留空(使用默认)  
- **Token**: 你的官方Claude token
- **代理**: 留空

## 📁 文件位置

- 配置目录: `~/.claude-switcher/`
- 配置文件: `~/.claude-switcher/profiles/*.conf`

## 🔒 安全说明

- 配置文件权限设置为 600 (仅用户可读写)
- Token 在界面中显示时自动掩码
- 启动前保存原环境变量，退出后自动恢复

## 📋 系统要求

- macOS 或 Linux
- bash, curl 
- Claude CLI (用于启动Claude)

## 🔄 从旧版本迁移

如果你之前使用的是 `claude-proxy-checker`，安装脚本会自动检测并提示删除：

```bash
# 一键安装 - 会自动检测旧版本
curl -sSL https://raw.githubusercontent.com/fiftyk/claude-switcher/main/install.sh | bash
```

安装时会提示：
- 是否删除旧的 `claude-proxy-checker` 脚本
- 是否删除旧的配置文件 `~/.claude_proxy_config`

**手动迁移配置：**
如果保留了旧配置文件，可以手动创建对应的新配置：

```bash
# 查看旧配置
cat ~/.claude_proxy_config

# 创建对应的新配置
claude-switcher  # 选择"创建新配置"
```

## 🛠️ 故障排除

### Claude CLI 未安装
```bash
# 安装Claude CLI
# 访问: https://github.com/anthropics/claude-cli
```

### 配置文件问题
配置文件位于 `~/.claude-switcher/profiles/`，可以手动编辑或删除

### 重新安装
```bash
# 删除旧版本
sudo rm -f /usr/local/bin/claude-switcher

# 重新安装
curl -sSL https://raw.githubusercontent.com/fiftyk/claude-switcher/main/install.sh | bash
```

## 📄 许可证

MIT License

---

**简单、直观、好用！** 🎯