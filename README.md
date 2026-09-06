# CloudFlow DevOps

Proyecto desarrollado para la asignatura **Ingeniería DevOps** como parte de la Evaluación Parcial N°1.

## Descripción

CloudFlow DevOps es un proyecto orientado a implementar un flujo de trabajo DevOps utilizando herramientas de control de versiones, colaboración, automatización y servicios Cloud.

El proyecto utiliza Git y GitHub para administrar el código fuente y su trazabilidad, GitHub Actions para automatizar procesos de integración y despliegue, y AWS EC2 como entorno Cloud para alojar el sitio web mediante Apache HTTP Server.

El flujo implementado permite validar los cambios realizados en el repositorio y desplegar automáticamente el sitio web hacia una instancia EC2.

## Tecnologías utilizadas

- Git
- GitHub
- GitHub Actions
- AWS EC2
- Amazon Linux 2023
- Apache HTTP Server
- HTML
- CSS
- SSH

## Estrategia de ramificación

Para el desarrollo del proyecto se utilizó una estrategia basada en **GitFlow**.

La estructura utilizada considera las siguientes ramas:

- `main`: contiene la versión estable del proyecto.
- `develop`: contiene los cambios que se encuentran en desarrollo e integración.
- `feature/<nombre>`: utilizada para desarrollar nuevas funcionalidades sin modificar directamente las ramas principales.
- `hotfix/<nombre>`: utilizada para realizar correcciones sobre la versión estable del proyecto.

Durante el desarrollo se utilizaron las siguientes ramas:

- `feature/diseno-inicial`
- `feature/seccion-servicios`
- `hotfix/correccion-titulo`

## Justificación de la estrategia de ramificación

Elegimos GitFlow porque era una metodología que ya conocíamos y personalmente nos resultaba más fácil de comprender y utilizar durante el desarrollo del proyecto.

La separación entre `main` y `develop` nos permitió mantener un trabajo más ordenado y una estructura más limpia. `main` se utilizó para mantener una versión estable del proyecto, mientras que `develop` permitió integrar y comprobar los cambios antes de incorporarlos definitivamente a la rama principal.

Las ramas `feature` fueron útiles para desarrollar nuevas funcionalidades de manera separada. De esta forma pudimos trabajar en cambios específicos sin afectar directamente la versión estable ni otros avances del proyecto. Posteriormente, estas funcionalidades fueron integradas mediante Pull Requests, permitiendo mantener una mejor trazabilidad de los cambios.

La rama `hotfix` permitió realizar una corrección específica sobre la versión estable. Esto ayudó a comprender cómo se pueden solucionar problemas de manera controlada y posteriormente sincronizar esa corrección con la rama de desarrollo.

Además, el uso de Pull Requests permitió revisar los cambios antes de integrarlos, identificar claramente qué modificaciones pertenecían a cada rama y mantener un registro del avance realizado.

En comparación con **trunk-based development**, consideramos que GitFlow fue más adecuado para este proyecto porque su separación mediante ramas `main`, `develop`, `feature` y `hotfix` nos permitió visualizar de manera más clara las diferentes etapas del desarrollo.

Trunk-based development se basa en integraciones frecuentes alrededor de una rama principal y en el uso de ramas de corta duración. Para nuestro proyecto preferimos GitFlow porque su estructura resultó más fácil de manejar y entender, especialmente al momento de separar nuevas funcionalidades, correcciones y versiones estables.

## Flujo de trabajo

El flujo utilizado durante el proyecto fue el siguiente:

1. Se creó la rama `main` con la estructura inicial del proyecto.
2. A partir de `main` se creó la rama `develop`.
3. Las nuevas funcionalidades se desarrollaron mediante ramas `feature`.
4. Cada `feature` fue integrada a `develop` mediante Pull Request.
5. La corrección realizada mediante `hotfix` se originó desde `main`.
6. El `hotfix` fue integrado a `main` mediante Pull Request.
7. Posteriormente, la corrección de `main` fue sincronizada con `develop`.
8. La versión desarrollada en `develop` fue integrada finalmente a `main`.
9. GitHub Actions se utilizó para validar automáticamente el proyecto y desplegar el sitio web hacia AWS EC2.

