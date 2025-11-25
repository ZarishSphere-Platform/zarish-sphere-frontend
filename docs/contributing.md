# Contributing to ZarishSphere Platform

Thank you for your interest in contributing to ZarishSphere Platform!

## Code of Conduct

Be respectful, inclusive, and professional in all interactions.

## How to Contribute

### Reporting Bugs

1. Check if the bug already exists in Issues
2. Create a new issue with:
   - Clear title
   - Steps to reproduce
   - Expected vs actual behavior
   - Environment details

### Suggesting Features

1. Check existing feature requests
2. Create an issue with:
   - Use case description
   - Proposed solution
   - Alternative approaches considered

### Pull Requests

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes
4. Write tests
5. Commit: `git commit -m 'Add amazing feature'`
6. Push: `git push origin feature/amazing-feature`
7. Open a Pull Request

## Development Setup

```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/zarish-fin.git
cd zarish-fin

# Add upstream
git remote add upstream https://github.com/ZarishSphere-Platform/zarish-fin.git

# Install dependencies
go mod download

# Run tests
go test ./...

# Run locally
go run cmd/server/main.go
```

## Coding Standards

### Go Code

- Follow [Effective Go](https://golang.org/doc/effective_go.html)
- Use `gofmt` for formatting
- Run `golint` before committing
- Write meaningful commit messages

### Commit Messages

```
type(scope): subject

body

footer
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

Example:
```
feat(api): add patient search endpoint

Implement search functionality for patients by name, MRN, or date of birth.
Includes pagination and filtering options.

Closes #123
```

## Testing

```bash
# Run all tests
go test ./...

# Run with coverage
go test -cover ./...

# Run specific test
go test -run TestCreatePatient ./internal/service
```

## Documentation

- Update README.md for user-facing changes
- Add inline comments for complex logic
- Update API documentation
- Include examples

## Questions?

- Open a Discussion on GitHub
- Join our community chat
- Email: zarishsphere@gmail.com

Thank you for contributing! 🎉
