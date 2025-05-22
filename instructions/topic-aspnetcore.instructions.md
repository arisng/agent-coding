# ASP.NET Core General Coding Standards

## Coding Style

- use file scoped namespace
- use region directives to group related code
- use explicit type declarations instead of `var` when the type is not obvious
- using nullable reference types if necessary
- put method invocations on a new line for multiple chained calls (just like fluent APIs)

## Naming Conventions

- private field naming convention: `_fieldName`
- public property naming convention: `PropertyName`

## Libraries

- use Mapster for mapping between DTOs and entities