# Todo List - .NET 8 Clean Architecture

A Todo List API built with .NET 8 following Clean Architecture principles.

## Project Structure

```
.
├── TodoList.sln                                    # Solution file
├── README.md                                        # This file
└── src/
    └── backend/
        └── services/
            ├── Todo.Api/                           # API Layer (ASP.NET Core Web API)
            │   └── Todo.Api.csproj
            ├── Todo.Application/                   # Application Layer (Business Logic)
            │   └── Todo.Application.csproj
            ├── Todo.Domain/                        # Domain Layer (Core Entities)
            │   └── Todo.Domain.csproj
            └── Todo.Infrastructure/                # Infrastructure Layer (Data Access)
                └── Todo.Infrastructure.csproj
```

## Architecture Layers

### 1. **Todo.Domain** (Core Layer)
- Contains enterprise business rules and entities
- No dependencies on other projects
- Pure business logic

### 2. **Todo.Application** (Application Layer)
- Contains application business rules
- Depends on: Todo.Domain
- Defines interfaces for infrastructure

### 3. **Todo.Infrastructure** (Infrastructure Layer)
- Contains data access and external services implementation
- Depends on: Todo.Domain
- Implements interfaces defined in Application layer

### 4. **Todo.Api** (Presentation Layer)
- ASP.NET Core Web API
- Depends on: Todo.Application, Todo.Infrastructure
- Entry point of the application

## Getting Started

### Prerequisites
- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)

### Build
```bash
dotnet build
```

### Run
```bash
cd src/backend/services/Todo.Api
dotnet run
```

### Test
```bash
dotnet test
```

## Project Dependencies

```
Todo.Api
  ├── Todo.Application
  │   └── Todo.Domain
  └── Todo.Infrastructure
      └── Todo.Domain
```