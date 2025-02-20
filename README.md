# DevExpress UI for Blazor
This project demonstrates the Preview (CTP) version of [DevExpress UI Components for Blazor](https://www.devexpress.com/blazor/).

The DevExpress UI components featured in this demo are available for free download and can be used in your next Blazor app.* 

> \* Like any software preview, the DevExpress UI for Blazor is not without fault. You should not use these products in production environments or in mission-critical applications.

# Live Demo
 
Check out this [demo in live](https://demos.devexpress.com/blazor/).

# Version compatibility

The following table describes the version compatibility of .NET Core 3.0 Preview and the DevExpress.Blazor NuGet package.

| .NET Core 3.0 version | DevExpress.Blazor.nuget version |
| ------------- | ------------- |
| .NET Core 3.0 Preview **5** | 0.0.**8** |
| .NET Core 3.0 Preview **5** | 0.0.**7** |
| .NET Core 3.0 Preview **5** | 0.0.**6** |
| .NET Core 3.0 Preview **5** | 0.0.**5** |
| .NET Core 3.0 Preview **4** | 0.0.**4** |
| .NET Core 3.0 Preview **3** | 0.0.**3** |

# Set up your environment

1. Install Visual Studio 2019 (latest update).
2. Ensure that you have .NET Core 3 (preview 4) installed.
3. If you work with the release version of Visual Studio 2019, make sure to enable the option "Use previews of the .NET Core SDK".

Depending on the Visual Studio build version this check box can be found here:

![Create New ASP.NET Core Web Application Project"](media/VS2019Release-EnablePreviewSDK.png)

or here:

![Create New ASP.NET Core Web Application Project"](media/VS2019Release-EnablePreviewSDK_2.png)

# How to run this demo on your machine

1. Download the "**demo**" directory from this repository.
2. Open **demo/BlazorDemo.ServerSide/BlazorDemo.ServerSide.sln** in Visual Studio 2019.
3. Start the application.

See also: 

[Official Microsoft Blazor site](https://dotnet.microsoft.com/apps/aspnet/web-apps/client)

# How to create a new project

Follow the steps below to try our UI for Blazor in your own application. 

1. Create a new solution using the "Blazor (server-side)" or "Blazor" template in Visual Studio 2019.

  In the "Create a new project" dialog select "ASP.NET Core Web Application (where the language is C#).
  
  ![Create New ASP.NET Core Web Application Project"](media/VisualStudio2019CreateNewProject_AspNetCoreWebApp.png)

  In the next step ensure that an "ASP.NET Core 3.\*" framework is selected, and select the "Blazor (server-side)" project template.
  
  ![Create New ASP.NET Core Web Application Project"](media/VisualStudio2019CreateNewProject_Blazor.png)

2. Register the DevExpress Early Access feed in Visual Studio's NuGet Package Manager.

  Open the "Package Manager Settings".

  ![Open the "Package Manager Settings"](media/NuGetPackageManagerSettings.png)

  Add new NuGet source:
  
  ```https://nuget.devexpress.com/early-access/api```

  ![Add new NuGet source](media/DevExpressEarlyAccessNuGetSource.png)

3. Install the "DevExpress.Blazor" NuGet package.

   Navigate to:
   
   ![Add new NuGet source](media/NuGetPackageManagerOpenManagerMenu.png)
   
   Select the "Early Access" NuGet package source you have just created in the "Package source" combo box.

   Make sure that the "Include prerelease" option is selected.
   
   Install the "DevExpress.Blazor" NuGet package.
   
   ![Add new NuGet source](media/VS2019Release-AddNuGetPackage.png)

4. Navigate to the GitHub repository and download all files from the "client-runtime" directory. Put the downloaded files into the "wwwroot" directory of your project. Include these files to your start page.
5. Register our tag namespace and helper in _Imports.razor file: 

  ```
  @using DevExpress.Blazor
  ```

6. Your application is ready to use DevExpress Blazor.

# Troubleshooting

## 1. DxDataGrid in Blazor

If you use Blazor (client-side) with DxDataGrid, you may see the following exception in a browser:

![Troubleshooting - No Generic Method 'Take' On Type System.Linq.Queryable](media/Troubleshooting-NoGenericMethodTakeOnTypeSystemLinqQueryable.png)

> "System.InvalidOperationException: No generic method 'Take' on type 'System.Linq.Queryable' is compatible with the supplied type arguments and arguments."

The solution is to follow the [official Blazor documentation](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/blazor/configure-linker?view=aspnetcore-3.0).

So, you can either [Disable linking](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/blazor/configure-linker?view=aspnetcore-3.0#disable-linking-with-a-msbuild-property) or [Control linking](https://docs.microsoft.com/en-us/aspnet/core/host-and-deploy/blazor/configure-linker?view=aspnetcore-3.0#control-linking-with-a-configuration-file).

In case you decide to control linking: the following types types must be added in the **Linker.xml** file:

```
    <type fullname="System.Linq.Expressions*" />
    <type fullname="System.Linq.Queryable*" />
    <type fullname="System.Linq.Enumerable*" />
    <type fullname="System.Linq.EnumerableRewriter*" />
```    

So, the **Linker.xml** file should look as follows:

```
<?xml version="1.0" encoding="UTF-8" ?>
...
<linker>
  <assembly fullname="mscorlib">
...
    <type fullname="System.Threading.WasmRuntime" />
  </assembly>
  <assembly fullname="System.Core">
...
    <type fullname="System.Linq.Expressions*" />
    <type fullname="System.Linq.Queryable*" />
    <type fullname="System.Linq.Enumerable*" />
    <type fullname="System.Linq.EnumerableRewriter*" />
  </assembly>
...
  <assembly fullname="[PUT YOUR ASSEMBLY NAME HERE]" />
</linker>
```

## 2. The "Early Access" NuGet Feed is empty in Visual Studio

If you don't see packages in the ```https://nuget.devexpress.com/early-access/api``` NuGet feed, make sure that the "Include prerelease" option is selected:
![Include prerelease](media/VisualStudio2019NuGetIncludePrerelease.png)

# Included Demo Modules

* Data Grid
  * Column Types
  * Templates
  * Large Datasets
* Pivot Grid
  * Data Binding Basics
  * Templates
  * Large Datasets
* Tabs
* Form Layout
* Form Validation
* Data Editors
  * Combo Box – Business Object List
  * Combo Box – Cascading Lists
  * Date Edit
  * Spin Edit
  * Text Box
* Pager

# NuGet Package Change Log

Check out thе NuGet package's [version history](changelog.md).
