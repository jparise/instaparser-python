# Instaparser Python Testing

This directory contains comprehensive tests for the Instaparser Python Library.

## Test Files

### `test_client.py` (67 tests)
Tests for the `InstaparserClient` class:
- Client initialization (with/without custom base URL)
- Response handling (success, errors, edge cases)
- Article API method (URL, content, output formats, caching)
- Summary API method (URL, content, streaming, caching)
- PDF API method (URL, file uploads, output formats, caching)
- Network errors and timeouts
- Edge cases (malformed responses, empty responses, large content)
- URL encoding and special characters
- Session header management

### `test_article.py` (25 tests)
Tests for the `Article` class:
- Initialization with various data configurations
- HTML vs text output handling
- Property access (title, author, words, images, videos, etc.)
- Edge cases (None values, empty strings, Unicode, special characters)
- Very long content handling
- Date handling (string, integer, None)
- Complex HTML structures
- Body fallback logic (HTML → text → None)

### `test_summary.py` (15 tests)
Tests for the `Summary` class:
- Initialization with key_sentences and overview
- Empty and whitespace-only content
- Very long content
- Unicode and special characters
- String representation methods (`__str__`, `__repr__`)

### `test_pdf.py` (20 tests)
Tests for the `PDF` class:
- Inheritance from Article
- PDF-specific behavior (is_rtl=False, videos=[])
- Override behavior (ensures is_rtl and videos are always correct)
- Unicode and special characters
- Very long content
- Text output format
- All Article properties and methods

### `test_exceptions.py` (13 tests)
Tests for exception classes:
- Exception inheritance hierarchy
- Base `InstaparserError`
- `InstaparserAPIError` with status codes and responses
- Specific exceptions (Authentication, RateLimit, Validation)
- Exception raising and catching

### `test_init.py` (10 tests)
Tests for package-level exports:
- All classes and exceptions are exported
- `__all__` list matches exports
- Version information
- Import functionality
- Exception inheritance chain verification

### `test_integration.py` (12 tests)
Integration-style tests:
- Complete workflows (Article, Summary, PDF)
- Error handling across the library
- Multiple client instances
- Client reuse for multiple requests
- Output format variations

### `conftest.py`
Shared pytest fixtures:
- `api_key`: Sample API key for testing
- `base_url`: Base URL for testing
- `client`: InstaparserClient instance
- `mock_article_response`: Mock article API response
- `mock_article_text_response`: Mock article API response (text format)
- `mock_summary_response`: Mock summary API response
- `mock_pdf_response`: Mock PDF API response
- `mock_response`: Factory for creating mock HTTP responses
- `mock_session`: Mock requests.Session

## Running Tests

### Run all tests:
```bash
pytest tests/
```

### Run specific test file:
```bash
pytest tests/test_client.py
```

### Run with coverage:
```bash
pytest tests/ --cov=instaparser --cov-report=html
```

### Run with verbose output:
```bash
pytest tests/ -v
```

### Run specific test:
```bash
pytest tests/test_client.py::TestInstaparserClientArticle::test_article_from_url
```

## Test Coverage

The test suite covers:
- ✅ All public API methods
- ✅ All classes and their properties
- ✅ Error handling and exceptions
- ✅ Edge cases (empty data, None values, large content)
- ✅ Unicode and special characters
- ✅ Network errors and timeouts
- ✅ Malformed responses
- ✅ Streaming functionality
- ✅ File uploads
- ✅ URL encoding
- ✅ Package exports
- ✅ Integration workflows

## Test Statistics

- **Total test files**: 8
- **Total test functions**: ~145
- **Test coverage**: Comprehensive across all components

## Dependencies

Tests require:
- `pytest>=6.0`
- `pytest-cov>=2.0` (optional, for coverage)
- `requests>=2.25.0` (for mocking)

Install test dependencies:
```bash
pip install -e ".[dev]"
```
