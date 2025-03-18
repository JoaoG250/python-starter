# python-starter
Python stater project template using uv

### How to reproduce

1. `uv init`
1. `uv add --dev ruff mypy pre-commit`
1. `uv add --group test pytest pytest-cov`
1. .pre-commit-config.yaml:
    ```yaml
    repos:
      - repo: https://github.com/astral-sh/ruff-pre-commit
        # Ruff version.
        rev: v0.11.0
        hooks:
          # Run the linter.
          - id: ruff
          # Run the formatter.
          - id: ruff-format
    ```
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
    ignore = ["E203", "E701", "T201"]
    ```
1. `uv sync --all-groups`
1. `uv run pre-commit install`


### Test if everything works

1. `uv run ruff check .`
1. `uv run mypy .`
1. `uv run pre-commit run --all-files`
