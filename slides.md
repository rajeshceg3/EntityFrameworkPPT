---
theme: '@slidev/theme-default'
background: 'linear-gradient(45deg, #1e3c72, #2a5298)'
highlighter: prism
lineNumbers: true
info: |
  ## Entity Framework Mastery
  A comprehensive guide to EF Core
drawings:
  persist: false
transition: slide-left
title: 'Mastering Entity Framework'
style: ./styles/custom.css # Link to custom styles
fonts:
  sans: 'Inter'
  serif: 'Inter'
  mono: 'Fira Code'
---

<!--
Note for Jules/User:
Using a generic database icon as a placeholder for the EF Core logo for now.
We can replace `/ef-logo-placeholder.svg` with an actual logo path if found.
A simple SVG icon for a database:
<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-database"><ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M21 12c0 1.66-4 3-9 3s-9-1.34-9-3"/><path d="M3 5v14c0 1.66 4 3 9 3s9-1.34 9-3V5"/></svg>
Will save this as public/ef-logo-placeholder.svg
-->

<div class="slidev-layout cover text-center">
  <div class="my-auto w-full">
    <img src="/ef-logo-placeholder.svg" alt="EF Logo" class="mx-auto mb-4 h-40" />
    <h1 class="text-5xl font-bold">Entity Framework Mastery</h1>
    <p class="text-2xl opacity-75">Mastering Data Access in .NET</p>
    <p class="mt-8 text-lg">
      By: <span class="font-semibold">[Your Name]</span> // <span class="font-semibold">[Date]</span>
    </p>
    <p class="mt-4 text-xl italic text-green-300">"From Code-First to Database-First Adventures!"</p>
  </div>
</div>

---
layout: default
---

# What is Entity Framework? (1/2)

<div class="grid grid-cols-2 gap-8 items-center">
<div>

Entity Framework (EF) is an **Object-Relational Mapper (ORM)** that enables .NET developers to work with a database using .NET objects. It eliminates the need for most of the data-access code that developers usually need to write.

<br/>

**Key Idea:** Work with your data as objects and let EF handle the database interactions. 💾➡️💻

</div>
<div>

<!-- Placeholder for Visual Metaphor -->
<div class="p-4 border rounded-lg text-center bg-gray-700">
  <p class="text-6xl">🌉</p>
  <p>EF as a Bridge</p>
  <p class="text-sm opacity-75">Your C# code speaks "objects", the database speaks "tables & rows". EF is the skilled interpreter in between.</p>
</div>

**ORM Concept:**
- Maps database tables to C# classes (Entities).
- Maps table columns to class properties.
- Allows CRUD operations using LINQ or EF-specific methods.
- Abstracts database-specific SQL.

</div>
</div>

---
layout: default
---

# What is Entity Framework? (2/2)

## Why use EF over Raw SQL?

<ul v-clicks>
  <li class="mb-2 flex items-start">
    <span class="text-green-400 mr-2 text-xl">🚀</span>
    <div>
      <strong>Increased Developer Productivity:</strong>
      <br/><span class="text-sm opacity-80">Less boilerplate data access code (ADO.NET), faster development cycles.</span>
    </div>
  </li>
  <li class="mb-2 flex items-start">
    <span class="text-green-400 mr-2 text-xl">🛡️</span>
    <div>
      <strong>Improved Maintainability:</strong>
      <br/><span class="text-sm opacity-80">Strongly-typed queries, compile-time checks, easier refactoring.</span>
    </div>
  </li>
  <li class="mb-2 flex items-start">
    <span class="text-green-400 mr-2 text-xl">🔄</span>
    <div>
      <strong>Database Agnostic (mostly):</strong>
      <br/><span class="text-sm opacity-80">Easier to switch database providers with minimal code changes (e.g., SQL Server to PostgreSQL).</span>
    </div>
  </li>
  <li class="mb-2 flex items-start">
    <span class="text-green-400 mr-2 text-xl">🔒</span>
    <div>
      <strong>Built-in Security Features:</strong>
      <br/><span class="text-sm opacity-80">Helps prevent SQL injection attacks by parameterizing queries by default.</span>
    </div>
  </li>
  <li class="mb-2 flex items-start">
    <span class="text-green-400 mr-2 text-xl">🧩</span>
    <div>
      <strong>Integration with .NET Ecosystem:</strong>
      <br/><span class="text-sm opacity-80">Works seamlessly with LINQ, ASP.NET Core, and other .NET libraries.</span>
    </div>
  </li>
</ul>

<br/>

> <p class="text-2xl italic text-purple-300 text-center p-4 bg-black bg-opacity-20 rounded-md">
>   "EF is like a highly skilled translator fluent in both C# and various database dialects, ensuring smooth communication." 🗣️📜
> </p>

---
layout: default
---

# EF Evolution Timeline (1/2) 🕰️

## From EF6 to EF Core: A Journey of Modernization

<div class="mt-6">
  <p class="text-lg">Entity Framework has evolved significantly. Here's a simplified timeline:</p>
  <ul class="list-disc pl-6 mt-4 space-y-2">
    <li>
      <strong>Entity Framework 1-5 (Classic EF, ~2008-2012):</strong>
      <br/><span class="text-sm opacity-75">Initial versions, part of .NET Framework. Introduced LINQ to Entities, EDMX (XML-based model).</span>
    </li>
    <li>
      <strong>Entity Framework 6 (EF6, ~2013):</strong>
      <br/><span class="text-sm opacity-75">Matured version for .NET Framework. Stable, feature-rich, but tied to Windows and System.Data.SqlClient. Still supported for legacy applications.</span>
    </li>
    <li>
      <strong>Entity Framework Core 1.0 (EF Core, ~2016):</strong>
      <br/><span class="text-sm opacity-75">Complete rewrite. Cross-platform, lightweight, extensible. Focused on performance and modern .NET. Initially lacked some EF6 features.</span>
    </li>
    <li>
      <strong>EF Core 2.x-3.x (~2017-2019):</strong>
      <br/><span class="text-sm opacity-75">Bridged feature gaps, significant LINQ provider improvements, performance enhancements.</span>
    </li>
    <li>
      <strong>EF Core 5.x (~2020):</strong>
      <br/><span class="text-sm opacity-75">Many-to-many relationships without join entity, filtered include, improved TPT mapping.</span>
    </li>
    <li>
      <strong>EF Core 6.x-8.x (~2021-Present):</strong>
      <br/><span class="text-sm opacity-75">Continued performance boosts (TechEmpower benchmarks), compiled models, temporal tables, JSON columns support, and more. Aligned with .NET release cadence.</span>
    </li>
  </ul>
  <p class="mt-4 text-center text-purple-300 italic">
    <!-- Placeholder for a Mermaid timeline diagram -->
    (Visual timeline diagram can be added here using Mermaid or a custom component)
  </p>
</div>

---
layout: default
---

# EF Evolution Timeline (2/2) 🚀

## EF6 vs EF Core: Key Differences & Improvements

<div class="grid grid-cols-2 gap-6 mt-4">
<div>
  <h3 class="text-xl font-semibold text-blue-300 mb-2">Entity Framework 6 (EF6)</h3>
  <ul class="list-disc pl-5 space-y-1 text-sm">
    <li>Windows-only, .NET Framework.</li>
    <li>Mature, stable, rich feature set.</li>
    <li>EDMX (XML designer) support.</li>
    <li>Can be slower, heavier.</li>
    <li>Limited extensibility.</li>
    <li>Magic strings for some configurations.</li>
    <li>Lazy loading enabled by default.</li>
  </ul>
</div>
<div>
  <h3 class="text-xl font-semibold text-green-300 mb-2">Entity Framework Core (EF Core)</h3>
  <ul class="list-disc pl-5 space-y-1 text-sm">
    <li>Cross-platform (Windows, macOS, Linux).</li>
    <li>Lightweight, modular, highly performant.</li>
    <li>No EDMX; Code-First & Fluent API focus.</li>
    <li>Designed for modern .NET (.NET Core / .NET 5+).</li>
    <li>Highly extensible, pluggable providers.</li>
    <li>Strongly-typed configurations.</li>
    <li>Lazy loading available but needs explicit setup.</li>
    <li>Batching, compiled models, advanced querying.</li>
  </ul>
</div>
</div>

<div class="mt-8 text-center">
  <h3 class="text-xl font-semibold mb-2">Performance Comparisons 📊</h3>
  <p class="opacity-80">
    EF Core generally outperforms EF6 significantly in various benchmarks due to its modern architecture and continuous optimizations.
    <br/> (Placeholder: Charts showing EF Core's performance gains in query speed, inserts, etc., often citing TechEmpower benchmarks or specific scenarios).
  </p>
  <div class="mt-4 p-3 bg-gray-700 rounded-lg">
    <p class="text-sm text-yellow-300">📈 EF Core consistently shows improvements in speed and resource usage with each major release.</p>
  </div>
</div>

---
layout: default
---

# Getting Started (1/3) 🚀

## Installation via NuGet Package Manager

Entity Framework Core is installed as a set of NuGet packages. The primary package you'll usually start with is the one for your specific database provider.

**1. Choose your Database Provider:**
   - For SQL Server: `Microsoft.EntityFrameworkCore.SqlServer`
   - For PostgreSQL: `Npgsql.EntityFrameworkCore.PostgreSQL`
   - For SQLite: `Microsoft.EntityFrameworkCore.Sqlite`
   - For MySQL: `Pomelo.EntityFrameworkCore.MySql`
   - For In-Memory (testing): `Microsoft.EntityFrameworkCore.InMemory`

**2. Install using Package Manager Console (Visual Studio):**
```powershell
# Example for SQL Server
Install-Package Microsoft.EntityFrameworkCore.SqlServer

# Example for EF Core Tools (for migrations)
Install-Package Microsoft.EntityFrameworkCore.Tools
```

**3. Install using .NET CLI:**
```bash
# Example for SQL Server
dotnet add package Microsoft.EntityFrameworkCore.SqlServer

# Example for EF Core Tools (for migrations)
dotnet add package Microsoft.EntityFrameworkCore.Tools
```
<div class="mt-4 p-3 bg-gray-700 rounded-lg">
  <p class="text-sm text-yellow-300 flex items-center">
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mr-2 lucide lucide-alert-triangle"><path d="m21.73 18-8-14a2 2 0 0 0-3.46 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3Z"/><path d="M12 9v4"/><path d="M12 17h.01"/></svg>
    Always ensure your EF Core packages (e.g., `SqlServer`, `Tools`, `Design`) are the same version!
  </p>
</div>

---
layout: default
---

# Getting Started (2/3) 🛠️

## Basic Project Setup (Console App Example)

Let's set up a simple console application.

**1. Create a new Console App:**
```bash
dotnet new console -o MyEfApp
cd MyEfApp
```

**2. Add EF Core Packages (e.g., for SQLite & Tools):**
```bash
dotnet add package Microsoft.EntityFrameworkCore.Sqlite
dotnet add package Microsoft.EntityFrameworkCore.Design # Needed for design-time operations
dotnet add package Microsoft.EntityFrameworkCore.Tools # For dotnet-ef commands
```
*(Note: `Microsoft.EntityFrameworkCore.Design` is crucial for migrations and scaffolding)*

**3. Create your first Entity and DbContext (example):**
   (We'll dive deeper into these in the next sections!)

```csharp
// In MyEfApp/Model.cs (Create this file)
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic;

public class BloggingContext : DbContext
{
    public DbSet<Blog> Blogs { get; set; }

    public string DbPath { get; }

    public BloggingContext()
    {
        var folder = Environment.SpecialFolder.LocalApplicationData;
        var path = Environment.GetFolderPath(folder);
        DbPath = System.IO.Path.Join(path, "blogging.db");
    }

    // The following configures EF to create a Sqlite database file in the
    // special "local" folder for your platform.
    protected override void OnConfiguring(DbContextOptionsBuilder options)
        => options.UseSqlite($"Data Source={DbPath}");
}

public class Blog
{
    public int BlogId { get; set; }
    public string Url { get; set; }
    public List<Post> Posts { get; set; } = new(); // Initialize collection
}

public class Post // Added for completeness, will be detailed later
{
    public int PostId { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }
    public int BlogId { get; set; }
    public Blog Blog { get; set; }
}
```
<span class="text-xs text-gray-400">This is a simplified example from Microsoft's docs to illustrate setup.</span>

---
layout: default
---

# Getting Started (3/3) 🔌

## Connection String Configuration

How your application connects to the database is crucial.

**1. Storing Connection Strings (ASP.NET Core Example):**
   Usually in `appsettings.json`:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\mssqllocaldb;Database=MyEfCoreDb;Trusted_Connection=True;"
  }
  // ... other settings
}
```

**2. Configuring DbContext in `Program.cs` or `Startup.cs` (ASP.NET Core):**
   You register your `DbContext` with the dependency injection container.

```csharp
// Program.cs (using minimal APIs in .NET 6+)
using Microsoft.EntityFrameworkCore;
// ... other usings ...

var builder = WebApplication.CreateBuilder(args);

// Retrieve connection string
var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");

// Add DbContext to services
builder.Services.AddDbContext<ApplicationDbContext>(options => // Replace ApplicationDbContext with your context
    options.UseSqlServer(connectionString)); // Or UseNpgsql, UseSqlite, etc.

// ... Add other services ...

var app = builder.Build();

// ... Configure middleware ...

app.Run();

// --- Example ApplicationDbContext (simplified) ---
// public class ApplicationDbContext : DbContext
// {
//     public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options) : base(options) { }
//     // public DbSet<YourEntity> YourEntities { get; set; }
// }
```
<div class="mt-2 p-2 bg-blue-900 rounded-md text-sm">
  <p class="text-blue-200">💡 **Tip:** For non-ASP.NET Core apps (like Console or WPF), you might configure the connection string directly in `OnConfiguring` or pass `DbContextOptions` manually.</p>
</div>

---
layout: default
---

# DbContext Deep Dive (1/4) 🌊

## What is `DbContext`?

The `DbContext` class is the **heart ❤️💾 of Entity Framework Core**. It's your primary API for interacting with the database.

Think of it as:
<ul>
  <li class="mb-2">A **session** with the database: It represents a single unit of work.</li>
  <li class="mb-2">A **gateway** to database operations: All queries and save operations go through it.</li>
  <li class="mb-2">A **tracker** of changes: It keeps track of changes made to entities during its lifetime.</li>
  <li class="mb-2">A **configuration hub**: It's where you configure database connections, model mappings (via Fluent API), and other EF Core behaviors.</li>
</ul>

<div class="mt-4 p-3 bg-gray-700 rounded-lg">
  <p class="text-sm text-yellow-300">Key responsibilities of a `DbContext` instance:</p>
  <ul class="list-disc pl-5 text-sm text-gray-300 mt-1">
    <li>Querying data from the database (LINQ to Entities).</li>
    <li>Change tracking for loaded entities.</li>
    <li>Persisting changes back to the database (`SaveChanges()`).</li>
    <li>Managing database connections and transactions.</li>
    <li>Caching data (first-level cache).</li>
  </ul>
</div>

Typically, you create a class that derives from `DbContext` for your application.

---
layout: default
---

# DbContext Deep Dive (2/4) 🧱

## Creating Your First Context

You'll define a class that inherits from `Microsoft.EntityFrameworkCore.DbContext`.

**1. Constructor and Options:**
   - Your context needs `DbContextOptions` to be configured. These options tell EF Core how to connect to the database, which provider to use, etc.
   - For ASP.NET Core, these options are typically injected via Dependency Injection.
   - For other app types, you might configure them in `OnConfiguring` or pass them manually.

**Example: Context for an ASP.NET Core application:**
```csharp
// MyAppContext.cs
using Microsoft.EntityFrameworkCore;

