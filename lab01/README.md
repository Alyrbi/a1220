# Project status

## What it does

Reads `data/tasks.csv`, counts completed tasks, and prints each task's name,
status, and owner. The supplied data contains five tasks, two of them complete.
The expected report is saved in `expected_output.txt`.

## Set up

Install Python 3.11 or newer and uv. From the repository root, run:

```sh
cd lab01
uv sync
```

This installs the project and its development tools into `.venv/`, using the
versions recorded in `uv.lock`. Runtime code uses only the Python standard
library. Run all commands below from the `lab01/` directory.

## Run

```sh
uv run python -m project_status
```

## Check

```sh
uv run python -m project_status | diff - expected_output.txt
uv run ruff format --check .
uv run ruff check .
uv run python -m unittest discover -s tests
```

The output comparison should print nothing, Ruff should report that all checks
passed, and unittest should end with `OK`.

To format code and apply safe lint fixes after editing:

```sh
uv run ruff format .
uv run ruff check --fix .
```
