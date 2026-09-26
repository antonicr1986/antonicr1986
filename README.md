[English](https://github.com/antonicr1986/antonicr1986/blob/main/README.en.md) · **Español**

### Hola, soy Antonio Company 👋

Desarrollador .NET en transición a DevOps CI/CD. Vengo del desarrollo y mantenimiento de aplicaciones empresariales (C#, SQL Server) y ahora mismo estoy construyendo mi perfil en Docker y automatización de pipelines.

## 🛠️ DevOps & Infraestructura
- Git / GitHub — control de versiones
- GitHub Actions — CI/CD sobre runners Linux y Windows
- Azure DevOps — Repos, Boards, Pipelines y Documentación (wiki)
- Docker y registros de imágenes (GHCR) — aplicado en proyectos personales
- Publicación automatizada de artefactos y Releases versionadas
- Despliegue controlado desde el pipeline (Vercel) — la publicación depende de que los controles pasen, no del push
- Seguridad en el pipeline — escaneo de secretos (gitleaks), reglas propias y excepciones documentadas
- Kubernetes, Jenkins — aprendiendo activamente


## 💻 Desarrollo
- C# / VB.NET · .NET Framework / .NET 8
- Entity Framework / EF Core / Windows Forms
- SQL Server
- HTML, CSS, JavaScript / TypeScript · Node.js, React, Tailwind CSS
- Java/Kotlin (desarrollo con Android Studio)

## 🚀 Proyectos destacados

- 🔗 [financetracker-web](https://github.com/antonicr1986/financetracker-web) — Interfaz web de FinanceTracker en Next.js 16, TypeScript y Tailwind CSS: registro e inicio de sesión, alta de transacciones, filtros por tipo, categoría y texto, dashboard con gráficos sin librerías externas, tema claro/oscuro e interfaz completa en español e inglés. Se entra en un clic con la cuenta de demostración, sin registrarse. El despliegue lo lanza **el propio pipeline**, y solo después de que el escaneo de secretos y la compilación estén en verde. **[Abrir la aplicación](https://financetracker-web-tau.vercel.app/login)**

[![CI financetracker-web](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-web/ci.yml?branch=main&style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-web/actions)
[![Demo](https://img.shields.io/badge/demo-online-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://financetracker-web-tau.vercel.app/login)

- 🔗 [financetracker-android](https://github.com/antonicr1986/financetracker-android) — Cliente Android de FinanceTracker en Kotlin: el **segundo consumidor de la misma API**, que es lo que la convierte en un contrato — mismos endpoints, mismos códigos de error y mismas reglas de negocio desde otra plataforma. Registro e inicio de sesión, selector de meses, totales, alta, edición y borrado de movimientos, presupuestos mensuales con barra de progreso y la misma estética que la web: paleta corporativa común, tema claro/oscuro y español/inglés desde la barra superior, con cambio sin parpadeo. Se entra en un toque con la cuenta de demostración. El pipeline escanea secretos, ejecuta las pruebas unitarias —y **falla si no se ejecuta ninguna**— y deja el **APK descargable** en cada ejecución.

[![CI financetracker-android](https://img.shields.io/github/actions/workflow/status/antonicr1986/financetracker-android/ci.yml?branch=main&style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/financetracker-android/actions)
![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)

- 🔗 [FinanceTracker](https://github.com/antonicr1986/FinanceTracker) — API REST en .NET 8 con arquitectura por capas, autenticación JWT y tests automatizados. Dockerizada (API + SQL Server) y con un pipeline que compila, ejecuta los tests y **publica la imagen en GitHub Container Registry**, etiquetada por commit para poder desplegar o revertir cualquier versión concreta. En producción corre sobre **Azure App Service contra Azure SQL**, desplegada desde el propio pipeline. **[Ver la API en Swagger](https://financetracker-api-cpctbta0gddddge5.belgiumcentral-01.azurewebsites.net/swagger)** — plan gratuito con SQL serverless, así que la primera petición tras un rato de inactividad tarda unos segundos.

[![CI FinanceTracker](https://img.shields.io/github/actions/workflow/status/antonicr1986/FinanceTracker/ci.yml?style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/FinanceTracker/actions)

- 🔗 [BlocDeNotas](https://github.com/antonicr1986/BlocDeNotas) — Aplicación de escritorio en Windows Forms (.NET Framework 4.7.2). Pipeline sobre runner de Windows con MSBuild y NuGet, y **publicación automática de Releases** al etiquetar una versión: empaqueta el ejecutable, genera el changelog y sella el número de versión en el propio binario.

[![CI BlocDeNotas](https://img.shields.io/github/actions/workflow/status/antonicr1986/BlocDeNotas/ci.yml?style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/actions)
[![Release](https://img.shields.io/github/v/release/antonicr1986/BlocDeNotas?style=for-the-badge&logo=github&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/releases/latest)

> Cuatro modelos de entrega distintos: uno publica una imagen de contenedor y despliega la API sobre Azure App Service; otro publica un ejecutable versionado listo para descargar; otro publica un sitio web, y solo si los controles previos pasan; y el último deja un APK instalable en cada ejecución. El pipeline se adapta a lo que hay que entregar.

## 🔒 Seguridad en mis repositorios

Todos mis repositorios públicos tienen escaneo de secretos con **gitleaks**, con una configuración propia que extiende las reglas estándar: las por defecto detectan claves de proveedores conocidos, pero no una contraseña dentro de una cadena de conexión, que es la forma que toma una fuga en un proyecto .NET.

Auditando mi propio historial con esas reglas aparecieron credenciales reales de 2023 y 2024. Están revocadas, y cada una queda registrada en un `.gitleaksignore` con qué era y qué se hizo — porque un pipeline permanentemente en rojo deja de leerse.

El escaneo en CI detecta, pero no impide: cuando el workflow falla, el commit ya está publicado. Por eso la misma configuración corre también en un hook `pre-commit` local, que bloquea el commit antes de que llegue a existir. Detectar y prevenir son capas distintas, y hacen falta las dos.

El proyecto más reciente, un bot de Telegram, nunca llegó a tener el token en el código: se lee de una variable de entorno desde el primer commit.

---

- 🔭 En SOLPORT: programador .NET, con incursiones en apps Android y web internas.
- 🌱 Aprendiendo ahora mismo: Docker, Kubernetes y Jenkins, aplicándolo en proyectos personales.
- 🤔 Me interesa profundizar en: arquitectura de aplicaciones, herramientas IA, testing y buenas prácticas.
- 📫 Contacto: [LinkedIn](https://www.linkedin.com/in/antoniocompany/ "Ir a mi perfil").
- ⚡ Fuera del código: sigo la actualidad tecnológica y me gusta hacer deporte.