public class MyAppContext : DbContext
{
    // Constructor used by Dependency Injection
    public MyAppContext(DbContextOptions<MyAppContext> options)
        : base(options)
    {
    }

    // DbSet properties for your entities go here
    // public DbSet<Product> Products { get; set; }
    // public DbSet<Order> Orders { get; set; }
}
```
<div class="text-xs text-gray-400 mt-1">
  In `Program.cs` (or `Startup.cs`), you'd register this like:
  `builder.Services.AddDbContext<MyAppContext>(opt => opt.UseSqlServer(connStr));`
</div>

This setup allows `MyAppContext` to be injected into your services, controllers, etc.

---
layout: default
---

# DbContext Deep Dive (3/4)  DbSet

## `DbSet<TEntity>` Properties

Inside your custom `DbContext` class, you define properties of type `DbSet<TEntity>` for each entity (table) you want to interact with.

```csharp
public class Product
{
    public int ProductId { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}

public class Order
{
    public int OrderId { get; set; }
    public DateTime OrderDate { get; set; }
    // ... other properties
}

// --- In your DbContext class ---
public class MyAppContext : DbContext
{
    public MyAppContext(DbContextOptions<MyAppContext> options) : base(options) { }

    public DbSet<Product> Products { get; set; } // Represents the 'Products' table
    public DbSet<Order> Orders { get; set; }     // Represents the 'Orders' table
}
```

**What `DbSet<TEntity>` allows you to do:**
<ul>
  <li>Serves as the entry point for querying a specific table (e.g., `context.Products.Where(...)`).</li>
  <li>Used to add new entities (`context.Products.Add(...)`).</li>
  <li>Used to remove entities (`context.Products.Remove(...)`).</li>
  <li>Participates in change tracking when entities are queried or modified.</li>
</ul>

<p class="mt-3 text-sm opacity-80">EF Core will typically use the property name (e.g., "Products") as the default table name, but this can be overridden using Fluent API or Data Annotations.</p>

---
layout: default
---

# DbContext Deep Dive (4/4) 📖 Example

## Code Example: `BlogContext`

Here's the `BlogContext` example as requested, demonstrating a common setup with `OnConfiguring` for simpler scenarios (like console apps or when DI isn't heavily used for context configuration).

```csharp
using Microsoft.EntityFrameworkCore;
using System.Collections.Generic; // For List<T>

// --- Define your entities first ---
public class Blog
{
    public int BlogId { get; set; }
    public string Url { get; set; } // Renamed from Title in issue for clarity
    public List<Post> Posts { get; set; } = new List<Post>();
}

public class Post
{
    public int PostId { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }
    public int BlogId { get; set; }
    public Blog Blog { get; set; }
}

// --- Then, define your DbContext ---
public class BlogContext : DbContext
{
    public DbSet<Blog> Blogs { get; set; }
    public DbSet<Post> Posts { get; set; }

    // This method is called by EF Core when it needs to configure the context.
    // It's often used for apps that don't use ASP.NET Core's DI system
    // or when you want to encapsulate the connection string logic within the context.
    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
    {
        // Ensure the connection string is valid for your chosen provider.
        // For example, for SQL Server:
        // optionsBuilder.UseSqlServer("Server=(localdb)\mssqllocaldb;Database=MyBlogDatabase;Trusted_Connection=True;");
        // For SQLite (as in a previous example):
        optionsBuilder.UseSqlite("Data Source=blogging.db");
    }
}
```
<div class="mt-2 p-2 bg-purple-900 rounded-md text-sm">
  <p class="text-purple-200">📝 **Note:** While `OnConfiguring` is convenient, using constructor injection for `DbContextOptions` (as shown on slide 10/4) is generally preferred in ASP.NET Core applications for better testability and configuration management via `appsettings.json`.</p>
</div>

---
layout: default
---

# Models & Entities (1/4) 🧩

## POCO Classes: The Building Blocks

In Entity Framework Core, your data models are typically represented by **POCOs (Plain Old CLR Objects)**.

**What are POCOs?**
- Simple C# classes that represent the structure of your data.
- They don't have any direct dependency on EF Core or any other framework.
- Properties of the class map to columns in a database table.
- An instance of a POCO class represents a row in the table.

**Example POCO:**
```csharp
// Student.cs
public class Student
{
    // Primary Key (by convention)
    public int StudentId { get; set; }

    public string FirstName { get; set; }
    public string LastName { get; set; }
    public DateTime DateOfBirth { get; set; }

    // Nullable property
    public string? Email { get; set; }
}
```
<div class="mt-3 p-3 bg-gray-700 rounded-lg text-sm">
  <p class="text-yellow-300">✨ **Simplicity is Key:**</p>
  <ul class="list-disc pl-5 text-gray-300 mt-1">
    <li>Easy to understand and test.</li>
    <li>Promotes a clean domain model, decoupled from data access concerns.</li>
    <li>EF Core uses conventions to map these classes to database tables, but you can override these with Data Annotations or Fluent API.</li>
  </ul>
</div>

---
layout: default
class: "text-center"
---

# 🧑‍💻 Live Coding Break!  kode

Let's dive into the code and see some of these concepts in action!

**Possible Demo Points:**
- Creating Entities and DbContext.
- Running first migration.
- Basic CRUD operations.

<p class="mt-6 text-sm opacity-75">(Presenter: Prepare your demo environment and code snippets!)</p>

---
layout: default
---

# Models & Entities (2/4) ⚙️

## Configuration: Data Annotations vs. Fluent API

EF Core needs to understand how your POCO classes map to the database schema (table names, column names, data types, relationships, constraints, etc.). There are two main ways to provide this configuration:

<div class="grid grid-cols-2 gap-6 mt-4">
<div>
  <h3 class="text-xl font-semibold text-blue-300 mb-2">Data Annotations</h3>
  <p class="text-sm opacity-80">Attributes applied directly to your entity classes and properties.</p>
  <ul class="list-disc pl-5 space-y-1 text-xs mt-2">
    <li>Simple and declarative.</li>
    <li>Keeps configuration close to the entity definition.</li>
    <li>Good for common configurations.</li>
    <li>Located in `System.ComponentModel.DataAnnotations` and `System.ComponentModel.DataAnnotations.Schema`.</li>
  </ul>
  <p class="text-sm font-semibold mt-2">Examples:</p>
  <pre class="text-xs"><code class="language-csharp">
  public class User
  {
      [Key] // Primary Key
      public int UserId { get; set; }

      [Required] // Not Null
      [MaxLength(100)] // nvarchar(100)
      public string Username { get; set; }

      [Column("EmailAddress", TypeName = "varchar(255)")]
      public string Email { get; set; }

      [NotMapped] // Not persisted to DB
      public string FullName => Username;
  }
  </code></pre>
</div>
<div>
  <h3 class="text-xl font-semibold text-green-300 mb-2">Fluent API</h3>
  <p class="text-sm opacity-80">Configuration applied using EF Core model builder methods, typically in `OnModelCreating` in your `DbContext`.</p>
  <ul class="list-disc pl-5 space-y-1 text-xs mt-2">
    <li>More powerful and flexible.</li>
    <li>Keeps entity classes clean (no EF-specific attributes).</li>
    <li>Better for complex mappings and database-specific features.</li>
    <li>Provides a centralized place for configuration.</li>
  </ul>
  <p class="text-sm font-semibold mt-2">Examples (in `OnModelCreating`):</p>
  <pre class="text-xs"><code class="language-csharp">
  modelBuilder.Entity&lt;User&gt;().ToTable("ApplicationUsers");

  modelBuilder.Entity&lt;User&gt;()
      .HasKey(u => u.UserId);

  modelBuilder.Entity&lt;User&gt;()
      .Property(u => u.Username)
      .IsRequired()
      .HasMaxLength(100);

  modelBuilder.Entity&lt;User&gt;()
      .Property(u => u.Email)
      .HasColumnName("EmailAddress")
      .HasColumnType("varchar(255)");

  modelBuilder.Entity&lt;User&gt;()
      .Ignore(u => u.FullName);
  </code></pre>
</div>
</div>
<p class="mt-4 text-center text-purple-300 italic text-sm">💡 You can use both! Fluent API overrides Data Annotations if there's a conflict.</p>

---
layout: default
---

# Models & Entities (3/4) 🔗

## Navigation Properties

Navigation properties are properties on your entity classes that represent relationships to other entities. They allow you to easily "navigate" from one entity to related entities.

**Types of Navigation Properties:**
<ul>
  <li class="mb-2">
    <strong>Reference Navigation Property:</strong> Represents a one-to-one or one-to-many (from the "one" side) relationship. Holds a single related entity.
    <br/><span class="text-xs opacity-75">Example: A `Post` entity might have a `public Blog Blog { get; set; }` property.</span>
  </li>
  <li class="mb-2">
    <strong>Collection Navigation Property:</strong> Represents a one-to-many (from the "many" side) or many-to-many relationship. Holds a collection of related entities (e.g., `ICollection<T>`, `List<T>`).
    <br/><span class="text-xs opacity-75">Example: A `Blog` entity might have a `public ICollection<Post> Posts { get; set; }` property.</span>
  </li>
</ul>

**How EF Core uses them:**
<ul>
  <li>To understand and create database relationships (foreign keys).</li>
  <li>To enable loading of related data (e.g., eager loading with `Include()`).</li>
  <li>To traverse object graphs in your code (e.g., `myBlog.Posts.Add(newPost)`).</li>
</ul>

**Example:**
```csharp
public class Author
{
    public int AuthorId { get; set; }
    public string Name { get; set; }

    // Collection Navigation Property (one-to-many with Book)
    public ICollection<Book> Books { get; set; } = new List<Book>();
}

public class Book
{
    public int BookId { get; set; }
    public string Title { get; set; }

    public int AuthorId { get; set; } // Foreign Key
    // Reference Navigation Property (many-to-one with Author)
    public Author Author { get; set; }
}
```
<p class="mt-2 text-sm text-green-300">🌱 Navigation properties are crucial for working with related data effectively in EF Core.</p>

---
layout: default
---

# Models & Entities (4/4) 📝 Example Models

## Example: `Blog` and `Post` with Relationships

Here are the `Blog` and `Post` POCO classes demonstrating a one-to-many relationship. This structure is fundamental for many applications.

```csharp
using System.Collections.Generic; // Required for List<T>

public class Blog
{
    // Primary Key (by convention: ClassName + Id or just Id)
    public int BlogId { get; set; }
    public string Title { get; set; } // As per issue (was Url in previous example)

    // Collection Navigation Property: A Blog can have many Posts
    // Initialized to prevent null reference exceptions.
    public List<Post> Posts { get; set; } = new List<Post>();
}

public class Post
{
    // Primary Key
    public int PostId { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }

    // Foreign Key Property: Links this Post to a Blog
    // Convention: RelatedEntityName + RelatedEntityPrimaryKeyName (Blog + BlogId)
    public int BlogId { get; set; }

    // Reference Navigation Property: A Post belongs to one Blog
    public Blog Blog { get; set; }
}
```
<div class="mt-3 p-3 bg-blue-900 rounded-lg text-sm">
  <p class="text-blue-200">🔍 **Key Points in this Example:**</p>
  <ul class="list-disc pl-5 text-blue-100 mt-1">
    <li>`Blog.Posts` (List&lt;Post&gt;): Allows you to access all posts related to a blog.</li>
    <li>`Post.Blog` (Blog): Allows you to access the parent blog of a post.</li>
    <li>`Post.BlogId` (int): The foreign key column in the `Posts` table that links to the `Blogs` table's primary key.</li>
    <li>EF Core conventions automatically detect this as a one-to-many relationship.</li>
  </ul>
</div>

---
layout: default
---

# Code-First Approach (1/4) 💻➡️🧱

## Concept: Define Schema Through Code

The **Code-First** approach is a popular workflow in Entity Framework Core where you define your database schema by writing C# classes (your entities and `DbContext`) first. EF Core then generates the database schema based on this code model.

**Key Idea:** Your code is the single source of truth for your database structure.

<div class="grid grid-cols-2 gap-8 items-center mt-4">
<div>
  **Advantages:**
  <ul class="list-disc pl-5 space-y-1 text-sm mt-2">
    <li>Developers can stay within their familiar C# environment.</li>
    <li>Version control for your database schema (as code and migrations).</li>
    <li>Easier to manage database changes alongside application code changes.</li>
    <li>Promotes a domain-driven design focus.</li>
  </ul>
  <br/>
  **Typical Workflow:**
  <ol class="list-decimal pl-5 space-y-1 text-sm">
    <li>Define POCO entity classes.</li>
    <li>Define `DbContext` with `DbSet` properties.</li>
    <li>Configure model using Data Annotations or Fluent API.</li>
    <li>Generate migrations to create/update the database.</li>
    <li>Apply migrations to the database.</li>
  </ol>
</div>
<div>
  <!-- Placeholder for Visual Diagram -->
  <div class="p-4 border rounded-lg text-center bg-gray-700">
    <p class="text-4xl">🧑‍💻 (Code Model)</p>
    <p class="text-2xl my-2">⬇️ EF Migrations ⬇️</p>
    <p class="text-4xl">🧱 (Database Schema)</p>
    <p class="text-sm opacity-75 mt-2">Visual: Developer writes C# classes, EF Migrations tool translates this into SQL scripts, which then create or update the database tables, columns, indexes, etc.</p>
  </div>
</div>
</div>

---
layout: default
---

# Code-First Approach (2/4) 🔄

## Migrations Workflow

EF Core Migrations provide a way to incrementally evolve your database schema as your model changes over time. Each change is captured in a "migration" file containing C# code to apply and revert the changes.

**Core Steps in the Workflow:**

1.  **Initial Model:** Create your initial set of entity classes and `DbContext`.
2.  **Add Migration:** Use `dotnet ef migrations add <MigrationName>` (e.g., `InitialCreate`).
    *   This creates a new migration file in a `Migrations` folder.
    *   The file contains `Up()` (to apply changes) and `Down()` (to revert changes) methods.
3.  **Review Migration:** Check the generated C# code in the migration file to ensure it matches your intended schema changes.
4.  **Apply Migration:** Use `dotnet ef database update`.
    *   This executes the `Up()` method of pending migrations, creating/modifying the database.
    *   EF Core keeps track of applied migrations in a special `__EFMigrationsHistory` table in your database.
5.  **Iterate:**
    *   Modify your entity classes (add/remove properties, entities, relationships).
    *   Add a new migration: `dotnet ef migrations add <DescriptiveNameForChange>`.
    *   Apply the migration: `dotnet ef database update`.

<div class="mt-4 p-3 bg-gray-700 rounded-lg">
  <p class="text-sm text-yellow-300">🔄 **Migrations Workflow Diagram Placeholder:**</p>
  <p class="text-xs text-gray-300 mt-1">
    (Imagine a flow: Model Change -> `migrations add` -> Migration File Generated -> `database update` -> DB Schema Updated & __EFMigrationsHistory table updated)
  </p>
  <ul class="text-xs text-gray-300 list-disc pl-4 mt-1">
    <li>Developer modifies C# model.</li>
    <li>Runs `dotnet ef migrations add MeaningfulName`.</li>
    <li>EF Core compares model to last migration snapshot, generates new migration file.</li>
    <li>Developer reviews migration file.</li>
    <li>Runs `dotnet ef database update`.</li>
    <li>EF Core executes SQL, updates `__EFMigrationsHistory`.</li>
  </ul>
</div>

---
layout: default
---

# Code-First Approach (3/4) 命令行

## Migrations Commands Demonstration

You'll primarily use the .NET CLI (`dotnet ef`) for managing migrations. Make sure you have `Microsoft.EntityFrameworkCore.Tools` package installed.

**Common Commands (execute in project directory where `.csproj` is):**

1.  **Adding a Migration:**
    *   After changing your model (entities, `DbContext`), create a migration to capture these changes.
    ```bash
    dotnet ef migrations add InitialCreate
    ```
    *   Replace `InitialCreate` with a descriptive name for your changes (e.g., `AddUserEmail`, `CreateProductTable`).
    *   This creates a C# file in the `Migrations` folder.

2.  **Applying Migrations to Database:**
    *   This command applies all pending migrations to the database, creating or updating the schema.
    ```bash
    dotnet ef database update
    ```
    *   You can target a specific migration: `dotnet ef database update <TargetMigrationName>` (to roll back or apply up to a point).

3.  **Listing Migrations:**
    ```bash
    dotnet ef migrations list
    ```

4.  **Removing the Last Migration (if not applied):**
    *   Useful if you made a mistake in the last migration and haven't applied it to the DB.
    ```bash
    dotnet ef migrations remove
    ```

<div class="mt-2 p-2 bg-blue-900 rounded-md text-sm">
  <p class="text-blue-200">💡 **Tip:** Always ensure your `DbContext` is correctly configured (e.g., connection string) and your project can build before running `dotnet ef` commands. These tools often need to instantiate your `DbContext` at design time.</p>
</div>

---
layout: default
---

# Code-First Approach (4/4) 📜

## Example Migration File Structure

When you run `dotnet ef migrations add <MigrationName>`, EF Core generates a migration file. Here's a simplified structure:

```csharp
// Migrations/YYYYMMDDHHMMSS_InitialCreate.cs (Timestamp ensures chronological order)
using Microsoft.EntityFrameworkCore.Migrations;

#nullable disable // For brevity in example

public partial class InitialCreate : Migration // Inherits from Migration base class
{
    // Called when applying the migration (dotnet ef database update)
    protected override void Up(MigrationBuilder migrationBuilder)
    {
        migrationBuilder.CreateTable(
            name: "Blogs", // Table name
            columns: table => new // Column definitions
            {
                BlogId = table.Column<int>(type: "INTEGER", nullable: false) // For SQLite: INTEGER
                    .Annotation("Sqlite:Autoincrement", true), // Primary Key, auto-increment
                Title = table.Column<string>(type: "TEXT", nullable: false) // For SQLite: TEXT
            },
            constraints: table =>
            {
                table.PrimaryKey("PK_Blogs", x => x.BlogId); // Define Primary Key constraint
            });

        migrationBuilder.CreateTable(
            name: "Posts",
            columns: table => new
            {
                PostId = table.Column<int>(type: "INTEGER", nullable: false)
                    .Annotation("Sqlite:Autoincrement", true),
                Title = table.Column<string>(type: "TEXT", nullable: false),
                Content = table.Column<string>(type: "TEXT", nullable: false),
                BlogId = table.Column<int>(type: "INTEGER", nullable: false) // Foreign Key column
            },
            constraints: table =>
            {
                table.PrimaryKey("PK_Posts", x => x.PostId);
                table.ForeignKey( // Define Foreign Key constraint
                    name: "FK_Posts_Blogs_BlogId",
                    column: x => x.BlogId,
                    principalTable: "Blogs",
                    principalColumn: "BlogId",
                    onDelete: ReferentialAction.Cascade); // Action on parent deletion
            });

        migrationBuilder.CreateIndex( // Example of creating an index
            name: "IX_Posts_BlogId",
            table: "Posts",
            column: "BlogId");
    }

