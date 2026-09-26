**English** · [Español](https://github.com/antonicr1986/antonicr1986/blob/main/README.md)

### Hi, I'm Antonio Company 👋

.NET developer moving into DevOps and CI/CD. I come from building and maintaining business applications (C#, SQL Server), and I'm currently building my profile around Docker and pipeline automation.

## 🛠️ DevOps & Infrastructure
- Git / GitHub — version control
- GitHub Actions — CI/CD on Linux and Windows runners
- Azure DevOps — Repos, Boards, Pipelines and Wiki
- Docker and container registries (GHCR) — applied in personal projects
- Automated artifact publishing and versioned Releases
- Pipeline-gated deployments (Vercel) — shipping depends on the checks passing, not on the push
- Pipeline security — secret scanning (gitleaks), custom rules and documented exceptions
- Kubernetes, Jenkins — actively learning

## 💻 Development
- C# / VB.NET · .NET Framework / .NET 8
- Entity Framework / EF Core / Windows Forms
- SQL Server
- HTML, CSS, JavaScript / TypeScript · Node.js, React, Tailwind CSS
- Java/Kotlin (Android Studio)

## 🚀 Featured projects

- 🔗 [financetracker-web](https://github.com/antonicr1986/financetracker-web) — Web interface for FinanceTracker, built with Next.js 16, TypeScript and Tailwind CSS: sign-up and sign-in, transaction entry, filtering by type, category and text, a dashboard with charts built without external libraries, a light/dark theme and a fully bilingual interface (Spanish/English). One click gets you in with the demo account, no sign-up needed. Deployment is triggered by **the pipeline itself**, and only once secret scanning and the build are green. **[Open the live app](https://financetracker-web-tau.vercel.app/login)**

[![CI financetracker-web](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-web/ci.yml?branch=main&style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-web/actions)
[![Demo](https://img.shields.io/badge/demo-online-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://financetracker-web-tau.vercel.app/login)

- 🔗 [financetracker-android](https://github.com/antonicr1986/financetracker-android) — Android client for FinanceTracker in Kotlin: the **second consumer of the same API**, which is what turns it into a contract — same endpoints, same error codes and same business rules from a different platform. Sign-up and sign-in, a month selector, totals, creating, editing and deleting transactions and the same look as the web app: a shared corporate palette, light/dark theme and Spanish/English from the top bar, switching without flashing. One tap gets you in with the demo account. The pipeline scans for secrets, runs the unit tests —and **fails if none ran**— and leaves a **downloadable APK** on every run.

[![CI financetracker-android](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-android/ci.yml?branch=main&style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-android/actions)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)

- 🔗 [FinanceTracker](https://github.com/antonicr1986/FinanceTracker) — REST API in .NET 8 with a layered architecture, JWT authentication and automated tests. Dockerised (API + SQL Server) and backed by a pipeline that builds, runs the tests and **publishes the image to GitHub Container Registry**, tagged by commit so any specific version can be deployed or rolled back. In production it runs on **Azure App Service against Azure SQL**, deployed from the pipeline itself. **[Browse the API in Swagger](https://financetracker-api-cpctbta0gddddge5.belgiumcentral-01.azurewebsites.net/swagger)** — it's on a free tier with serverless SQL, so the first request after a while idle takes a few seconds.

[![CI FinanceTracker](https://img.shields.io/github/actions/workflow/status/antonicr1986/FinanceTracker/ci.yml?style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/FinanceTracker/actions)

- 🔗 [BlocDeNotas](https://github.com/antonicr1986/BlocDeNotas) — Desktop application in Windows Forms (.NET Framework 4.7.2). Pipeline on a Windows runner using MSBuild and NuGet, with **automatic Release publishing** when a version tag is pushed: it packages the executable, generates the changelog and stamps the version number into the binary itself.

[![CI BlocDeNotas](https://img.shields.io/github/actions/workflow/status/antonicr1986/BlocDeNotas/ci.yml?style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/actions)
[![Release](https://img.shields.io/github/v/release/antonicr1986/BlocDeNotas?style=for-the-badge&logo=github&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/releases/latest)

> Three different delivery models: one publishes a container image and deploys the API to Azure App Service; another publishes a versioned executable ready to download; the third publishes a website, and only if the preceding checks pass. The pipeline adapts to whatever has to be delivered.

## 🔒 Security across my repositories

Every public repository of mine runs secret scanning with **gitleaks**, using a custom configuration that extends the default rules: the defaults catch keys from well-known providers, but not a password inside a connection string — which is the shape a leak takes in a .NET project.

Auditing my own history with those rules surfaced real credentials from 2023 and 2024. They are revoked, and each one is recorded in a `.gitleaksignore` along with what it was and what was done about it — because a pipeline that stays permanently red stops being read.

Scanning in CI detects, but does not prevent: by the time the workflow fails, the commit is already published. That's why the same configuration also runs in a local `pre-commit` hook, which blocks the commit before it exists. Detecting and preventing are different layers, and both are needed.

The most recent project, a Telegram bot, never had its token in the code at all: it reads from an environment variable from the very first commit.

---

- 🔭 At SOLPORT: .NET developer, with some work on Android and internal web apps.
- 🌱 Currently learning: Docker, Kubernetes and Jenkins, applying them in personal projects.
- 🤔 Interested in going deeper into: application architecture, AI tooling, testing and best practices.
- 📫 Contact: [LinkedIn](https://www.linkedin.com/in/antoniocompany/ "Go to my profile").
- ⚡ Outside of code: I follow tech news and enjoy sport.
