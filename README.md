# Local Offline Bootstrap Setup Guide in Visual Studio 2022 

---

## ✅ Prerequisites

- ✅ Visual Studio 2022 installed
- ✅ .NET 8.0 or .NET 9.0 SDK installed

---

## 🛠️ Setup Instructions

### 1. Right click in your project go to add and find Client-Side Library
![Step 1](Screenshot%202025-06-11%20155005.png)

---

### 2. Create a new project  
![Step 2](Screenshot%202025-06-11%20153512.png)

- Click on **"Create a new project"**

---


### 3. Select "ASP.NET Core Empty"  
![Step 3](Screenshot%202025-06-11%20153529.png)

- Search for **"ASP.NET Core Empty"**
- Select it and click **Next**


---

### 4. Select .NET 8.0 or 9.0  
![Step 4](Screenshot%202025-06-11%20153547.png)

- Choose either **.NET 8.0** or **.NET 9.0** as the framework
- Click **Create**

---

### 5. Go to `Program.cs`  
![Step 5](Screenshot%202025-06-11%20155628.png)

- Open the `Program.cs` file from the **Solution Explorer**

---

### 6. Replace with this code  

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllersWithViews();

var app = builder.Build();

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection();
app.UseStaticFiles();


app.UseRouting();
app.UseAuthorization();


app.MapControllerRoute(
    name:"default",
    pattern: "{controller=Home}/{action=Index}/{id?}"
);


app.Run();


```


# Code Overview and Functionality

```csharp
var builder = WebApplication.CreateBuilder(args);
```
Create a builder instance for configuring the web application.

<br>
<br>

```csharp
builder.Services.AddControllersWithViews();
```
Register MVC services to enable controller and view support.

<br>
<br>

```csharp
var app = builder.Build();
```
Build the application using the configured services.

<br>
<br>

```csharp
if (!app.Environment.IsDevelopment())
```
Check if the app is not running in development mode.

<br>
<br>

```csharp
app.UseExceptionHandler("/Error");
```
Set up a global error handler for production.

<br>
<br>

```csharp
app.UseHsts();
```
Enable HTTP Strict Transport Security (HSTS) to enforce HTTPS.

<br>
<br>

```csharp
app.UseHttpsRedirection();
```
Redirect all HTTP requests to HTTPS.


<br>
<br>

```csharp
app.UseStaticFiles();
```
Enable wwwRoot serving static files (e.g. CSS, JS, images).

<br>
<br>

```csharp
app.UseRouting();
```
Enable request routing.


<br>
<br>

```csharp
app.UseAuthorization();
```
Enable authorization middleware (for protected routes).

<br>
<br>


```csharp
app.MapControllerRoute(...)
```
Define the default route pattern for controller actions.

<br>
<br>

```csharp
app.Run();
```
Start the web application.





