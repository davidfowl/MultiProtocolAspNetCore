## Multi-protocol Server with ASP.NET Core and Kestrel

The following sample shows how you can host a TCP server and HTTP server in the same ASP.NET Core application. The TCP server runs on port 8007 and the HTTP server runs on ports 5000 and 5001.

Under the covers, it's the same server (Kestrel) running different protocols on different ports. The [ConnectionHandler](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.connections.connectionhandler?view=aspnetcore-2.1) is a new primitive introduced in ASP.NET Core 2.1 to support non-HTTP scenarios. ConnectionHandlers are actived by the dependency injection system in ASP.NET Core. This means you can access any registered service as part of the construction of your ConnectionHandler. The sample shows how you can log from your custom ConnectionHandler using the built in `ILogger<T>`. The ConnectionHandler also provides access to the connected client via a [ConnectionContext](https://docs.microsoft.com/en-us/dotnet/api/microsoft.aspnetcore.connections.connectioncontext?view=aspnetcore-2.1) which represents the raw data stream with[System.IO.Pipelines](https://blogs.msdn.microsoft.com/dotnet/2018/07/09/system-io-pipelines-high-performance-io-in-net/).

## What is this really?

This is part of a larger effort called Bedrock. You can read more about it [here](https://github.com/aspnet/KestrelHttpServer/issues/1980).