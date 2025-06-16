# Contributing to Monad Developer Hub

Thank you for your interest in contributing to the Monad Developer Hub! This document provides guidelines and information for contributors.

## 🌟 How to Contribute

### Types of Contributions
- **Bug Fixes** - Help us identify and fix issues
- **Feature Development** - Add new functionality
- **Documentation** - Improve guides, API docs, and examples
- **Performance Improvements** - Optimize existing code
- **Testing** - Add or improve test coverage
- **UI/UX Enhancements** - Improve user experience

### Getting Started

1. **Fork the Repository**
   ```bash
   git clone https://github.com/your-username/monad-developer-hub.git
   cd monad-developer-hub
   ```

2. **Set Up Development Environment**
   - Follow the setup instructions in each service's README
   - Ensure all services can run locally
   - Verify tests pass: `make test` (where available)

3. **Create a Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/issue-description
   ```

## 🛠️ Development Workflow

### Service-Specific Guidelines

#### Frontend (`monad-devhub-fe`)
- **Framework**: Next.js 15+ with TypeScript
- **Styling**: Tailwind CSS with Radix UI components
- **Testing**: Jest and React Testing Library
- **Standards**: ESLint configuration, Prettier formatting

```bash
cd monad-devhub-fe
npm install
npm run dev
npm run lint
npm run type-check
```

#### Backend (`monad-devhub-be`)
- **Language**: Go 1.21+
- **Framework**: Gin for HTTP, GORM for database
- **Testing**: Go's built-in testing framework
- **Standards**: gofmt, golint

```bash
cd monad-devhub-be
go mod download
go run main.go
go test ./...
go fmt ./...
```

#### Ponder Indexer (`monad-ponder-indexer`)
- **Framework**: Ponder with TypeScript
- **Database**: PostgreSQL
- **Standards**: ESLint, TypeScript strict mode

```bash
cd monad-ponder-indexer
npm install
npm run dev
npm run lint
npm run typecheck
```

#### Indexer Interface (`monad-devhub-indexer-interface`)
- **Language**: Go 1.21+
- **Framework**: Gin for HTTP, WebSocket support
- **Testing**: Go testing with database integration
- **Standards**: gofmt, golint

```bash
cd monad-devhub-indexer-interface
go mod tidy
go run main.go
go test ./...
```

### Code Standards

#### General Principles
- **Write Clear Code** - Prefer readability over cleverness
- **Add Tests** - Include unit tests for new functionality
- **Document Changes** - Update relevant documentation
- **Follow Conventions** - Use established patterns in each service
- **Error Handling** - Implement proper error handling and logging

#### TypeScript/JavaScript
- Use TypeScript for all new code
- Follow ESLint configuration
- Use Prettier for consistent formatting
- Prefer functional components and hooks
- Add proper type definitions

#### Go
- Follow Go conventions and idioms
- Use `gofmt` for formatting
- Add proper error handling
- Write comprehensive tests
- Document public functions with comments

### Commit Guidelines

#### Commit Message Format
```
type(scope): short description

Longer description if needed

Fixes #issue-number
```

#### Types
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation changes
- `style` - Code style changes (formatting, etc.)
- `refactor` - Code refactoring
- `test` - Adding or updating tests
- `chore` - Maintenance tasks

#### Examples
```bash
git commit -m "feat(frontend): add real-time transaction monitoring dashboard"
git commit -m "fix(indexer): resolve memory leak in websocket connections"
git commit -m "docs(readme): update installation instructions for Docker"
```

### Pull Request Process

1. **Before Submitting**
   - Ensure all tests pass
   - Run linting and formatting tools
   - Update documentation if needed
   - Add tests for new functionality

2. **Pull Request Description**
   - Clearly describe the changes
   - Reference related issues
   - Include screenshots for UI changes
   - List breaking changes if any

3. **Review Process**
   - Maintainers will review your PR
   - Address feedback and suggestions
   - Keep commits focused and atomic
   - Rebase if requested

### Template Pull Request
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Performance improvement

## Testing
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed

## Screenshots (if applicable)
Add screenshots for UI changes

## Breaking Changes
List any breaking changes

## Related Issues
Fixes #issue-number
```