    // Called when reverting the migration (e.g., dotnet ef database update <PreviousMigration>)
    protected override void Down(MigrationBuilder migrationBuilder)
    {
        migrationBuilder.DropTable(
            name: "Posts");

        migrationBuilder.DropTable(
            name: "Blogs");
    }
}
```
<span class="text-xs text-gray-400 mt-1">Note: Actual types (`INTEGER`, `TEXT`) depend on the database provider (SQLite shown here). SQL Server would have `int`, `nvarchar(max)`, etc.</span>

---
layout: default
---

# Database-First Approach (1/4) 🧱➡️💻

## Concept: Generating Code from an Existing Database

The **Database-First** approach is used when you already have an existing database, and you want to generate EF Core entity classes and a `DbContext` based on that database's schema. This process is often called **reverse engineering**.

**Key Idea:** Your existing database is the source of truth for your model.

<div class="grid grid-cols-2 gap-8 items-center mt-4">
<div>
  **Advantages:**
  <ul class="list-disc pl-5 space-y-1 text-sm mt-2">
    <li>Ideal for working with legacy databases or databases managed by a separate DBA team.</li>
    <li>Quickly creates an EF Core model that matches the existing schema.</li>
    <li>Can save significant time compared to manually defining entities for complex databases.</li>
  </ul>
  <br/>
  **Typical Workflow:**
  <ol class="list-decimal pl-5 space-y-1 text-sm">
    <li>Ensure you have an existing database.</li>
    <li>Install necessary EF Core tools and provider packages.</li>
    <li>Use the `Scaffold-DbContext` command (or `dotnet ef dbcontext scaffold`) to generate code.</li>
    <li>Review and customize the generated code if needed.</li>
    <li>Use the generated `DbContext` and entities in your application.</li>
  </ol>
</div>
<div>
  <!-- Placeholder for Visual Diagram -->
  <div class="p-4 border rounded-lg text-center bg-gray-700">
    <p class="text-4xl">🧱 (Existing Database)</p>
    <p class="text-2xl my-2">⬇️ EF Scaffolding Tools ⬇️</p>
    <p class="text-4xl">🧑‍💻 (Generated Code Model)</p>
    <p class="text-sm opacity-75 mt-2">Visual: An existing database schema (tables, columns, relationships) is read by EF Core tools, which then generate corresponding C# entity classes and a DbContext.</p>
  </div>
</div>
</div>
<p class="mt-2 text-xs text-gray-400">Note: While you can modify the generated code, be aware that re-scaffolding might overwrite your changes unless you use partial classes or other strategies.</p>

---
layout: default
---

# Database-First Approach (2/4) 🛠️⚙️

## `Scaffold-DbContext` Command

The primary tool for Database-First is the `Scaffold-DbContext` command (in Package Manager Console) or `dotnet ef dbcontext scaffold` (.NET CLI).

**Command Syntax (.NET CLI):**
```bash
dotnet ef dbcontext scaffold "<connection_string>" <database_provider_package> \
    --output-dir <output_directory_for_models> \
    --context <DbContext_name> \
    --context-dir <output_directory_for_DbContext> \
    [options]
```

**Key Parameters & Options:**
<ul>
  <li><code>&lt;connection_string&gt;</code>: The connection string to your existing database. (<strong>Important:</strong> Be careful with sensitive data in CLI history; consider user secrets or environment variables for production scenarios).</li>
  <li><code>&lt;database_provider_package&gt;</code>: The EF Core provider package (e.g., `Microsoft.EntityFrameworkCore.SqlServer`, `Npgsql.EntityFrameworkCore.PostgreSQL`).</li>
  <li><code>--output-dir</code> (or <code>-o</code>): Directory to output entity classes (e.g., "Models").</li>
  <li><code>--context</code> (or <code>-c</code>): Name for the generated DbContext class (e.g., "MyDatabaseContext").</li>
  <li><code>--context-dir</code>: Directory to output the DbContext class (if different from entities).</li>
  <li><code>--tables</code> (or <code>-t</code>): Specific tables to scaffold (e.g., <code>-t Product -t Order</code>). If omitted, all tables are scaffolded.</li>
  <li><code>--data-annotations</code> (or <code>-d</code>): Use Data Annotations for configuration where possible (default is Fluent API).</li>
  <li><code>--force</code> (or <code>-f</code>): Overwrite existing files.</li>
  <li><code>--no-onconfiguring</code>: Don't generate `OnConfiguring` with the connection string (useful if you configure it in `Startup.cs` or `Program.cs`).</li>
</ul>

**Example (SQL Server):**
```bash
dotnet ef dbcontext scaffold "Server=(localdb)\mssqllocaldb;Database=MyExistingDb;Trusted_Connection=True;" \
    Microsoft.EntityFrameworkCore.SqlServer \
    --output-dir Models \
    --context MyExistingDbContext \
    --context-dir DataAccess \
    --force
```

---
layout: default
---

# Database-First Approach (3/4) 📄

## Generated Code Examples

When you run `Scaffold-DbContext`, EF Core generates:
1.  **Entity Classes:** POCOs for each table scaffolded.
2.  **DbContext Class:** A class derived from `DbContext` with `DbSet` properties and Fluent API configurations.

**Example: Generated Entity (simplified `Product` table)**
```csharp
// Models/Product.cs (Generated)
using System;
using System.Collections.Generic;

namespace MyProject.Models // Namespace based on project/output dir
{
    public partial class Product // 'partial' allows extending in another file
    {
        public Product()
        {
            OrderItems = new HashSet<OrderItem>(); // Collection initialized
        }

        public int ProductId { get; set; } // Primary Key
        public string ProductName { get; set; } = null!; // Non-nullable string
        public decimal? UnitPrice { get; set; } // Nullable decimal
        public int? CategoryId { get; set; } // Nullable Foreign Key

        // Navigation properties generated based on DB relationships
        public virtual Category? Category { get; set; }
        public virtual ICollection<OrderItem> OrderItems { get; set; }
    }
}
```

**Example: Generated DbContext (simplified)**
```csharp
// DataAccess/MyExistingDbContext.cs (Generated)
using System;
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Metadata;
using MyProject.Models; // Assuming Models folder

namespace MyProject.DataAccess
{
    public partial class MyExistingDbContext : DbContext
    {
        public MyExistingDbContext() { } // May be present

        public MyExistingDbContext(DbContextOptions<MyExistingDbContext> options)
            : base(options) { } // For DI

        public virtual DbSet<Product> Products { get; set; } = null!;
        public virtual DbSet<Category> Categories { get; set; } = null!;
        // ... other DbSets ...

        // OnConfiguring might be generated if --no-onconfiguring isn't used
        // protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
        // {
        //     if (!optionsBuilder.IsConfigured)
        //     {
        // #warning To protect potentially sensitive information in your connection string...
        //         optionsBuilder.UseSqlServer("your_connection_string_here");
        //     }
        // }

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            modelBuilder.Entity<Product>(entity =>
            {
                entity.HasKey(e => e.ProductId); // Primary Key
                entity.Property(e => e.ProductName).HasMaxLength(100).IsRequired();
                entity.Property(e => e.UnitPrice).HasColumnType("decimal(18, 2)");

                entity.HasOne(d => d.Category) // Relationship
                      .WithMany(p => p.Products)
                      .HasForeignKey(d => d.CategoryId)
                      .HasConstraintName("FK_Product_Category"); // DB constraint name
            });
            // ... other entity configurations ...

            OnModelCreatingPartial(modelBuilder); // Hook for custom partial method
        }
        partial void OnModelCreatingPartial(ModelBuilder modelBuilder); // Allows customization
    }
}
```

---
layout: default
class: "text-center"
---

# 🧠 Quiz Time! 🧐

Test your EF Core knowledge so far!

**1. Which command is used to apply pending migrations to the database?**
   A) `dotnet ef migrations add MyMigration`
   B) `dotnet ef database update`
   C) `dotnet ef dbcontext scaffold`
   D) `dotnet watch run`

<br/>
<v-click>
<p class="text-green-400">Answer: B) `dotnet ef database update`</p>
</v-click>

---
layout: default
---

# Database-First Approach (4/4) 🤔

## When to Use Which Approach?

Both Code-First and Database-First are valid approaches. The best choice depends on your project's context.

| Feature / Scenario        | Code-First Approach                                  | Database-First Approach                             |
|---------------------------|------------------------------------------------------|-----------------------------------------------------|
| **Source of Truth**       | Your C# Code (Entities, DbContext)                   | Existing Database Schema                            |
| **New Projects**          | Often preferred, especially for greenfield apps.     | If DB already exists and is complex.                |
| **Existing Databases**    | Possible, but might require manual model creation.   | **Primary use case.** Generates model from DB.      |
| **DB Schema Control**     | Full control via code and migrations.                | DB schema managed externally (e.g., by DBAs).       |
| **Migrations**            | Core feature for evolving schema with code.          | Not typically used; re-scaffold to update model.    |
| **Team Workflow**         | Developers manage schema changes.                    | DBAs or other tools manage schema changes.          |
| **Flexibility**           | High, model can be designed for optimal app use.     | Model reflects existing DB, might not be optimal.   |
| **Initial Setup Speed**   | Slower if models are complex and typed manually.     | Faster for existing complex DBs due to generation.  |
| **POCO Cleanliness**      | Can be very clean (using Fluent API).                | Generated code might have attributes or partials.   |

<br/>
<div class="p-3 bg-purple-900 rounded-md text-sm">
  <p class="text-purple-200">Hybrid Approaches? 💡</p>
  <p class="text-xs text-purple-300 mt-1">
    Sometimes, teams use a hybrid:
    1. Scaffold once from an existing database to get a baseline model.
    2. Then, switch to a Code-First workflow, take ownership of the model, and use migrations for future changes. This requires careful management.
    3. Or, periodically re-scaffold to a separate directory and manually merge changes if the database is the master.
  </p>
</div>

---
layout: default
---

# CRUD Operations (1/4) ✨ Create

## Adding New Data (Create)

Adding new entities to the database involves creating an instance of your entity class, adding it to the appropriate `DbSet` on your `DbContext`, and then calling `SaveChanges()` (or `SaveChangesAsync()`).

**General Steps:**
1. Create a new instance of your entity object and populate its properties.
2. Add the new entity to its corresponding `DbSet<TEntity>` in your `DbContext`.
   - `context.MyEntities.Add(newEntity);`
   - Or `context.Add(newEntity);` (EF Core can often infer the DbSet)
3. Call `await context.SaveChangesAsync();` (or `context.SaveChanges();` for synchronous code).
   - This is when EF Core generates and executes the `INSERT` SQL command.

**Example: Adding a new Blog**
```csharp
// Assuming 'context' is an instance of your BlogContext
// And Blog model is defined as in previous examples

public async Task AddNewBlogAsync(string blogTitle, string blogUrl)
{
    Console.WriteLine("Creating a new blog...");
    var newBlog = new Blog
    {
        Title = blogTitle, // Assuming Blog has a Title property now
        Url = blogUrl     // And a Url property
    };

    context.Blogs.Add(newBlog); // Mark the entity as Added

    // EF Core tracks this new entity.
    // No database interaction happens until SaveChangesAsync()

    await context.SaveChangesAsync(); // Generates INSERT INTO Blogs...

    // After SaveChangesAsync, newBlog.BlogId will be populated if it's an auto-generated key.
    Console.WriteLine($"Blog '{newBlog.Title}' added with ID: {newBlog.BlogId}");
}

