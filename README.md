# python-starter
Python stater project template using uv

### Install

```bash
pip install uv
uv sync --all-groups
```

### How to replicate

1. `uv init`
1. `uv add --dev ruff mypy`
1. `uv add --group test pytest pytest-cov`
1. Add tools config in pyproject.toml:
    ```toml
    [tool.mypy]
    strict = true
    disallow_untyped_defs = true

    [tool.ruff]
    line-length = 120
    indent-width = 4
    exclude = ["build/", "dist/", ".venv/", "__pycache__/"]

    [tool.ruff.lint]
    select = ["E", "F", "I", "A", "B", "C", "N", "Q", "T"]
    ignore = ["E203", "E701"]
    ```
1. `uv sync --all-groups`


### Test if everything works

1. `uv run ruff check .`
1. `uv run mypy .`
