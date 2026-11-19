<details open>
<summary><b>🇬🇧 English</b> <sub>· 🇪🇸 Versión en español más abajo</sub></summary>

### Hi, I'm Antonio Company 👋

**DevOps · DevSecOps | Azure · CI/CD · Kubernetes · Terraform | .NET**

.NET developer with DevOps and DevSecOps experience. At work I own the CI/CD of several applications (Azure DevOps Pipelines and GitHub Actions), migrated repositories from TFS 2018 to Git and organise the work in Azure Boards. In my own projects I apply Docker, Terraform on Azure and AWS, Kubernetes and security inside the pipeline (SAST, SCA, secrets, containers, IaC and DAST): I want security to speed delivery up, not slow it down. I come from .NET development, so I understand the code I deploy, not just the pipeline.

[![Interactive CV](https://img.shields.io/badge/Interactive%20CV-antonio--cv-10B981?style=for-the-badge&logo=vercel&logoColor=white)](https://antonio-cv-five.vercel.app/?lang=en) [![LinkedIn](https://img.shields.io/badge/LinkedIn-antoniocompany-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/antoniocompany/?locale=en-US)

## ⚙️ CI/CD & DevOps
- Git / GitHub — version control; migrated repos from TFS 2018 to Git
- GitHub Actions — CI/CD on Linux and Windows runners
- Azure DevOps — Repos (mirrored from GitHub), Boards, Pipelines and Wiki
- Jenkins — declarative Jenkinsfile, Linux agent on Docker Compose, JUnit
- Versioned Releases and automated artifacts
- Pipeline-gated deployments: shipped only when every check passes
- 🔒 DevSecOps — gitleaks, CodeQL, Trivy, OWASP ZAP, cosign + Syft and least privilege with OIDC ([details](#-security-across-my-repositories-devsecops))

## ☁️ Cloud & Infrastructure
- Docker and GHCR — images tagged by commit
- Terraform — Azure and AWS, remote state and a `plan` on every PR
- Azure — App Service, Azure SQL and Key Vault with managed identity
- AWS — ECS Express Mode + RDS, brought up on demand (multicloud)
- Kubernetes and Helm — my own chart, validated in CI
- Observability — Application Insights (OpenTelemetry) and Azure Monitor alerts

## 💻 Development
- C# / VB.NET · .NET Framework / .NET 8
- Entity Framework / EF Core / Windows Forms
- SQL Server
- HTML, CSS, JavaScript / TypeScript · Node.js, React, Tailwind CSS
- Java/Kotlin (Android Studio)
- AI-assisted development — Claude Code every day, guided by my own kit of rules and skills ([ai-project-kit](#other-projects)): tests first, and the AI never commits

## 🚀 Featured projects

### FinanceTracker — one API, three clients

<p align="center"><img src="assets/financetracker-demo.gif" alt="FinanceTracker on web, Windows and Android, in light and dark theme" width="900"></p>


**⚡ Try it in one minute**

| 🌐 Web | 📱 Android | 🪟 Windows | 🔌 API |
|:---:|:---:|:---:|:---:|
| [Open the demo](https://financetracker-web-tau.vercel.app/login) | [Download APK](https://github.com/antonicr1986/financetracker-android/releases/latest/download/financetracker.apk) | [Microsoft Store](https://apps.microsoft.com/detail/9NT27R8DZ2DQ?hl=en-us) | [Swagger](https://financetracker-api-cpctbta0gddddge5.belgiumcentral-01.azurewebsites.net/swagger) |
| In the browser, nothing to install | Android 7.0 or later | Windows 10/11, one click | Documented endpoints |

Use the **demo account** button or `demo@financetracker.app` / `Demo1234!`. The database is serverless and pauses when idle: all three apps wake it as soon as the sign-in screen opens, so the wait happens while you read it.

A REST API and three clients on different platforms: the same endpoints, error codes and business rules reached from three languages, which is what turns the API into a contract. Shared look, light/dark theme, Spanish/English and one demo account.

```mermaid
flowchart LR
    subgraph Clients
        WEB[Web · Next.js]
        AND[Android · Kotlin]
        DESK[Desktop · WPF]
    end

    API[REST API · .NET 8]

    subgraph AZURE[Azure · production]
        AZ[App Service]
        DB[(Azure SQL)]
    end

    subgraph AWSC[AWS · on demand]
        ECS[ECS Express Mode]
        RDS[(RDS SQL Server)]
    end

    WEB --> API
    AND --> API
    DESK --> API
    AZ --> DB
    ECS --> RDS

    API -. CI .-> GHCR[GHCR image · scanned with Trivy · signed with cosign]
    GHCR -. CD .-> AZ
    GHCR -. Terraform .-> ECS
    WEB -. CI/CD .-> VER[Vercel]
    AND -. CI .-> APK[Downloadable APK]
    DESK -. CI/CD .-> REL[GitHub Release · .exe/.zip + Microsoft Store]
    GHCR -. Helm .-> K8S[Kubernetes · Helm chart validated in CI]
```

- 🔗 [FinanceTracker](https://github.com/antonicr1986/FinanceTracker) — REST API in .NET 8 (JWT, sign-in with Google, MFA) used by all three clients.
  - **CI/CD**: Docker image per commit in GHCR, signed with cosign + SBOM, deployed to Azure App Service without rebuilding
  - **Security**: deploys only if tests, secrets, Trivy and OWASP ZAP pass; secrets in Key Vault via managed identity
  - **Sign-in**: optional TOTP MFA (encrypted secrets, trusted devices for 30 days), sign out of all devices (JWT revocation), rate limiting, account lockout and breached-password check (HIBP)
  - **IaC and multicloud**: Terraform on Azure and AWS (ECS + RDS on demand), `plan` on every PR via OIDC
  - **Kubernetes and observability**: Helm chart validated in CI · Application Insights with alerts

  **[Browse the API in Swagger](https://financetracker-api-cpctbta0gddddge5.belgiumcentral-01.azurewebsites.net/swagger)**

[![CI FinanceTracker](https://img.shields.io/github/actions/workflow/status/antonicr1986/FinanceTracker/ci.yml?style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/FinanceTracker/actions)

- 🔗 [financetracker-web](https://github.com/antonicr1986/financetracker-web) — Web client in Next.js 16, TypeScript and Tailwind CSS.
  - Sign-in with Google, filters, dashboard with charts, light/dark and Spanish/English
  - Deployed to Vercel by the pipeline itself, only with the secret scan and build green
  - OWASP ZAP scans the live site after every deployment

  **[Open the live app](https://financetracker-web-tau.vercel.app/login)**

[![CI financetracker-web](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-web/ci.yml?branch=main&style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-web/actions)
[![Demo](https://img.shields.io/badge/demo-online-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://financetracker-web-tau.vercel.app/login)

- 🔗 [financetracker-android](https://github.com/antonicr1986/financetracker-android) — Android client in Kotlin.
  - Sign-in with Google (Credential Manager), transactions, budgets and the same look as the web app
  - CI with secret scanning, MobSF and unit tests that fail if none ran
  - Downloadable APK on every run and a signed Release on every tag

  **[Download the latest APK](https://github.com/antonicr1986/financetracker-android/releases/latest/download/financetracker.apk)** · Android 7.0+

[![CI financetracker-android](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-android/ci.yml?branch=main&style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-android/actions)
[![APK](https://img.shields.io/badge/Download_APK-Android_7.0%2B-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://github.com/antonicr1986/financetracker-android/releases/latest/download/financetracker.apk)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)

- 🔗 [financetracker-desktop](https://github.com/antonicr1986/financetracker-desktop) — Windows client in WPF and .NET 8 with MVVM.
  - Sign-in with Google, session encrypted with DPAPI and 150+ tests with no UI or network
  - Windows runner: self-contained Release (`.zip` / `.exe`) on every tag
  - MSIX package published on the Microsoft Store

  **[Available on the Microsoft Store](https://apps.microsoft.com/detail/9NT27R8DZ2DQ?hl=en-us)**

[![CI financetracker-desktop](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-desktop/ci.yml?branch=main&style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-desktop/actions)
[![Release](https://img.shields.io/github/v/release/antonicr1986/financetracker-desktop?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/antonicr1986/financetracker-desktop/releases/latest)
[![Microsoft Store](https://img.shields.io/badge/Microsoft_Store-Available-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://apps.microsoft.com/detail/9NT27R8DZ2DQ?hl=en-us)

### Other projects

- 🧰 **ai-project-kit** *(private repo · [download it from my CV](https://antonio-cv-five.vercel.app/?lang=en))* — Kit to develop any project safely with AI assistants.
  - Rules for the AI (`CLAUDE.md`, `AGENTS.md`) and skills `/backlog` → `/story` → `/pair` → `/code-review`: tests first, the AI never commits
  - CI templates for GitHub Actions and Azure DevOps with Gitleaks and least privilege
  - PowerShell installer, automatic releases, 8 ADRs and 113 Pester tests

![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=gnometerminal&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude_Code-D97757?style=for-the-badge&logo=claude&logoColor=white)

- 📄 **antonio-cv** *(private repo · [open it](https://antonio-cv-five.vercel.app/?lang=en))* — My interactive CV in Next.js 16 and React 19: bilingual, light/dark and printable to PDF.
  - AI chat (OpenAI) hardened like a public API: rate limits and same-origin requests only
  - Deploys to Vercel only with gitleaks, lint, `npm audit`, tests and build green; then smoke test and OWASP ZAP

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![OpenAI](https://img.shields.io/badge/AI_chat-412991?style=for-the-badge&logo=openai&logoColor=white)

- 🔧 **Jenkins CI for .NET** *(private repos)* — Jenkins on Docker Compose, set up the way a company would.
  - Controller with 0 executors and a Linux agent with the .NET 10 SDK
  - Declarative Jenkinsfile: build, JUnit tests and artifacts; if tests fail, nothing is published
  - Its own CI with Gitleaks, Hadolint and Trivy: 20 high vulnerabilities found and fixed

![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)
![Docker](https://img.shields.io/badge/Docker_Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white)

- 🔗 [BlocDeNotas](https://github.com/antonicr1986/BlocDeNotas) — Windows Forms app (.NET Framework 4.7.2): Windows runner with MSBuild and NuGet, and a Release with changelog and versioned binary on every tag.

[![CI BlocDeNotas](https://img.shields.io/github/actions/workflow/status/antonicr1986/BlocDeNotas/ci.yml?style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/actions)
[![Release](https://img.shields.io/github/v/release/antonicr1986/BlocDeNotas?style=for-the-badge&logo=github&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/releases/latest)

> **Four delivery models, each where it fits:** container image (API), gated website (web), versioned executable (desktop) and APK (Android).

## 🔒 Security across my repositories (DevSecOps)

[![Security KPIs of my repositories](https://raw.githubusercontent.com/antonicr1986/security-dashboard/main/data/summary-card.en.svg)](https://github.com/antonicr1986/security-dashboard/blob/main/REPORT.md)

<sub>Live figures from my [security-dashboard](https://github.com/antonicr1986/security-dashboard): a weekly GitHub Actions job reads the alerts and workflows of every repo and applies a quality gate. Click the card for the full report.</sub>

> **Detecting and preventing are different layers, and both are needed.**

| Layer | Tool | When it acts |
|---|---|---|
| 🛑 Prevent secret leaks | **gitleaks** in a `pre-commit` hook | Before the commit exists |
| 🔍 Detect secret leaks | **gitleaks** in CI · GitHub *push protection* | On every push, in all my public repos |
| 🧠 Static code analysis (SAST) | **CodeQL** | On every push and pull request |
| 📦 Vulnerable dependencies | `dotnet list package --vulnerable` · `npm audit` · dependency graph + *dependency review* | On every pipeline and pull request |
| 🐳 Docker image | **Trivy** | Before pushing to GHCR |
| ✍️ Image signing and SBOM | **cosign** (keyless) · **Syft** (SPDX) | When pushing to GHCR, verifiable with `cosign verify` |
| 📱 Android APK | **MobSF** | On every push and pull request (blocks on new high findings) |
| 🏗️ Infrastructure as code | **Trivy** (`trivy config`) | Before deploying |
| 🌐 Running application (DAST) | **OWASP ZAP**: active and authenticated in a throwaway environment · passive in production | Before deploying the API (blocks) and after every deployment |
| 🗝️ Production secrets | **Azure Key Vault** · managed identity · **AWS SSM** (write-only) | Always: the API reads them at startup |
| 🔑 User sign-in | **TOTP MFA** · session revocation · rate limiting · lockout · **Have I Been Pwned** | On every sign-in in my FinanceTracker apps |
| 👤 Cloud access | **AWS IAM Identity Center** (SSO) · MFA | When running Terraform: 1-hour credentials, no long-lived access keys |
| 🔐 Least privilege | read-only `GITHUB_TOKEN` · **OIDC** | In every workflow |
| 🌿 Main branch protection | GitHub **rulesets** | On the main branch of my public repos |
| 📬 Vulnerability reporting | `SECURITY.md` · *private vulnerability reporting* | In my public repos |
| 🔄 Staying up to date | **Dependabot** | One pull request a month |

<details>
<summary><b>How I apply it: secrets, dependencies and from pipeline to production</b></summary>

### 🔑 Secrets
- **Custom gitleaks rules** to catch passwords inside .NET connection strings, which the defaults miss
- **Audited history**: real 2023-2024 credentials found, revoked and documented in `.gitleaksignore`
- **CI detects, the `pre-commit` hook prevents**: a leak is blocked before the commit exists

### 📦 Dependencies
- **One tool per ecosystem**, transitive dependencies included (.NET, npm and Gradle via dependency review)
- **Trivy on the image** also covers the base OS libraries: with a fixable high/critical, it is not published
- **Dependabot without noise**: one monthly PR; major versions left out on purpose

### 🚦 From pipeline to production
- **Every check must pass** (tests, secrets, image and IaC) or nothing is deployed
- **Blocking DAST**: ZAP attacks a throwaway API before deploying; accepted risks documented in `.zap/rules.tsv`
- **Least privilege**: read-only `GITHUB_TOKEN`, OIDC to Azure, managed identity and SSO + MFA on AWS
- **Rotatable secrets**: Terraform *write-only* values that never reach the state
- **Signed image** with cosign keyless + SBOM, verifiable with `cosign verify`
- **Production monitored**: security headers and Azure Monitor alerts on 5xx and 401/403 spikes

</details>

---

- 🔭 At work: .NET developer and owner of the CI/CD of several applications (Azure DevOps and GitHub Actions); I also manage their SQL Server database and Azure services, built a generative AI chatbot with RAG, and do some Android and web work.
- 🎓 Latest course: [Claude Code in Action](https://verify.skilljar.com/c/fmhryo5fni98) (Anthropic, Aug 2026).
- 🌱 Currently learning: GitOps with Argo CD and Jenkins Configuration as Code, applying them in personal projects.
- 🤔 Interested in going deeper into: application architecture, AI tooling, testing and best practices.
- 📫 Contact: [LinkedIn](https://www.linkedin.com/in/antoniocompany/?locale=en-US "Go to my profile") · [Interactive CV](https://antonio-cv-five.vercel.app/?lang=en "See my interactive CV").
- ⚡ Outside of code: I follow tech news and enjoy sport.

</details>

<details>
<summary><b>🇪🇸 Español</b></summary>

### Hola, soy Antonio Company 👋

**DevOps · DevSecOps | Azure · CI/CD · Kubernetes · Terraform | .NET**

Desarrollador .NET con experiencia en DevOps y DevSecOps. En el trabajo llevo el CI/CD de varias aplicaciones (Azure DevOps Pipelines y GitHub Actions), he migrado repositorios de TFS 2018 a Git y organizo el trabajo en Azure Boards. En mis proyectos aplico Docker, Terraform en Azure y AWS, Kubernetes y seguridad dentro del pipeline (SAST, SCA, secretos, contenedores, IaC y DAST): busco que la seguridad acelere la entrega, no que la frene. Vengo del desarrollo .NET, así que entiendo el código que despliego y no solo el pipeline.

[![CV web](https://img.shields.io/badge/CV_web-antonio--cv-10B981?style=for-the-badge&logo=vercel&logoColor=white)](https://antonio-cv-five.vercel.app/?lang=es) [![LinkedIn](https://img.shields.io/badge/LinkedIn-antoniocompany-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/antoniocompany/?locale=es_ES)

## ⚙️ CI/CD y DevOps
- Git / GitHub — control de versiones; migración de repos de TFS 2018 a Git
- GitHub Actions — CI/CD sobre runners Linux y Windows
- Azure DevOps — Repos (espejo desde GitHub), Boards, Pipelines y Wiki
- Jenkins — Jenkinsfile declarativo, agente Linux en Docker Compose, JUnit
- Releases versionadas y artefactos automáticos
- Despliegues controlados por el pipeline: solo si pasan todos los controles
- 🔒 DevSecOps — gitleaks, CodeQL, Trivy, OWASP ZAP, cosign + Syft y mínimo privilegio con OIDC ([ver detalle](#-seguridad-en-mis-repositorios-devsecops))

## ☁️ Cloud e Infraestructura
- Docker y GHCR — imágenes etiquetadas por commit
- Terraform — Azure y AWS, estado remoto y `plan` en cada PR
- Azure — App Service, Azure SQL y Key Vault con identidad administrada
- AWS — ECS Express Mode + RDS, levantado bajo demanda (multicloud)
- Kubernetes y Helm — chart propio validado en CI
- Observabilidad — Application Insights (OpenTelemetry) y alertas en Azure Monitor

## 💻 Desarrollo
- C# / VB.NET · .NET Framework / .NET 8
- Entity Framework / EF Core / Windows Forms
- SQL Server
- HTML, CSS, JavaScript / TypeScript · Node.js, React, Tailwind CSS
- Java/Kotlin (desarrollo con Android Studio)
- Desarrollo asistido por IA — Claude Code a diario, guiado por mi propio kit de reglas y skills ([ai-project-kit](#otros-proyectos)): tests primero, y la IA nunca hace commit

## 🚀 Proyectos destacados

### FinanceTracker — una API y tres clientes

<p align="center"><img src="assets/financetracker-demo.gif" alt="FinanceTracker en web, Windows y Android, en tema claro y oscuro" width="900"></p>


**⚡ Pruébalo en 1 minuto**

| 🌐 Web | 📱 Android | 🪟 Windows | 🔌 API |
|:---:|:---:|:---:|:---:|
| [Abrir la demo](https://financetracker-web-tau.vercel.app/login) | [Descargar APK](https://github.com/antonicr1986/financetracker-android/releases/latest/download/financetracker.apk) | [Microsoft Store](https://apps.microsoft.com/detail/9NT27R8DZ2DQ?hl=es-es) | [Swagger](https://financetracker-api-cpctbta0gddddge5.belgiumcentral-01.azurewebsites.net/swagger) |
| En el navegador, sin instalar nada | Android 7.0 o superior | Windows 10/11, un clic | Endpoints documentados |

Entra con el botón de la **cuenta de demostración** o con `demo@financetracker.app` / `Demo1234!`. La base de datos es serverless y se pausa cuando no se usa: las tres apps la despiertan en cuanto se abre el login, así que la espera ocurre mientras lo lees.

Una API REST y tres clientes en plataformas distintas: los mismos endpoints, códigos de error y reglas de negocio desde tres lenguajes, que es lo que convierte la API en un contrato. Estética común, tema claro/oscuro, español/inglés y una cuenta de demostración.

```mermaid
flowchart LR
    subgraph Clientes
        WEB[Web · Next.js]
        AND[Android · Kotlin]
        DESK[Escritorio · WPF]
    end

    API[API REST · .NET 8]

    subgraph AZURE[Azure · producción]
        AZ[App Service]
        DB[(Azure SQL)]
    end

    subgraph AWSC[AWS · bajo demanda]
        ECS[ECS Express Mode]
        RDS[(RDS SQL Server)]
    end

    WEB --> API
    AND --> API
    DESK --> API
    AZ --> DB
    ECS --> RDS

    API -. CI .-> GHCR[Imagen en GHCR · escaneada con Trivy · firmada con cosign]
    GHCR -. CD .-> AZ
    GHCR -. Terraform .-> ECS
    WEB -. CI/CD .-> VER[Vercel]
    AND -. CI .-> APK[APK descargable]
    DESK -. CI/CD .-> REL[GitHub Release · .exe/.zip + Microsoft Store]
    GHCR -. Helm .-> K8S[Kubernetes · chart de Helm validado en CI]
```

- 🔗 [FinanceTracker](https://github.com/antonicr1986/FinanceTracker) — API REST en .NET 8 (JWT, inicio de sesión con Google, MFA) que consumen los tres clientes.
  - **CI/CD**: imagen Docker por commit en GHCR, firmada con cosign + SBOM, desplegada en Azure App Service sin recompilar
  - **Seguridad**: solo despliega si pasan tests, secretos, Trivy y OWASP ZAP; secretos en Key Vault con identidad administrada
  - **Inicio de sesión**: MFA opcional con TOTP (secretos cifrados, dispositivos de confianza 30 días), cierre de sesión en todos los dispositivos (revocación de JWT), límite de intentos, bloqueo de cuenta y contraseñas filtradas rechazadas (HIBP)
  - **IaC y multicloud**: Terraform en Azure y AWS (ECS + RDS bajo demanda), `plan` en cada PR con OIDC
  - **Kubernetes y observabilidad**: chart de Helm validado en CI · Application Insights con alertas

  **[Ver la API en Swagger](https://financetracker-api-cpctbta0gddddge5.belgiumcentral-01.azurewebsites.net/swagger)**

[![CI FinanceTracker](https://img.shields.io/github/actions/workflow/status/antonicr1986/FinanceTracker/ci.yml?style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/FinanceTracker/actions)

- 🔗 [financetracker-web](https://github.com/antonicr1986/financetracker-web) — Cliente web en Next.js 16, TypeScript y Tailwind CSS.
  - Inicio de sesión con Google, filtros, dashboard con gráficos, tema claro/oscuro y español/inglés
  - Lo despliega en Vercel el propio pipeline, solo con el escaneo de secretos y el build en verde
  - OWASP ZAP analiza la web publicada tras cada despliegue

  **[Abrir la aplicación](https://financetracker-web-tau.vercel.app/login)**

[![CI financetracker-web](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-web/ci.yml?branch=main&style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-web/actions)
[![Demo](https://img.shields.io/badge/demo-online-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://financetracker-web-tau.vercel.app/login)

- 🔗 [financetracker-android](https://github.com/antonicr1986/financetracker-android) — Cliente Android en Kotlin.
  - Inicio de sesión con Google (Credential Manager), movimientos, presupuestos y la misma estética que la web
  - CI con escaneo de secretos, MobSF y pruebas unitarias que fallan si no se ejecuta ninguna
  - APK descargable en cada ejecución y Release firmada en cada versión

  **[Descargar el último APK](https://github.com/antonicr1986/financetracker-android/releases/latest/download/financetracker.apk)** · Android 7.0+

[![CI financetracker-android](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-android/ci.yml?branch=main&style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-android/actions)
[![APK](https://img.shields.io/badge/Descargar_APK-Android_7.0%2B-3DDC84?style=for-the-badge&logo=android&logoColor=white)](https://github.com/antonicr1986/financetracker-android/releases/latest/download/financetracker.apk)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)

- 🔗 [financetracker-desktop](https://github.com/antonicr1986/financetracker-desktop) — Cliente de Windows en WPF y .NET 8 con MVVM.
  - Inicio de sesión con Google, sesión cifrada con DPAPI y más de 150 pruebas sin ventanas ni red
  - Runner de Windows: Release autocontenida (`.zip` / `.exe`) en cada versión
  - Paquete MSIX publicado en la Microsoft Store

  **[Disponible en Microsoft Store](https://apps.microsoft.com/detail/9NT27R8DZ2DQ?hl=es-es)**

[![CI financetracker-desktop](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-desktop/ci.yml?branch=main&style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-desktop/actions)
[![Release](https://img.shields.io/github/v/release/antonicr1986/financetracker-desktop?style=for-the-badge&logo=windows&logoColor=white)](https://github.com/antonicr1986/financetracker-desktop/releases/latest)
[![Microsoft Store](https://img.shields.io/badge/Microsoft_Store-Disponible-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://apps.microsoft.com/detail/9NT27R8DZ2DQ?hl=es-es)

### Otros proyectos

- 🧰 **ai-project-kit** *(repo privado · [descárgalo desde mi CV](https://antonio-cv-five.vercel.app/?lang=es))* — Kit para desarrollar cualquier proyecto con asistentes de IA de forma segura.
  - Reglas para la IA (`CLAUDE.md`, `AGENTS.md`) y skills `/backlog` → `/story` → `/pair` → `/code-review`: tests primero y la IA nunca hace commit
  - Plantillas de CI para GitHub Actions y Azure DevOps con Gitleaks y permisos mínimos
  - Instalador en PowerShell, releases automáticas, 8 ADR y 113 pruebas con Pester

![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=gnometerminal&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude_Code-D97757?style=for-the-badge&logo=claude&logoColor=white)

- 📄 **antonio-cv** *(repo privado · [ábrelo](https://antonio-cv-five.vercel.app/?lang=es))* — Mi CV interactivo en Next.js 16 y React 19: bilingüe, claro/oscuro e imprimible en PDF.
  - Chat con IA (OpenAI) protegido como una API pública: límites de uso y solo peticiones del mismo origen
  - Solo despliega en Vercel con gitleaks, lint, `npm audit`, tests y build en verde; después, smoke test y OWASP ZAP

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![OpenAI](https://img.shields.io/badge/Chat_con_IA-412991?style=for-the-badge&logo=openai&logoColor=white)

- 🔧 **Jenkins CI para .NET** *(repos privados)* — Jenkins en Docker Compose, montado como en una empresa.
  - Controller con 0 ejecutores y un agente Linux con el SDK de .NET 10
  - Jenkinsfile declarativo: build, tests JUnit y artefactos; si fallan tests, no se publica nada
  - CI propio con Gitleaks, Hadolint y Trivy: 20 vulnerabilidades altas encontradas y resueltas

![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)
![Docker](https://img.shields.io/badge/Docker_Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white)

- 🔗 [BlocDeNotas](https://github.com/antonicr1986/BlocDeNotas) — App de Windows Forms (.NET Framework 4.7.2): runner de Windows con MSBuild y NuGet, y Release con changelog y binario versionado en cada etiqueta.

[![CI BlocDeNotas](https://img.shields.io/github/actions/workflow/status/antonicr1986/BlocDeNotas/ci.yml?style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/actions)
[![Release](https://img.shields.io/github/v/release/antonicr1986/BlocDeNotas?style=for-the-badge&logo=github&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/releases/latest)

> **Cuatro modelos de entrega, cada uno donde encaja:** imagen de contenedor (API), web con despliegue controlado (web), ejecutable versionado (escritorio) y APK (Android).

## 🔒 Seguridad en mis repositorios (DevSecOps)

[![KPIs de seguridad de mis repositorios](https://raw.githubusercontent.com/antonicr1986/security-dashboard/main/data/summary-card.es.svg)](https://github.com/antonicr1986/security-dashboard/blob/main/REPORT.md)

<sub>Cifras reales de mi [security-dashboard](https://github.com/antonicr1986/security-dashboard): un job semanal de GitHub Actions lee las alertas y los workflows de cada repo y aplica un quality gate. Pulsa la tarjeta para ver el informe completo.</sub>

> **Detectar y prevenir son capas distintas, y hacen falta las dos.**

| Capa | Herramienta | Cuándo actúa |
|---|---|---|
| 🛑 Prevenir fugas de secretos | **gitleaks** en un hook `pre-commit` | Antes de que el commit exista |
| 🔍 Detectar fugas de secretos | **gitleaks** en CI · *push protection* de GitHub | En cada push, en todos mis repos públicos |
| 🧠 Análisis estático del código (SAST) | **CodeQL** | En cada push y pull request |
| 📦 Dependencias vulnerables | `dotnet list package --vulnerable` · `npm audit` · grafo de dependencias + *dependency review* | En cada pipeline y pull request |
| 🐳 Imagen Docker | **Trivy** | Antes de publicar en GHCR |
| ✍️ Firma y SBOM de la imagen | **cosign** (keyless) · **Syft** (SPDX) | Al publicar en GHCR, verificables con `cosign verify` |
| 📱 APK de Android | **MobSF** | En cada push y pull request (bloquea con hallazgos altos nuevos) |
| 🏗️ Infraestructura como código | **Trivy** (`trivy config`) | Antes de desplegar |
| 🌐 Aplicación en marcha (DAST) | **OWASP ZAP**: activo y autenticado en un entorno desechable · pasivo en producción | Antes de desplegar la API (bloquea) y después de cada despliegue |
| 🗝️ Secretos en producción | **Azure Key Vault** · identidad administrada · **AWS SSM** (write-only) | Siempre: la API los lee al arrancar |
| 🔑 Inicio de sesión de usuarios | **MFA con TOTP** · revocación de sesiones · límite de intentos · bloqueo · **Have I Been Pwned** | En cada inicio de sesión de mis apps FinanceTracker |
| 👤 Acceso a la nube | **AWS IAM Identity Center** (SSO) · MFA | Al lanzar Terraform: credenciales de 1 hora, sin claves de acceso fijas |
| 🔐 Mínimo privilegio | `GITHUB_TOKEN` de solo lectura · **OIDC** | En todos los workflows |
| 🌿 Protección de la rama principal | **Rulesets** de GitHub | En la rama principal de mis repos públicos |
| 📬 Reporte de vulnerabilidades | `SECURITY.md` · *private vulnerability reporting* | En mis repos públicos |
| 🔄 Mantenerse al día | **Dependabot** | Una pull request al mes |

<details>
<summary><b>Cómo lo aplico: secretos, dependencias y del pipeline a producción</b></summary>

### 🔑 Secretos
- **Reglas propias de gitleaks** para detectar contraseñas en cadenas de conexión .NET, que las de serie no ven
- **Historial auditado**: credenciales reales de 2023-2024 encontradas, revocadas y documentadas en `.gitleaksignore`
- **El CI detecta, el hook `pre-commit` previene**: la fuga se bloquea antes de que exista el commit

### 📦 Dependencias
- **Cada ecosistema con su herramienta**, también transitivas (.NET, npm y Gradle con *dependency review*)
- **Trivy en la imagen** revisa también las librerías del SO base: con una alta/crítica con parche, no se publica
- **Dependabot sin ruido**: una PR mensual; las versiones mayores se excluyen a propósito

### 🚦 Del pipeline a producción
- **Tienen que pasar todos los controles** (tests, secretos, imagen e IaC) o no se despliega
- **DAST que bloquea**: ZAP ataca una API desechable antes de desplegar; riesgos aceptados en `.zap/rules.tsv`
- **Mínimo privilegio**: `GITHUB_TOKEN` de solo lectura, OIDC a Azure, identidad administrada y SSO + MFA en AWS
- **Secretos rotables**: valores *write-only* de Terraform que nunca llegan al estado
- **Imagen firmada** con cosign keyless + SBOM, verificable con `cosign verify`
- **Producción vigilada**: cabeceras de seguridad y alertas de Azure Monitor ante 5xx y picos de 401/403

</details>

---

- 🔭 En el trabajo: programador .NET y responsable del CI/CD de varias aplicaciones (Azure DevOps y GitHub Actions); también administro su base de datos SQL Server y sus servicios en Azure, he desarrollado un chatbot de IA generativa con RAG y hago algo de Android y web.
- 🎓 Último curso: [Claude Code in Action](https://verify.skilljar.com/c/fmhryo5fni98) (Anthropic, agosto de 2026).
- 🌱 Aprendiendo ahora mismo: GitOps con Argo CD y Jenkins Configuration as Code, aplicándolo en proyectos personales.
- 🤔 Me interesa profundizar en: arquitectura de aplicaciones, herramientas IA, testing y buenas prácticas.
- 📫 Contacto: [LinkedIn](https://www.linkedin.com/in/antoniocompany/?locale=es-ES "Ir a mi perfil") · [CV web](https://antonio-cv-five.vercel.app/?lang=es "Ver mi CV").
- ⚡ Fuera del código: sigo la actualidad tecnológica y me gusta hacer deporte.

</details>
