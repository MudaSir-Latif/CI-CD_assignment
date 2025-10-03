# CI-CD_assignment

A small Python calculator module with unit tests. This repository is a compact exercise for CI/CD pipelines and basic Python testing. It provides simple arithmetic functions and a test suite demonstrating good testing practices.

## Repository structure

- `calculator.py` — Implementation of basic arithmetic functions: `add`, `subtract`, `multiply`, and `divide`.
- `test_calculator.py` — Unit tests for the functions in `calculator.py` using the standard `unittest` framework.
- `run.sh` — A small bash script that prints a greeting message.
- `README.md` — This file.

## Project overview

This project shows a minimal Python module and tests. It’s suitable for demonstrating continuous integration (CI) workflows, test runners, and basic code quality checks.

The `calculator.py` module exposes four functions:

- `add(d, c)` — returns the sum of two numbers.
- `subtract(a, b)` — returns the difference (a - b).
- `multiply(a, b)` — returns the product.
- `divide(a, b)` — returns the quotient (a / b). Raises `ValueError` when dividing by zero.

All functions accept numeric inputs (ints or floats). Division returns a float when applicable.

## Quickstart (Windows PowerShell)

1. Ensure you have Python 3.7+ installed and available on your PATH.

2. Open PowerShell and change to the repository directory:

```powershell
cd "C:\Users\corei\Desktop\CI-CD_assignment"
```

3. Run the tests:

```powershell
python -m unittest -v test_calculator.py
```

You should see the tests run and succeed. Example output:

- "OK" or a list of tests with status `ok` for each, followed by `OK`.

## Running the module interactively

You can import the module in a Python REPL or a script. Example:

```python
from calculator import add, subtract, multiply, divide

print(add(2, 3))        # 5
print(subtract(5, 2))   # 3
print(multiply(4, 3))   # 12
print(divide(10, 2))    # 5.0
```

Handling divide-by-zero:

```python
from calculator import divide

try:
    divide(5, 0)
except ValueError as e:
    print(e)  # "Cannot divide by zero"
```

## About `run.sh`

`run.sh` is a small bash script that prints a greeting. On Windows, run it from Git Bash, WSL, or any bash-compatible shell:

```bash
./run.sh
```

From PowerShell you can run it via WSL if available, or use Git Bash shipped with Git for Windows.

## Tests

Tests are written with Python's built-in `unittest` framework in `test_calculator.py`. The test file includes:

- `test_add`
- `test_subtract`
- `test_multiply`
- `test_divide`
- `test_divide_by_zero`

To run all tests:

```powershell
python -m unittest discover -v
```

## Contributing

Small repository — contributions are welcome. Suggested changes:

- Add more edge-case tests (large numbers, floats, negative numbers, non-numeric inputs).
- Add type hints and a mypy configuration for static type checking.
- Add linting (flake8 / black) and a CI workflow (GitHub Actions) to run tests on every push.

If you make changes, please ensure the test suite remains green.

## Suggested CI (GitHub Actions)

A minimal workflow to run tests on push (place under `.github/workflows/python-tests.yml`):

```yaml
name: Python tests

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - name: Install dependencies
        run: python -m pip install --upgrade pip
      - name: Run tests
        run: python -m unittest discover -v
```

## Authors

- Owias Iqbal
- Mudassir Latif

(Names taken from `run.sh`.)

## License

No license file is included. Add a `LICENSE` file if you want to specify how the code can be reused.

## Notes

- This is intentionally small and dependency-free to make CI/CD demonstration straightforward.
- If you want, I can add type hints, a requirements file, and a GitHub Actions workflow file next.
