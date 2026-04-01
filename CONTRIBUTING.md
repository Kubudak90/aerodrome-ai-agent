# Contributing to Aerodrome AI Agent

Thank you for your interest in contributing to the Aerodrome Protocol Intelligence Brain! This document provides guidelines and instructions for contributing to our AI-powered knowledge system for the Aerodrome Finance protocol.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Submitting Changes](#submitting-changes)
- [Style Guidelines](#style-guidelines)
- [Testing](#testing)
- [Community](#community)

## Code of Conduct

This project and everyone participating in it is governed by our commitment to:

- **Be respectful**: Treat everyone with respect. Healthy debate is encouraged, but harassment is not tolerated.
- **Be constructive**: Provide constructive feedback and be open to receiving it.
- **Focus on what's best for the community**: Prioritize the collective benefit of the protocol and its users.
- **Show empathy**: Understand that we all have different backgrounds and perspectives.

## Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher recommended)
- **npm** or **yarn**
- **Git**
- **Python** (v3.9+ for ML components, if applicable)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/sonu96/aerodrome-ai-agent.git
   cd aerodrome-ai-agent
   ```

2. **Install dependencies**:
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**:
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Verify installation**:
   ```bash
   npm run build
   npm test
   ```

## Development Workflow

### Branching Strategy

- `main` — Production-ready code
- `develop` — Integration branch for features
- Feature branches — Create from `develop` using the naming convention:
  - `feature/description` for new features
  - `fix/description` for bug fixes
  - `docs/description` for documentation updates
  - `refactor/description` for code refactoring
  - `agent/improvement` for AI agent enhancements

### Building

Compile the TypeScript:
```bash
npm run build
```

Watch mode for development:
```bash
npm run dev
```

### Environment Setup

Required environment variables:
- `OPENAI_API_KEY` — For AI-powered analysis
- `AERODROME_SUBGRAPH_URL` — GraphQL endpoint for protocol data
- `BASE_RPC_URL` — Base network RPC endpoint
- `PRIVATE_KEY` — For on-chain interactions (optional for development)

## Submitting Changes

### Pull Request Process

1. **Fork the repository** and create your branch from `develop`.

2. **Make your changes** following our style guidelines.

3. **Add or update tests** as necessary.

4. **Update documentation** if your changes affect usage or architecture.

5. **Ensure all checks pass**:
   - TypeScript compilation
   - Tests
   - Linting

6. **Fill out the pull request template** with:
   - Clear description of changes
   - Motivation for the changes
   - Any breaking changes
   - Testing performed
   - Impact on AI agent performance (if applicable)

7. **Request review** from maintainers.

8. **Address review feedback** promptly.

### Commit Message Guidelines

We follow conventional commits:

- `feat:` — New feature
- `fix:` — Bug fix
- `docs:` — Documentation changes
- `style:` — Code style changes (formatting, no logic change)
- `refactor:` — Code refactoring
- `test:` — Adding or updating tests
- `chore:` — Maintenance tasks
- `agent:` — AI agent improvements
- `memory:` — Memory system changes

Example:
```
feat: add volatility prediction to pool analysis

Implements machine learning model to predict
pool volatility based on historical TVL changes.
```

## Style Guidelines

### TypeScript

- Follow the [TypeScript Style Guide](https://google.github.io/styleguide/tsguide.html)
- Use strict TypeScript configuration
- Prefer `const` and `let` over `var`
- Use explicit return types for public functions
- Maximum line length: 100 characters
- Use 2 spaces for indentation

### Code Organization

```
src/
├── agents/           # AI agent implementations
├── memory/           # Memory management system
├── knowledge/        # Protocol knowledge base
├── analysis/         # Data analysis modules
├── blockchain/       # On-chain interactions
├── types/            # TypeScript type definitions
└── utils/            # Utility functions
```

### AI Agent Development

When contributing to agent capabilities:

- **Document prompt engineering** decisions
- **Include confidence scoring** for predictions
- **Implement proper error handling** for AI responses
- **Add memory context** for multi-turn conversations
- **Test with real protocol data** when possible

### Error Handling

- Use descriptive error messages
- Implement retry logic for external API calls
- Log errors appropriately for debugging
- Handle edge cases in protocol data

## Testing

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run specific test file
npm test -- analysis/pool.test.ts
```

### Writing Tests

We use **Jest** for testing. Tests should be placed in `__tests__/` directories or as `*.test.ts` files.

Example test structure:
```typescript
import { describe, it, expect } from '@jest/globals';
import { PoolAnalyzer } from '../src/analysis/pool';

describe('PoolAnalyzer', () => {
  it('should calculate correct APY for stable pools', () => {
    const analyzer = new PoolAnalyzer();
    const result = analyzer.calculateAPY({
      tvl: 1000000,
      volume24h: 50000,
      fees: 0.0005
    });
    expect(result).toBeGreaterThan(0);
  });

  it('should handle missing data gracefully', () => {
    const analyzer = new PoolAnalyzer();
    expect(() => analyzer.calculateAPY(null)).toThrow('Invalid pool data');
  });
});
```

### Integration Testing

For blockchain interactions:
- Use Base Sepolia testnet for development
- Mock external API calls in unit tests
- Include integration tests for critical paths

## Community

### Communication Channels

- **GitHub Issues**: For bug reports and feature requests
- **GitHub Discussions**: For questions and ideas
- **Discord**: Join the Aerodrome community (link in README)

### Getting Help

If you need help:

1. Check existing documentation and README
2. Search closed issues and discussions
3. Ask in the community Discord
4. Open a discussion for complex questions

### Reporting Bugs

When reporting bugs, please include:

- **Description**: Clear description of the bug
- **Steps to Reproduce**: Minimal steps to reproduce the issue
- **Expected Behavior**: What you expected to happen
- **Actual Behavior**: What actually happened
- **Environment**: Node.js version, OS, commit hash
- **Logs**: Relevant error messages or logs
- **Protocol State**: Relevant pool/token data if applicable

### Requesting Features

When requesting features:

- Describe the use case
- Explain how it improves the AI agent
- Provide examples if possible
- Be open to discussion about implementation

### Recognition

Contributors will be recognized in our release notes and documentation. Significant contributions may be eligible for additional rewards at the team's discretion.

## Security

### Reporting Vulnerabilities

**DO NOT** open public issues for security vulnerabilities.

Instead, please report security issues privately via GitHub Security Advisories or email.

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

### Security Best Practices

When contributing code:

- Never commit private keys or API keys
- Validate all external inputs
- Use environment variables for sensitive data
- Follow blockchain security best practices
- Be cautious with on-chain transactions

---

Thank you for helping build the future of AI-powered DeFi analysis on Base!
