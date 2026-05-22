# 01_REPO_MAP.md — AutoGen Repository Map

## Directory Structure
```
autogen/
├── .github/
│   ├── ISSUE_TEMPLATE/     # Issue templates (bug, doc, maintainer)
│   └── workflows/          # CI/CD workflows
├── docs/                   # Top-level documentation
├── dotnet/                 # .NET implementation
├── protos/                 # Protocol Buffer definitions
├── python/                 # Main Python implementation
│   ├── docs/               # Sphinx documentation source
│   ├── packages/           # Python packages (see below)
│   ├── samples/            # Example scripts
│   ├── templates/          # Package templates
│   ├── pyproject.toml      # Workspace root config
│   └── README.md           # Development guide
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── FAQ.md
├── LICENSE
├── README.md
├── SECURITY.md
├── SUPPORT.md
└── TRANSPARENCY_FAQS.md
```

## Python Packages

### autogen-core
- **Path**: `python/packages/autogen-core/`
- **Purpose**: Interface definitions, agent runtime, model/tool/workbench/memory/tracing implementations
- **CI Tests**: mypy, pyright, test

### autogen-agentchat
- **Path**: `python/packages/autogen-agentchat/`
- **Purpose**: Single and multi-agent workflows (AgentChat API)
- **Built on**: autogen-core
- **CI Tests**: mypy, pyright, test

### autogen-ext
- **Path**: `python/packages/autogen-ext/`
- **Purpose**: Ecosystem integrations (OpenAI, Azure AI, MCP, code executors, etc.)
- **Extras**: openai, azure, mcp, anthropic, google, litellm, docker, etc.
- **CI Tests**: mypy, pyright, test, test-grpc, test-windows (PowerShell)

### autogen-studio
- **Path**: `python/packages/autogen-studio/`
- **Purpose**: Web-based IDE for building/running AutoGen agents
- **Frontend**: Node.js-based UI

### agbench
- **Path**: `python/packages/agbench/`
- **Purpose**: Benchmarking suite for evaluating agent performance
- **CI Tests**: mypy, pyright

### magentic-one-cli
- **Path**: `python/packages/magentic-one-cli/`
- **Purpose**: CLI for Magentic-One multi-agent system
- **CI Tests**: mypy, pyright

### pyautogen (Legacy)
- **Path**: `python/packages/pyautogen/`
- **Purpose**: Legacy v0.2 compatibility layer
- **Note**: For migration from v0.2 to v0.4+

### autogen-test-utils
- **Path**: `python/packages/autogen-test-utils/`
- **Purpose**: Shared test utilities for all packages

### component-schema-gen
- **Path**: `python/packages/component-schema-gen/`
- **Purpose**: Schema generation for components

## Key Entry Points

### Core API
- `autogen_core` package entry point

### AgentChat API
- `autogen_agentchat` package entry point
- Key classes: `AssistantAgent`, `BaseGroupChat`, `AgentTool`

### Extensions API
- `autogen_ext` package with submodules for various integrations

### AutoGen Studio
- `autogenstudio ui --port 8080` — Run studio

## Code Quality Tools
- **Formatter**: ruff (with format plugin)
- **Linter**: ruff (E, F, W, B, Q, I, ASYNC, T20 rules)
- **Type Checkers**: mypy (strict), pyright
- **Test Runner**: pytest with asyncio support
- **Code Coverage**: pytest-cov + codecov

## Recent Issue Activity (Sample)
- Many UTF-8 encoding fixes across packages (Windows compatibility)
- BaseGroupChat validation improvements
- MCP tool serialization fixes
- Documentation typo fixes
- Security fixes (SSRF, memory poisoning)

## Contributing Notes
- Uses `uv` for dependency management
- Uses `poethepoet` (poe) for task automation
- All packages versioned together (semantic versioning)
- Breaking changes bump minor version, patches for features/fixes
- Docstring format: Google-style with versionadded/versionchanged directives
- CLA required for contributions