// Usage:
// await AddNewBlogAsync("My Awesome Tech Blog", "http://mytechblog.example.com");
```
<div class="mt-2 p-2 bg-green-900 rounded-md text-sm">
  <p class="text-green-200">💡 `SaveChangesAsync()` is generally preferred in async applications (like ASP.NET Core) to avoid blocking threads.</p>
</div>

---
layout: default
---

# CRUD Operations (2/4) 🔍 Read

## Querying Data (Read) with LINQ

EF Core allows you to use **LINQ (Language Integrated Query)** to write strongly-typed queries against your `DbContext`. EF Core translates these LINQ queries into SQL queries for your database.

**Common LINQ Operations:**
<ul>
  <li><code>Where()</code>: Filter data based on conditions.</li>
  <li><code>Select()</code>: Project data into specific shapes or anonymous types.</li>
  <li><code>OrderBy()</code> / <code>OrderByDescending()</code>: Sort data.</li>
  <li><code>FirstOrDefault()</code> / <code>SingleOrDefault()</code>: Retrieve a single entity.</li>
  <li><code>ToList()</code> / <code>ToArray()</code> / <code>ToListAsync()</code>: Execute the query and retrieve results.</li>
  <li><code>Include()</code> / <code>ThenInclude()</code>: Eager load related data (more on this later).</li>
</ul>

**Example: Reading Blogs and their Posts**
```csharp
public async Task PrintAllBlogsWithPostsAsync()
{
    Console.WriteLine("Querying for all blogs and their posts...");

    // Basic query to get all blogs
    var allBlogs = await context.Blogs.ToListAsync();
    foreach (var blog in allBlogs)
    {
        Console.WriteLine($"Blog: {blog.Title} (ID: {blog.BlogId})");
    }

    // Query for blogs with a specific title, including their posts
    string searchTerm = "My Awesome Tech Blog";
    var blogsWithPosts = await context.Blogs
        .Where(b => b.Title.Contains(searchTerm))
        .Include(b => b.Posts) // Eager load the Posts navigation property
        .ToListAsync();

    foreach (var blog in blogsWithPosts)
    {
        Console.WriteLine($"Found Blog: {blog.Title}");
        if (blog.Posts.Any())
        {
            foreach (var post in blog.Posts)
            {
                Console.WriteLine($"  - Post: {post.Title}");
            }
        }
        else
        {
            Console.WriteLine("  - No posts found for this blog.");
        }
    }
}
```
<p class="text-xs text-gray-400 mt-1">The `.Include(b => b.Posts)` tells EF Core to also fetch all related `Post` entities for each `Blog` found.</p>

---
layout: default
---

# CRUD Operations (3/4) ✏️ Update

## Modifying Existing Data (Update)

Updating data typically involves:
1. Fetching an entity from the database.
2. Modifying its properties.
3. Calling `SaveChangesAsync()`. EF Core's change tracker automatically detects modifications to tracked entities.

**General Steps (Connected Scenario):**
1. Retrieve an entity: `var entityToUpdate = await context.MyEntities.FindAsync(id);`
2. If found, modify its properties: `entityToUpdate.SomeProperty = newValue;`
3. Call `await context.SaveChangesAsync();`
   - EF Core's change tracker notes the modified properties and generates the `UPDATE` SQL.

**Example: Updating a Blog's Title**
```csharp
public async Task UpdateBlogTitleAsync(int blogId, string newTitle)
{
    Console.WriteLine($"Attempting to update blog ID: {blogId} with new title: '{newTitle}'");
    var blogToUpdate = await context.Blogs.FindAsync(blogId); // Find by primary key

    if (blogToUpdate != null)
    {
        blogToUpdate.Title = newTitle; // Modify the property
        // The DbContext is now tracking this change.

        await context.SaveChangesAsync(); // Generates UPDATE Blogs SET Title = ... WHERE BlogId = ...
        Console.WriteLine("Blog title updated successfully.");
    }
    else
    {
        Console.WriteLine($"Blog with ID: {blogId} not found.");
    }
}

// Usage:
// await UpdateBlogTitleAsync(1, "My Updated Awesome Tech Blog");
```

<div class="mt-2 p-2 bg-yellow-800 bg-opacity-30 rounded-md text-sm">
  <p class="text-yellow-300">⚠️ **Disconnected Scenario:** If the entity was modified outside the current `DbContext`'s scope (e.g., data from an API request), you need to attach it and set its state:
  `context.Update(modifiedEntity);` or `context.Entry(modifiedEntity).State = EntityState.Modified;` before `SaveChangesAsync()`.
  </p>
</div>

---
layout: default
---

# CRUD Operations (4/4) 🗑️ Delete & Summary

## Removing Data (Delete)

Deleting an entity involves:
1. Fetching the entity (or creating an instance with the correct PK if you know it exists).
2. Marking it for deletion using `DbSet.Remove()` or `DbContext.Remove()`.
3. Calling `SaveChangesAsync()`.

**Example: Deleting a Blog**
```csharp
public async Task DeleteBlogAsync(int blogId)
{
    Console.WriteLine($"Attempting to delete blog ID: {blogId}");
    var blogToDelete = await context.Blogs.FindAsync(blogId);

    if (blogToDelete != null)
    {
        context.Blogs.Remove(blogToDelete); // Mark for deletion
        // Or context.Remove(blogToDelete);

        await context.SaveChangesAsync(); // Generates DELETE FROM Blogs WHERE BlogId = ...
        Console.WriteLine("Blog deleted successfully.");
    }
    else
    {
        Console.WriteLine($"Blog with ID: {blogId} not found for deletion.");
    }
}
```

## All CRUD Operations Example (from issue):

```csharp
// Assuming 'context' is an instance of your DbContext
// and Blog, Post entities are defined.

// CREATE
var blog = new Blog { Title = "My New Blog", Url = "http://mynewblog.com" };
context.Blogs.Add(blog);
await context.SaveChangesAsync();
Console.WriteLine($"Created Blog ID: {blog.BlogId}");

// READ (Example: Get a specific blog and its posts)
var specificBlog = await context.Blogs
    .Include(b => b.Posts) // Eager load posts
    .FirstOrDefaultAsync(b => b.BlogId == blog.BlogId);

if (specificBlog != null) {
    Console.WriteLine($"Read Blog: {specificBlog.Title}");
    foreach (var post in specificBlog.Posts) {
        Console.WriteLine($" - Post: {post.Title}");
    }
}

// UPDATE (the blog we just created)
if (specificBlog != null) {
    specificBlog.Title = "My Updated Blog Title";
    specificBlog.Url = "http://myupdatedblog.com";
    await context.SaveChangesAsync();
    Console.WriteLine($"Updated Blog Title to: {specificBlog.Title}");
}

// DELETE (the blog we created and updated)
if (specificBlog != null) {
    context.Blogs.Remove(specificBlog);
    await context.SaveChangesAsync();
    Console.WriteLine($"Deleted Blog ID: {specificBlog.BlogId}");
}
```

---
layout: default
---

# Relationships & Navigation (1/4) 🧑‍🤝‍🧑

## One-to-One Relationships

A one-to-one relationship exists when one entity instance is related to exactly one other entity instance, and vice-versa. Both entities share the same primary key, or one has a foreign key that is also its primary key and references the other's PK.

**Example: `Student` and `StudentAddress`**
A student has one address, and that address belongs to only one student.

```csharp
public class Student
{
    public int StudentId { get; set; } // Primary Key
    public string Name { get; set; }

    // Navigation property to the dependent entity (StudentAddress)
    public virtual StudentAddress Address { get; set; }
}

public class StudentAddress
{
    // Primary Key is also a Foreign Key to Student
    [Key, ForeignKey("Student")]
    public int StudentId { get; set; }
    public string Street { get; set; }
    public string City { get; set; }

    // Navigation property back to the principal entity (Student)
    public virtual Student Student { get; set; }
}
```
**Configuration (Fluent API in `DbContext.OnModelCreating`):**
```csharp
modelBuilder.Entity<Student>()
    .HasOne(s => s.Address)        // Student has one Address
    .WithOne(ad => ad.Student)     // Address has one Student
    .HasForeignKey<StudentAddress>(ad => ad.StudentId); // FK is StudentAddress.StudentId
```
<div class="mt-2 p-2 bg-blue-900 rounded-md text-sm">
  <p class="text-blue-200">Key Points:
    <ul class="list-disc pl-4 text-xs">
      <li>The dependent entity (`StudentAddress`) has its PK (`StudentId`) also act as the FK to the principal (`Student`).</li>
      <li>Navigation properties are defined on both sides.</li>
      <li>`virtual` keyword on navigation properties can enable lazy loading (if configured).</li>
    </ul>
  </p>
</div>

---
layout: default
---

# Relationships & Navigation (2/4) 👨‍👧‍👦

## One-to-Many Relationships

This is the most common type of relationship. One entity instance can be related to many instances of another entity, but an instance of the "many" side entity can only be related to one instance of the "one" side.

**Example: `Blog` and `Post` (revisited)**
A blog can have many posts, but each post belongs to only one blog.

```csharp
public class Blog
{
    public int BlogId { get; set; }
    public string Title { get; set; }

    // Collection Navigation Property (One Blog -> Many Posts)
    public virtual ICollection<Post> Posts { get; set; } = new List<Post>();
}

public class Post
{
    public int PostId { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }

    public int BlogId { get; set; } // Foreign Key property
    // Reference Navigation Property (Many Posts -> One Blog)
    public virtual Blog Blog { get; set; }
}
```
**Configuration (Fluent API in `DbContext.OnModelCreating`):**
```csharp
modelBuilder.Entity<Blog>()
    .HasMany(b => b.Posts)          // Blog has many Posts
    .WithOne(p => p.Blog)           // Each Post has one Blog
    .HasForeignKey(p => p.BlogId)   // The FK in Post is BlogId
    .OnDelete(DeleteBehavior.Cascade); // Optional: Configure delete behavior
                                      // (e.g., Cascade = delete posts if blog is deleted)
```
<p class="text-xs text-gray-400 mt-1">EF Core conventions often detect this relationship automatically if FK property (`BlogId`) and navigation properties (`Blog.Posts`, `Post.Blog`) are correctly named.</p>

---
layout: default
---

# Relationships & Navigation (3/4) 🤝

## Many-to-Many Relationships (EF Core 5+)

In a many-to-many relationship, instances of one entity can be related to many instances of another entity, and vice-versa. EF Core 5+ introduced a way to model these without explicitly defining a join entity class in many common cases.

**Example: `Post` and `Tag`**
A post can have many tags, and a tag can be applied to many posts.

```csharp
public class Post
{
    public int PostId { get; set; }
    public string Title { get; set; }
    // ... other properties ...

    // Collection Navigation Property to Tags
    public virtual ICollection<Tag> Tags { get; set; } = new List<Tag>();
}

public class Tag
{
    public int TagId { get; set; }
    public string Name { get; set; }

    // Collection Navigation Property to Posts
    public virtual ICollection<Post> Posts { get; set; } = new List<Post>();
}
```
**Configuration (Fluent API in `DbContext.OnModelCreating`):**
```csharp
modelBuilder.Entity<Post>()
    .HasMany(p => p.Tags) // Post has many Tags
    .WithMany(t => t.Posts) // Tag has many Posts
    // EF Core will implicitly create a join table (e.g., "PostTag")
    // You can customize the join table if needed:
    .UsingEntity(j => j.ToTable("PostTags")); // Explicitly name the join table
```
<div class="mt-2 p-2 bg-green-900 rounded-md text-sm">
  <p class="text-green-200">✨ **Implicit Join Table:** EF Core automatically creates a join table (e.g., `PostTag`) with foreign keys to both `Posts` (`PostId`) and `Tags` (`TagId`).
  <br/>If you need to store additional data in the join table (e.g., `DateTagged`), you must create an explicit join entity class (e.g., `PostTag` entity) and configure two one-to-many relationships.
  </p>
</div>

---
layout: default
---

# Relationships & Navigation (4/4) 🚚

## Loading Strategies for Related Data

When you query for an entity, EF Core doesn't automatically load all its related data by default (to avoid over-fetching). You need to specify how related data should be loaded.

**1. Eager Loading:**
   - Loads related data as part of the initial query using the `Include()` and `ThenInclude()` methods.
   - **Pros:** Fewer database roundtrips if data is always needed.
   - **Cons:** Can lead to large queries if too much is included.
```csharp
// Eager Loading: Load Blogs, their Posts, and then Comments for each Post
var blogs = await context.Blogs
    .Include(b => b.Posts)       // Include Posts related to Blog
        .ThenInclude(p => p.Comments) // Then include Comments related to each Post
    .ToListAsync();
```

**2. Explicit Loading:**
   - Manually load related data for an entity that's already been loaded, using `context.Entry(entity).Collection()` or `.Reference().Load()`.
   - **Pros:** Load data only when specifically needed.
   - **Cons:** Requires an extra database roundtrip.
```csharp
var blog = await context.Blogs.FindAsync(1); // Load a single blog
// ... some time later, if you need its posts ...
await context.Entry(blog).Collection(b => b.Posts).LoadAsync(); // Explicitly load Posts
await context.Entry(blog).Reference(b => b.Author).LoadAsync(); // Explicitly load Author (if it's a reference)
```

**3. Lazy Loading (Requires `Microsoft.EntityFrameworkCore.Proxies`):**
   - Related data is automatically loaded from the database when a navigation property is accessed for the first time.
   - Requires navigation properties to be `virtual`.
   - **Pros:** Simplifies code as loading is transparent.
   - **Cons:** Can lead to N+1 query problems if not used carefully, performance issues.
```csharp
// Requires Microsoft.EntityFrameworkCore.Proxies and virtual navigation properties
// In DbContext OnConfiguring: optionsBuilder.UseLazyLoadingProxies();
// Or if using DI: services.AddDbContext<MyContext>(b => b.UseLazyLoadingProxies().UseSqlServer(...));

// context.ChangeTracker.LazyLoadingEnabled = true; // Can also be set, but proxies are common

var blog = await context.Blogs.FindAsync(1);
// Accessing blog.Posts here would trigger a DB query to load posts IF lazy loading is enabled
// foreach (var post in blog.Posts) { /* ... */ }
```
<p class="mt-1 text-xs text-yellow-300">⚠️ Lazy loading can be convenient but is often disabled by default due to potential performance traps (N+1 problem). Be very cautious with it.</p>

---
layout: default
---

# Advanced Querying (1/4) 🎣

## LINQ Methods Showcase

Beyond basic `Where`, `Select`, `OrderBy`, LINQ offers a rich set of methods for complex data retrieval. EF Core translates many of these into efficient SQL.

**Grouping & Aggregates:**
```csharp
// Get count of posts per blog
var postsPerBlog = await context.Blogs
    .Select(b => new
    {
        BlogTitle = b.Title,
        PostCount = b.Posts.Count() // Count related posts
    })
    .ToListAsync();

// Get average rating for products in a category
var averageRating = await context.Products
    .Where(p => p.CategoryId == 1)
    .AverageAsync(p => p.Rating); // Assuming a Rating property
```

**Paging Results:**
```csharp
int pageNumber = 1;
int pageSize = 10;
var pagedPosts = await context.Posts
    .OrderByDescending(p => p.PublishedDate)
    .Skip((pageNumber - 1) * pageSize) // Skip previous pages
    .Take(pageSize) // Take current page size
    .ToListAsync();
```

**Set Operations (Union, Intersect, Except - require compatible projections):**
```csharp
var groupA = context.Students.Where(s => s.GroupName == "A").Select(s => s.Name);
var groupB = context.Students.Where(s => s.GroupName == "B").Select(s => s.Name);
var allUniqueNames = await groupA.Union(groupB).ToListAsync(); // All unique names from A and B
```

**Projection to Custom Types / DTOs:**
```csharp
public class PostViewModel { public string Title { get; set; } public int AuthorId { get; set; } }
var postViewModels = await context.Posts
    .Select(p => new PostViewModel { Title = p.Title, AuthorId = p.Blog.AuthorId }) // Assuming Blog has AuthorId
    .ToListAsync();
```
<p class="text-xs text-gray-400 mt-1">EF Core's LINQ provider is powerful, but always test complex queries for correct translation and performance.</p>

---
layout: default
---

# Advanced Querying (2/4) 📜

## Raw SQL Execution

While LINQ is preferred for safety and maintainability, EF Core allows you to drop down to raw SQL when necessary.

**1. `FromSqlRaw` / `FromSqlInterpolated` (for querying entities):**
   - Used when you want to execute a raw SQL query that returns entity data.
   - The SQL query **must** return columns that match the properties of the entity type.
   - **Always parameterize user input** to prevent SQL injection. `FromSqlInterpolated` helps with this.

```csharp
// Assuming Blog entity has BlogId and Url properties
var searchTerm = "example.com";

