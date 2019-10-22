# Event handling and data binding

Next we'll build a simple todo list and explore Blazor's event handling and data binding features.

## Event handling

Event handlers for DOM elements can be specified using the standard HTML event handling attributes (`onclick`, `oninput`, etc.), but prefixed with an `@` character to specify a C# method. The `@` character won't show up in the rendered markup, but is used as a Razor compiler directive. The value of the attribute can be a method group name (`@onclick="OnClick"`), or an inline delegate defined using lambda syntax (`@onclick="() => currentCount++"`). Event handlers can be sync or async and can take event specific arguments. When a component handles an event it is automatically rendered after the event handler has executed.

## Data binding

Data binding sets up a two-way binding between a DOM element value (or a component value) and a specified value. When the value of the DOM element is updated, the specified value is update. Also, when the specified value changes, its new value is rendered into the DOM element. To bind a DOM element value to a specific value, use the `@bind` attribute.

## Create a todo list

Let's add a todo list to the *Pages/Todo.razor* page:

1. Add a *TodoItem.cs* file to the root of the project to hold a class that represents a todo item. Use the following C# code for the `TodoItem` class:

    ```
    public class TodoItem
    {
        public string Title { get; set; }
        public bool IsDone { get; set; }
    }
    ```

1. Return to the `Todo` component (*Pages/Todo.razor*):

   * Add a field for the todo items in an `@code` block. The `Todo` component uses this field to maintain the state of the todo list.
   * Add unordered list markup and a `foreach` loop to render each todo item as a list item (`<li>`).

    ```
    @page "/todo"

    <h1>Todo</h1>

    <ul>
        @foreach (var todo in todos)
        {
            <li>@todo.Title</li>
        }
    </ul>

    @code {
        private IList<TodoItem> todos = new List<TodoItem>();
    }
    ```

1. The app requires UI elements for adding todo items to the list. Add a text input (`<input>`) and a button (`<button>`) below the unordered list (`<ul>...</ul>`):

    ```
    <input placeholder="Something todo" />
    <button>Add todo</button>
    ```

1. Refresh the app in the browser. When the **Add todo** button is selected, nothing happens because an event handler isn't wired up to the button.

1. Add an `AddTodo` method to the `Todo` component and register it for button selections using the `@onclick` attribute. The `AddTodo` C# method is called when the button is selected:

    ```
    <input placeholder="Something todo" />
    <button @onclick="AddTodo">Add todo</button>

    @code {
        private IList<TodoItem> todos = new List<TodoItem>();

        private void AddTodo()
        {
            // Todo: Add the todo
        }
    }
    ```

1. To get the title of the new todo item, add a `newTodo` string field at the top of the `@code` block and bind it to the value of the text input using the `bind` attribute in the `<input>` element:

    ```
    <input placeholder="Something todo" @bind="newTodo" />
    <button @onclick="AddTodo">Add todo</button>

    @code {
        private IList<TodoItem> todos = new List<TodoItem>();
        private string newTodo;
        
        private void AddTodo()
        {
            // Todo: Add the todo
        }
    }
    ```

1. Update the `AddTodo` method to add the `TodoItem` with the specified title to the list. Clear the value of the text input by setting `newTodo` to an empty string:

    ```
    private void AddTodo()
    {
        if (!string.IsNullOrWhiteSpace(newTodo))
        {
            todos.Add(new TodoItem { Title = newTodo });
            newTodo = string.Empty;
        }
    }
    ```

1. Refresh the app in the browser. Add some todo items to the todo list to test the new code.

    ![Simple todo list](https://user-images.githubusercontent.com/1874516/67261585-3aa88c00-f456-11e9-8a5d-d2dde0734e9f.png)

1. The title text for each todo item can be made editable, and a check box can help the user keep track of completed items. Add a check box input for each todo item and bind its value to the `IsDone` property. Change `@todo.Title` to an `<input>` element bound to `@todo.Title`:

    ```
    <ul>
        @foreach (var todo in todos)
        {
            <li>
                <input type="checkbox" @bind="todo.IsDone" />
                <input @bind="todo.Title" />
            </li>
        }
    </ul>
    ```

1. To verify that these values are bound, update the `<h1>` header to show a count of the number of todo items that aren't complete (`IsDone` is `false`).

   ```
   <h1>Todo (@todos.Count(todo => !todo.IsDone))</h1>
   ```

1. The completed `Todo` component (*Pages/Todo.razor*):

    ```
    @page "/todo"

    <h1>Todo (@todos.Count(todo => !todo.IsDone))</h1>

    <ul>
        @foreach (var todo in todos)
        {
            <li>
                <input type="checkbox" @bind="todo.IsDone" />
                <input @bind="todo.Title" />
            </li>
        }
    </ul>

    <input placeholder="Something todo" @bind="newTodo" />
    <button @onclick="AddTodo">Add todo</button>

    @code {
        private IList<TodoItem> todos = new List<TodoItem>();
        private string newTodo;

        private void AddTodo()
        {
            if (!string.IsNullOrWhiteSpace(newTodo))
            {
                todos.Add(new TodoItem { Title = newTodo });
                newTodo = string.Empty;
            }
        }
    }
    ```

1. Refresh the app in the browser. Add todo items to test the new code.

    ![Finished todo list](https://user-images.githubusercontent.com/1874516/67261547-fcab6800-f455-11e9-9665-ba38a3ad4922.png)