El flujo general puede representarse de la siguiente manera:

```text
feature/diseno-inicial ───────┐
                              │
feature/seccion-servicios ────┼──► develop
                              │
                              ▼
                        GitHub Actions
                              │
                              ▼
                           AWS EC2
                              │
                              ▼
                         Apache HTTP
                              │
                              ▼
                           Sitio Web


main ──► hotfix/correccion-titulo ──► main
                                      │
                                      ▼
                                   develop
```

## Convención de nombres de ramas

Para mantener una estructura clara dentro del repositorio se establecieron las siguientes convenciones:

```text
feature/<nombre-descriptivo>
hotfix/<nombre-descriptivo>
```

Ejemplos utilizados:

```text
feature/diseno-inicial
feature/seccion-servicios
hotfix/correccion-titulo
```

Los nombres de las ramas deben:

- Estar escritos en minúsculas.
- Utilizar nombres descriptivos.
- Separar palabras mediante guiones.
- Identificar claramente el propósito de la rama.

## Convención de commits

Para los mensajes de commit se utilizó una convención basada en **Conventional Commits**.

Los principales tipos utilizados fueron:

- `feat`: incorporación de una nueva funcionalidad.
- `fix`: corrección de un problema.
- `docs`: cambios relacionados con documentación.
- `chore`: tareas de mantenimiento o configuración.
- `ci`: cambios relacionados con integración o despliegue continuo.

Ejemplos utilizados durante el proyecto:

```text
chore: crear estructura inicial del proyecto

feat: implementar diseño inicial del sitio web

feat: agregar seccion de tecnologias utilizadas

fix: corregir titulo de la pagina

docs: documentar estrategia y buenas practicas del repositorio

ci: agregar pipeline de validacion y despliegue
```

Esta convención permite identificar rápidamente el propósito de cada cambio realizado en el repositorio.

## Pull Requests

Los cambios importantes se integraron mediante Pull Requests.

Durante el proyecto se realizaron Pull Requests para:

- Integrar `feature/diseno-inicial` a `develop`.
- Integrar `feature/seccion-servicios` a `develop`.
- Integrar `hotfix/correccion-titulo` a `main`.
- Integrar la versión desarrollada desde `develop` hacia `main`.

Antes de realizar un merge se debe comprobar:

- Que la rama de origen sea correcta.
- Que la rama de destino corresponda al flujo definido.
- Que los archivos modificados sean los esperados.
- Que el título del Pull Request describa claramente el cambio.
- Que la descripción detalle las modificaciones realizadas.
- Que no existan conflictos de merge.
- Que las validaciones automáticas hayan finalizado correctamente.

## Estrategia de revisión

Antes de aprobar un cambio se revisan los siguientes aspectos:

1. Funcionamiento correcto del cambio.
2. Archivos modificados.
3. Calidad y organización del código.
4. Uso correcto de las ramas.
5. Convención utilizada en los commits.
6. Posibles conflictos con otros cambios.
7. Ausencia de credenciales o información sensible.
8. Resultado de las validaciones realizadas por GitHub Actions.

Esta revisión permite reducir errores antes de incorporar cambios a las ramas principales.

## Estructura del repositorio

La estructura principal del proyecto es:

```text
cloudflow-devops/
│
├── .github/
│   └── workflows/
│       └── ci-cd.yml
│
├── index.html
│
└── README.md
```

### `.github/workflows/`

Contiene el workflow utilizado por GitHub Actions.

### `index.html`

Contiene el sitio web que es publicado automáticamente en AWS EC2.

### `README.md`

Contiene la documentación técnica, estrategia de trabajo, convenciones y buenas prácticas utilizadas durante el proyecto.

## Integración y despliegue continuo

El proyecto utiliza **GitHub Actions** para implementar un flujo básico de CI/CD.

El workflow se encuentra en:

```text
.github/workflows/ci-cd.yml
```

