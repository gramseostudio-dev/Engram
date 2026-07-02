# Technology Stack

## Core Language & Runtime
- **Python:** 3.10+
- **Rust:** Used for performance-critical components (indicated by `Cargo.toml`/`maturin`).

## Key Dependencies
- **Bittensor:** Core protocol (`>=7.4.0`)
- **Vector Search:** FAISS (`faiss-cpu`)
- **Embeddings:** `sentence-transformers`, OpenAI
- **Data Management:** `pydantic` (validation), `numpy` (data handling)
- **Infrastructure:** `aiohttp` (networking), `qdrant-client` (vector storage)

## Development Toolchain
- **CLI:** `typer`, `rich`
- **Linting/Formatting:** `ruff`
- **Typing:** `mypy`
- **Testing:** `pytest`, `pytest-asyncio`
- **Build/Packaging:** `setuptools`, `maturin`

## Operational Notes
- **Entrypoints:** CLI tool `engram` mapped to `engram.cli:app`.
- **Environment:** Requires `python-dotenv` for configuration.
- **Port:** Default operational port is 8091.
