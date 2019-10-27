# Dependency injection

Services configured in the `Startup.ConfigureServices` are made available to components through dependency injection. To inject a service into a component use the `@inject` directive. The `@inject` directive defines a property on the component that will be populated with the specified service through dependency injection. The `FetchData` component uses the configured `WeatherForecastService` to get weather data, which it then renders in a table.

Open *Pages/FetchData.razor* and examine its contents.

- `@page "/fetchdata"`: Defines the route for the `FetchData` component.
- `@using BlazorApp1.Data`: Adds a using statement for the namespace of the `WeatherForecastService` and related types.
- `@inject WeatherForecastService ForecastService`: Injects the `WeatherForecastService` into the `FetchData` component using the `ForecastService` property.
- `@if (forecasts == null) { ... }`: This `@if` statement renders a place holder if the weather forecast data isn't yet available. Since the forecast data is retrieved asynchronously, the component might render before the forecast data is available. 
- `@foreach (var forecast in forecasts) { ... }`: Loops over each weather forecast and renders a corresponding row in the table.
- `OnInitializedAsync()`: A component lifecycle method that is called when a component is initialized. The `FetchData` component retrieves the weather forecast data when it is initialized. The component is automatically rendered after the lifecycle event completes *and* after the returned `Task` completes.
