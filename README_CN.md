# Unity C# Explorer

[English](README.md) | [中文](README_CN.md)

一个用于探索 Unity 引擎 C# 源代码的自定义 Agent，支持 [UnityCsReference](https://github.com/Unity-Technologies/UnityCsReference) 仓库和 Unity Packages 源代码（`Library/PackageCache` 和 `Packages` 目录）。

## 功能特性

- 根据项目的 Unity 版本自动克隆对应版本的 UnityCsReference
- 探索 Unity Packages 源代码（URP、HDRP、Input System、Addressables 等）
- 在整个 Unity C# 源码树中进行全局搜索
- 理解 Unity 架构：组件系统、序列化、编辑器扩展、原生/托管互操作
- 提供文件路径、代码片段和解释说明

## 安装

### AI 辅助安装（推荐）

只需将以下命令粘贴到你的 AI 编程工具（Claude Code、Cursor 等）：

```txt
阅读 https://raw.githubusercontent.com/zhing2006/unity-csharp-explorer/main/INSTALL.md 并执行安装步骤。
```

### 手动安装

将 Agent 文件复制到你的项目中：

```bash
mkdir -p .claude/agents
curl -fsSL "https://raw.githubusercontent.com/zhing2006/unity-csharp-explorer/main/.claude/agents/unity-csharp-explorer.md" -o .claude/agents/unity-csharp-explorer.md
```

然后重启你的 AI 编程工具以激活 Agent。

## 使用方法

当你遇到以下情况时，Agent 会自动被调用：

- 遇到 Unity C# 错误（方法不存在、属性缺失或签名错误）
- 询问 Unity API 的实现细节
- 需要查找类定义或继承层次
- 需要探索 Unity Packages 源代码

### 示例查询

- "MonoBehaviour 在哪里定义的？"
- "Transform.SetParent 内部是怎么工作的？"
- "查找 SerializedProperty 的实现"
- "EditorWindow 有哪些方法？"
- "看看 URP 中 ScriptableRenderer 的实现"
- "Input System 的 InputAction 是怎么工作的？"

## 工作原理

1. **确保源码可用**：读取 `ProjectSettings/ProjectVersion.txt` 并克隆匹配的 UnityCsReference tag
2. **检查 Packages 可用性**：验证 `Library/PackageCache` 是否存在以支持 Package 源码探索
3. **全局搜索**：使用 Grep/Glob 在整个源码树中搜索
4. **上下文分析**：读取源文件和相关类
5. **清晰呈现**：返回文件路径、代码片段和解释说明

## 系统要求

- Git 已安装并在 PATH 中可用
- 包含 `ProjectSettings/ProjectVersion.txt` 的 Unity 项目
- 如需探索 Packages 源码：需要先用 Unity Editor 打开过项目

## 目录结构

```txt
.claude/agents/
  unity-csharp-explorer.md    # Agent 定义文件
docs/
  unity-csharp-explorer-cn.md # 中文参考文档
INSTALL.md                    # AI 可执行的安装说明
UnityCsReference/             # 由 Agent 自动克隆（不包含在本仓库中）
```

## 说明

本仓库不包含 UnityCsReference 源代码。Agent 会在需要时自动从 [Unity-Technologies/UnityCsReference](https://github.com/Unity-Technologies/UnityCsReference) 克隆。UnityCsReference 是 Unity Technologies 拥有的只读参考代码。

## 许可证

Apache 2.0
