# Umbraco Installation Guide (macOS with M3 Chip)

This guide walks you through setting up Umbraco on your macOS machine using .NET without Docker. Ideal for initial development and local testing.

---

## 🛠 Prerequisites

- macOS with M3 chip
- [Install .NET SDK (v8 or newer)](https://dotnet.microsoft.com/en-us/download)
  - Make sure to download the **ARM64 version** for M1/M2/M3 Macs.
- [Visual Studio Code](https://code.visualstudio.com/)
- Terminal access

---

## 🚀 Step-by-Step Installation

### 1. Verify .NET Installation

Open terminal and run:

```bash
dotnet --info

You should see info about the installed .NET SDK.

⸻

2. Install Umbraco Templates

dotnet new install Umbraco.Templates

This adds the latest Umbraco templates to your .NET SDK.

⸻

3. Create a New Project

dotnet new umbraco -n MyProject
cd MyProject

	•	Replace MyProject with your desired folder name.
	•	A .csproj file should be generated inside.

⸻

4. Trust the Development HTTPS Certificate

To fix the HTTPS error on macOS:

dotnet dev-certs https --trust



⸻

5. Run Umbraco

dotnet run

After a few seconds, the terminal will show:

Now listening on: https://localhost:443xx

Copy this URL and open it in your browser. You’ll see the Install Umbraco screen 🎉

⸻

🗄 Database Options

Since you are not using Docker or SQL Server yet, Umbraco will use SQLite by default.

This is great for:
	•	Local dev
	•	Fast setup
	•	No config needed

You can always switch to SQL Server later (see the Docker setup below).

⸻

🐳 Planning to Use Docker + SQL Server?

If you want to set up Docker for Umbraco + Microsoft SQL Server later, follow the next steps in a separate guide (README-docker.md). This setup is perfect when:
	•	You need SQL Server features
	•	Preparing for production
	•	Collaborating with others

⸻

✅ Useful Links
	•	Official Umbraco Docs
	•	Getting Started with Umbraco 9+
	•	Azure Data Studio (DB management)



