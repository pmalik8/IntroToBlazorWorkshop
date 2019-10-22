# Get started with Blazor

## Setup your machine

Blazor is fast and easy to get started with. We've already done all the work you'll need to get started on these machines. But to set up a machine with Blazor yourself, here's what you need to do:

1. Go to https://blazor.net
1. Click on the "Get Started" link

    ![Blazor Get Started](https://user-images.githubusercontent.com/1874516/67251093-b7ba0e00-f422-11e9-9b76-35f823dbad05.png)

1. Follow the instructions for the platform of your choice - Windows, macOS, or Linux.

Blazor requires the .NET Core 3.0 (or newer) SDK. Visual Studio on Windows will install this for you. On macOS or Linux, you can use Visual Studio Code with the C# extension.

## Create a Blazor app

To create a Blazor app from Visual Studio:

1. Create a new project
1. Select **Blazor App**. Select **Next**.
1. Specify "BlazorApp1" in the **Project name** field. Select **Create**.
1. Select the **Blazor Server App** template. Select **Create**.

## Build and run the Blazor app

To build and run the Blazor
1. Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the app.

## Explore the Blazor app

The Blazor app consists of three different tabs: Home, Counter, and Fetch data.

The Home tab just contains some static content.

![Home](https://user-images.githubusercontent.com/1874516/67256798-c19d3a80-f43d-11e9-8bda-8a474a8576c4.png)

The Counter tab has a button and displays the number of times the button has been pressed. Notice that the page doesn't refresh when you increment the count. This is client-side UI in action!

![Counter](https://user-images.githubusercontent.com/1874516/67256817-d11c8380-f43d-11e9-9a81-dd4e31e2b7e2.png)

The Fetch data tab displays a table of weather forecast data.

![Fetch data](https://user-images.githubusercontent.com/1874516/67256836-eb566180-f43d-11e9-9876-42ded95ddc24.png)

## What is a Blazor Server app?

Blazor Server apps host Blazor components on the server and handle UI interactions over a real-time SignalR connection. As the user interacts with the app, the UI events are sent to the server over the connection to be handled by the various components that make up the app. When a component handles a UI event, it’s rendered based on its updated state. Blazor compares the newly rendered output with what was rendered previously and send the changes back to the browser and applies them to the DOM.

![Blazor Server](https://devblogs.microsoft.com/aspnet/wp-content/uploads/sites/16/2019/02/aspnet-core-razor-components.png)

To see the mechanics of your Blazor Server app in action:

1. Press <kbd>F12</kbd> in the browser to see the browser dev tools.
1. Select the **Network** tab.
1. Press <kbd>F5</kbd> to refresh the app in the browser.

![Blazor Server network](https://user-images.githubusercontent.com/1874516/67256961-82231e00-f43e-11e9-919f-f96512a4878c.png)

The request to *_blazor* sets up a websocket connection with the server which is used to drive the UI of the app.

Since Blazor Server apps run on .NET Core on the server, they enjoy all the benefits of running on .NET Core including great runtime performance and tooling. Blazor Server apps can leverage the full ecosystem of .NET Standard libraries without any browser imposed limitations.

Alternatively, Blazor apps can run directly in the browser via WebAssembly. Blazor WebAssembly apps host components in the browser using a WebAssembly-based .NET runtime. The components handle UI events and execute their rendering logic directly in the browser. Blazor WebAssembly apps use only open web standards to run .NET code client-side, without the need for any browser plugins or code transpilation. Just like with Blazor Server apps, the Blazor framework handles comparing the newly rendered output with what was rendered previous and updates the DOM accordingly, but with Blazor WebAssembly the UI rendering is handled client-side.

![Blazor WebAssembly](https://devblogs.microsoft.com/aspnet/wp-content/uploads/sites/16/2019/02/blazor.png)

Blazor WebAssembly is still in preview and isn’t yet ready for production use yet. If you’re looking for a production ready solution, then Blazor Server is what we’d recommend.

For more information on the different [Blazor hosting models](https://docs.microsoft.com/aspnet/core/blazor/hosting-models) including Blazor WebAssembly see the Blazor docs.
