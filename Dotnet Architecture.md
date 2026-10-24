Your understanding is largely correct, but there are a few important clarifications, especially around where ASP.NET and desktop runtimes sit. Let me give you the full picture first, then diagram it.

**Corrections and clarifications:**

1. **SDK ⊃ Runtime** — correct. The SDK bundles the runtime plus build tools (`dotnet build`, `dotnet publish`, Roslyn compilers, MSBuild, NuGet, etc.). A machine running a deployed app only needs the runtime.
    
2. **Runtime = BCL + CLR** — correct, but the naming has evolved. In .NET 5+, the base runtime package is called the **.NET Runtime** (`Microsoft.NETCore.App`). This is exactly what you described: BCL + CLR (GC, JIT, thread/memory management, exception handling, interop).
    
3. **App frameworks are NOT just "on top of" the runtime** — this is where your model needs a correction. Microsoft ships **three distinct runtime packages**, each a superset of the previous:
    
    |Runtime package|Contains|
    |---|---|
    |`Microsoft.NETCore.App`|CLR + BCL only|
    |`Microsoft.AspNetCore.App`|Above + Kestrel, middleware, MVC, SignalR, etc.|
    |`Microsoft.WindowsDesktop.App`|Above (NETCore.App) + WPF + WinForms assemblies|
    
    So **ASP.NET Core Runtime** and **Windows Desktop Runtime** are actual separate installable runtimes shipped by Microsoft — not just libraries floating on top. EF Core, Blazor, MAUI, etc., are NuGet-distributed libraries/workloads, not separate runtime packages.
    
4. **Where does EF Core live?** — pure NuGet library, no separate runtime. It ships as packages (`Microsoft.EntityFrameworkCore.*`) and runs entirely on the base .NET Runtime.
    
5. **MAUI and Blazor** — workloads installed via `dotnet workload install`. On mobile/native targets, MAUI uses Mono-based runtime (AOT compiled); on web, Blazor WebAssembly ships its own WASM build of the .NET runtime into the browser.**Key takeaways from the corrected model:**

![[Pasted image 20260521102439.png]]
    

**ASP.NET Core Runtime** is a proper runtime superset — it's an installable package (`dotnet-aspnetcore-runtime-8.x`) that includes the base .NET Runtime _plus_ the core ASP.NET assemblies (Kestrel, DI, routing, auth middleware, etc.). When you deploy a web app, the target machine needs _this_ runtime, not just the base one.

**Windows Desktop Runtime** is similarly a superset — it wraps the base .NET Runtime and adds WPF and WinForms assemblies. It only exists on Windows. WPF and WinForms are not workload-installed; they're baked into this runtime package.

**The workload layer (EF Core, Blazor, MAUI, etc.)** is NuGet-distributed, not runtime-packaged. They run _on_ the base .NET Runtime, with no separate runtime installer needed. MAUI is the exception on mobile — it uses a Mono-based AOT runtime under the hood.

**Blazor WASM** is architecturally unique: it ships a trimmed build of the .NET Runtime as a `.wasm` binary into the browser. The CLR literally runs inside the browser's WASM sandbox.

**One clarification on your SDK model:** The SDK doesn't just "contain" the runtime — it also ships Roslyn (C#/F# compiler), MSBuild engine, the `dotnet` CLI host, and the workload manifest system. The runtime is independently installable without the SDK (production servers only need the runtime).