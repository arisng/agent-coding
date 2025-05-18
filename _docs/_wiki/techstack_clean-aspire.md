# CleanAspire - .NET 9 Minimal API + Blazor WebAssembly PWA Template with Aspire Support 

[![.NET](https://github.com/neozhu/cleanaspire/actions/workflows/dotnet.yml/badge.svg)](https://github.com/neozhu/cleanaspire/actions/workflows/dotnet.yml)
[![CodeQL](https://github.com/neozhu/cleanaspire/actions/workflows/github-code-scanning/codeql/badge.svg)](https://github.com/neozhu/cleanaspire/actions/workflows/github-code-scanning/codeql)
[![Build and Push Docker Image](https://github.com/neozhu/cleanaspire/actions/workflows/docker.yml/badge.svg)](https://github.com/neozhu/cleanaspire/actions/workflows/docker.yml)

![blazorclient](https://github.com/neozhu/cleanaspire/blob/main/blazorclient.jpg?raw=true)

## 🚀 Overview  

Github repo: <https://github.com/neozhu/cleanaspire>

**CleanAspire** is a cutting-edge, open-source template built on **.NET 9**, designed to accelerate the development of **lightweight**, **fast**, and **simple** Blazor WebAssembly or Progressive Web Applications (PWA). It seamlessly integrates **Minimal APIs**, **Aspire**, and **Scalar** for modern API documentation.  

With a focus on **Clean Architecture** and **extreme code simplicity**, CleanAspire provides developers with the tools to create responsive and maintainable web applications with minimal effort. The template also supports **Microsoft.Kiota** to simplify API client generation, ensuring consistency and productivity in every project.

## 🎉 Auto-generate Code Using Chat GPTs

![chatgpt](./gpts.png)
 [Link to CleanAspire Code Generator](https://chatgpt.com/g/g-677e40252ff88191933bb84567b62e7b-cleanaspire-code-generator)

## 🌐 Offline Support  

CleanAspire fully supports **offline mode** through its integrated PWA capabilities, enabling your application to function seamlessly without an internet connection. By leveraging **Service Workers** and **browser caching**, the application can store essential resources and data locally, ensuring quick load times and uninterrupted access. Additionally, CleanAspire offers streamlined configuration options to help developers manage caching strategies and data synchronization effortlessly, guaranteeing that users receive the latest updates once the network is restored.

**Key Features of Offline Support:**

- **Service Workers Integration:** Efficiently handle caching and background synchronization to manage offline functionality.
- **Automatic Resource Caching:** Automatically caches essential assets and API responses, ensuring critical parts of the application are accessible offline.
- **Seamless Data Synchronization:** Maintains data consistency by synchronizing local changes with the server once the connection is reestablished.
- **User Experience Enhancements:** Provides fallback UI components and notifications to inform users about their offline status and any pending actions.

By incorporating robust offline capabilities, CleanAspire empowers developers to build resilient applications that deliver a consistent and reliable user experience, regardless of network conditions.

## 🔑 Key Features  

1. **Built-in Aspire Support**  
   - Fully integrated with **Aspire** for efficient application hosting and configuration.  
   - Simplifies the setup process while providing a robust foundation for lightweight applications.  

2. **Fast and Minimal .NET 9 Minimal APIs**  
   - Uses the latest .NET 9 features to create high-performance and efficient APIs.  
   - Includes **Scalar** for modern and concise OpenAPI documentation, replacing traditional Swagger tools.  

3. **Designed for Simplicity and Speed**  
   - Adopts extreme code simplicity for rapid development without sacrificing functionality.  
   - Ideal for developers looking to build quick, responsive Blazor WebAssembly applications or PWAs.  

4. **Blazor WebAssembly and PWA Integration**  
   - Combines the power of Blazor WebAssembly for interactive and lightweight client-side UIs.  
   - PWA capabilities ensure offline support and a seamless native-like experience, allowing users to access the application and data even when offline.  

5. **Streamlined API Client Integration**  
   - Utilizes **Microsoft.Kiota** to automatically generate strongly-typed API clients, reducing development overhead.  
   - Ensures consistent and error-free client-server communication.  

6. **Clean Architecture**  
   - Promotes modular, maintainable, and testable codebases through clear architectural layers.  

7. **Cloud-Ready with Docker**  
   - Preconfigured for Docker, enabling easy deployment to cloud platforms or local environments.  

8. **Real-Time Web Push Notifications**  
   - Integrated **Webpushr** to deliver instant browser notifications.  
   - Keeps users informed and engaged with real-time updates.  
   - Fully customizable notifications with targeted delivery and analytics support.  

9. **Integrated CI/CD Pipelines**  
   - Includes GitHub Actions workflows for automated building, testing, and deployment.  

10. **Offline Mode Support**  
    - **Offline mode enabled by default** to provide a seamless experience even without internet access.  
    - Uses **IndexedDB** to cache data locally, allowing the application to retrieve data and function offline.  
    - The system detects the online/offline status and fetches data from **IndexedDB** when offline, ensuring uninterrupted access to key features.

## How to Create a New Object in a CRUD Application: A Step-by-Step Guide

<https://github.com/neozhu/cleanaspire/issues/34>

## 🌟 Why Choose CleanAspire?  

- **Lightweight and Fast:** Designed to create high-performance, minimal Blazor WebAssembly or PWA projects.  
- **Effortless Development:** Extreme simplicity in code makes it easy to start quickly and scale effectively.  
- **Advanced API Integration:** Automate client-side API generation with Microsoft.Kiota for faster results.  
- **Future-Ready Architecture:** Leverages the latest .NET 9 capabilities and Aspire hosting for modern web applications.
-

## OpenAPI documentation

- <https://apiservice.blazorserver.com/scalar/v1>
- <https://cleanapi.blazors.app:8443/scalar/v1>

## Demo site

- <https://cleanweb.blazors.app:8443/>

## Blazor WebAssembly Standalone PWA

- <https://standalone.blazorserver.com/>
- <https://standalone.blazors.app:8443/>

## Quick Start

1. **Clone the Repo**:

   ```bash
   git clone https://github.com/neozhu/cleanaspire.git
   ```

2. **Navigate to the Project Folder**:

   ```bash
   cd CleanAspire
   ```

3. **Run the Application**:

   ```bash
   dotnet run
   ```

4. **Access the Application**:
   Open your browser and go to `https://localhost:5001` to see the Blazor WebAssembly PWA in action.

## Architecture

CleanAspire is structured following the **Clean Architecture** approach, dividing the solution into distinct layers:

```text
CleanAspire/
│
├── Solution Items/
│   ├── .editorconfig
│
├── src/
│   ├── CleanAspire.Api/                # API Layer - .NET Minimal API
│   │   └── CleanAspire.Api.csproj
│   ├── CleanAspire.AppHost/            # Hosting Layer - Application hosting and configuration
│   │   └── CleanAspire.AppHost.csproj
│   ├── CleanAspire.Application/        # Application Layer - Business Logic
│   │   └── CleanAspire.Application.csproj
│   ├── CleanAspire.ClientApp/          # Client App Layer - Blazor WebAssembly or other client logic
│   │   └── CleanAspire.ClientApp.csproj
│   ├── CleanAspire.Domain/             # Domain Layer - Core Entities, including EF entities
│   │   └── CleanAspire.Domain.csproj
│   ├── CleanAspire.Infrastructure/     # Infrastructure Layer - Data Access, External Services
│   │   └── CleanAspire.Infrastructure.csproj
│   ├── CleanAspire.ServiceDefaults/    # Service Defaults - Predefined configurations for services
│   │   └── CleanAspire.ServiceDefaults.csproj
│
├── src/Migrators/
│   ├── Migrators.MSSQL/                # SQL Server Migration Scripts
│   │   └── Migrators.MSSQL.csproj
│   ├── Migrators.PostgreSQL/           # PostgreSQL Migration Scripts
│   │   └── Migrators.PostgreSQL.csproj
│   ├── Migrators.SQLite/               # SQLite Migration Scripts
│   │   └── Migrators.SQLite.csproj
│
├── tests/
│   ├── CleanAspire.Tests/              # Unit and Integration Tests
│   │   └── CleanAspire.Tests.csproj
│
├── README.md                           # Project README
├── LICENSE                             # License Information
└── CleanAspire.sln                     # Solution File
```
