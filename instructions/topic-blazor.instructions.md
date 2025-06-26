---
applyTo: "*.razor,*.razor.cs"
---

# Blazor Coding Standards

Apply the [ASP.NET Core General Coding Standards](./topic-aspnetcore.instructions.md) to all code.

**Design Patterns & Architecture**

- **Component-Based Model**: Emphasize reusable, platform-agnostic components with a focus on separation of concerns (UI design vs. code).
- **Code-Behind Approach**: Use `.razor.cs` files for business logic, avoiding inline JavaScript in UI components.
- **Parameter & Callbacks**: Avoid business logic in reusable components; use parameters and callbacks for functionality.
- **JS Isolation**: Prefer "modules" approach for JavaScript.

**Rendering Performance**

- **Precise Render Control**: Override `ShouldRender` to minimize unnecessary re-renders.
- **Immutable Data**: Use primitive types (`int`, `string`) and immutable objects for component parameters.
- **Component Granularity**: Break down complex UI into lean, focused components; avoid unnecessary child component rendering.
- **Virtualization**: Use `Virtualize<TItem>` for large data lists/grids to reduce memory usage.
- **Cascading Value Optimization**: Use `IsFixed` flag on `<CascadingValue>` for static values to avoid extraneous subscriptions.
- **Event Handling**: Throttle/debounce high-frequency events (e.g., scrolling) and cache event handlers.
- **Attribute Processing**: Avoid splatting attributes in performance-critical components to reduce overhead.
- **Parameter Setting**: Override `SetParametersAsync` for performance-sensitive scenarios with many parameters to bypass costly reflection-based parameter assignment.

**Best Practices for Blazor**

- **Pre-rendering**: Prefer `OnAfterRenderAsync` over `OnInitializedAsync` for data loading to optimize performance.
- **Navigation**: Use a custom `NavigationService` for routes to avoid code duplication and enable back-button functionality.

## State Management

- Prefer **Cascading Parameters** for application-wide state sharing.
- Use **Dependency Injection (DI)** for service-based state management.
- Implement **local storage** for persistent state.

## UI & Styling

- Use **CSS isolation** for component-specific styles (`.razor.css`).
- Define **global styles** in `wwwroot/css/fsh.css`.
- Utilize MudBlazor for UI components and styling.

## Code Formatting

- each component parameter should be on a new line.

## Dependency Injection

- always inject services in code behind classes
- using this convention for inject localization service: `private IStringLocalizer<name_of_component> L { get; set; } = default!;`