El workflow se activa en los siguientes eventos:

```text
push → develop

pull_request → main
```

### Integración Continua — CI

Cuando se ejecuta el workflow se realizan validaciones automáticas sobre el repositorio.

Entre ellas:

- Descarga del código fuente.
- Verificación de la existencia de `index.html`.
- Verificación de la existencia de `README.md`.
- Validación básica de la estructura HTML.

Esto permite detectar problemas antes de continuar con el proceso de despliegue.

### Despliegue Continuo — CD

Cuando ocurre un `push` hacia la rama `develop` y las validaciones finalizan correctamente, GitHub Actions ejecuta el proceso de despliegue.

El proceso realiza:

```text
GitHub
   │
   ▼
GitHub Actions
   │
   ├── Validación
   │
   ▼
Conexión SSH
   │
   ▼
AWS EC2
   │
   ▼
/var/www/html/
   │
   ▼
Apache HTTP Server
```

El archivo `index.html` se copia automáticamente hacia la instancia EC2 y posteriormente se publica mediante Apache.

## Entorno Cloud

Para alojar el sitio web se utilizó una instancia **AWS EC2**.

La instancia utiliza:

```text
Sistema operativo: Amazon Linux 2023
Servidor web: Apache HTTP Server
Protocolo web: HTTP
Puerto web: TCP 80
Administración: SSH
Puerto SSH: TCP 22
```

Apache publica el sitio desde:

```text
/var/www/html/
```

El servicio utilizado corresponde a:

```text
httpd
```

## Seguridad

Las credenciales utilizadas por GitHub Actions no se encuentran almacenadas directamente dentro del repositorio.

Para proteger los datos de conexión se utilizaron **GitHub Secrets**.

Los secrets configurados son:

```text
EC2_HOST
EC2_USER
EC2_SSH_KEY
```

### `EC2_HOST`

Contiene la dirección del servidor EC2.

### `EC2_USER`

Contiene el usuario utilizado para realizar la conexión mediante SSH.

### `EC2_SSH_KEY`

Contiene la clave privada utilizada por GitHub Actions para autenticarse en la instancia EC2.

La clave privada no debe almacenarse directamente dentro del repositorio.

## Buenas prácticas

Durante el proyecto se aplicaron buenas prácticas de control de versiones y trabajo colaborativo, entre ellas:

- No trabajar directamente sobre `main` para desarrollar nuevas funcionalidades.
- Utilizar ramas específicas según el tipo de cambio.
- Utilizar nombres de ramas descriptivos.
- Mantener mensajes de commit claros.
- Utilizar Pull Requests antes de integrar cambios.
- Revisar los cambios antes de realizar un merge.
- Mantener documentación actualizada.
- Evitar almacenar credenciales dentro del repositorio.
- Utilizar GitHub Secrets para información sensible.
- Validar automáticamente el proyecto mediante GitHub Actions.
- Mantener trazabilidad mediante commits y Pull Requests.

## Resultado

El proyecto permitió implementar un flujo DevOps en el que los cambios realizados localmente pueden ser enviados a GitHub, validados automáticamente mediante GitHub Actions y posteriormente desplegados hacia una instancia AWS EC2.

El flujo implementado es:

```text
Desarrollo local
      │
      ▼
     Git
      │
      ▼
    GitHub
      │
      ▼
Pull Requests
      │
      ▼
GitHub Actions
      │
      ├── CI: Validación
      │
      └── CD: Despliegue
                │
                ▼
             AWS EC2
                │
                ▼
              Apache
                │
                ▼
             Sitio Web
```

## Uso de Inteligencia Artificial

Durante el desarrollo del proyecto se utilizó ChatGPT como herramienta de apoyo para orientar pasos de configuración, revisar sintaxis y mejorar la organización y redacción de la documentación.

Las configuraciones implementadas fueron comprobadas mediante su ejecución en Git, GitHub, GitHub Actions y AWS EC2.

## Autores

Proyecto desarrollado como parte de la **Evaluación Parcial N°1 de Ingeniería DevOps**.