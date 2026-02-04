# Contributing to HappyCapy Skill Creator

Thank you for your interest in contributing! We appreciate your help in making this project better.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
- [Development Setup](#development-setup)
- [Coding Standards](#coding-standards)
- [Testing](#testing)
- [Pull Request Process](#pull-request-process)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Enhancements](#suggesting-enhancements)

## 🤝 Code of Conduct

This project follows a simple code of conduct:
- Be respectful and constructive
- Focus on collaboration and learning
- Welcome newcomers and diverse perspectives

## 🛠️ How to Contribute

### Types of Contributions

We welcome:
- 🐛 Bug fixes
- ✨ New features
- 📝 Documentation improvements
- 🧪 Test coverage enhancements
- 🎨 Code quality improvements

### Before You Start

1. Check [existing issues](https://github.com/Y1fe1-Yang/happycapy-skill-creator/issues)
2. For large changes, open an issue first to discuss
3. For small fixes, feel free to submit a PR directly

## 💻 Development Setup

### 1. Fork and Clone

```bash
# Fork the repository on GitHub, then clone your fork
git clone https://github.com/YOUR_USERNAME/happycapy-skill-creator.git
cd happycapy-skill-creator
```

### 2. Install Dependencies

```bash
# Install runtime dependencies
pip install -r requirements.txt

# Install development dependencies
pip install -r requirements-dev.txt
```

### 3. Set Up Pre-commit Hooks (Optional but Recommended)

```bash
pre-commit install
```

This will automatically format and lint your code before each commit.

### 4. Create a Branch

```bash
git checkout -b feature/my-feature
# or
git checkout -b fix/my-bugfix
```

## 📏 Coding Standards

### Python Style Guide

We follow PEP 8 with some modifications:
- **Line length**: 100 characters (configured in pyproject.toml)
- **Formatting**: Use Black for automatic formatting
- **Imports**: Sort imports (use isort if available)

### Code Formatting

```bash
# Format code with Black
black scripts/ tests/

# Check formatting without changes
black --check scripts/ tests/
```

### Linting

```bash
# Run flake8
flake8 scripts/ tests/

# Check specific file
flake8 scripts/create_skill.py
```

### Type Hints

We encourage but don't require type hints:

```python
def search_similar_skills(query: str, top_k: int = 3) -> List[Dict[str, Any]]:
    """
    Search for similar skills.

    Args:
        query: User's requirement description
        top_k: Number of results to return

    Returns:
        List of matching skills with similarity scores
    """
    ...
```

### Documentation

- Add docstrings to all public functions and classes
- Use Google-style or NumPy-style docstrings
- Update README.md if adding new features
- Update CHANGELOG.md following [Keep a Changelog](https://keepachangelog.com/)

## 🧪 Testing

### Running Tests

```bash
# Run all tests
pytest

# Run with coverage report
pytest --cov=scripts --cov-report=html

# Run specific test file
pytest tests/test_semantic_search.py

# Run tests matching a pattern
pytest -k "test_docker"
```

### Writing Tests

- Place tests in `tests/` directory
- Name test files as `test_*.py`
- Name test functions as `test_*`
- Use descriptive test names

Example:

```python
def test_semantic_search_returns_valid_results():
    """Test that semantic search returns properly formatted results."""
    results = search_similar_skills("compress PDF", top_k=3)

    assert isinstance(results, list)
    assert len(results) <= 3
    assert all("name" in r and "similarity" in r for r in results)
```

### Test Categories

Mark tests appropriately:

```python
import pytest

@pytest.mark.slow
def test_full_skill_creation():
    """This test takes a long time."""
    ...

@pytest.mark.integration
def test_api_integration():
    """This test requires API access."""
    ...
```

Run specific categories:

```bash
# Skip slow tests
pytest -m "not slow"

# Run only integration tests
pytest -m integration
```

## 🔄 Pull Request Process

### 1. Update Your Branch

```bash
# Fetch latest changes from upstream
git fetch upstream
git rebase upstream/main
```

### 2. Make Your Changes

- Write clear, concise commit messages
- Keep commits focused (one logical change per commit)
- Follow the coding standards above

### 3. Test Your Changes

```bash
# Run tests
pytest

# Check code formatting
black --check scripts/ tests/

# Run linter
flake8 scripts/ tests/
```

### 4. Update Documentation

- Update README.md if needed
- Update CHANGELOG.md under "Unreleased" section
- Add docstrings to new functions

### 5. Push and Create PR

```bash
git push origin feature/my-feature
```

Then open a Pull Request on GitHub with:
- Clear title describing the change
- Description of what and why
- Reference to related issue (if any)
- Screenshots (if UI changes)

### PR Checklist

Before submitting, ensure:

- [ ] Code follows style guidelines
- [ ] Tests pass locally
- [ ] New tests added for new features
- [ ] Documentation updated
- [ ] CHANGELOG.md updated
- [ ] Commit messages are clear

## 🐛 Reporting Bugs

### Before Reporting

1. Check [existing issues](https://github.com/Y1fe1-Yang/happycapy-skill-creator/issues)
2. Try the latest version
3. Collect relevant information

### Bug Report Template

```markdown
**Describe the bug**
A clear description of what the bug is.

**To Reproduce**
Steps to reproduce:
1. Run command '...'
2. See error

**Expected behavior**
What you expected to happen.

**Environment:**
- OS: [e.g., Ubuntu 22.04]
- Python version: [e.g., 3.11.5]
- Project version: [e.g., 1.2.0]

**Additional context**
Error messages, logs, screenshots, etc.
```

## 💡 Suggesting Enhancements

### Enhancement Suggestion Template

```markdown
**Is your feature request related to a problem?**
A clear description of the problem.

**Describe the solution you'd like**
What you want to happen.

**Describe alternatives you've considered**
Other approaches you've thought about.

**Additional context**
Mockups, examples, use cases, etc.
```

## 📞 Getting Help

- 💬 [Open an issue](https://github.com/Y1fe1-Yang/happycapy-skill-creator/issues/new)
- 📖 Read the [README](README.md)
- 🔍 Check [references/](references/) for detailed docs

## 🎉 Recognition

Contributors will be:
- Listed in release notes
- Mentioned in CHANGELOG.md
- Added to contributors list (future)

Thank you for contributing to HappyCapy Skill Creator!

---

**Happy coding!** 🚀
