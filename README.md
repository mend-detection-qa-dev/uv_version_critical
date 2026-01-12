# Test Case: UV Version Critical - MODERN PYTHON FEATURES TEST

## Package Manager
UV

## Python Version Detection
- **Source**: .python-version (PRIORITY #1)
- **Expected Version**: 3.12.0
- **Conflict**: pyproject.toml says >=3.9 (SHOULD BE IGNORED)

## Dependencies (CRITICAL FOR MODERN FEATURES)
- `httpx>=0.27.0` - Optimized for Python 3.12+
- `pydantic>=2.5.0` - Type hints work best on Python 3.12+

## Test Purpose
**CRITICAL TEST FOR MODERN PYTHON FEATURES**

### Why This Test Matters
Modern packages like pydantic 2.5+ and httpx 0.27+ use:
- PEP 695 syntax (Python 3.12+)
- Improved type annotations
- Performance optimizations for 3.12+

If tool uses **3.12.0** from .python-version:
- ✅ All modern features available
- ✅ Optimal performance
- ✅ Type checking works correctly
- ✅ No syntax errors or warnings

If tool uses **3.9** from pyproject.toml:
- ⚠️ Installation may succeed but...
- ❌ Performance degradation
- ❌ Missing type hint features
- ❌ Potential syntax errors in newer pydantic validators
- ❌ Runtime errors with modern syntax

## Expected Behavior
1. Tool detects .python-version (3.12.0) as highest priority
2. Tool ignores pyproject.toml requires-python (>=3.9)
3. Uses Python 3.12 for installation
4. All modern features work correctly

## Real-World Impact
This represents the common scenario:
- **pyproject.toml**: Specifies minimum Python version for backwards compatibility
- **.python-version**: Specifies actual development/production Python version
- **Dependencies**: Use modern features from newer Python

**Wrong version detection = degraded performance + missing features + potential runtime errors**

## UV-Specific Importance
UV is designed for modern Python workflows. Users expect:
- Fast resolution with latest Python
- Modern type hints working correctly
- Optimal performance

Using older Python version defeats UV's purpose!
