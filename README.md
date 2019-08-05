# Introduction to Blazor
Blazor is a framework for building interactive client-side web UI with .NET:
  - Create rich interactive UIs using C# instead of JavaScript.
  - Share server-side and client-side app logic written in .NET.
  - Render the UI as HTML and CSS for wide browser support, including mobile browsers.
  
Using .NET for client-side web development offers the following advantages:
  - Write code in C# instead of JavaScript.
  - Leverage the existing .NET ecosystem of .NET libraries.
  - Share app logic across server and client.
  - Benefit from .NET's performance, reliability, and security.
  - Stay productive with Visual Studio on Windows, Linux, and macOS.
  - Build on a common set of languages, frameworks, and tools that are stable, feature-rich, and easy to use.

# Components
Blazor apps are based on components. A component in Blazor is an element of UI, such as a page, dialog, or data entry form.

Components are .NET classes built into .NET assemblies that:
  - Define flexible UI rendering logic.
  - Handle user events.
  - Can be nested and reused.
  - Can be shared and distributed as Razor class libraries or NuGet packages.

The component class is usually written in the form of a Razor markup page with a .razor file extension. Components in Blazor are formally referred to as Razor components. Razor is a syntax for combining HTML markup with C# code designed for developer productivity. Razor allows you to switch between HTML markup and C# in the same file with IntelliSense support. Razor Pages and MVC also use Razor. Unlike Razor Pages and MVC, which are built around a request/response model, components are used specifically for client-side UI logic and composition.

The following Razor markup demonstrates a component (Dialog.razor), which can be nested within another component:
  ```html
  <div>
     <h1>@Title</h1>
     @ChildContent
     <button @onclick="OnYes">Yes!</button>
   </div>

  @code {
     [Parameter]
     private string Title { get; set; }
     
     [Parameter]
     private RenderFragment ChildContent { get; set; }
     
     private void OnYes()
     {
       Console.WriteLine("Write to the console in C#! 'Yes' button was selected.");
     }
  }
  ```    
The dialog's body content (ChildContent) and title (Title) are provided by the component that uses this component in its UI. OnYes is a C# method triggered by the button's onclick event.

Blazor uses natural HTML tags for UI composition. HTML elements specify components, and a tag's attributes pass values to a component's properties.

In the following example, the Index component uses the Dialog component. ChildContent and Title are set by the attributes and content of the <Dialog> element.

Index.razor:
  ```html
  @page "/"
  <h1>Hello, world!</h1>
  
  Welcome to your new app.
  
  <Dialog Title="Blazor">
    Do you want to <i>learn more</i> about Blazor?
  </Dialog>
  ```
  
The dialog is rendered when the parent (Index.razor) is accessed in a browser:
<img src="https://docs.microsoft.com/en-us/aspnet/core/blazor/index/_static/dialog.png?view=aspnetcore-3.0" alt="Dialog component rendered in the browser" data-linktype="relative-path" class="x-hidden-focus">

When this component is used in the app, IntelliSense in Visual Studio and Visual Studio Code speeds development with syntax and parameter completion.

Components render into an in-memory representation of the browser's Document Object Model (DOM) called a render tree, which is used to update the UI in a flexible and efficient way.
# Blazor client-side
Blazor decouples component rendering logic from how UI updates are applied. Blazor server-side provides support for hosting Razor components on the server in an ASP.NET Core app. UI updates are handled over a SignalR connection.

The runtime handles sending UI events from the browser to the server and applies UI updates sent by the server back to the browser after running the components.

The connection used by Blazor server-side to communicate with the browser is also used to handle JavaScript interop calls.
<img src="https://docs.microsoft.com/en-us/aspnet/core/blazor/index/_static/blazor-server-side.png?view=aspnetcore-3.0" alt="Blazor server-side runs .NET code on the server and interacts with the Document Object Model on the client over a SignalR connection" data-linktype="relative-path" class="x-hidden-focus">

# Blazor server-side

# JavaScript interop

# Code sharing and .NET Standard
