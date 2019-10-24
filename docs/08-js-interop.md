# JavaScript interop

Blazor apps can call into existing JavaScript libraries and browser APIs. Library authors can create convenient .NET APIs for calling into JavaScript and then share these APIs as NuGet packages. Consumers of these libraries can then call into JavaScript code as if it were C#! To invoke a JavaScript function from Blazor use the `IJSRuntime` service.

Use the JavaScript interop code in RazorClassLibrary1 to call the JavaScript `prompt` function:

1. In *Pages/_Host.cshtml* add a script reference to *wwwroot/exampleJsInterop.js* from RazorClassLibrary1.

    ```
    <script src="_content/RazorClassLibrary1/exampleJsInterop.js"></script>
    ```

1. Inject the `IJSRuntime` service into the `Index` component.

    ```
    @inject IJSRuntime JS
    ```

1. In *Pages/Index.razor* add a button to display a JavaScript prompt and display the returned value from the prompt. Since JavaScript interop calls are async, the click handler must also be async.

    ```
    <button @onclick="OnClick">Show prompt</button>
    <p>@message</p>

    @code {
        string message;

        async Task OnClick()
        {
            message = await ExampleJsInterop.Prompt(JS, "What is your favorite color?");
        }
    }
    ```

1. Refresh the app in the browser and try out the **Show prompt** button.

    ![JavaScript prompt](https://user-images.githubusercontent.com/1874516/67264251-6bd98a00-f45f-11e9-949b-ce9860216482.png)

