### Hola, soy Antonio Company 👋

Desarrollador .NET en transición a DevOps CI/CD. Vengo del desarrollo y mantenimiento de aplicaciones empresariales (C#, SQL Server) y ahora mismo estoy construyendo mi perfil en Docker y automatización de pipelines.

## 🛠️ DevOps & Infraestructura
- Git / GitHub — control de versiones
- GitHub Actions — CI/CD sobre runners Linux y Windows
- Azure DevOps — Repos, Boards, Pipelines y Documentación (wiki)
- Docker y registros de imágenes (GHCR) — aplicado en proyectos personales
- Publicación automatizada de artefactos y Releases versionadas
- Seguridad en el pipeline — escaneo de secretos (gitleaks), reglas propias y excepciones documentadas
- Kubernetes, Jenkins — aprendiendo activamente


## 💻 Desarrollo
- C# / VB.NET · .NET Framework / .NET 8
- Entity Framework / EF Core / Windows Forms
- SQL Server
- HTML, CSS, JavaScript / TypeScript · Node.js, React, Tailwind CSS
- Java (desarrollo con Android Studio)

## 🚀 Proyectos destacados

- 🔗 [financetracker-web](https://github.com/antonicr1986/financetracker-web) - Interfaz web de FinanceTracker en Next.js 16, TypeScript y Tailwind CSS. Desplegada en Vercel con entrega continua: cada push a `main` publica automaticamente.

**[Abrir la aplicacion](https://financetracker-web.vercel.app)**

- 🔗 [FinanceTracker](https://github.com/antonicr1986/FinanceTracker) — API REST en .NET 8 con arquitectura por capas, autenticación JWT y tests automatizados. Dockerizada (API + SQL Server) y con un pipeline que compila, ejecuta los tests y **publica la imagen en GitHub Container Registry**, etiquetada por commit para poder desplegar o revertir cualquier versión concreta.

[![CI FinanceTracker](https://img.shields.io/github/actions/workflow/status/antonicr1986/FinanceTracker/ci.yml?style=for-the-badge&label=CI%2FCD&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/FinanceTracker/actions)

- 🔗 [BlocDeNotas](https://github.com/antonicr1986/BlocDeNotas) — Aplicación de escritorio en Windows Forms (.NET Framework 4.7.2). Pipeline sobre runner de Windows con MSBuild y NuGet, y **publicación automática de Releases** al etiquetar una versión: empaqueta el ejecutable, genera el changelog y sella el número de versión en el propio binario.

[![CI BlocDeNotas](https://img.shields.io/github/actions/workflow/status/antonicr1986/BlocDeNotas/ci.yml?style=for-the-badge&label=CI&logo=githubactions&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/actions)
[![Release](https://img.shields.io/github/v/release/antonicr1986/BlocDeNotas?style=for-the-badge&logo=github&logoColor=white)](https://github.com/antonicr1986/BlocDeNotas/releases/latest)

> Dos modelos de entrega continua distintos: uno publica una imagen de contenedor lista para desplegar en un servidor; el otro publica un ejecutable versionado listo para descargar. El pipeline se adapta a lo que hay que entregar.
> 
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
