# Umbraco Installation Guide (macOS with M3 Chip)

# MyUmbraco Project

This project sets up an Umbraco 15+ website locally using the .NET SDK and prepares it for Docker deployment.

---

## ✅ Prerequisites

- [.NET SDK 8.0 or higher](https://dotnet.microsoft.com/en-us/download)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Azure Data Studio (optional)](https://learn.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio)

---

## 🧪 Local Setup (Without Docker)

### 1. Install Umbraco Templates

```bash
dotnet new install Umbraco.Templates

2. Create a New Umbraco Project

dotnet new umbraco -n MyUmbraco
cd MyUmbraco

3. Trust the HTTPS Certificate (macOS/Windows only)

dotnet dev-certs https --trust

4. Run the Project

dotnet run

Once it runs, check the console for a message like:

Now listening on: https://localhost:443xx

Open the URL in your browser to complete the Umbraco setup.

---

SQL Server Setup with Docker

You can spin up SQL Server in Docker like this:

docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=YourStrongPassword123" \
  -p 1433:1433 -d mcr.microsoft.com/mssql/server:2019-latest

You can manage the database using Azure Data Studio.
Use localhost, sa, and the password you set (YourStrongPassword123) when connecting.

---

Preparing for Docker

Next steps:
	•	Add Dockerfile
	•	Add docker-compose.yml
	•	Connect to the SQL Server container
	•	Configure the connection string in appsettings.json

---

Build & Run with Docker (to be added)

docker-compose up --build

---

Useful Links
	•	Official Umbraco Docs
	•	Getting Started with Umbraco 9+
	•	Azure Data Studio - DB management
	•	SQL Server Docker Hub

---

Creating a Simple Umbraco Website

This guide is a continuation of the local Umbraco installation steps. Now that your Umbraco CMS is running, let’s build a small website with a Home page and an About Me page.

---

Create the Page Template in Umbraco

1. Go to “Settings” → “Document Types”

Click “Document Type with Template” to create a new content page.

Set the following:
	•	Name: Page
	•	Alias: page
	•	Allow at root: ✅ (Toggle enabled)

Then click Save.

---

2. Add Content Fields to the Page

In the same Document Type, click the “Design” tab.
	1.	Add Group: Name it Content
	2.	Add Properties:
	•	Title
	•	Alias: title
	•	Editor: Textstring
	•	Body Text
	•	Alias: bodyText
	•	Editor: Rich Text Editor

Click Save again.

---

 Edit the Page Template
	1.	Go to Settings → Templates
	2.	Click on Page.cshtml
	3.	Replace the content with this minimal Razor view:

@inherits Umbraco.Cms.Web.Common.Views.UmbracoViewPage
@{
    Layout = null;
}

<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <title>@Model.Value("title")</title>
</head>
<body>
    <h1>@Model.Value("title")</h1>
    <div>
        @Model.Value("bodyText")
    </div>
</body>
</html>

Click Save.

---

Create Your Pages
	1.	Go to Content
	2.	Click “Create” → Choose Page

Create:
	•	Home Page
	•	Title: Welcome to My Cake Site!
	•	Body: 🍰 A place to explore delicious cake recipes and ideas.
	•	About Me Page
	•	Title: About Me
	•	Body: 👩‍🍳 I’m a cake enthusiast who loves baking sweet things on weekends.

Click Save and Publish for both.

---

Done!

You now have a basic Umbraco site with:
	•	A homepage about cake
	•	An about page



