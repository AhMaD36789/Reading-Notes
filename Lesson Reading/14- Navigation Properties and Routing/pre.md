# ASP.NET MVC Routing

## Using the Default Route Table

When you create a new ASP.NET MVC application, the application is already configured to use ASP.NET Routing. ASP.NET Routing is setup in two places.

First, ASP.NET Routing is enabled in your application's Web configuration file (Web.config file). There are four sections in the configuration file that are relevant to routing: the system.web.httpModules section, the system.web.httpHandlers section, the system.webserver.modules section, and the system.webserver.handlers section. Be careful not to delete these sections because without these sections routing will no longer work.

Second, and more importantly, a route table is created in the application's Global.asax file. The Global.asax file is a special file that contains event handlers for ASP.NET application lifecycle events. The route table is created during the Application Start event.

## Routing in ASP.NET Core

Routing is responsible for matching incoming HTTP requests and dispatching those requests to the app's executable endpoints. Endpoints are the app's units of executable request-handling code. Endpoints are defined in the app and configured when the app starts. The endpoint matching process can extract values from the request's URL and provide those values for request processing. Using endpoint information from the app, routing is also able to generate URLs that map to endpoints.

Apps can configure routing using:

- Controllers
- Razor Pages
- SignalR
- gRPC Services
- Endpoint-enabled middleware such as Health Checks.
- Delegates and lambdas registered with routing.

## outing basics

All ASP.NET Core templates include routing in the generated code. Routing is registered in the middleware pipeline in Startup.Configure.

Routing uses a pair of middleware, registered by UseRouting and UseEndpoints:

UseRouting **app.UseRouting();** adds route matching to the middleware pipeline. This middleware looks at the set of endpoints defined in the app, and selects the best match based on the request.

UseEndpoints **app.UseEndpoints(endpoints =>{** adds endpoint execution to the middleware pipeline. It runs the delegate associated with the selected endpoint.

## Endpoint

The MapGet method is used to define an endpoint. An endpoint is something that can be:

Selected, by matching the URL and HTTP method.
Executed, by running the delegate.

Endpoints that can be matched and executed by the app are configured in UseEndpoints. For example, MapGet, MapPost, and similar methods connect request delegates to the routing system.

Additional methods can be used to connect ASP.NET Core framework features to the routing system:

- MapRazorPages for Razor Pages
- MapControllers for controllers
- MapHub< THub> for SignalR
- MapGrpcService< TService> for gRPC

## Endpoint metadata

an authorization check is performed. This demonstrates that endpoints can have extra data attached to them. This extra data is called endpoint metadata:

The metadata can be processed by routing-aware middleware.
The metadata can be of any .NET type.

## Routing concepts

The routing system builds on top of the middleware pipeline by adding the powerful endpoint concept. Endpoints represent units of the app's functionality that are distinct from each other in terms of routing, authorization, and any number of ASP.NET Core's systems.

## ASP.NET Core endpoint definition

An ASP.NET Core endpoint is:

- Executable: Has a RequestDelegate.
- Extensible: Has a Metadata collection.
- Selectable: Optionally, has routing information.
- Enumerable: The collection of endpoints can be listed by retrieving the EndpointDataSource from DI.

 It covers the basics of routing, routing concepts, route templates, routing with special characters, and more. Apps can configure routing using Controllers, Razor Pages, SignalR, gRPC Services, Endpoint-enabled middleware such as Health Checks, and Delegates and lambdas registered with routing. This article is a low-level detail of ASP.NET Core routing.
 