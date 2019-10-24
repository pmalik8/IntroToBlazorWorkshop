# Pages, routing, and layouts

## Routing to pages

Each page in our Blazor app is simply a component with a route. The *Pages* folder has no special meaning in Blazor apps, but we put all of our pages in this folder by convention. To add a route to a component use the `@page` directive.

The `Router` component handles identifying all routable components within the app assembly and any additional assemblies specified. When the browser navigates, the `Router` finds the component with a route that matches the new address and renders it. The `Router` component is typically setup in the root component of the app.

To add a page to the app:

1. Right-click on the *Pages* folder and select Add > New item.
1. Select Razor Component from the Add New Item dialog. Name the file *Todo.razor*.

    ![Add Razor Component](https://user-images.githubusercontent.com/1874516/67260815-57db5b80-f452-11e9-8c96-49bf4d114086.png)

1. Replace the markup in *Todo.razor* with some basic markup for a new page.

    ```
    @page "/todo"

    <h1>Todo</h1>

    @code {

    }
    ```

1. Browse to `/todo` to see the new page.

    ![New Todo page](https://user-images.githubusercontent.com/1874516/67260905-dcc67500-f452-11e9-86a7-802c59d2e4b5.png)

## Layout

Notice that the new Todo page is rendered using the default app layout. The `Router` component can render pages using a default layout. The layout for our app is defined by the `MainLayout` component, which is specified as the default layout for the app in *App.razor*. Layouts in Blazor are components that inherit from `LayoutComponentBase`, which defines a `Body` property that the layout can use to specify where body content should be rendered. To have a component inherit from a base class, use the `@inherits` directive.

Add the Todo page to the nav menu in the app's layout:

1. Open *Shared/NavMenu.razor*
1. Add the following list item below the existing list items

    ```
    <li class="nav-item px-3">
        <NavLink class="nav-link" href="todo">
            <span class="oi oi-list-rich" aria-hidden="true"></span> Todo
        </NavLink>
    </li>
    ```

1. Switch back to the browser and refresh the page. Verify that the Todo page now shows up in the nav menu.

    ![Todo in nav menu](https://user-images.githubusercontent.com/1874516/67261191-77738380-f454-11e9-85e0-ac7d59a170bc.png)
