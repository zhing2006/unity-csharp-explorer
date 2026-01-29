# unity-csharp-explorer

> A Claude Code agent that helps you explore Unity Engine C# source code (UnityCsReference) and Unity Packages source code (Library/PackageCache, Packages). It can find class definitions, trace implementations, and understand Unity's internal APIs.

I want you to install unity-csharp-explorer agent for me. Execute all the steps below autonomously.

## OBJECTIVE

Install the unity-csharp-explorer agent file to the user's project directory so it becomes available in Claude Code, Cursor, and other AI coding tools.

## DONE WHEN

- The file `.claude/agents/unity-csharp-explorer.md` exists
- The user has been informed to restart their AI tool

## TODO

- [ ] Check if git is installed
- [ ] Get the latest tag from the repository
- [ ] Create the target directory
- [ ] Download the agent file directly to the target location
- [ ] Verify and inform the user

## Steps

### Step 1: Check if git is installed

You need to verify that git is available on the system.

```bash
git --version
```

If git is not installed, stop and tell the user:

> "Git is not installed. Please install git first and try again."
>
> - Windows: <https://git-scm.com/download/win>
> - macOS: `brew install git` or `xcode-select --install`
> - Linux: `sudo apt install git` or `sudo yum install git`

### Step 2: Get the latest tag from the repository

You need to fetch the latest release tag from the repository.

```bash
git ls-remote --tags --sort=-v:refname https://github.com/zhing2006/unity-csharp-explorer.git | head -1 | sed 's/.*refs\/tags\///'
```

Store the result as `LATEST_TAG`. If no tags exist, use `main` branch instead.

### Step 3: Create the target directory

You need to ensure the target directory exists first.

```bash
mkdir -p .claude/agents
```

### Step 4: Download the agent file

You need to download the agent file directly to the target location.

```bash
curl -fsSL "https://raw.githubusercontent.com/zhing2006/unity-csharp-explorer/${LATEST_TAG}/.claude/agents/unity-csharp-explorer.md" -o .claude/agents/unity-csharp-explorer.md
```

### Step 5: Verify and inform the user

Verify the installation by checking the file exists:

```bash
cat .claude/agents/unity-csharp-explorer.md | head -10
```

Then tell the user:

> "unity-csharp-explorer agent has been installed successfully!"
>
> "Please restart your AI coding tool (Claude Code, Cursor, VS Code, etc.) to activate the agent."
>
> "After restart, the agent will automatically help you explore Unity C# source code when needed."

If the user is communicating in Chinese, respond in Chinese.
