# Blazor project structure

  - Startup
    - `AddServerSideBlazor()`
    - `MapBlazorHub()`
  - *_Host.cshtml*
    - *blazor.server.js*
    - `@(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))`
  - *.razor* files
  - Root component: *App.razor*, sets up client-side routing
  - *Pages* folder contains routable components 
  - *Shared* folder contains other UI components
  - *Data* folder contains a simple service for getting some dummy weather forecast data
  - *_Imports.razor*