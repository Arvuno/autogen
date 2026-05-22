# 00_STATE.md — AutoGen Repository Analysis

## Repository Identity
- **Full Name**: microsoft/autogen
- **Fork**: okwn/autogen (forked from microsoft/autogen)
- **License**: CC-BY-4.0 (Creative Commons Attribution 4.0 International)
- **Archived**: false
- **Language**: Python
- **Stars**: 58,298
- **Forks**: 8,802
- **Open Issues**: 843
- **Default Branch**: main

## Repository Status
- **Maintenance Mode**: AutoGen is in maintenance mode as of late 2024/early 2025
- **Recommendation**: New users directed to Microsoft Agent Framework
- **Community-Managed**: Going forward, community managed

## Key Metadata
- **Python Version**: 3.10+ required
- **Package Manager**: uv (Astral)
- **Task Runner**: poethepoet (poe)
- **Linting**: ruff
- **Type Checking**: mypy, pyright
- **Testing**: pytest, pytest-asyncio, pytest-xdist

## Package Structure
```
python/packages/
├── autogen-core/          # Core interface definitions and reference implementations
├── autogen-agentchat/     # Single/multi-agent workflows on top of autogen-core
├── autogen-ext/           # Ecosystem integrations (OpenAI, Azure, MCP, etc.)
├── autogen-studio/        # Web-based IDE for building/running agents
├── autogen-test-utils/    # Shared test utilities
├── agbench/               # Benchmarking suite for agent performance
├── magentic-one-cli/      # CLI for Magentic-One (multi-agent team)
├── component-schema-gen/  # Schema generation for components
└── pyautogen/            # Legacy v0.2 compatibility package
```

## CI/CD Workflows
- `checks.yml`: format, lint, mypy, pyright, test, docs, samples-code-check, markdown-code-lint, check-proto-changes
- `integration.yml`: Integration tests
- `docs.yml`: Documentation build
- `python-package-0.2.yml`: Legacy v0.2 package tests
- `dotnet-build.yml` / `dotnet-release.yml`: .NET builds
- `codeql.yml`: Code security scanning
- `single-python-package.yml`: Per-package releases

## Development Setup
```bash
cd python
uv sync --all-extras
source .venv/bin/activate
poe check  # Run all checks
```

## Key Commands
- `poe format` — Format code
- `poe lint` — Lint code
- `poe test` — Run tests
- `poe mypy` — Type check with mypy
- `poe pyright` — Type check with pyright
- `poe docs-build` — Build documentation
- `poe docs-check` — Check documentation