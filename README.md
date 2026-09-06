# CloudFlow DevOps

Proyecto desarrollado para la asignatura Ingeniería DevOps.

## Descripción

CloudFlow DevOps implementa un flujo de trabajo DevOps utilizando Git,
GitHub, GitHub Actions y AWS EC2.

El proyecto aplica control de versiones, estrategia de ramificación,
Pull Requests, automatización y despliegue de una aplicación web
sobre un servidor Apache alojado en una instancia EC2.

## Tecnologías utilizadas

- Git
- GitHub
- GitHub Actions
- AWS EC2
- Amazon Linux 2023
- Apache HTTP Server
- HTML
- CSS
- JavaScript

## Estrategia de ramificación

Para este proyecto se utiliza una estrategia basada en GitFlow.

Las ramas principales son:

- `main`: contiene la versión estable del proyecto.
- `develop`: contiene los cambios integrados durante el desarrollo.
- `feature/<nombre>`: se utiliza para desarrollar nuevas funcionalidades.
- `hotfix/<nombre>`: se utiliza para aplicar correcciones urgentes sobre la versión estable.

## Flujo de trabajo

El flujo utilizado es el siguiente:

1. Las nuevas funcionalidades se crean desde `develop`.
2. Cada funcionalidad se desarrolla en una rama `feature/<nombre>`.
3. Los cambios se integran a `develop` mediante Pull Request.
4. Las correcciones urgentes se crean desde `main` mediante ramas `hotfix/<nombre>`.
5. Los hotfix se integran a `main` mediante Pull Request.
6. Los cambios realizados en `main` también se sincronizan posteriormente con `develop`.

## Convención de nombres de ramas

Se utiliza la siguiente nomenclatura:

- `feature/diseno-inicial`
- `feature/seccion-servicios`
- `hotfix/correccion-titulo`

Las ramas deben utilizar nombres descriptivos, en minúsculas y separados mediante guiones.

## Convención de commits

Se utiliza una convención basada en Conventional Commits.

Ejemplos:

- `feat: implementar diseño inicial del sitio web`
- `feat: agregar seccion de tecnologias utilizadas`
- `fix: corregir titulo de la pagina`
- `chore: crear estructura inicial del proyecto`

Tipos principales utilizados:

- `feat`: nueva funcionalidad.
- `fix`: corrección de errores.
- `chore`: tareas de mantenimiento o configuración.
- `docs`: cambios en documentación.

## Pull Requests

Todos los cambios importantes deben integrarse mediante Pull Request.

Antes de realizar un merge se debe revisar:

- Que la rama destino sea correcta.
- Que los archivos modificados correspondan al cambio propuesto.
- Que el nombre del Pull Request sea descriptivo.
- Que la descripción detalle los cambios realizados.
- Que no existan conflictos de merge.

## Estrategia de revisión

Antes de aprobar un Pull Request se revisa:

1. Funcionamiento del cambio.
2. Calidad del código.
3. Convención de commits.
4. Uso correcto de ramas.
5. Ausencia de archivos sensibles o credenciales.
6. Compatibilidad con la versión actual del proyecto.

## Estructura del repositorio

```text
cloudflow-devops/
├── .github/
│   └── workflows/
├── assets/
├── index.html
└── README.md