// FromSqlInterpolated (safer, handles parameterization)
var blogs = await context.Blogs
    .FromSqlInterpolated($"SELECT * FROM Blogs WHERE Url LIKE '%' + {searchTerm} + '%'")
    .ToListAsync();

// FromSqlRaw (use with caution, ensure parameters are handled)
var blogsRaw = await context.Blogs
    .FromSqlRaw("SELECT * FROM Blogs WHERE Url LIKE '%' + @p0 + '%'", searchTerm)
    .ToListAsync();
```
   <p class="text-xs text-yellow-300">⚠️ `FromSqlRaw` requires careful handling of parameters (e.g., `DbParameter` objects or provider-specific syntax like `@p0`). `FromSqlInterpolated` is generally safer.</p>

**2. `ExecuteSqlRawAsync` / `ExecuteSqlInterpolatedAsync` (for non-query commands):**
   - Used for `INSERT`, `UPDATE`, `DELETE`, or DDL commands that don't return entity data directly.
   - Returns the number of rows affected.

```csharp
var newTitle = "Archived Blog";
var blogIdToArchive = 1;

// ExecuteSqlInterpolatedAsync (safer)
int rowsAffected = await context.Database
    .ExecuteSqlInterpolatedAsync($"UPDATE Blogs SET Title = {newTitle} WHERE BlogId = {blogIdToArchive}");

// ExecuteSqlRawAsync
// int rowsAffectedRaw = await context.Database
//    .ExecuteSqlRawAsync("UPDATE Blogs SET Title = @p0 WHERE BlogId = @p1", newTitle, blogIdToArchive);

Console.WriteLine($"{rowsAffected} row(s) updated.");
```
<p class="text-xs text-gray-400 mt-1">Use raw SQL judiciously. It can be powerful for complex scenarios not easily expressed in LINQ or for performance tuning specific queries, but you lose some compile-time safety and database abstraction.</p>

---
layout: default
---

# Advanced Querying (3/4) 📦

## Stored Procedures

EF Core can work with stored procedures (SPs) in your database.

**1. Querying Data using SPs (returning entities):**
   - Use `FromSqlRaw` or `FromSqlInterpolated` with the SP execution syntax.
   - The SP's result set columns **must match** the entity properties.

```csharp
// Assuming an SP `GetBlogsByAuthor` that returns Blog entities
var authorName = "Alice";
var blogsByAuthor = await context.Blogs
    .FromSqlInterpolated($"EXEC GetBlogsByAuthor {authorName}")
    .ToListAsync();
```
   - If your SP doesn't map directly to an entity, you might need to define a "keyless entity type" (query type in older EF Core versions) to map the results.

**2. Executing SPs that don't return queryable data (e.g., for modifications):**
   - Use `ExecuteSqlRawAsync` or `ExecuteSqlInterpolatedAsync`.

```csharp
var oldDomain = "oldsite.com";
var newDomain = "newsite.com";
await context.Database
    .ExecuteSqlInterpolatedAsync($"EXEC UpdateBlogDomains {oldDomain}, {newDomain}");
```

**3. Mapping Entities to Stored Procedures for CUD (EF Core 7+):**
   - EF Core 7+ introduced the ability to map `Insert`, `Update`, and `Delete` operations for an entity directly to stored procedures.
```csharp
// In OnModelCreating:
modelBuilder.Entity<Blog>()
    .InsertUsingStoredProcedure(
        "Blog_Insert", // SP name for insert
        spb => spb.HasParameter(b => b.Title) // Map parameters
                  .HasParameter(b => b.Url)
                  .HasResultColumn(b => b.BlogId)) // Output parameter for generated ID
    .UpdateUsingStoredProcedure( /* ... similar configuration ... */ )
    .DeleteUsingStoredProcedure( /* ... similar configuration ... */ );
```
   - When `context.SaveChanges()` is called, EF Core will call these SPs instead of generating standard SQL.

<p class="text-xs text-gray-400 mt-1">Working with SPs can be useful for encapsulating complex business logic in the database or leveraging existing database assets.</p>

---
layout: default
---

# Advanced Querying (4/4) ⏱️ Performance & Example

## Performance Tips for Querying

- **Select only needed data:** Use `Select()` to project only the columns you need, especially for read-only views or DTOs. Avoid fetching entire entities if only a few properties are used.
- **Use `AsNoTracking()` for read-only queries:** If you're fetching data only for display and don't intend to modify it, `AsNoTracking()` can significantly improve performance by disabling change tracking.
  ```csharp
  var blogs = await context.Blogs.AsNoTracking().ToListAsync();
  ```
- **Be mindful of N+1 query problem:** Especially with lazy loading. Eager load (`Include()`) or project data appropriately.
- **Filter early, sort late (generally):** Apply `Where()` clauses as early as possible to reduce the dataset before operations like sorting or joining.
- **Use asynchronous operations:** `ToListAsync()`, `FirstOrDefaultAsync()`, `SaveChangesAsync()` etc., to keep your application responsive.
- **Database indexing:** Ensure your database tables have appropriate indexes on columns frequently used in `WHERE` clauses, `JOIN` conditions, and `ORDER BY` clauses. This is a database-level optimization but crucial for EF Core performance.
- **Compiled Queries (for highly repetitive queries):** For queries executed very frequently with the same structure, compiled queries can offer a small performance boost by caching the query compilation. (More advanced).

<div class="mt-2 p-2 bg-gray-700 rounded-lg text-sm">
  <p class="text-yellow-300">📊 **Visual Metrics Placeholder:**</p>
  <p class="text-xs text-gray-300 mt-1">
    (Imagine charts here showing: Query time with vs. without `AsNoTracking()`; Impact of N+1 vs. Eager Loading; Benefit of `Select()` projection.)
  </p>
</div>

## Complex LINQ Query Example (from issue):
```csharp
// Assuming Post has PublishedDate and ViewCount properties
var popularPosts = await context.Posts
    .Where(p => p.PublishedDate > DateTime.Now.AddMonths(-1)) // Posts in the last month
    .OrderByDescending(p => p.ViewCount) // Order by most viewed
    .Take(10) // Get top 10
    .Select(p => new { p.Title, p.ViewCount, BlogTitle = p.Blog.Title }) // Project to anonymous type
    .ToListAsync();

foreach (var post in popularPosts)
{
    Console.WriteLine($"'{post.Title}' (from blog: {post.BlogTitle}) - Views: {post.ViewCount}");
}
```

---
layout: default
---

# Performance & Best Practices (1/4) ⏱️

## Change Tracking Explained

EF Core's **Change Tracking** is a powerful feature that automatically keeps track of the state of entities loaded by a `DbContext` instance. When you modify an entity, the change tracker records these modifications. When `SaveChanges()` is called, EF Core uses this information to generate and execute the necessary `INSERT`, `UPDATE`, or `DELETE` statements.

**How it works (simplified):**
1.  **Loading:** When an entity is queried from the database (and not using `AsNoTracking()`), the `DbContext` creates a "snapshot" of its original values.
2.  **Modification:** When you change a property of a tracked entity, its state changes (e.g., from `Unchanged` to `Modified`).
3.  **`SaveChanges()`:** EF Core compares the current values of tracked entities with their snapshots to identify changes.
4.  **Database Update:** SQL commands are generated and executed for entities in `Added`, `Modified`, or `Deleted` states.

**Entity States:**
- `Detached`: Not tracked by the context.
- `Unchanged`: Tracked, but no changes detected from original values.
- `Added`: Marked to be inserted into the database.
- `Modified`: Tracked, and some property values have changed.
- `Deleted`: Marked to be deleted from the database.

<div class="mt-3 grid grid-cols-2 gap-4 items-center">
  <div>
    <p class="text-sm text-yellow-300">Benefits:</p>
    <ul class="list-disc pl-4 text-xs">
      <li>Simplifies data persistence logic.</li>
      <li>Automatically generates efficient SQL for CUD operations.</li>
      <li>Manages relationships and foreign keys automatically.</li>
    </ul>
  </div>
  <div>
    <!-- Placeholder for Change Tracking Diagram -->
    <div class="p-2 border rounded-lg text-center bg-gray-700 text-xs">
      <p class="text-2xl">🔄</p>
      <p>DB Query ➡️ Entity (Unchanged)</p>
      <p>Entity.Property = NewValue ➡️ Entity (Modified)</p>
      <p>`SaveChanges()` ➡️ SQL UPDATE ➡️ Entity (Unchanged)</p>
      <p class="opacity-75 mt-1">(Visual: Diagram showing entity states and transitions)</p>
    </div>
  </div>
</div>
<p class="text-xs text-gray-400 mt-2">While powerful, change tracking has overhead. For read-only scenarios, disabling it can boost performance.</p>

---
layout: default
---

# Performance & Best Practices (2/4) 🚀

## `AsNoTracking()` Usage

For queries where you retrieve data **for read-only purposes** and do not intend to make changes to it and save those changes back to the database, using `AsNoTracking()` can provide significant performance improvements.

**How it helps:**
- **Disables Change Tracking:** EF Core doesn't create snapshots or track changes for these entities.
- **Reduces Memory Overhead:** Less memory is used as snapshots aren't stored.
- **Faster Query Execution:** Avoids the overhead of setting up change tracking information.

**When to use `AsNoTracking()`:**
- Displaying data in web pages, reports, or UIs where no updates will be made based on the queried data within the same `DbContext` instance.
- Scenarios where entities are short-lived and only used for reading information.

**Example:**
```csharp
// Standard query (change tracking enabled by default)
var trackedBlogs = await context.Blogs.ToListAsync();
// These blogs are tracked. Changes to them can be saved with SaveChanges().

// Query with AsNoTracking()
var noTrackingBlogs = await context.Blogs
                                .AsNoTracking() // Disables change tracking for this query
                                .ToListAsync();
// These blogs are NOT tracked. Changes to them will NOT be detected by SaveChanges().
// Ideal for read-only lists, dashboards, etc.
```

<div class="mt-3 p-2 bg-green-900 rounded-md text-sm">
  <p class="text-green-200">✅ **Best Practice:** Default to `AsNoTracking()` for all queries that don't lead to an update operation within the same `DbContext` scope.
  <br/> If you later need to update an entity fetched with `AsNoTracking()`, you'll need to attach it to a context and set its state (e.g., `context.Update(entity)`).
  </p>
</div>

You can also set `AsNoTracking()` as the default for all queries on a `DbContext` instance:
```csharp
// In DbContext constructor or OnConfiguring:
// this.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
```
But be cautious with this global setting, as it changes the default behavior everywhere.

---
layout: default
---

# Performance & Best Practices (3/4) ⚡

## Batch Operations (EF Core 7+)

Prior to EF Core 7, updating or deleting multiple entities based on a condition typically required loading them into memory first, then modifying or removing them, which could be inefficient for large datasets (N+1 problem for CUD).

EF Core 7 introduced `ExecuteUpdateAsync` and `ExecuteDeleteAsync` for performing **batch operations** directly in the database without loading entities into memory.

**`ExecuteDeleteAsync`:**
Deletes multiple entities matching a LINQ query predicate.

```csharp
// Example: Delete all posts from a specific blog without loading them
var blogIdToDeletePostsFrom = 1;
int numberOfDeletedPosts = await context.Posts
    .Where(p => p.BlogId == blogIdToDeletePostsFrom)
    .ExecuteDeleteAsync(); // Executes a DELETE FROM Posts WHERE BlogId = ...

Console.WriteLine($"{numberOfDeletedPosts} posts were deleted.");
```

**`ExecuteUpdateAsync`:**
Updates properties of multiple entities matching a LINQ query predicate.

```csharp
// Example: Mark all old posts as "Archived"
var cutoffDate = DateTime.UtcNow.AddYears(-2);
int numberOfUpdatedPosts = await context.Posts
    .Where(p => p.PublishedDate < cutoffDate && !p.IsArchived) // Assuming IsArchived property
    .ExecuteUpdateAsync(setters => setters
        .SetProperty(p => p.IsArchived, true)
        .SetProperty(p => p.LastUpdated, DateTime.UtcNow) // Example of setting another property
    );

Console.WriteLine($"{numberOfUpdatedPosts} posts were archived.");
```
<div class="mt-2 p-2 bg-blue-900 rounded-md text-sm">
  <p class="text-blue-200">🚀 **Benefits of Batch Operations:**
    <ul class="list-disc pl-4 text-xs">
      <li>Significant performance improvement for bulk CUD operations.</li>
      <li>Reduces network traffic and memory usage by not loading entities.</li>
      <li>Executes a single database command (or few) instead of many individual ones.</li>
    </ul>
  </p>
  <p class="text-xs text-yellow-300 mt-1">⚠️ Note: These operations do not involve the change tracker and bypass `SaveChanges()`. Interceptors and events related to `SaveChanges` won't be triggered.</p>
</div>

---
layout: default
---

# Performance & Best Practices (4/4) 🛠️

## Connection Pooling & Monitoring

**Connection Pooling:**
- ADO.NET (which EF Core uses underneath) provides database connection pooling by default for most providers (e.g., SQL Server, PostgreSQL).
- **How it works:** Instead of opening and closing physical database connections for each operation (which is expensive), connections are kept in a pool and reused.
- **EF Core benefits automatically:** When your `DbContext` opens and closes connections, it's typically interacting with the pool.
- **Configuration:** Pooling is usually configured at the ADO.NET provider level or via the connection string (e.g., `Max Pool Size`, `Min Pool Size`).
- **Best Practice:** Ensure your application disposes `DbContext` instances promptly (often handled by DI). This returns the connection to the pool, making it available for other requests. Don't keep `DbContext` instances alive longer than necessary (typically scoped per HTTP request in web apps).

**Performance Monitoring Tools:**
- **Logging:** EF Core can log SQL queries and other operations. Configure logging via `DbContextOptionsBuilder.LogTo()` or integrate with `ILoggerFactory`.
  ```csharp
  // Example: Log to console in OnConfiguring
  // optionsBuilder.LogTo(Console.WriteLine, LogLevel.Information);
  ```
- **Database Profiling Tools:**
    - SQL Server: SQL Server Management Studio (SSMS) Activity Monitor, Extended Events, SQL Profiler (deprecated but still used).
    - PostgreSQL: `pg_stat_statements` extension, `EXPLAIN ANALYZE` command.
    - Other DBs have similar tools.
- **Application Performance Monitoring (APM) Tools:**
    - Solutions like Azure Application Insights, Datadog, Dynatrace, New Relic can provide deep insights into EF Core performance, track query times, and identify bottlenecks.
- **MiniProfiler:** A simple but effective profiler for .NET applications, including ASP.NET Core, that can show SQL queries executed per request.

<div class="mt-2 p-2 bg-purple-900 rounded-md text-sm">
  <p class="text-purple-200">🔬 Regular monitoring and profiling are key to identifying and addressing performance issues in data-driven applications.</p>
</div>

---
layout: default
class: "text-center"
---

# 📊 Quick Poll! 🙋‍♀️🙋‍♂️

What's your biggest challenge when working with EF Core?

(Presenter: Use this as a point for live audience interaction, e.g., show of hands, online poll tool)

<ul class="mt-4 text-left mx-auto w-max space-y-2">
  <li>A) Understanding LINQ query translation to SQL</li>
  <li>B) Performance tuning complex queries</li>
  <li>C) Managing migrations in a team</li>
  <li>D) Debugging runtime exceptions</li>
  <li>E) Other (please share!)</li>
</ul>

<p class="mt-6 text-sm opacity-75">(This is a placeholder for an interactive poll)</p>

---
layout: default
---

# Configuration & Fluent API (1/4) 🛠️

## `OnModelCreating` - The Configuration Hub

The `OnModelCreating(ModelBuilder modelBuilder)` method in your `DbContext` is the primary way to configure your model using the **Fluent API**. It's called by EF Core when the context is first initialized to build the model.

**Why use Fluent API in `OnModelCreating`?**
- **Centralized Configuration:** Keeps all your entity mapping and database schema configurations in one place.
- **Powerful & Flexible:** Offers more configuration options than Data Annotations.
- **Clean POCOs:** Keeps your entity classes free from EF-specific attributes.
- **Overrides Conventions & Data Annotations:** Fluent API provides the highest level of precedence.

**Basic Structure:**
```csharp
using Microsoft.EntityFrameworkCore;

