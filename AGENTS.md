# Repository Guidelines

## Project Structure & Module Organization
The repository is intentionally lean. `main.py` hosts the current entrypoint; expand it or migrate logic into a package directory (e.g., `langgraph_prac_workspace/`) when features grow. Keep reusable workflows in dedicated modules and place notebooks or exploratory scripts under `notebooks/` to avoid polluting the runtime path. Align data files or prompt templates under `assets/` and stash environment examples in `.env.example` so automation can pick them up.

## Build, Test, and Development Commands
Install dependencies with `uv sync` (preferred) or `uv pip install -r pyproject.toml` for targeted updates. Run the app locally with `uv run python main.py`. Start a REPL or notebook kernel inside the managed environment using `uv run ipython` or `uv run jupyter lab`. Regenerate dependency locks via `uv lock --upgrade` when bumping pinned versions.

## Coding Style & Naming Conventions
Stick to Python 3.12 features and type hints throughout. Use Black-compatible 4-space indentation and format code with `uv run black .`; pair it with `uv run ruff check --fix .` for linting. Favor descriptive snake_case for module, function, and variable names; reserve PascalCase for classes and UPPER_SNAKE for constants, environment keys, and agent identifiers.

## Testing Guidelines
Adopt `pytest` once test coverage is introduced. Mirror modules under `tests/` using `test_<module>.py` filenames and descriptive `TestClass` groupings. Run suites with `uv run pytest`. Target meaningful assertions over integration endpoints and add regression tests for bugs before shipping fixes. Track coverage using `uv run pytest --cov` and aim for steady growth past 80% as the codebase evolves.

## Commit & Pull Request Guidelines
No commits exist yet, so follow Conventional Commits (`feat:`, `fix:`, `chore:`) in imperative mood to keep history searchable. Reference issue IDs in the footer when available. Pull requests should summarize intent, list verification steps (`uv run pytest`, `uv run python main.py`), and capture screenshots or logs for user-facing changes. Request a second reviewer when altering the agent loop or dependency stack.

## Environment & Security Tips
Store secrets in `.env` and load them via `python-dotenv` rather than hardcoding values. Never commit API keys or local notebooks containing credentials; add them to `.gitignore` if needed. Validate new dependencies against `pyproject.toml` to avoid supply-chain surprises.
