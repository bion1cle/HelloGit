# CLAUDE.md

This file provides guidance for AI assistants working with this repository.

## Repository Overview

HelloGit is a minimal C# console application ("Hello World") created as a Git learning/demonstration project. It was originally created with Visual Studio 2013 targeting .NET Framework 4.5.

## Repository Structure

```
HelloGit/
├── README.md                          # Minimal project readme
├── CLAUDE.md                          # This file
└── HelloGitWorld/
    ├── HelloGitWorld.sln              # Visual Studio 2013 solution file
    └── Hello/
        ├── Hello.csproj               # MSBuild project file (ToolsVersion 12.0, .NET 4.5)
        ├── App.config                 # Application config (targets .NET 4.5 runtime)
        ├── Program.cs                 # Entry point - prints "Hello world" and current directory
        └── Properties/
            └── AssemblyInfo.cs        # Assembly metadata (version 1.0.0.0, copyright 2014)
```

## Key Files

- **`HelloGitWorld/Hello/Program.cs`**: The sole application source file. Contains a `Main` method in the `Hello` namespace that writes `"Hello world"` and the current working directory to stdout.
- **`HelloGitWorld/HelloGitWorld.sln`**: Solution file for Visual Studio 2013 (Format Version 12.00). References the single `Hello` project by GUID `{05786FE7-3D7F-42ED-9464-C3BF8043FE7F}`.
- **`HelloGitWorld/Hello/Hello.csproj`**: MSBuild project targeting `v4.5`. Output type is `Exe`. Defines `Debug` and `Release` configurations targeting `AnyCPU`.

## Build & Run

This project uses the classic MSBuild/Visual Studio project format. There is no modern `dotnet` SDK-style project file.

**Build (requires .NET Framework / Mono or MSBuild):**
```bash
# With Mono on Linux
msbuild HelloGitWorld/HelloGitWorld.sln /p:Configuration=Debug

# With Visual Studio on Windows: open HelloGitWorld/HelloGitWorld.sln and build normally
```

**Run:**
```bash
# After building, the output lands in Hello/bin/Debug/ (or Release/)
mono HelloGitWorld/Hello/bin/Debug/Hello.exe
```

Expected output:
```
Hello world
<current working directory>
```

## Build Configurations

| Configuration | Output path              | Optimized | Debug symbols |
|---------------|--------------------------|-----------|---------------|
| Debug         | `Hello/bin/Debug/`       | No        | Full PDB      |
| Release       | `Hello/bin/Release/`     | Yes       | PDB-only      |

Both configurations target `AnyCPU` platform.

## Git Conventions

- **Main branch**: `master`
- **Feature/AI branches**: follow the pattern `claude/<description>-<id>` (e.g., `claude/add-claude-documentation-iyd2h`)
- Commit messages are short and descriptive (see history: "Initial commit", "1", "Update Program.cs")

## Development Notes for AI Assistants

- The project is intentionally minimal; avoid over-engineering changes.
- There are no tests, linters, or CI pipelines configured.
- The solution file and `.csproj` use the legacy MSBuild XML format — do not convert to SDK-style unless explicitly requested.
- Assembly metadata lives in `Properties/AssemblyInfo.cs`; update version numbers there when relevant.
- `App.config` only declares the supported .NET runtime; no application-specific configuration exists.
- When making changes, prefer editing existing files over creating new ones.
