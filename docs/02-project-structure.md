# Blazor project structure

Blazor Server apps are ASP.NET Core apps based on .NET Core. In this section we'll take a look at the various parts of the project for the Blazor Server app.

Take a look at the following important files and folders that make up the Blazor Server app:

1. *Program.cs*: This is the entry point for the app that sets up the ASP.NET Core host. This code is boilerplate and is common to all ASP.NET Core apps.
1. *Startup.cs*: The startup logic for your app. The `Startup` class defines two important methods: `Configure`, and `ConfigureServices`.

    - `Configure`: Configures the request handling pipeline for the app. 
      - The call to `MapBlazorHub` sets up the hub endpoint for the real-time connection with the browser. The connection is set up using SignalR, a framework for adding real-time web functionality to apps.
      - The call to `MapFallbackToPage("/_Host")` sets up the root page of the app and enables support for deep links.
    - `ConfigureServices`: Configures the services that should be available to the app through dependency injection. 
      - The Blazor Server services are added by calling `AddServerSideBlazor()`.
      - The `WeatherForecastService` used by the app to generate the weather data is also configured here.
1. *Pages/_Host.cshtml*: The root page of the app implemented a Razor Page. When any page of the app is initially request, this page is rendered and returned in the response.

    - *_framework/blazor.server.js*: Framework provide JavaScript that sets up the real-time SignalR connection with the server from the browser.
    - `@(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))`: Specifies where the root component of the app (`App`) should be rendered.

1. *App.razor*: The root component of the app that sets up client-side routing using the `Router` component.
1. *Pages/\*.razor*: The routable components, or pages, that make up the Blazor app. The route for each page is specified using the `@page` directive. The `Router` components intercepts browser navigations and renders the page that matches new address.
    
    - *Index.razor*: Implements the Home page.
    - *Counter.razor*: Implements the Counter page.
    - *FetchData.razor*: Implements the Fetch data page.
    - *Error.razor*: Page rendered when an unhandled exception occurs in the app.

1. *Shared/\*.razor*: Other UI components used by the app.

    - *MainLayout.razor*: The layout component that provides the layout for the app.
    - *NavMenu.razor*: Implements the left nav bar.

1. *_Imports.razor*: Includes common Razor directives, like `@using` statements, to be included in all *.razor* files.
1. *Data/\*.cs*: Implementation of the `WeatherForecastService` used to provide dummy weather data for the app.
1. *wwwroot*: The web root folder for the app containing all web addressable static assets.
1. *appsettings.json, appsettings.Development.json*: Configuration settings for the app.

When the Blazor Server app is run, the initial browser request is routed to the *Pages/_Host.cshtml* page. The page is rendered into the response along with the prerendered content of the `App` component. When the browser receives the response, it executes the *blazor.server.js* script, which sets up the real-time connection with the server. Once the connection is established the app is now interactive. Any UI events, such as tab navigations or button clicks, are sent by the framework to the server. Components handling these events render updated content and just the changes are sent back to the browser to be applied to the DOM.

  