## 🧪 Testing

### Frontend Testing
```bash
cd monad-devhub-fe
npm run test          # Unit tests
npm run test:e2e      # End-to-end tests (if available)
npm run lint          # Linting
npm run type-check    # TypeScript checking
```

### Backend Testing
```bash
cd monad-devhub-be
go test ./...                    # All tests
go test -cover ./...             # With coverage
go test ./internal/handlers      # Specific package
go test -race ./...              # Race condition detection
```

### Integration Testing
```bash
# Start all services locally
docker-compose up -d

# Run integration tests
make test-integration
```

## 📝 Documentation

### Types of Documentation
- **Code Comments** - Inline documentation for complex logic
- **API Documentation** - Update OpenAPI/Swagger specs
- **README Updates** - Keep setup instructions current
- **Architecture Docs** - Document significant design decisions

### Documentation Standards
- Use clear, concise language
- Include code examples
- Keep examples up to date
- Add diagrams for complex flows

## 🐛 Reporting Issues

### Bug Reports
Include the following information:
- **Environment** (OS, Node.js/Go version, etc.)
- **Steps to Reproduce** 
- **Expected Behavior**
- **Actual Behavior**
- **Screenshots/Logs** (if applicable)

### Feature Requests
- **Problem Description** - What problem does this solve?
- **Proposed Solution** - How should it work?
- **Alternatives Considered** - Other approaches considered
- **Additional Context** - Any other relevant information

## 🏗️ Architecture Guidelines

### Frontend Architecture
- Use Next.js App Router for new pages
- Implement proper error boundaries
- Use React Context for global state
- Follow component composition patterns
- Implement proper accessibility (a11y)

### Backend Architecture
- Follow clean architecture principles
- Separate concerns (handlers, services, repositories)
- Use dependency injection where appropriate
- Implement proper middleware for cross-cutting concerns
- Add comprehensive logging

### Database Guidelines
- Use migrations for schema changes
- Follow naming conventions
- Add proper indexes for performance
- Use transactions for data consistency
- Implement proper backup strategies

## 🚀 Performance Guidelines

### Frontend Performance
- Optimize bundle size with dynamic imports
- Use proper image optimization
- Implement proper caching strategies
- Monitor Core Web Vitals
- Use React profiling tools

### Backend Performance
- Profile critical paths
- Use connection pooling
- Implement proper caching
- Monitor memory usage
- Use efficient database queries

## 🔒 Security Guidelines

### General Security
- Never commit secrets or credentials
- Use environment variables for configuration
- Implement proper input validation
- Use HTTPS in production
- Follow OWASP guidelines

### Authentication & Authorization
- Use secure password hashing (bcrypt)
- Implement proper JWT handling
- Add rate limiting
- Use secure session management
- Implement proper CORS policies

## 🤝 Community Guidelines

### Code of Conduct
- Be respectful and inclusive
- Focus on what's best for the community
- Use welcoming and inclusive language
- Be collaborative and constructive
- Show empathy towards others

### Communication
- **Issues** - For bug reports and feature requests
- **Discussions** - For questions and general discussion
- **Discord** - For real-time community chat
- **Email** - For private/security concerns

## 📞 Getting Help

### Resources
- **Documentation** - Check README files and docs
- **Issues** - Search existing issues first
- **Discord** - Join our community chat
- **Stack Overflow** - Tag questions with `monad-devhub`

### Maintainer Contact
- **Email** - [maintainers@monaddevhub.com](mailto:maintainers@monaddevhub.com)
- **Discord** - Join our development channel
- **GitHub** - Create an issue or discussion

## 🎉 Recognition

Contributors will be recognized in:
- **Contributors List** - GitHub contributors page
- **Release Notes** - Mention significant contributions
- **Community Spotlights** - Feature outstanding contributors
- **Swag** - Stickers and merchandise for active contributors

---

Thank you for contributing to the Monad Developer Hub! Your efforts help build better tools for the entire Monad ecosystem. 🚀 