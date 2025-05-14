# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Mem0 ("mem-zero") is a memory layer for AI assistants and agents that enables personalized interactions by helping AI systems remember user preferences, conversation context, and learn over time.

The repository consists of:
1. A Python package (`mem0ai`) - Core library
2. A TypeScript/JavaScript SDK (`mem0ai` npm package)
3. OpenMemory - A self-hostable, open-source variant
4. Documentation and examples

## Repository Structure

The repository is organized into these main components:

- `mem0/` - Main Python package with core functionality
  - `client/` - Client interface for the memory system
  - `llms/` - Integrations with various LLM providers
  - `embeddings/` - Embedding model implementations
  - `vector_stores/` - Vector database integrations
  - `memory/` - Core memory management system
  - `graphs/` - Graph memory capabilities

- `mem0-ts/` - TypeScript SDK
  - `src/` - Source code for the TypeScript client

- `openmemory/` - Self-hosted, open-source memory layer
  - `api/` - Backend API server
  - `ui/` - Frontend web interface

- `examples/` - Example applications and integrations
- `tests/` - Test suite

## Development Commands

### Python Development

```bash
# Install dependencies
make install                # Install basic dependencies
make install_all            # Install all dependencies including optional ones

# Activate virtual environment
poetry shell

# Code quality
make format                 # Format code with ruff
make sort                   # Sort imports with isort
make lint                   # Lint code with ruff

# Testing
make test                   # Run all tests
poetry run pytest tests/memory/test_main.py    # Run specific test file
poetry run pytest tests/memory/test_main.py::test_function_name  # Run specific test

# Building and publishing
make build                  # Build the package
make publish                # Publish to PyPI
make clean                  # Clean build artifacts
```

### TypeScript Development

```bash
# Navigate to TypeScript directory
cd mem0-ts

# Install dependencies
npm install

# Development
npm run dev                 # Run development server
npm run example             # Run example

# Building
npm run build               # Clean and build the project

# Testing
npm run test                # Run all tests
npm run test:watch          # Run tests in watch mode

# Code quality
npm run format              # Format code with Prettier
npm run format:check        # Check formatting
```

## Architecture and Design

### Memory System

1. **Memory Layer**: The core functionality that stores and retrieves memories
   - Multi-level memory (user, session, agent)
   - Support for various vector stores (Qdrant, Pinecone, etc.)
   - Graph-based memory for relational data

2. **Integration Points**:
   - LLM providers (OpenAI, Anthropic, Google, etc.)
   - Embedding models
   - Vector databases

3. **Key Workflows**:
   - Memory creation and storage
   - Memory search and retrieval
   - Contextual memory optimization
   - Memory updates and feedback

### Performance Considerations

Mem0 is designed to optimize the balance between:
- Accuracy (+26% over OpenAI Memory)
- Response latency (91% faster than full-context)
- Token efficiency (90% fewer tokens than full-context)

## Testing Guidelines

1. All new code should include unit tests in the `tests/` directory
2. Tests should be comprehensive but focused on functionality
3. Run the full test suite before submitting a PR

## Tips for Working in this Codebase

1. Many integrations have optional dependencies to keep the core package lightweight. Use `make install_all` for development with all integrations.

2. When implementing a new feature, look at similar existing components (LLM providers, vector stores, etc.) to maintain consistency.

3. The documentation is extensive and provides valuable context for understanding the system's architecture and capabilities.