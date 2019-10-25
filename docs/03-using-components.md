# Using components

Blazor apps are made up of *components*. A component is reusable piece of UI. Components are typically authored in Razor component files (.razor), which define dynamic rendering logic using a combination of HTML and C#. At build time, Razor components are compiled into .NET classes that capture the authored rendering logic. The name of the generated component class matches the name of the *.razor* file.

## The Counter component

Open *Pages/Counter.razor* and look at its contents.

- `@page "/counter"`: Defines the route for the `Counter` component.
- *HTML markup*: The component renders standard HTML markup. The HTML markup is captured in the generated component class so that Blazor can track any changes as components render updates.
- `@currentCount`: Renders the value of the `currentCount` field. Razor syntax uses the `@` character to transition between HTML and C# code. 
- `@onclick="IncrementCount"`: Specifies an `onclick` handler using the `IncrementCount` method.
- `@code {...}`: A code block containing members that will get added to the generated class.

Normally click events in a browser would be handled using JavaScript, but our `Counter` component uses C# instead!

Each time the **Click me** button is selected:

* The `onclick` event is fired.
* The `IncrementCount` method is called.
* The `currentCount` is incremented.
* The component is rendered again.

The runtime compares the new content to the previous content and only applies the changed content to the DOM.

## Using the Counter component

To use a component in markup, add an element that matches the name of the component class.

1. Add a `Counter` component to the home page of the app by adding a `<Counter />` tag to *Pages/Index.razor*:

    ```
    @page "/"

    <h1>Hello, world!</h1>

    Welcome to your new app.

    <Counter />
    ```

1. Refresh the app in the browser. You should now see a Counter on the Home page as well as on the Counter page.

    ![Counter on Home page](https://user-images.githubusercontent.com/1874516/67259642-d4b70700-f44b-11e9-8f07-ce0a1e01ed9c.png)

## Component parameters

You can pass data into components using parameters. Component parameters are defined using public properties attributed with `[Parameter]`. To specify arguments for component parameters in markup, use attributes.

Add an `IncrementAmount` parameter to the `Counter` component and configure the `Counter` on the Home page to increment by 10 instead of 1:

1. In *Pages/Counter.razor* add an `IncrementAmount` public property in the `@code` block. Apply the `[Parameter]` attribute to the property and set its default value to 1. Update the `IncrementCount` method to increment by `IncrementAmount`.

    ```
    @code {
        private int currentCount = 0;

        [Parameter]
        public int IncrementAmount { get; set; } = 1;

        private void IncrementCount()
        {
            currentCount += IncrementAmount;
        }
    }
    ```

1. Update the `Counter` component on the Home page to increment by 10 by adding the `IncrementAmount` attribute. Save the file.

    ```
    <Counter IncrementAmount="10" />
    ```

1. Switch back to the browser and refresh the page. Verify that the counter on the Home page now increments by 10, while the counter on the Counter tab still increments by 1.

    ![Increment amount](https://user-images.githubusercontent.com/1874516/67259988-b9e59200-f44d-11e9-9fa1-37036bde790a.png)
