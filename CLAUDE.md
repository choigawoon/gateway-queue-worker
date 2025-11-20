# CLAUDE.md

This file provides guidance for AI assistants working with the gateway-queue-worker codebase.

## Project Overview

**gateway-queue-worker** is a Python project for processing queue-based tasks. The project is currently in its initial template state, using `uv` as the package manager.

- **Python Version**: 3.13+
- **Package Manager**: uv
- **Project Type**: Queue worker service

## Project Structure

```
gateway-queue-worker/
├── main.py              # Application entry point
├── pyproject.toml       # Project configuration and dependencies
├── uv.lock              # Lock file for reproducible installs
├── .python-version      # Python version specification (3.13)
├── README.md            # Project documentation
└── CLAUDE.md            # AI assistant guidance (this file)
```

## Development Setup

### Prerequisites

- Python 3.13 or higher
- [uv](https://github.com/astral-sh/uv) package manager

### Installation

```bash
# Install dependencies
uv sync

# Run the application
uv run python main.py
```

## Common Commands

### Running the Application

```bash
uv run python main.py
```

### Dependency Management

```bash
# Add a new dependency
uv add <package-name>

# Add a development dependency
uv add --dev <package-name>

# Update dependencies
uv sync
```

### Testing (when implemented)

```bash
# Run tests
uv run pytest

# Run tests with coverage
uv run pytest --cov
```

### Linting and Formatting (when configured)

```bash
# Format code with ruff
uv run ruff format .

# Lint code with ruff
uv run ruff check .

# Type checking with mypy
uv run mypy .
```

## Code Conventions

### Python Style

- Follow PEP 8 style guidelines
- Use type hints for all function parameters and return values
- Keep functions focused and single-purpose
- Use descriptive variable and function names

### File Organization

- Place source code in a `src/` directory as the project grows
- Keep tests in a `tests/` directory mirroring the source structure
- Configuration files stay in the project root

### Documentation

- Use docstrings for all public functions, classes, and modules
- Follow Google-style docstring format
- Keep README.md updated with usage instructions

## Architecture Guidelines

### Queue Worker Patterns

When implementing queue worker functionality:

- Use async/await for I/O-bound operations
- Implement proper error handling and retry logic
- Add logging for observability
- Use environment variables for configuration
- Implement graceful shutdown handling

### Dependencies to Consider

For a queue worker, typical dependencies might include:
- `redis` or `celery` - for queue management
- `pydantic` - for data validation
- `structlog` - for structured logging
- `httpx` - for async HTTP requests

## Testing Guidelines

### Test Structure

- Use pytest as the test framework
- Place tests in `tests/` directory
- Name test files with `test_` prefix
- Use fixtures for common test setup

### Test Types

- Unit tests for individual functions
- Integration tests for queue processing
- Use mocking for external dependencies

## Environment Configuration

Use environment variables for configuration:

```bash
# Example environment variables
QUEUE_URL=redis://localhost:6379
LOG_LEVEL=INFO
WORKER_CONCURRENCY=4
```

Consider using `python-dotenv` for local development.

## AI Assistant Guidelines

### When Making Changes

1. **Read before editing**: Always read relevant files before making changes
2. **Preserve style**: Match existing code style and conventions
3. **Add tests**: Include tests for new functionality
4. **Update documentation**: Keep README.md and docstrings current
5. **Type safety**: Add type hints to all new code

### Commit Conventions

- Use clear, descriptive commit messages
- Focus on "why" not just "what"
- Keep commits focused on single changes

### Common Tasks

- **Adding a feature**: Create tests first, then implement
- **Fixing a bug**: Write a failing test, then fix
- **Refactoring**: Ensure tests pass before and after

### Things to Avoid

- Don't commit secrets or credentials
- Don't add unnecessary dependencies
- Don't break existing functionality without updating tests
- Don't skip type hints or documentation

## Future Development

As this project evolves, consider:

1. Setting up CI/CD pipelines
2. Adding pre-commit hooks for linting
3. Implementing health check endpoints
4. Adding metrics and monitoring
5. Containerization with Docker

## Resources

- [uv documentation](https://github.com/astral-sh/uv)
- [Python typing documentation](https://docs.python.org/3/library/typing.html)
- [pytest documentation](https://docs.pytest.org/)
- [ruff documentation](https://docs.astral.sh/ruff/)
