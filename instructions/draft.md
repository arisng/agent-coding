Certainly! Here's a detailed `.instructions.md` file for a Blazor WebAssembly (Blazor WASM) project:

```markdown
---
applyTo: "**/*.razor, **/*.cs"
---

# Blazor WebAssembly Development Guidelines

## General Principles
- Use **Blazor WebAssembly** for interactive client-side applications.
- Prefer **component-based architecture** for modular and reusable UI elements.
- Ensure **efficient state management** using dependency injection and proper binding.

## Project Structure
- Follow a **clean folder structure**:
```

/BlazorApp
├── wwwroot/       # Static assets (CSS, JS, images)
├── Components/    # Reusable Blazor components
├── Pages/         # Page-specific components
├── Services/      # Business logic and API calls
├── Shared/        # Layouts and shared components
├── Models/        # Data models
├── wwwroot/css/   # Global styles

```
- Use **partial classes** in `Pages/` for clean separation of UI and logic.

## Component Development
- Define **Blazor components** in `.razor` files:
  ```razor
  <h3>@Title</h3>
  <p>@Description</p>

  @code {
    [Parameter] public string Title { get; set; }
    [Parameter] public string Description { get; set; }
  }
  ```

- Use **EventCallback** instead of `Action` for event handling:

  ```razor
  <button @onclick="OnClick">Click Me</button>

  @code {
    [Parameter] public EventCallback OnClick { get; set; }
  }
  ```

- Avoid **excessive re-renders** by using `shouldRender`.

## State Management

- Prefer **Cascading Parameters** for application-wide state sharing.
- Use **Dependency Injection (DI)** for service-based state management.
- Implement **local storage** for persistent state:

  ```csharp
  using Microsoft.JSInterop;
  
  public class LocalStorageService
  {
      private readonly IJSRuntime _jsRuntime;
      public LocalStorageService(IJSRuntime jsRuntime) => _jsRuntime = jsRuntime;

      public async Task SetItemAsync(string key, string value) =>
          await _jsRuntime.InvokeVoidAsync("localStorage.setItem", key, value);

      public async Task<string> GetItemAsync(string key) =>
          await _jsRuntime.InvokeAsync<string>("localStorage.getItem", key);
  }
  ```

- Use `ObservableObject` from `CommunityToolkit.Mvvm` for state binding in MVVM.

## API Integration

- Use **HttpClient** for fetching data:

  ```csharp
  using System.Net.Http;
  using System.Threading.Tasks;
  using System.Text.Json;

  public class DataService
  {
      private readonly HttpClient _httpClient;
      public DataService(HttpClient httpClient) => _httpClient = httpClient;

      public async Task<List<Item>> GetItemsAsync()
      {
          var response = await _httpClient.GetStringAsync("https://api.example.com/items");
          return JsonSerializer.Deserialize<List<Item>>(response);
      }
  }
  ```

- Implement **error handling** for API failures:

  ```csharp
  try
  {
      var response = await _httpClient.GetAsync("https://api.example.com/items");
      response.EnsureSuccessStatusCode();
  }
  catch (HttpRequestException ex)
  {
      Console.WriteLine($"Error fetching data: {ex.Message}");
  }
  ```

## UI & Styling

- Use **CSS isolation** for component-specific styles (`.razor.css`).
- Define **global styles** in `wwwroot/css/site.css`.
- Prefer **Bootstrap or Tailwind CSS** for UI design.

## Optimization & Performance

- Enable **AOT compilation** for faster load times.
- Reduce **Blazor WASM bundle size** using tree shaking.
- Use **lazy loading** for non-critical components:

  ```razor
  <LazyComponent type="typeof(MyComponent)" />
  ```

## Testing & Debugging

- Use **bUnit** for component testing:

  ```csharp
  using Bunit;
  using Xunit;
  
  public class MyComponentTest
  {
      [Fact]
      public void ShouldRenderTitle()
      {
          var ctx = new TestContext();
          var component = ctx.RenderComponent<MyComponent>(parameters => parameters.Add(p => p.Title, "Test Title"));

          Assert.Contains("Test Title", component.Markup);
      }
  }
  ```

- Utilize **logging** for debugging (`ILogger`).
- Use **hot reload** for UI changes.

## Deployment & CI/CD

- Publish **Blazor WASM as a static site**:

  ```bash
  dotnet publish -c Release --output ./publish
  ```

- Configure **GitHub Actions** for automated builds.
- Host on **Azure Static Web Apps**, **Netlify**, or **GitHub Pages**.

---

This `.instructions.md` file ensures a structured, efficient, and scalable Blazor WebAssembly project. 🚀 Let me know if you need modifications!

```
