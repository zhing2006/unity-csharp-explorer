# Unity C# Explorer

[English](README.md) | [中文](README_CN.md)

A custom agent for exploring Unity Engine C# source code from the [UnityCsReference](https://github.com/Unity-Technologies/UnityCsReference) repository and Unity Packages source code from `Library/PackageCache` and `Packages` directories.

## Features

- Automatically clones the correct version of UnityCsReference based on your project's Unity version
- Explores Unity Packages source code (URP, HDRP, Input System, Addressables, etc.)
- Global search across the entire Unity C# source tree
- Understands Unity's architecture: Component system, Serialization, Editor extensions, Native/Managed interop
- Provides file paths, code snippets, and explanations

## Installation

### AI-Assisted Installation (Recommended)

Simply paste the following command to your AI coding tool (Claude Code, Cursor, etc.):

```txt
Read https://raw.githubusercontent.com/zhing2006/unity-csharp-explorer/main/INSTALL.md and execute the installation steps.
```

### Manual Installation

Copy the agent file to your project:

```bash
mkdir -p .claude/agents
curl -fsSL "https://raw.githubusercontent.com/zhing2006/unity-csharp-explorer/main/.claude/agents/unity-csharp-explorer.md" -o .claude/agents/unity-csharp-explorer.md
```

Then restart your AI coding tool to activate the agent.

## Usage

The agent will be automatically invoked when you:

- Encounter Unity C# errors (missing methods, properties, or incorrect signatures)
- Ask about Unity API implementations
- Need to find class definitions or inheritance hierarchies
- Need to explore Unity Packages source code

### Example Queries

- "Where is MonoBehaviour defined?"
- "How does Transform.SetParent work internally?"
- "Find the implementation of SerializedProperty"
- "What methods does EditorWindow have?"
- "Show me the ScriptableRenderer implementation in URP"
- "How does InputAction work in Input System?"

## How It Works

1. **Ensures source availability**: Reads `ProjectSettings/ProjectVersion.txt` and clones the matching UnityCsReference tag
2. **Checks Packages availability**: Verifies `Library/PackageCache` exists for Package source exploration
3. **Global search**: Uses Grep/Glob to search the entire source tree
4. **Context analysis**: Reads source files and related classes
5. **Clear presentation**: Returns file paths, code snippets, and explanations

## Requirements

- Git installed and available in PATH
- A Unity project with `ProjectSettings/ProjectVersion.txt`
- For Packages exploration: Open the project with Unity Editor at least once

## Directory Structure

```txt
.claude/agents/
  unity-csharp-explorer.md    # The agent definition
docs/
  unity-csharp-explorer-cn.md # Chinese reference documentation
INSTALL.md                    # AI-executable installation instructions
UnityCsReference/             # Auto-cloned by agent (not included in this repo)
```

## Note

This repository does not include the UnityCsReference source code. The agent will automatically clone it from [Unity-Technologies/UnityCsReference](https://github.com/Unity-Technologies/UnityCsReference) when needed. The UnityCsReference is read-only reference code owned by Unity Technologies.

## License

Apache 2.0
