# Unity C# Explorer

[English](README.md) | [中文](README_CN.md)

A custom agent for exploring Unity Engine C# source code from the [UnityCsReference](https://github.com/Unity-Technologies/UnityCsReference) repository.

## Features

- Automatically clones the correct version of UnityCsReference based on your project's Unity version
- Global search across the entire Unity C# source tree
- Understands Unity's architecture: Component system, Serialization, Editor extensions, Native/Managed interop
- Provides file paths, code snippets, and explanations

## Installation

Copy the agent file to your project:

```bash
mkdir -p .claude/agents
cp .claude/agents/unity-csharp-explorer.md .claude/agents/
```

Or copy to your user directory for global access:

```bash
mkdir -p ~/.claude/agents
cp .claude/agents/unity-csharp-explorer.md ~/.claude/agents/
```

## Usage

The agent will be automatically invoked when you:

- Encounter Unity C# errors (missing methods, properties, or incorrect signatures)
- Ask about Unity API implementations
- Need to find class definitions or inheritance hierarchies

### Example Queries

- "Where is MonoBehaviour defined?"
- "How does Transform.SetParent work internally?"
- "Find the implementation of SerializedProperty"
- "What methods does EditorWindow have?"

## How It Works

1. **Ensures source availability**: Reads `ProjectSettings/ProjectVersion.txt` and clones the matching UnityCsReference tag
2. **Global search**: Uses Grep/Glob to search the entire source tree
3. **Context analysis**: Reads source files and related classes
4. **Clear presentation**: Returns file paths, code snippets, and explanations

## Requirements

- Git installed and available in PATH
- A Unity project with `ProjectSettings/ProjectVersion.txt`

## Directory Structure

```txt
.claude/agents/
  unity-csharp-explorer.md    # The agent definition
docs/
  unity-csharp-explorer-cn.md # Chinese reference documentation
UnityCsReference/             # Auto-cloned by agent (not included in this repo)
```

## Note

This repository does not include the UnityCsReference source code. The agent will automatically clone it from [Unity-Technologies/UnityCsReference](https://github.com/Unity-Technologies/UnityCsReference) when needed. The UnityCsReference is read-only reference code owned by Unity Technologies.

## License

Apache 2.0
