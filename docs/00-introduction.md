# Introduction

*Welcome to Blazor!*

![Blazor icon](https://devblogs.microsoft.com/aspnet/wp-content/uploads/sites/16/2019/04/BrandBlazor_nohalo_128x.png)

Blazor is client web UI framework based on .NET and C#. With Blazor you can build interactive without having to write JavaScript. Both client server code is written in C#, allowing you to share code and libraries. It's full stack web development with .NET!

Blazor apps can run your UI logic either on the server or client-side in the browser via WebAssembly. Blazor Server apps run on the server and handle all UI interactions over a real-time connection with the browser. Alterntively, Blazor WebAssembly apps run your client-side C# code directly in the browser, using a WebAssembly based .NET runtime. Blazor apps use existing open web standards without custom plugins or code transpilation.

Blazor apps are composed of reusable web UI components implemented using C#, HTML, and CSS. Blazor components are normal .NET classes with dynamic rendering logic authored using a combination of HTML and C# called Razor. Components can be compiled into class libraries and easily shared as NuGet packages. For cases where you still need to call into JavaScript, Blazor enables JavaScript interop so that you can call any existing JavaScript library or API.

In this workshop we will learn how to get setup with Blazor, create a Blazor app, understand the Blazor project structure and component model, and build a simple to do list app. You'll also learn how to create and use component libraries and how to interop with JavaScript.

Let's get started!