public class MyAppContext : DbContext
{
    // DbSet properties...
    public DbSet<Blog> Blogs { get; set; }
    public DbSet<Post> Posts { get; set; }
    // ...

    public MyAppContext(DbContextOptions<MyAppContext> options) : base(options) { }

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        base.OnModelCreating(modelBuilder); // Good practice to call base method

        // === Entity Configurations Start Here ===

        // Example: Configure the Blog entity
        modelBuilder.Entity<Blog>(entity =>
        {
            entity.ToTable("WebsiteBlogs", schema: "dbo"); // Map to specific table and schema
            entity.HasKey(b => b.BlogId); // Define primary key
            // ... more Blog configurations ...
        });

        // Example: Configure the Post entity
        modelBuilder.Entity<Post>(entity =>
        {
            // ... Post configurations from the issue ...
            entity.HasIndex(p => p.Title).IsUnique(); // As per issue
            entity.Property(p => p.Content).HasMaxLength(5000); // Modified from issue (1000 to 5000)
            // ... more Post configurations ...
        });

        // You can also separate configurations into IEntityTypeConfiguration<T> classes
    }
}
```
<p class="text-xs text-gray-400 mt-1">`ModelBuilder` is the main API you interact with to define shapes of entities, relationships, and how they map to the database.</p>

---
layout: default
---

# Configuration & Fluent API (2/4) 🔩

## Entity Configuration Examples

Fluent API provides a rich set of methods to configure entities.

**Common Entity-Level Configurations:**
- **Table Mapping:**
  ```csharp
  modelBuilder.Entity<Customer>().ToTable("ClientDetails", schema: "sales");
  ```
- **Primary Key:**
  ```csharp
  modelBuilder.Entity<Book>().HasKey(b => b.ISBN); // Single PK
  modelBuilder.Entity<OrderItem>().HasKey(oi => new { oi.OrderId, oi.ProductId }); // Composite PK
  ```
- **Alternate Keys (Unique Constraints):**
  ```csharp
  modelBuilder.Entity<User>().HasAlternateKey(u => u.Username);
  ```
- **Ignoring Properties (Not Mapped):**
  ```csharp
  modelBuilder.Entity<Product>().Ignore(p => p.CalculatedDiscount);
  ```
- **Table Comments (Provider specific, e.g., SQL Server EF Core 7+):**
  ```csharp
  // modelBuilder.Entity<Blog>().HasComment("Contains all blog entries");
  ```

**Common Property-Level Configurations:**
- **Column Name & Type:**
  ```csharp
  modelBuilder.Entity<Employee>()
      .Property(e => e.FullName)
      .HasColumnName("EmployeeName")
      .HasColumnType("nvarchar(150)");
  ```
- **Required / Optional:**
  ```csharp
  modelBuilder.Entity<Post>().Property(p => p.Title).IsRequired(); // NOT NULL
  modelBuilder.Entity<Post>().Property(p => p.SubTitle).IsRequired(false); // NULLable
  ```
- **Max Length:**
  ```csharp
  modelBuilder.Entity<Category>().Property(c => c.CategoryName).HasMaxLength(100);
  ```
- **Concurrency Tokens:**
  ```csharp
  modelBuilder.Entity<Product>().Property(p => p.RowVersion).IsRowVersion(); // For optimistic concurrency
  ```
- **Default Values:**
  ```csharp
  modelBuilder.Entity<Post>().Property(p => p.CreatedDate).HasDefaultValueSql("GETDATE()"); // SQL Server
  modelBuilder.Entity<User>().Property(u => u.IsActive).HasDefaultValue(true);
  ```

---
layout: default
---

# Configuration & Fluent API (3/4) 🔑

## Index Creation

Indexes are crucial for database query performance. Fluent API allows detailed configuration of database indexes.

**Creating a Simple Index:**
```csharp
// Creates an index on the 'Url' column of the 'Blogs' table
modelBuilder.Entity<Blog>()
    .HasIndex(b => b.Url);
```
By default, this creates a non-unique index named `IX_Blogs_Url`.

**Creating a Unique Index:**
Ensures that all values in the indexed column (or columns) are unique.
```csharp
// Creates a unique index on the 'Username' column of the 'Users' table
modelBuilder.Entity<User>()
    .HasIndex(u => u.Username)
    .IsUnique(); // Makes the index unique
```

**Creating a Composite Index (index on multiple columns):**
```csharp
// Creates an index on LastName and FirstName columns
modelBuilder.Entity<Person>()
    .HasIndex(p => new { p.LastName, p.FirstName });
```

**Naming an Index:**
```csharp
modelBuilder.Entity<Product>()
    .HasIndex(p => p.ProductCode)
    .IsUnique()
    .HasDatabaseName("UX_Product_Code"); // Custom unique index name
```

**Included Columns (SQL Server specific, improves query performance for covered queries):**
```csharp
// modelBuilder.Entity<Order>()
//     .HasIndex(o => o.OrderDate)
//     .IncludeProperties(o => new { o.OrderTotal, o.CustomerId }) // SQL Server specific
//     .HasDatabaseName("IX_Order_OrderDate_Includes");
```

**Filtered Indexes (defines a WHERE clause for the index):**
```csharp
// Creates an index only for active users
modelBuilder.Entity<User>()
    .HasIndex(u => u.Email)
    .HasFilter("[IsActive] = 1"); // SQL WHERE clause for the index
```
<p class="text-xs text-gray-400 mt-1">Proper indexing is vital for performance. Analyze your query patterns to determine which columns need indexes.</p>

---
layout: default
---

# Configuration & Fluent API (4/4) 🌱

## Seed Data

EF Core can automatically seed your database with initial data when migrations are applied. This is useful for lookup tables, default admin users, or sample data for development.

**Seeding Data using `HasData` in `OnModelCreating`:**
- The `HasData` method is called within an entity's configuration.
- You provide instances of your entity with their primary keys specified.
- This data is inserted during migration (`dotnet ef database update`).

**Example (from issue, adapted for Blog/Post):**
```csharp
// In OnModelCreating(ModelBuilder modelBuilder) within your DbContext:

// Seed a Blog
modelBuilder.Entity<Blog>().HasData(
    new Blog { BlogId = 1, Title = "Tech Insights", Url = "http://techinsights.example.com" }
);

// Seed Posts for that Blog
modelBuilder.Entity<Post>().HasData(
    new Post
    {
        PostId = 1,
        BlogId = 1, // Foreign Key to the seeded Blog
        Title = "EF Core Basics",
        Content = "An introduction to Entity Framework Core..."
    },
    new Post
    {
        PostId = 2,
        BlogId = 1,
        Title = "Advanced EF Core",
        Content = "Diving deeper into EF Core features..."
    }
);

// Other configurations (as per issue, for example on Post)
modelBuilder.Entity<Post>(entity =>
{
    // Index on Title (can be combined with HasData for the same entity type)
    entity.HasIndex(p => p.Title)
          .IsUnique(); // Ensures post titles are unique

    // Max length for Content
    entity.Property(p => p.Content)
          .HasMaxLength(5000); // Max 5000 characters for post content
});
```
<div class="mt-2 p-2 bg-green-900 rounded-md text-sm">
  <p class="text-green-200">Considerations for Seed Data:
    <ul class="list-disc pl-4 text-xs">
      <li>Primary keys must be provided and must be unique.</li>
      <li>For auto-generated keys (like identity), you still need to provide a value for seeding. EF Core handles it correctly for the migration.</li>
      <li>`HasData` is for static, relatively unchanging data. For dynamic or large datasets, consider custom seeding logic outside migrations.</li>
      <li>Changes to seed data will generate new migrations.</li>
    </ul>
  </p>
</div>

---
layout: default
---

# Testing with EF (1/4) 🧪

## In-Memory Database for Testing

For unit and integration tests, EF Core offers an **In-Memory database provider** (`Microsoft.EntityFrameworkCore.InMemory`). This allows you to run tests quickly without needing a real database server.

**Key Features & Use Cases:**
- **Fast:** Operations are in-memory, no disk I/O or network latency.
- **Isolated:** Each test can have its own clean database instance.
- **Good for Unit Tests:** Testing business logic in services that use `DbContext`, ensuring LINQ queries are syntactically correct.
- **Not a Relational Database:** It's important to remember the In-Memory provider is **not** a true relational database. It doesn't mimic all behaviors of SQL Server, PostgreSQL, etc. (e.g., constraints, raw SQL, transactions across multiple contexts might behave differently or not be supported).

**Setup Example (xUnit):**
```csharp
// Add NuGet package: Microsoft.EntityFrameworkCore.InMemory

public class MyServiceTests : IDisposable // For context cleanup
{
    private readonly MyDbContext _context;
    private readonly MyService _service;

    public MyServiceTests()
    {
        var options = new DbContextOptionsBuilder<MyDbContext>()
            .UseInMemoryDatabase(databaseName: Guid.NewGuid().ToString()) // Unique DB per test run
            .Options;

        _context = new MyDbContext(options);
        _service = new MyService(_context); // Assuming MyService takes MyDbContext

        // Optional: Seed initial data for tests
        _context.Blogs.Add(new Blog { BlogId = 1, Title = "Test Blog 1" });
        _context.SaveChanges();
    }

    [Fact]
    public async Task GetBlog_ShouldReturnExistingBlog()
    {
        var blog = await _service.GetBlogAsync(1);
        Assert.NotNull(blog);
        Assert.Equal("Test Blog 1", blog.Title);
    }

    public void Dispose()
    {
        _context.Database.EnsureDeleted(); // Clean up the In-Memory database
        _context.Dispose();
    }
}
```
<p class="text-xs text-yellow-300 mt-1">⚠️ For tests requiring true relational database behavior or provider-specific features, consider using SQLite in-memory mode or test containers with a real database engine.</p>

---
layout: default
---

# Testing with EF (2/4) 🎯

## Unit Testing Strategies

When unit testing code that uses EF Core, the goal is to isolate the logic you're testing from the actual database.

**What to Test:**
- Business logic within your services, repositories, or classes that consume `DbContext`.
- Correctness of LINQ query construction (though the In-Memory provider helps here).
- How your code handles data returned from `DbContext`.
- Logic that manipulates entities before saving or after fetching.

**Strategies:**

1.  **Using the In-Memory Provider (as shown on previous slide):**
    *   **Pros:** Easy to set up, good for testing most LINQ queries and CUD operations against a simplified in-memory store.
    *   **Cons:** Not a real relational database; doesn't enforce all constraints or support all DB-specific functions. Raw SQL against it won't work like against SQL Server.

2.  **Using SQLite in In-Memory Mode:**
    *   SQLite can run in a purely in-memory mode, offering a closer-to-real relational database experience than the `InMemory` provider.
    *   Supports more relational features, transactions, and constraints.
    *   Setup: `optionsBuilder.UseSqlite("Data Source=:memory:");` and ensure a connection is kept open.

3.  **Mocking `DbContext` and `DbSet` (covered next):**
    *   **Pros:** Full isolation, no database dependency (real or in-memory). Fast.
    *   **Cons:** Can be complex to set up mocks for `DbSet` behavior (querying, adding, saving). Testing the EF Core query translation itself is not possible.

4.  **Repository Pattern:**
    *   Abstracting data access behind a repository interface (`IRepository<T>`) allows you to mock the repository easily, rather than `DbContext` directly.
    *   Your service depends on `IRepository<T>`, which can have a fake implementation for tests.

<div class="mt-2 p-2 bg-blue-900 rounded-md text-sm">
  <p class="text-blue-200">💡 Choose the strategy that best fits the specific test's goal. For complex query logic tied to a specific database, integration tests against a test database (or test containers) might be more appropriate.</p>
</div>

---
layout: default
---

# Testing with EF (3/4) 🎭

## Mocking DbContext and DbSet

Mocking `DbContext` and `DbSet` provides complete isolation from the database, allowing you to test your application logic without any database interaction. This is useful for pure unit tests where you want to control exactly what the data access layer returns.

**Challenges:**
- `DbSet<T>` implements `IQueryable<T>`, `IEnumerable<T>`, and specific methods like `Add`, `Remove`, `FindAsync`. Mocking all this behavior can be verbose.
- Testing LINQ query translation is not possible with mocks, as there's no query provider.

**Using a Mocking Framework (e.g., Moq):**

```csharp
// Requires Moq NuGet package

// Helper to create a mock DbSet from a List<T>
public static DbSet<T> CreateMockDbSet<T>(List<T> sourceList) where T : class
{
    var queryable = sourceList.AsQueryable();
    var dbSet = new Mock<DbSet<T>>();

    dbSet.As<IQueryable<T>>().Setup(m => m.Provider).Returns(queryable.Provider);
    dbSet.As<IQueryable<T>>().Setup(m => m.Expression).Returns(queryable.Expression);
    dbSet.As<IQueryable<T>>().Setup(m => m.ElementType).Returns(queryable.ElementType);
    dbSet.As<IQueryable<T>>().Setup(m => m.GetEnumerator()).Returns(() => queryable.GetEnumerator());

    dbSet.Setup(d => d.Add(It.IsAny<T>())).Callback<T>(sourceList.Add);
    // ... mock other CUD operations as needed ...

    // For FindAsync (example, assuming single int PK)
    // dbSet.Setup(m => m.FindAsync(It.IsAny<object[]>()))
    //    .Returns<object[]>(ids =>
    //        Task.FromResult(sourceList.FirstOrDefault(e => GetPrimaryKeyValue(e) == (int)ids[0])));

    return dbSet.Object;
}
// private static int GetPrimaryKeyValue<T>(T entity) { /* Reflection to get PK value */ return 0; }


// In your test:
var mockBlogs = new List<Blog>
{
    new Blog { BlogId = 1, Title = "Mocked Blog 1" }
};
var mockDbSet = CreateMockDbSet(mockBlogs);

var mockContext = new Mock<MyDbContext>(new DbContextOptions<MyDbContext>()); // Ensure constructor is mockable
mockContext.Setup(c => c.Blogs).Returns(mockDbSet);
// If SaveChangesAsync needs to be tested for calls:
// mockContext.Setup(c => c.SaveChangesAsync(It.IsAny<CancellationToken>())).ReturnsAsync(1);

var service = new MyService(mockContext.Object);
var blog = await service.GetBlogAsync(1); // Service method uses context.Blogs

Assert.NotNull(blog);
Assert.Equal("Mocked Blog 1", blog.Title);
```
<p class="text-xs text-yellow-300 mt-1">⚠️ Mocking `FindAsync` and async operations on `DbSet` can be tricky. Libraries like `EntityFrameworkCore.Testing.Moq` can simplify this significantly.</p>

---
layout: default
---

# Testing with EF (4/4) 📝

## Test Examples with xUnit (and InMemory)

Here are more focused examples using xUnit and the InMemory provider.

**Test Class Setup:**
```csharp
// MyBlogService.cs (Example service to test)
public class MyBlogService
{
    private readonly BlogContext _context;
    public MyBlogService(BlogContext context) { _context = context; }

    public async Task<Blog> GetBlogByIdAsync(int id) => await _context.Blogs.FindAsync(id);

    public async Task<List<Blog>> GetBlogsWithMinPostsAsync(int minPosts)
    {
        return await _context.Blogs
            .Where(b => b.Posts.Count >= minPosts)
            .Include(b => b.Posts) // Ensure posts are loaded for the count
            .ToListAsync();
    }

