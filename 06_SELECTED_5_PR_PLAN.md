# 06_SELECTED_5_PR_PLAN.md — Selected PR Plan for AutoGen

## Repository
- **Name**: microsoft/autogen (fork: okwn/autogen)
- **License**: CC-BY-4.0
- **Status**: Maintenance mode, community-managed

## Selected PR Candidates

### PR 1: Fix duplicated words in Python docs
- **Issue**: #7690
- **Title**: docs: fix duplicated words in Python docs
- **Type**: Documentation fix
- **Risk Level**: Very Low
- **Packages Affected**: Likely autogen-core or autogen-agentchat

**Steps**:
1. Search for duplicated words in Python source docstrings
2. Fix any duplicated word occurrences
3. Run `poe --directory ./packages/autogen-core fmt` to format
4. Run `poe --directory ./packages/autogen-core lint` to verify
5. Create PR

**Search Pattern**: Use regex to find common duplicated words (e.g., "the the", "and and", etc.)

---

### PR 2: Fix typo in custom agents documentation
- **Issue**: #7689
- **Title**: Fix typo in custom agents documentation
- **Type**: Documentation typo fix
- **Risk Level**: Very Low

**Steps**:
1. Find custom agents documentation
2. Identify and fix the typo
3. Run formatting/linting
4. Create PR

---

### PR 3: Add missing TextMessage import in custom agents docs
- **Issue**: #7676
- **Title**: docs(agentchat): add missing TextMessage import in custom agents docs
- **Type**: Documentation fix
- **Risk Level**: Very Low

**Steps**:
1. Find the custom agents documentation file
2. Check if TextMessage import is missing
3. Add the import if needed
4. Run formatting/linting
5. Create PR

---

### PR 4: Fix minor doc comment typos
- **Issue**: #7675
- **Title**: docs: fix minor doc comment typos
- **Type**: Documentation typo fix
- **Risk Level**: Very Low

**Steps**:
1. Search for common typos in docstrings
2. Fix any found typos
3. Verify with `poe fmt` and `poe lint`
4. Create PR

---

### PR 5: Add encoding='utf-8' to remaining open() calls
- **Issue**: #5566 continuation
- **Title**: fix: add encoding='utf-8' to open() calls in remaining samples
- **Type**: Bug fix (cross-platform compatibility)
- **Risk Level**: Low

**Steps**:
1. Find all open() calls in python/samples that lack encoding parameter
2. Add encoding='utf-8' to each
3. Verify with tests if applicable
4. Create PR

---

## CI/CD Checks Required

All PRs must pass:
- `poe format` — Code formatting
- `poe lint` — Linting
- `poe mypy` — Type checking
- `poe test` — Unit tests

## Development Workflow

```bash
cd /root/oss-pr-campaign/repos/autogen/python

# Setup
uv sync --all-extras
source .venv/bin/activate

# Make changes
# ... edit files ...

# Verify
poe format
poe lint
poe --directory ./packages/autogen-core test

# Commit and push to fork
git add .
git commit -m "fix: description"
git push origin main
```

## Notes
- AutoGen is in maintenance mode — only small fixes and documentation improvements
- CLA must be signed before PR can be merged
- Community-managed, responses may be limited