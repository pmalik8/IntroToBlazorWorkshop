# Component libraries

Components can be built into reusable component libraries and shared as NuGet packages. Component libraries can also provide static assets, like CSS and JavaScript files, to the app. Libraries of sophisticated components (grids, charts, tab views, etc.) are available for Blazor from popular component vendors and from the open source community.

To create a component library:

1. Add a new project to the solution.
1. Select **Razor Class Library**. Select **Next**.
1. Specify "RazorClassLibrary1" in the **Project name** field. Select **Create**.
1. Select the **Razor Class Library** template. Select **Create**.
1. The generated Razor Class Library project contains a single component, *Component1.razor*, with some static markup.
1. Add a reference to RazorClassLibrary1 from BlazorApp1.
1. Add `Component1` from RazorClassLibrary1 to the Home page of the app by specifying the full name of the component type: `RazorClassLibrary1.Component1`

    ```
    <RazorClassLibrary1.Component1 />
    ```

1. To add `Component1` without specifying its namespace, add a `@using` statement in *_Imports.razor* for the `RazorClassLibrary1` namespace.

    ```
    @using RazorClassLibrary1
    ```

    ```
    <Component1 />
    ```

1. Add a link to the *wwwroot/styles.css* file from RazorClassLibrary1 to BlazorApp1 in *Pages/_Host.cshtml*. Static assets in Razor Class Libraries can be referenced using the path `_content/[library name]/[path under wwwroot]`.

    ```
    <link href="_content/RazorClassLibrary1/styles.css" rel="stylesheet"/>
    ```

1. Run the app (<kbd>Ctrl</kbd>+<kbd>F5</kbd>) to see `Component1` rendered to the Home page using the custom stylesheet.

    ![Component1](https://user-images.githubusercontent.com/1874516/67262748-b3114c00-f45a-11e9-88a2-09de1ab3103b.png)

