## Architecture (SOLID)
- Single Responsibility: one class = one purpose
- Open/Closed: extend via abstraction, never modify stable code
- Dependency Inversion: depend on abstractions, never concrete implementations
- Prefer composition over inheritance
- Inject all dependencies — never instantiate services inside classes
- All external services behind interfaces (DB, API, cache)

## Planning Rules
- Think deeply before architecture decisions
- Break large tasks into subtasks — confirm plan before implementing
- Never over-engineer — solve the actual problem
- Layer separation: routes → controllers → services → repositories
- Never put business logic in route handlers or middleware
