# Market Research Copilot

An agentic RAG assistant over SEC filings and stock price data that can also call a forecasting model.

## Status

**Phase 0 — scaffolding only.** No features implemented yet.

## Project layout

```
src/market_copilot/
    data/       # Data ingestion, loading, and preprocessing (SEC filings, price data)
    models/     # Forecasting model training/inference code
    agent/      # Agentic RAG orchestration (retrieval, tool-calling, planning)
    api/        # API layer exposing the assistant (e.g. FastAPI app)
    eval/       # Evaluation harnesses and metrics for retrieval/forecasting/agent quality
    viz/        # Plotting and reporting utilities
tests/          # Unit and integration tests (mirrors src/ layout)
notebooks/      # Exploratory analysis, not imported by application code
data/           # Local data files (git-ignored) — use DVC or a remote store for real data
.github/workflows/  # CI pipelines
```

## Setup

This project uses [uv](https://docs.astral.sh/uv/) for dependency management and pins Python 3.11.

```bash
uv sync --extra dev
cp .env.example .env  # then fill in real values
```

## Commands

| Task   | Make (Linux/macOS/CI) | PowerShell (Windows)  |
|--------|------------------------|------------------------|
| Lint   | `make lint`            | `./scripts/lint.ps1`   |
| Format | `make format`          | `./scripts/format.ps1` |
| Test   | `make test`            | `./scripts/test.ps1`   |

## Configuration

Settings are loaded from environment variables (or a local `.env` file) via `pydantic-settings` in
[`src/market_copilot/config.py`](src/market_copilot/config.py). See `.env.example` for the required
variables. Never commit `.env`.
