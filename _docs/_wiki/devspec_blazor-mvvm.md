# Development Specification: Integrating DotVVM ViewModel Concepts into Blazor WASM with Best Practices

- [Development Specification: Integrating DotVVM ViewModel Concepts into Blazor WASM with Best Practices](#development-specification-integrating-dotvvm-viewmodel-concepts-into-blazor-wasm-with-best-practices)
  - [1. Introduction](#1-introduction)
  - [2. Objectives](#2-objectives)
  - [3. Architectural Overview](#3-architectural-overview)
  - [4. Implementation Details](#4-implementation-details)
    - [4.1. Designing the ViewModel Using Best Practices](#41-designing-the-viewmodel-using-best-practices)
      - [4.1.1. Separation of Properties (Different Semantics)](#411-separation-of-properties-different-semantics)
      - [4.1.2. Avoid Business Logic in the ViewModel](#412-avoid-business-logic-in-the-viewmodel)
      - [4.1.3. Use of Nested ViewModels](#413-use-of-nested-viewmodels)
    - [4.2. Registering the ViewModel with Dependency Injection](#42-registering-the-viewmodel-with-dependency-injection)
    - [4.3. Integrating the ViewModel into Blazor Components](#43-integrating-the-viewmodel-into-blazor-components)
    - [4.4. Approaches for State Persistence](#44-approaches-for-state-persistence)
      - [4.4.1. In-Memory Persistence](#441-in-memory-persistence)
      - [4.4.2. Local/Session Storage Using JS Interop](#442-localsession-storage-using-js-interop)
      - [4.4.3. Server-Side Persistence (Optional)](#443-server-side-persistence-optional)
  - [5. Testing and Validation](#5-testing-and-validation)
  - [6. Future Enhancements](#6-future-enhancements)
  - [7. Conclusion](#7-conclusion)

## 1. Introduction

This document outlines how to integrate a DotVVM-style ViewModel into an existing Blazor WebAssembly (WASM) application while incorporating best practices from DotVVM. By applying these practices, we aim to create clear, maintainable, and secure state management that separates core data, UI state, and auxiliary (environment) data. Furthermore, this spec covers approaches for both in-memory and persisted state.

## 2. Objectives

- **Centralize State Management:** Encapsulate UI state and user actions in dedicated ViewModel classes.
- **Adopt Best Practices:** Structure the ViewModel by:
  - **Separating Concerns:** 
    - **Main Data:** Core data exposed via Data Transfer Objects (DTOs) with simple get/set properties.
    - **Page State:** Transient values controlling UI behavior (e.g., editability) isolated from data.
    - **Environment Data:** Auxiliary, read-only data used to populate UI controls.
- **Leverage Dependency Injection:** Register and inject viewmodels as scoped services across components.
- **State Persistence:** Outline methods for preserving state using in-memory storage, browser storage, or server-side persistence.
- **Maintain a Clean Separation:** Keep presentation logic in the viewmodel and delegate complex business logic and database access to separate layers.

## 3. Architectural Overview

- **ViewModel Classes:** The core classes that hold UI state and provide methods to trigger user actions. They must be simple, with no business processing in getters/setters.
- **Data Separation:** Main data is defined in DTOs, while UI state and environmental data are maintained as separate properties or nested viewmodels.
- **Dependency Injection:** Register viewmodels as scoped services for easy access across components with minimal overhead.
- **State Persistence Strategies:** Provide options to save state locally on the client (via local/session storage) or on the server via API endpoints.

## 4. Implementation Details

### 4.1. Designing the ViewModel Using Best Practices

#### 4.1.1. Separation of Properties (Different Semantics)

- **Main Data:**  
  Use simple DTOs to hold core data. DTOs should expose properties as plain `{ get; set; }` without side effects.  
  **Example:**

  ```csharp
  public class CustomerDetailDto
  {
      public int Id { get; set; }
      public string FirstName { get; set; }
      public string LastName { get; set; }
      public int CountryId { get; set; }
  }
  ```

- **Page State:**  
  Stores transient values (e.g., whether a user can edit data). Mark these properties or use additional server-side measures (e.g., signing data) to prevent tampering.  
  **Example:**

  ```csharp
  public bool IsEditable { get; set; }
  ```

- **Environment Data:**  
  Holds auxiliary data (e.g., lists for dropdowns) required by the UI but not part of the main entity.  
  **Example:**

  ```csharp
  public List<CountryDto> Countries { get; set; } = new List<CountryDto>();
  ```

#### 4.1.2. Avoid Business Logic in the ViewModel

- **Guideline:**  
  Viewmodels should handle presentation logic (e.g., data formatting) and delegate database interactions or other external communications to dedicated service or business layers.
  
- **Example:**

  ```csharp
  public class CustomerDetailViewModel
  {
      public CustomerDetailDto Customer { get; set; } = new CustomerDetailDto();
      public bool IsEditable { get; set; }
      public List<CountryDto> Countries { get; set; } = new List<CountryDto>();

      public async Task SaveAsync(ICustomerService customerService)
      {
          // Delegate business processing to the service layer
          await customerService.SaveCustomerAsync(Customer);
      }
  }
  ```

#### 4.1.3. Use of Nested ViewModels

- **Recommendation:**  
  For complex pages (e.g., pages with multiple logical sections or dialogs), decompose the viewmodel into nested viewmodels. This separation improves readability and maintainability.
  
- **Example:**

  ```csharp
  public class PageViewModel
  {
      public CustomerDetailViewModel CustomerDetail { get; set; } = new CustomerDetailViewModel();
      public OrderHistoryViewModel OrderHistory { get; set; } = new OrderHistoryViewModel();
  }
  ```

### 4.2. Registering the ViewModel with Dependency Injection

- **Purpose:**  
  Making viewmodels available as scoped services ensures that they persist across the user's session within the application.

- **Example (in Program.cs):**

  ```csharp
  builder.Services.AddScoped<CustomerDetailViewModel>();
  ```

### 4.3. Integrating the ViewModel into Blazor Components

- **Injection and Data Binding:**  
  Inject the viewmodel into Razor components and bind UI elements using Blazor’s `@bind` syntax.
  
- **Example: CustomerDetail.razor**

  ```razor
  @page "/customer-detail"
  @inject CustomerDetailViewModel ViewModel
  @inject ICustomerService customerService

  <div>
      <label>First Name:</label>
      <input type="text" @bind="ViewModel.Customer.FirstName" placeholder="Enter first name" />
  </div>
  <div>
      <label>Last Name:</label>
      <input type="text" @bind="ViewModel.Customer.LastName" placeholder="Enter last name" />
  </div>
  <div>
      <label>Country:</label>
      <select @bind="ViewModel.Customer.CountryId">
          @foreach (var country in ViewModel.Countries)
          {
              <option value="@country.Id">@country.Name</option>
          }
      </select>
  </div>
  <button @onclick="() => ViewModel.SaveAsync(customerService)">Save</button>
  ```

### 4.4. Approaches for State Persistence

#### 4.4.1. In-Memory Persistence

- **Method:**  
  Rely on DI-scoped instances which persist for the duration of a user’s session in the current application instance.
- **Consideration:**  
  This approach loses the state on a full page refresh.

#### 4.4.2. Local/Session Storage Using JS Interop

- **Process:**
  1. **Serialization:**  
     Ensure the viewmodel is JSON-serializable. Use `JsonSerializer` to convert the viewmodel into a string.
  2. **Saving/Restoring State:**  
     Use JavaScript Interop to store and retrieve the state from localStorage (or sessionStorage).
  
- **Example:**

  ```razor
  @inject IJSRuntime JS

  @code {
      protected override async Task OnInitializedAsync()
      {
          // Retrieve the stored JSON state from localStorage
          var json = await JS.InvokeAsync<string>("localStorage.getItem", "CustomerDetailViewModel");
          if (!string.IsNullOrEmpty(json))
          {
              var restored = JsonSerializer.Deserialize<CustomerDetailViewModel>(json);
              // Update current ViewModel with restored values
              ViewModel.Customer = restored.Customer;
              ViewModel.IsEditable = restored.IsEditable;
              ViewModel.Countries = restored.Countries;
          }
      }

      private async Task SaveStateAsync()
      {
          var json = JsonSerializer.Serialize(ViewModel);
          await JS.InvokeVoidAsync("localStorage.setItem", "CustomerDetailViewModel", json);
      }
  }
  ```

  - **Action Points:**  
    Trigger the `SaveStateAsync` method after significant state updates, such as after a “Save” operation.

#### 4.4.3. Server-Side Persistence (Optional)

- **Purpose:**  
  For scenarios where state must be reliably preserved across sessions or devices.
- **Implementation:**  This specification now incorporates the best practices (such as property separation, minimal logic in getters/setters, and the effective use of nested viewmodels) along with our strategies for state persistence using both client- and server-based approaches.
  Expose API endpoints to save and restore the serialized viewmodel.
- **Security Consideration:**  
  Ensure strong authentication, authorization, and encryption to protect sensitive data.

## 5. Testing and Validation

- **Unit Testing:**  
  Create tests to verify that viewmodel methods (e.g., calculations, state updates) function as expected.
- **Integration Testing:**  
  Validate state persistence scenarios (both client- and server-side) to ensure state is properly saved and restored.
- **Security Assessment:**  
  Review data serialization to guarantee that sensitive information is not unnecessarily exposed on the client.

## 6. Future Enhancements

- **Robust Error Handling:**  
  Enhance error handling during interactions with browser storage or server endpoints.
- **Optimized Serialization:**  
  Examine performance implications when serializing large viewmodel data and optimize as needed.
- **Extended State Management:**  
  Consider advanced patterns (e.g., Redux-style state containers) for more complex applications.
- **Client-to-Server Integrity Checks:**  
  Explore the use of signing or encryption to defend against client tampering with state values.

## 7. Conclusion

This specification now incorporates the best practices (such as property separation, minimal logic in getters/setters, and the effective use of nested viewmodels) along with our strategies for state persistence using both client- and server-based approaches.
By integrating the DotVVM ViewModel concepts with these best practices into your Blazor WASM application, you achieve a clear separation of concerns, streamlined state management, and enhanced security. 
This specification ensures that the presentation layer remains clean while business logic stays in its rightful place, whether you opt for in-memory, local storage, or server-side state persistence.

*Additional topics for further exploration:*  

- Advanced nested viewmodel management for large UIs.  
- Integration with external caching or synchronization strategies.
