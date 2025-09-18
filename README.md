# go-hexagonal-architecture

# Product Overview

This is a Go-based application implementing hexagonal architecture (also known as ports and adapters pattern). The system appears to be designed for handling orders and user management with both API and worker components.

## Key Features
- RESTful API service
- Background worker processing
- User management
- Order processing
- Multi-protocol support (HTTP, gRPC)
- Database integration (PostgreSQL, Redis)
- External service integrations

## Architecture Philosophy
The project follows hexagonal architecture principles to maintain clean separation between business logic and external concerns, enabling high testability and flexibility in changing adapters without affecting core business rules.
# Technology Stack

## Language & Runtime
- **Go**: Primary programming language
- Follow Go conventions and idioms
- Use Go modules for dependency management

## Infrastructure & Storage
- **PostgreSQL**: Primary database for persistent data
- **Redis**: Caching and session storage
- **Docker**: Containerization (configuration in `/docker`)
- **Database Migrations**: Managed in `/migrations` directory

## Protocols & APIs
- **HTTP/REST**: Primary API interface
- **gRPC**: Alternative API protocol for internal services
- Support for multiple transport protocols

## Shared Libraries
- **Logger**: Custom logging utilities (`pkg/logger`)
- **Validator**: Input validation utilities (`pkg/validator`)

## Common Commands
Since this is a Go project, typical commands would include:

```bash
# Initialize Go module (if not already done)
go mod init <module-name>

# Download dependencies
go mod tidy

# Build API service
go build -o bin/api ./cmd/api

# Build worker service  
go build -o bin/worker ./cmd/worker

# Run tests
go test ./...

# Run tests with coverage
go test -cover ./...

# Format code
go fmt ./...

# Lint code (requires golangci-lint)
golangci-lint run

# Run database migrations (tool-dependent)
# migrate -path migrations -database "postgres://..." up
```

# Project Structure

This project follows hexagonal architecture (ports and adapters) with clear separation of concerns.

## Architecture Rules
1. **Dependency Direction**: Dependencies point inward toward the domain
2. **Domain Isolation**: Domain layer has no external dependencies
3. **Interface Segregation**: Use specific interfaces in ports
4. **Adapter Independence**: Adapters can be swapped without changing domain logic
5. **Single Responsibility**: Each layer has a clear, single purpose