    public async Task AddBlogAsync(Blog blog)
    {
        _context.Blogs.Add(blog);
        await _context.SaveChangesAsync();
    }
}

// MyBlogServiceTests.cs
public class MyBlogServiceTests : IDisposable
{
    private readonly BlogContext _context;
    private readonly MyBlogService _service;

    public MyBlogServiceTests()
    {
        var options = new DbContextOptionsBuilder<BlogContext>()
            .UseInMemoryDatabase(databaseName: Guid.NewGuid().ToString()) // Unique name
            .Options;
        _context = new BlogContext(options); // Assuming BlogContext has appropriate constructor
        _service = new MyBlogService(_context);
    }

    // Seed data for each test or constructor as needed
    private void SeedData()
    {
        _context.Blogs.AddRange(
            new Blog { BlogId = 1, Title = "Seed Blog 1", Posts = new List<Post>() },
            new Blog { BlogId = 2, Title = "Seed Blog 2", Posts = new List<Post> { new Post { PostId = 1, Title = "P1" } } }
        );
        _context.SaveChanges();
    }

    [Fact]
    public async Task GetBlogByIdAsync_ReturnsCorrectBlog()
    {
        SeedData();
        var blog = await _service.GetBlogByIdAsync(1);
        Assert.NotNull(blog);
        Assert.Equal("Seed Blog 1", blog.Title);
    }

    [Fact]
    public async Task AddBlogAsync_AddsBlogToDatabase()
    {
        var newBlog = new Blog { BlogId = 3, Title = "New Test Blog" };
        await _service.AddBlogAsync(newBlog);

        var blogFromDb = await _context.Blogs.FindAsync(3); // Verify directly from context
        Assert.NotNull(blogFromDb);
        Assert.Equal("New Test Blog", blogFromDb.Title);
    }

    [Fact]
    public async Task GetBlogsWithMinPostsAsync_ReturnsFilteredBlogs()
    {
        SeedData(); // Blog 2 has 1 post
        var blogs = await _service.GetBlogsWithMinPostsAsync(1);
        Assert.Single(blogs); // Expecting only Seed Blog 2
        Assert.Equal("Seed Blog 2", blogs[0].Title);
    }

    public void Dispose() // xUnit calls Dispose after each test
    {
        _context.Database.EnsureDeleted(); // Crucial for InMemory provider test isolation
        _context.Dispose();
    }
}
```
<p class="text-xs text-gray-400 mt-1">This structure provides a clean way to test services interacting with EF Core using the InMemory provider, ensuring each test runs with a fresh, isolated data store.</p>

---
layout: default
---

# EF Core Features (1/4) 🌐

## Global Query Filters

Global query filters allow you to define LINQ query predicates that are **automatically applied** to all queries for a given entity type. This is extremely useful for implementing soft deletes, multi-tenancy, or other conditions that should always apply.

**How it works:**
- Defined in `OnModelCreating` using `HasQueryFilter()`.
- The filter is applied to all queries for that entity, including those via navigation properties.
- Can be disabled for a specific query using `IgnoreQueryFilters()`.

**Example: Soft Deletes**
Assume an `IsDeleted` property on a `BlogPost` entity. We only want to retrieve non-deleted posts by default.

```csharp
public class BlogPost
{
    public int BlogPostId { get; set; }
    public string Title { get; set; }
    public bool IsDeleted { get; set; } // Soft delete flag
    // ... other properties
}

// In DbContext.OnModelCreating():
modelBuilder.Entity<BlogPost>()
    .HasQueryFilter(p => !p.IsDeleted); // Automatically filter out deleted posts

// --- Usage ---
// This query will now automatically add 'WHERE IsDeleted = 0' (or equivalent)
var activePosts = await context.BlogPosts.ToListAsync();

// To include soft-deleted items for admin purposes:
var allPostsIncludingDeleted = await context.BlogPosts
    .IgnoreQueryFilters() // Temporarily disable the global filter
    .ToListAsync();
```
<div class="mt-2 p-2 bg-blue-900 rounded-md text-sm">
  <p class="text-blue-200">✨ **Use Cases:**
    <ul class="list-disc pl-4 text-xs">
      <li>Soft deletes (as shown).</li>
      <li>Multi-tenancy (e.g., `HasQueryFilter(p => p.TenantId == _currentTenantId)`).</li>
      <li>Filtering based on status (e.g., only show "Published" articles).</li>
    </ul>
  </p>
</div>

---
layout: default
---

# EF Core Features (2/4) 影子

## Shadow Properties

Shadow properties are properties that are **not defined in your .NET entity class** but are part of the EF Core model for that entity type. Their values and state are maintained purely in the Change Tracker.

**Why use Shadow Properties?**
- When you don't want to expose a database column on your entity class (e.g., for auditing fields like `LastUpdated`, `CreatedDate` that are managed by the database or EF Core interceptors).
- To avoid cluttering your domain model with persistence-specific concerns.

**Configuration (Fluent API):**
```csharp
// In DbContext.OnModelCreating():
modelBuilder.Entity<Blog>()
    .Property<DateTime>("LastUpdated") // Defines a shadow property of type DateTime
    .HasDefaultValueSql("GETDATE()"); // Example: SQL Server function for default

modelBuilder.Entity<Blog>()
    .Property<string>("CreatedBy");
```

**Accessing Shadow Properties:**
You use the `EF.Property<T>(entity, "PropertyName")` method.
```csharp
// Setting a shadow property value
context.Entry(myBlog).Property("CreatedBy").CurrentValue = "admin";

// Getting a shadow property value in a query
var blogsWithLastUpdated = await context.Blogs
    .OrderByDescending(b => EF.Property<DateTime>(b, "LastUpdated"))
    .Select(b => new
    {
        b.Title,
        LastUpdated = EF.Property<DateTime>(b, "LastUpdated")
    })
    .ToListAsync();
```
<div class="mt-2 p-2 bg-yellow-800 bg-opacity-30 rounded-md text-sm">
  <p class="text-yellow-300">💡 Shadow properties are useful for database columns that your application code doesn't directly interact with but are important for the database schema or auditing. Foreign keys can also be shadow properties by convention if you don't explicitly define them in your entity.</p>
</div>

<br/>
<div class="p-3 mt-4 bg-blue-900 rounded-lg text-sm">
  <p class="font-bold text-blue-200">💡 Did you know?</p>
  <p class="text-blue-300 mt-1">
    Foreign key properties can also be shadow properties! If you define a navigation property (e.g., `Blog.Posts`) but don't explicitly create a foreign key property in your entity class (e.g., `Post.BlogId`), EF Core will create one as a shadow property by convention.
  </p>
</div>

---
layout: default
---

# EF Core Features (3/4) 🛡️

## Backing Fields

EF Core can read and/or write to a **backing field** instead of a property. This allows more control over how data is accessed and can be useful for encapsulation or implementing business logic around property access.

**Configuration:**
- By convention, EF Core looks for fields matching certain patterns (e.g., `_<propertyName>`, `m_<propertyName>`).
- Can be configured explicitly using Fluent API: `Property(b => b.Url).HasField("_blogUrl")`.
- You can also specify `PropertyAccessMode` (e.g., `Field`, `FieldDuringConstruction`, `PreferField`).

**Example: Read-only property with a backing field for URL validation**
```csharp
public class Blog
{
    private string _url; // Backing field

    public int BlogId { get; set; }
    public string Title { get; set; }

    public string Url // Read-only property in the class
    {
        get { return _url; }
        // No public setter, or a private one
    }

    // Constructor or method to set the URL, potentially with validation
    public Blog(string title, string url)
    {
        Title = title;
        SetUrl(url); // Use a method to set the backing field
    }

    public void SetUrl(string newUrl) // Method that EF Core can use to set the field
    {
        if (string.IsNullOrWhiteSpace(newUrl) || !Uri.IsWellFormedUriString(newUrl, UriKind.Absolute))
        {
            throw new ArgumentException("Invalid URL format");
        }
        _url = newUrl;
    }
}

// In DbContext.OnModelCreating():
modelBuilder.Entity<Blog>()
    .Property(b => b.Url) // Configure the 'Url' property
    .HasField("_url")     // Tell EF Core to use the '_url' backing field
    .UsePropertyAccessMode(PropertyAccessMode.Field); // Always use field for DB ops
                                                     // (or PreferFieldDuringConstruction etc.)
```
<div class="mt-2 p-2 bg-green-900 rounded-md text-sm">
  <p class="text-green-200">✅ Benefits:
    <ul class="list-disc pl-4 text-xs">
      <li>Encapsulation: Hide setters or apply logic when properties are accessed.</li>
      <li>Validation: Enforce rules before data is set to the field.</li>
      <li>Read-only properties in your model that are still mapped to database columns.</li>
    </ul>
  </p>
</div>

---
layout: default
---

# EF Core Features (4/4) 🔄🧱

## Value Conversions & Owned Entity Types

**Value Conversions:**
- Allow property values to be converted when reading from or writing to the database.
- Useful for mapping types not natively supported by the database provider or for encrypting/transforming data.
```csharp
// Example: Storing an Enum as a string
public enum BlogStatus { Draft, Published, Archived }
public class Article { /* ... */ public BlogStatus Status { get; set; } }

// In OnModelCreating():
modelBuilder.Entity<Article>()
    .Property(e => e.Status)
    .HasConversion(
        v => v.ToString(), // Convert enum to string for DB
        v => (BlogStatus)Enum.Parse(typeof(BlogStatus), v)); // String from DB to enum

// Example: Simple DateOnly to DateTime conversion (EF Core 6+)
// modelBuilder.Entity<MyEntity>().Property(e => e.MyDateOnlyProperty); // EF Core 6+ handles this often
```

**Owned Entity Types (Complex Types / Value Objects):**
- Allow you to model entities that can only exist as part of another "owner" entity. They don't have their own primary key and are conceptually part of the owner.
- Mapped to the same table as the owner by default (table splitting).
```csharp
// Address is an Owned Entity Type, part of Customer
public class Address { public string Street { get; set; } public string City { get; set; } }
public class Customer
{
    public int CustomerId { get; set; }
    public Address ShippingAddress { get; set; } // Owned
    public Address BillingAddress { get; set; }  // Another owned instance
}

// In OnModelCreating():
modelBuilder.Entity<Customer>().OwnsOne(c => c.ShippingAddress, sa => {
    sa.Property(p => p.Street).HasColumnName("ShippingStreet"); // Columns prefixed by default
    sa.Property(p => p.City).HasColumnName("ShippingCity");
});
modelBuilder.Entity<Customer>().OwnsOne(c => c.BillingAddress, ba => {
    // ... configure BillingAddress columns ...
});
```
<div class="mt-1 p-1 bg-purple-900 rounded-md text-xs">
  <p class="text-purple-200">🚀 These features provide greater flexibility in how your domain model maps to the database schema, enabling cleaner domain models and handling of various data types.</p>
</div>

---
layout: default
---

# Common Pitfalls & Solutions (1/3) ⚠️

## The N+1 Query Problem

This is a classic performance pitfall where an application makes **N** additional database queries to fetch related data for **N** parent entities, instead of fetching it all in one go or a few queries. It often occurs with lazy loading or inefficient explicit loading.

**Scenario:** Displaying a list of Blogs and their first Post's title.

**Problematic Code (Illustrative - often with Lazy Loading):**
```csharp
// Assuming Lazy Loading is enabled or posts are loaded inefficiently per blog
var blogs = await context.Blogs.ToListAsync(); // 1 query to get all blogs

foreach (var blog in blogs) // Loop N times (for N blogs)
{
    // If Posts are lazy-loaded, this access triggers a SEPARATE query for each blog:
    var firstPostTitle = blog.Posts.FirstOrDefault()?.Title ?? "No posts";
    Console.WriteLine($"Blog: {blog.Title}, First Post: {firstPostTitle}");
}
// Total Queries = 1 (for blogs) + N (for posts of each blog) = N+1 queries!
```

<div class="text-center my-4">
  <p class="text-sm opacity-75">[Placeholder for a relatable "N+1 queries be like..." meme 🖼️]</p>
  <p class="text-xs text-gray-500">(Imagine a picture of someone making many trips for groceries)</p>
</div>

**Solution: Eager Loading with `Include()` or Projection**
```csharp
// Solution 1: Eager Loading
var blogsWithPosts = await context.Blogs
    .Include(b => b.Posts) // Fetches blogs and their related posts in fewer queries (often 1 or 2)
    .ToListAsync();

foreach (var blog in blogsWithPosts)
{
    var firstPostTitle = blog.Posts.FirstOrDefault()?.Title ?? "No posts";
    Console.WriteLine($"Blog: {blog.Title}, First Post: {firstPostTitle}");
}

// Solution 2: Projection (Select only what you need)
var blogPostTitles = await context.Blogs
    .Select(b => new
    {
        BlogTitle = b.Title,
        FirstPostTitle = b.Posts.OrderBy(p => p.PostId).Select(p => p.Title).FirstOrDefault() ?? "No posts"
    })
    .ToListAsync(); // EF Core often translates this into an efficient single query.

