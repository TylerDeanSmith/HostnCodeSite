# GitHub Copilot Instructions for HostnCodeSite

## Project Overview

This is a .NET Aspire distributed application built with C# and .NET 8.0. The project demonstrates cloud-native application patterns with service defaults, API services, and a web frontend.

### Project Structure

- **HostnCodeWebApp.AppHost**: Aspire orchestration host that manages the application lifecycle
- **HostnCodeWebApp.ApiService**: Backend API service
- **HostnCodeWebApp.Web**: Frontend web application
- **HostnCodeWebApp.ServiceDefaults**: Shared service configuration and defaults
- **HostnCodeWebApp.Tests**: Integration and unit tests

## Technology Stack

- .NET 8.0
- ASP.NET Core
- .NET Aspire 9.5.0
- OpenTelemetry (for observability)
- xUnit (for testing)

## Setup and Build Instructions

### Prerequisites

- .NET 8.0 SDK or later
- Docker Desktop (for running Aspire dashboard and local resources)

### Building the Project

```bash
cd HostnCodeWebApp
dotnet restore
dotnet build
```

### Running the Application

```bash
cd HostnCodeWebApp/HostnCodeWebApp.AppHost
dotnet run
```

The Aspire dashboard will open automatically, showing the application's telemetry and logs.

### Running Tests

```bash
cd HostnCodeWebApp
dotnet test
```

**Note**: Tests may require Docker to be running as they use Aspire's integration testing framework.

## Coding Conventions

### C# Style Guidelines

- Use C# 12 features and modern patterns
- Enable nullable reference types (`<Nullable>enable</Nullable>`)
- Use implicit usings where appropriate
- Follow Microsoft's C# coding conventions
- Use async/await for asynchronous operations
- Prefer dependency injection over static classes

### Naming Conventions

- PascalCase for public members, types, and namespaces
- camelCase for private fields and local variables
- Prefix private fields with underscore `_` when it improves readability
- Use descriptive names that convey intent

### Project-Specific Patterns

- Use Aspire's service defaults for consistent configuration across services
- Implement structured logging with semantic logging patterns
- Add OpenTelemetry instrumentation for new endpoints and operations
- Follow RESTful API conventions in the ApiService

## What to Modify

✅ **Feel free to modify:**

- Business logic in API services
- UI components and pages in the Web project
- Service configurations in ServiceDefaults
- Test files to increase coverage
- Documentation files

⚠️ **Be cautious when modifying:**

- AppHost configuration (orchestration logic)
- Dependency injection setup
- OpenTelemetry configuration
- Service discovery patterns

❌ **Do not modify:**

- Build artifacts (bin/, obj/ directories)
- `.vs/` directory
- User-specific files (*.user, *.suo)
- NuGet package cache

## Testing Requirements

- Write unit tests for new business logic
- Add integration tests for new API endpoints
- Ensure tests follow the existing xUnit patterns
- Mock external dependencies appropriately
- Tests should be deterministic and not rely on external services

## Documentation

- Update XML documentation comments for public APIs
- Keep README files up to date with new features
- Document configuration changes in appropriate files
- Use clear, concise commit messages

## Best Practices for GitHub Copilot

When working on this repository:

1. **Start with tests**: For bug fixes and new features, write or update tests first
2. **Keep changes focused**: Make small, incremental changes rather than large refactorings
3. **Respect existing patterns**: Follow the established architectural patterns in the codebase
4. **Build frequently**: Run `dotnet build` after making changes to catch errors early
5. **Check the Aspire dashboard**: When making changes to services, verify they appear correctly in the Aspire dashboard
6. **Update dependencies carefully**: Aspire has specific version requirements; check compatibility before updating packages

## Common Tasks

### Adding a New API Endpoint

1. Add the endpoint in `HostnCodeWebApp.ApiService`
2. Add appropriate OpenTelemetry instrumentation
3. Write integration tests in `HostnCodeWebApp.Tests`
4. Update API documentation

### Adding a New Service

1. Create the project in the `HostnCodeWebApp` directory
2. Reference `HostnCodeWebApp.ServiceDefaults` for shared configuration
3. Register the service in `HostnCodeWebApp.AppHost`
4. Add appropriate tests

### Updating Configuration

1. Service-specific config goes in `appsettings.json` in each project
2. Shared config goes in `ServiceDefaults`
3. Environment-specific config uses `appsettings.{Environment}.json`
4. Sensitive data should use User Secrets or environment variables

## Additional Resources

- [.NET Aspire Documentation](https://learn.microsoft.com/dotnet/aspire)
- [C# Coding Conventions](https://learn.microsoft.com/dotnet/csharp/fundamentals/coding-style/coding-conventions)
- [ASP.NET Core Best Practices](https://learn.microsoft.com/aspnet/core/fundamentals/best-practices)