foreach (var item in blogPostTitles)
{
    Console.WriteLine($"Blog: {item.BlogTitle}, First Post: {item.FirstPostTitle}");
}
```
<div class="mt-2 p-2 bg-red-700 bg-opacity-80 rounded-md text-sm">
  <p class="text-red-100">🔴 **Impact:** N+1 queries lead to excessive database chattiness, increased latency, and poor application performance, especially with large datasets.</p>
  <p class="text-green-200 mt-1">✅ **Fix:** Use `Include()` for related data you know you'll need, or project into specific DTOs/anonymous types.</p>
</div>

---
layout: default
---

# Common Pitfalls & Solutions (2/3) 💧

## Memory Leaks & DbContext Lifetime

Improper management of `DbContext` lifetime is a common source of issues, including memory leaks and incorrect data sharing.

**Key Principle:** `DbContext` is designed to be a **short-lived unit of work**.
- In ASP.NET Core, it's typically scoped to the HTTP request.
- For other app types, create and dispose it for each logical operation.

**Common Pitfalls:**
1.  **Long-Lived DbContext Instances (e.g., Singleton):**
    *   The context tracks all entities it has ever loaded. Over time, this can lead to huge memory consumption.
    *   Data can become stale as the context won't automatically refresh entities from the database unless explicitly told to.
    *   Concurrency issues can arise if a single instance is shared across multiple threads.
    *   **Solution:** Use DI to scope `DbContext` correctly (e.g., `AddDbContext` in ASP.NET Core registers it as scoped by default). Manually, use `using` statements.

2.  **Not Disposing DbContext:**
    *   `DbContext` implements `IDisposable`. Failing to dispose it can prevent connections from being returned to the pool promptly and can hold onto memory.
    *   **Solution:**
        ```csharp
        // ASP.NET Core DI handles disposal.
        // Manual usage:
        using (var context = new MyDbContext(options))
        {
            // Use context
        } // context.Dispose() is called here
        ```

3.  **Overuse of `AsNoTracking()` when Updates are Needed:**
    *   While good for read-only, if you fetch with `AsNoTracking()` and then decide to update, you must re-attach the entity and set its state, which can be error-prone if not handled correctly.
    *   **Solution:** Understand when data is for reading vs. modification. Load with tracking if updates are likely within the same unit of work.

4.  **Large Number of Tracked Entities:**
    *   Even with proper scoping, loading and tracking thousands of entities in a single `DbContext` instance for a complex operation can be memory-intensive.
    *   **Solution:** Process data in smaller batches if possible. Use `AsNoTracking()` for parts of the operation that are read-only. Consider batch `ExecuteUpdate/Delete` for bulk modifications.

---
layout: default
---

# Common Pitfalls & Solutions (3/3) 🐛

## Exception Handling & Debugging

Understanding and handling EF Core exceptions, and effectively debugging issues, is crucial.

**Common EF Core Exceptions:**
- `DbUpdateException`: Generic exception when `SaveChanges()` fails. Inner exception often has more details (e.g., `SqlException` for constraint violations).
- `DbUpdateConcurrencyException`: Thrown during `SaveChanges()` if a concurrency conflict is detected (e.g., optimistic locking failure).
- `InvalidOperationException`: Often indicates incorrect usage, such as trying to use a disposed context, issues with LINQ query translation, or model configuration errors.
- Provider-Specific Exceptions (e.g., `SqlException`, `NpgsqlException`): Indicate database-level errors.

**Best Practices for Exception Handling:**
```csharp
try
{
    // ... EF Core operations ...
    await context.SaveChangesAsync();
}
catch (DbUpdateConcurrencyException ex)
{
    // Handle optimistic concurrency conflict (e.g., reload data, inform user)
    Console.WriteLine("Concurrency conflict: " + ex.Message);
    // ex.Entries gives access to the entities that failed to save.
}
catch (DbUpdateException ex)
{
    // Inspect inner exception for database-specific errors
    Console.WriteLine("Error saving changes: " + ex.Message);
    if (ex.InnerException != null)
    {
        Console.WriteLine("Inner exception: " + ex.InnerException.Message);
        // Check for specific DB error codes if needed (e.g., unique constraint violation)
    }
}
catch (Exception ex) // Generic fallback
{
    Console.WriteLine("An unexpected error occurred: " + ex.Message);
    // Log the full exception details
}
```

**Debugging Tips:**
1.  **Logging:** Enable EF Core logging (see Performance slide) to view generated SQL and other diagnostics.
2.  **Debugger:** Step through your code. Inspect `ChangeTracker.DebugView` for a detailed view of tracked entities and their states.
3.  **LINQ Query Debugging:**
    *   Break down complex LINQ queries into smaller parts.
    *   Examine the generated SQL (via logging or profiler).
    *   Be aware that `ToString()` on an `IQueryable` in EF Core (before .NET 7) often didn't show the SQL; use logging.
4.  **Database Profiler:** Use your database's native profiling tools to capture and analyze executed SQL.
5.  **Check Model Configuration:** Ensure your entities, relationships, and keys are correctly configured in `OnModelCreating` or via Data Annotations.
6.  **Migration Status:** Ensure your database schema is up-to-date with your model (`dotnet ef database update`).

---
layout: default
---

# Real-World Scenarios (1/3) 🛒

## E-commerce Application Example

EF Core is well-suited for complex applications like e-commerce platforms. Consider these core entities and relationships:

<div class="grid grid-cols-2 gap-6 mt-4 text-sm">
<div>
**Core Entities:**
<ul class="list-disc pl-5">
  <li>`Customer` (UserId, Name, Email, Addresses)</li>
  <li>`Product` (ProductId, Name, Description, Price, StockQuantity, CategoryId)</li>
  <li>`Category` (CategoryId, Name)</li>
  <li>`Order` (OrderId, CustomerId, OrderDate, TotalAmount, ShippingAddress, BillingAddress)</li>
  <li>`OrderItem` (OrderItemId, OrderId, ProductId, Quantity, UnitPrice)</li>
  <li>`ShoppingCart` / `CartItem` (for managing user carts)</li>
  <li>`Inventory` (if stock management is complex)</li>
  <li>`Review` (ReviewId, ProductId, CustomerId, Rating, Comment)</li>
</ul>
</div>
<div>
**Key Relationships & EF Core Concepts:**
<ul class="list-disc pl-5">
  <li>**Customer to Orders:** One-to-Many (`Customer.Orders`)</li>
  <li>**Order to OrderItems:** One-to-Many (`Order.OrderItems`)</li>
  <li>**Product to OrderItems:** One-to-Many (`Product.OrderItems`)</li>
  <li>**Product to Category:** Many-to-One (`Product.Category`)</li>
  <li>**Product to Reviews:** One-to-Many (`Product.Reviews`)</li>
  <li>**Owned Entity Types:** `Address` can be owned by `Customer` and `Order`.</li>
  <li>**Complex Queries:** Calculating total sales, finding popular products, customer order history (using LINQ, `GroupBy`, `Sum`, `Average`).</li>
  <li>**Transactions:** Ensuring `Order` and `OrderItem` creation, and stock deduction happen atomically (`DbContext.Database.BeginTransactionAsync()`).</li>
  <li>**Concurrency Control:** For `StockQuantity` updates (`IsRowVersion()` / optimistic concurrency).</li>
</ul>
</div>
</div>

<!-- Placeholder for Mermaid Diagram -->
<div class="mt-4 p-3 bg-gray-700 rounded-lg text-center">
  <p class="text-yellow-300">🛍️ E-commerce Data Model</p>
```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : "is part of"
    PRODUCT ||--|{ REVIEW : "has"
    CUSTOMER ||--o{ REVIEW : "writes"
    CATEGORY ||--o{ PRODUCT : "groups"

    CUSTOMER { int CustomerId PK; string Name; string Email; }
    PRODUCT { int ProductId PK; string Name; decimal Price; int StockQuantity; int CategoryId FK; }
    CATEGORY { int CategoryId PK; string Name; }
    ORDER { int OrderId PK; int CustomerId FK; datetime OrderDate; decimal TotalAmount; }
    ORDER_ITEM { int OrderItemId PK; int OrderId FK; int ProductId FK; int Quantity; decimal UnitPrice; }
    REVIEW { int ReviewId PK; int ProductId FK; int CustomerId FK; int Rating; string Comment; }
```
</div>

---
layout: default
---

# Real-World Scenarios (2/3) 📝

## Blog System Implementation

We've used `Blog` and `Post` entities throughout. Let's expand on how EF Core facilitates a more complete blog system.

**Extended Entities:**
- `User` (AuthorId, Username, PasswordHash, Email) - for authors.
- `Comment` (CommentId, PostId, AuthorName, Content, CommentDate).
- `Tag` (TagId, Name) and `PostTag` (join entity for Many-to-Many between Post and Tag).

**EF Core Features in Action:**
- **Relationships:**
    - `User` to `Post` (One-to-Many: Author has many Posts).
    - `Post` to `Comment` (One-to-Many: Post has many Comments).
    - `Post` to `Tag` (Many-to-Many, possibly via explicit `PostTag` entity if payload needed on join).
- **Advanced Querying:**
    - Fetching posts with author details, comment counts, and tags.
    - Searching posts by keyword, tag, or author.
    - Paginating posts and comments.
    - `FromSqlRaw` for full-text search if needed (database-specific).
- **Data Seeding:** Initial admin user, default categories/tags.
- **Global Query Filters:** To show only "Published" posts by default.
- **Code-First Migrations:** To evolve the schema as new features are added (e.g., likes, categories).

**Example: Query for a post with its author, comments, and tags**
```csharp
var postId = 1;
var postDetails = await context.Posts
    .Where(p => p.PostId == postId && p.IsPublished) // Assuming IsPublished flag
    .Include(p => p.Author) // User entity linked to Post
    .Include(p => p.Comments)
        .ThenInclude(c => c.Author) // If comments also have authors
    .Include(p => p.PostTags) // Join entity
        .ThenInclude(pt => pt.Tag) // Actual Tag entity
    .Select(p => new PostDetailViewModel // Projecting to a DTO
    {
        Title = p.Title,
        Content = p.Content,
        AuthorName = p.Author.Username,
        PublishedDate = p.PublishedDate,
        Tags = p.PostTags.Select(pt => pt.Tag.Name).ToList(),
        Comments = p.Comments.Select(c => new CommentViewModel
        {
            CommenterName = c.Author.Username, // Or a display name property
            Text = c.Content,
            Date = c.CommentDate
        }).ToList()
    })
    .FirstOrDefaultAsync();
```

---
layout: default
---

# Real-World Scenarios (3/3) 🌐

## API Integration Patterns (e.g., ASP.NET Core Web API)

EF Core is a common choice for the data access layer in Web APIs.

**Key Patterns & Considerations:**

1.  **Repository Pattern (Optional but Common):**
    -   `public interface IBlogRepository { Task<Blog> GetByIdAsync(int id); /* ... */ }`
    -   `public class BlogRepository : IBlogRepository { private readonly MyDbContext _context; /* ... */ }`
    -   Controllers depend on `IBlogRepository`, not `MyDbContext` directly.
    -   **Pros:** Decouples controllers from EF Core specifics, easier unit testing of controllers (mock repository).
    -   **Cons:** Can add abstraction overhead if simple. EF Core's `DbSet` already acts like a generic repository.

2.  **Data Transfer Objects (DTOs):**
    -   API endpoints should typically receive and return DTOs, not EF Core entities directly.
    -   **Pros:**
        -   Decouples API contract from database schema.
        -   Prevents over-posting/under-posting issues.
        -   Avoids exposing internal entity structure or circular references.
        -   Allows shaping data specifically for the client.
    -   Use libraries like AutoMapper or manual projection (`Select()`) to map between entities and DTOs.
    ```csharp
    // Controller Action
    [HttpGet("{id}")]
    public async Task<ActionResult<BlogDto>> GetBlog(int id)
    {
        var blog = await _context.Blogs
            .Select(b => new BlogDto { Id = b.BlogId, Title = b.Title, Url = b.Url })
            .FirstOrDefaultAsync(b => b.Id == id);
        if (blog == null) return NotFound();
        return blog;
    }
    ```

3.  **DbContext Lifetime Management:**
    -   In ASP.NET Core, `DbContext` is typically scoped per HTTP request (`services.AddDbContext<...>`). This is crucial.

4.  **Async Operations:** Use `async` and `await` for all EF Core calls to keep API threads unblocked.

5.  **Error Handling & Validation:**
    -   Use middleware for global exception handling.
    -   Validate DTOs using Data Annotations or FluentValidation.
    -   Return appropriate HTTP status codes (e.g., `404 Not Found`, `400 Bad Request`).

6.  **Concurrency Control:** Implement optimistic concurrency for PUT/PATCH operations if needed.

<div class="mt-2 p-2 bg-purple-900 rounded-md text-sm">
  <p class="text-purple-200">💡 A well-structured API with EF Core often involves: Controllers ➡️ Services (optional business logic layer) ➡️ Repositories (optional data access abstraction) ➡️ DbContext ➡️ Database. DTOs are used at the API boundary.</p>
</div>

---
layout: default
---

# What's Next? (1/2) 🗺️

## EF Core Roadmap & Future

Entity Framework Core is continuously evolving, with new features and performance improvements in each release.

**General Direction & Roadmap:**
- Aligns with .NET releases (e.g., EF Core 9 with .NET 9, EF Core 10 with .NET 10).
- **Focus Areas Often Include:**
    - Performance enhancements (query speed, resource usage).
    - Support for new C# language features.
    - Improved SQL translation and database provider capabilities.
    - Addressing highly requested features from the community.
    - Enhancements to existing features (e.g., JSON columns, Cosmos DB provider).

- **Official Roadmap Information:**
    - EF Core Releases and Planning: [learn.microsoft.com/ef/core/what-is-new/](https://learn.microsoft.com/en-us/ef/core/what-is-new/)
    - .NET Core Roadmap (includes EF Core): [github.com/dotnet/core/blob/main/roadmap.md](https://github.com/dotnet/core/blob/main/roadmap.md)
    - As of late 2024, EF Core 9 is the latest stable, with EF Core 10 planned for Nov 2025.

**Advanced Topics to Explore:**
- **Compiled Models:** Improve startup time for contexts with large models.
- **Cosmos DB Provider:** Working with NoSQL databases using EF Core.
- **Temporal Tables:** Querying historical data (SQL Server specific, support in EF Core).
- **JSON Columns:** Mapping and querying JSON data stored in database columns (EF Core 7+).
- **Advanced Data Seeding Strategies:** Beyond `HasData`, for complex or large seed datasets.
- **Interceptors:** Low-level interception of database operations.
- **Custom Value Converters & Comparers:** For complex type mappings.
- **Building Custom Database Providers:** (Very advanced).
- **GraphQL Integration:** Using EF Core as a data source for GraphQL APIs.
- **Distributed Transactions:** (Complex, requires careful consideration).

---
layout: default
---

# What's Next? (2/2) 📚

## Resources, Learning Paths & Community

**Official Documentation:**
- **Microsoft Docs - EF Core:** [learn.microsoft.com/ef/core/](https://learn.microsoft.com/en-us/ef/core/)
    - Tutorials, API reference, conceptual overviews. This is your primary resource!
- **What's New in EF Core:** (Link from previous slide) For release-specific features.

**Learning Paths & Tutorials:**
- **Microsoft Learn - EF Core:** [learn.microsoft.com/training/browse/?products=entity-framework-core](https://learn.microsoft.com/en-us/training/browse/?products=entity-framework-core)
- **ASP.NET Core Data Tutorials (often use EF Core):** [dotnet.microsoft.com/learn/aspnet/data](https://dotnet.microsoft.com/en-us/learn/aspnet/data)
- **Community Blogs & Articles:** Many .NET MVPs and developers share EF Core insights. Search for specific topics.
    - (e.g., Blogs by Julie Lerman, Erik EJ, Arthur Vickers - though check for latest content)

**Books (check for latest editions):**
- "Entity Framework Core in Action" by Jon P. Smith
- "Programming Entity Framework Core" by Julie Lerman

**Community & Support:**
- **Stack Overflow - `entity-framework-core` tag:** [stackoverflow.com/questions/tagged/entity-framework-core](https://stackoverflow.com/questions/tagged/entity-framework-core)
- **GitHub - `dotnet/efcore`:** [github.com/dotnet/efcore](https://github.com/dotnet/efcore)
    - Report issues, suggest features, view source code.
- **.NET Virtual User Group:** [virtualusergroup.com](https://virtualusergroup.com/) (for events and talks)
- **Reddit - r/dotnet, r/csharp:** Communities for discussion.

**Tools:**
- **EF Core Power Tools:** Visual Studio extension for reverse engineering, migrations UI, model visualization. [marketplace.visualstudio.com](https://marketplace.visualstudio.com/items?itemName=ErikEJ.EFCorePowerTools) (Search for it)
- **LINQPad:** Excellent for interactively querying databases with LINQ, including EF Core contexts. [linqpad.net](https://www.linqpad.net/)

<div class="mt-2 p-2 bg-green-900 rounded-md text-sm">
  <p class="text-green-200">🚀 Continuous learning is key! The .NET and EF Core ecosystem is vibrant and always improving.</p>
</div>

---
layout: cover # Using cover layout for a distinct final slide feel
class: text-center
# You can also define a specific background for this slide if desired
# background: 'url_to_a_closing_image.jpg'
---

<div class="my-auto w-full">
  <h1 class="text-6xl font-bold text-green-400">Thank You! 🙏</h1>

  <img src="/ef-logo-placeholder.svg" alt="EF Logo" class="mx-auto my-8 h-32 opacity-75" />

  <h2 class="text-4xl mt-4">Q&A</h2>
  <p class="text-xl mt-2 opacity-80">Open to your questions and discussions.</p>

  <div class="mt-10 text-lg">
    <p><strong>Contact / Connect:</strong></p>
    <p class="opacity-75">[Your Name / Company]</p>
    <p class="opacity-75">[your.email@example.com]</p>
    <p class="opacity-75">[linkedin.com/in/yourprofile] | [github.com/yourusername] | [@YourTwitterHandle]</p>
  </div>

  <div class="mt-8">
    <p class="text-lg"><strong>Demo Repository & Resources:</strong></p>
    <p class="opacity-75">[Link to GitHub Repo: github.com/yourusername/ef-core-presentation-demo]</p>
    <p class="opacity-75">[Link to these Slides: your-slides-url.com]</p>
  </div>

  <p class="mt-12 text-2xl italic text-purple-300">
    "May your queries be fast and your migrations smooth! 🚀"
  </p>
</div>
