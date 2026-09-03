# FRONTEND RESTAURANTE

Aplicación web del proyecto **P5 Digital Academy - Restaurante**, desarrollada con Vue 3, Vite y Tailwind CSS. Este frontend será responsable de mostrar la interfaz de usuario, gestionar el estado de la aplicación, navegar entre pantallas y comunicarse con la API del backend.

## Planificación

Antes de desarrollar las funcionalidades es necesario definir:

- Las vistas y los componentes reutilizables de la aplicación.
- Las rutas públicas y privadas y los permisos de cada tipo de usuario.
- El estado global necesario para sesión, productos, carrito y pedidos.
- Los servicios que se comunicarán con la API REST.
- El flujo principal del MVP: catálogo, carrito, pedido, pago y seguimiento.
- La estrategia de pruebas unitarias y cobertura.
- Las variables de entorno necesarias, como la URL de la API.

## Requisitos

- Node.js `^20.19.0` o `>=22.12.0`.
- npm, incluido con Node.js.

## Instalación y ejecución

Instala exactamente las versiones registradas en `package-lock.json`:

```bash
npm ci
```

Inicia el servidor local de desarrollo:

```bash
npm run dev
```

Vite mostrará en la terminal la URL local en la que se puede abrir la aplicación.

## Comandos disponibles

| Comando                 | Descripción                                                        |
| ----------------------- | ------------------------------------------------------------------ |
| `npm run dev`           | Inicia el servidor de desarrollo de Vite con recarga automática.   |
| `npm run build`         | Genera en `dist/` la versión optimizada para producción.           |
| `npm run preview`       | Sirve localmente la compilación de producción para revisarla.      |
| `npm run lint`          | Analiza los archivos JavaScript y Vue con ESLint.                  |
| `npm run lint:fix`      | Corrige automáticamente los problemas que ESLint puede solucionar. |
| `npm run format`        | Formatea el proyecto con Prettier.                                 |
| `npm run format:check`  | Comprueba el formato sin modificar archivos.                       |
| `npm run test:unit`     | Ejecuta Vitest en modo interactivo.                                |
| `npm run test:coverage` | Ejecuta una vez los tests y genera el informe de cobertura.        |

## Estructura del proyecto

```text
project-p5-digital-academy-team3-restaurant-frontend/
├── public/                     # Archivos estáticos servidos sin transformación
├── docs/                       # Documentación con decisiónes técnicas del proyecto
├── src/                        # Código fuente de la aplicación
│   ├── assets/                 # Imágenes, iconos, fuentes y estilos procesados por Vite
│   ├── components/             # Componentes Vue reutilizables
│   ├── core/                   # Infraestructura y configuración global de la aplicación
│   ├── router/                 # Definición de rutas y guardas de navegación
│   ├── shared/                 # Utilidades, constantes y recursos compartidos
│   ├── stores/                 # Stores globales de Pinia
│   ├── views/                  # Vistas asociadas a las rutas de la aplicación
│   ├── App.vue                 # Componente raíz
│   ├── main.js                 # Punto de entrada y montaje de Vue
│   └── style.css               # Estilos globales
├── .vscode/                    # Recomendaciones y ajustes compartidos de VS Code
├── .gitignore                  # Archivos y carpetas excluidos de Git
├── .prettierignore             # Archivos que Prettier no debe procesar
├── .prettierrc.json            # Reglas de formato de Prettier
├── eslint.config.js            # Configuración de ESLint para JavaScript y Vue
├── index.html                  # Documento HTML de entrada utilizado por Vite
├── package.json                # Scripts, dependencias y metadatos del proyecto
├── package-lock.json           # Versiones exactas del árbol de dependencias
├── vite.config.js              # Configuración de Vite y sus plugins
└── README.md                   # Documentación del frontend
```

Las carpetas que todavía no contienen código incluyen un archivo `.gitkeep`. Git no registra carpetas vacías, por lo que este archivo permite conservar la estructura inicial en el repositorio.

### Responsabilidad de las carpetas de `src`

- **`assets/`**: recursos importados desde los componentes, como imágenes y hojas de estilo. Vite los procesa, optimiza y añade a la compilación.
- **`components/`**: piezas de interfaz reutilizables. Por ejemplo, botones, tarjetas de producto, cabeceras o formularios.
- **`core/`**: elementos centrales que se configuran una sola vez, como el cliente HTTP de Axios, interceptores, autenticación o configuración de la API.
- **`router/`**: instancia de Vue Router, listado de rutas y guardas para controlar el acceso a vistas protegidas.
- **`shared/`**: código sin responsabilidad de negocio específica que se utiliza en varios módulos: constantes, helpers, validaciones o composables comunes.
- **`stores/`**: estado global administrado con Pinia. Aquí pueden vivir los stores de autenticación, carrito, productos y pedidos.
- **`views/`**: componentes que representan páginas completas y que normalmente se enlazan desde Vue Router.

## Dependencias de producción

Estas dependencias forman parte del funcionamiento de la aplicación y pueden incorporarse al bundle que se entrega al navegador.

### Vue

Framework principal de la interfaz. Proporciona componentes, reactividad, directivas, propiedades computadas y la Composition API. Los archivos `.vue` permiten reunir plantilla, lógica y estilos de cada componente.

### Vue Router

Router oficial para Vue. Relaciona cada URL con una vista, permite navegar sin recargar la página y ofrece guardas de navegación para proteger rutas según la sesión o el rol del usuario.

### Pinia

Sistema oficial de gestión de estado para Vue. Centraliza información que debe compartirse entre componentes, como el usuario autenticado, los productos, el carrito o el estado de un pedido.

### Axios

Cliente HTTP utilizado para consumir la API REST del backend. Facilita las peticiones `GET`, `POST`, `PUT` y `DELETE`, permite definir una URL base y ofrece interceptores para añadir tokens o gestionar errores globalmente.

## Dependencias de desarrollo

Se utilizan durante el desarrollo, las pruebas o la compilación. No representan funcionalidades que el usuario deba descargar por separado.

### Compilación y desarrollo

- **Vite**: servidor de desarrollo y herramienta de compilación. Ofrece arranque rápido, recarga automática y genera el bundle optimizado de producción.
- **`@vitejs/plugin-vue`**: integra Vue con Vite y permite transformar los componentes de archivo único `.vue`.
- **Tailwind CSS**: framework CSS basado en clases de utilidad. Permite construir la interfaz directamente desde las plantillas Vue utilizando clases para colores, tamaños, espaciado, tipografía y diseño responsive.
- **`@tailwindcss/vite`**: plugin oficial que integra Tailwind CSS 4 con Vite. Detecta las clases utilizadas por la aplicación y genera únicamente los estilos necesarios durante el desarrollo y la compilación.
- **`vite-plugin-vue-devtools`**: integra las herramientas de desarrollo de Vue con Vite para inspeccionar componentes, rutas y estado durante el desarrollo.
- **`sass-embedded`**: compilador de Sass. Permite utilizar SCSS o Sass dentro de los estilos globales y de los componentes Vue.

### Testing

- **Vitest**: framework de pruebas integrado con Vite. Ejecuta tests unitarios con una configuración y transformación compatibles con el proyecto.
- **`@vitest/coverage-v8`**: genera informes de cobertura mediante el motor V8 e indica qué líneas, funciones y ramas han sido probadas.
- **`@vue/test-utils`**: utilidades oficiales para montar componentes Vue, interactuar con ellos y comprobar el HTML o los eventos que producen.
- **`@pinia/testing`**: facilita la creación de instancias de Pinia controladas para probar componentes y stores de forma aislada.
- **jsdom**: simula APIs del navegador y un DOM dentro de Node.js para poder probar componentes sin abrir un navegador real.

### Calidad y formato del código

- **ESLint**: analiza estáticamente JavaScript y detecta errores, variables sin utilizar y patrones problemáticos.
- **`@eslint/js`**: contiene la configuración de reglas recomendadas para JavaScript mantenida por ESLint.
- **`eslint-plugin-vue`**: permite a ESLint analizar archivos `.vue` y añade reglas específicas para scripts y plantillas de Vue.
- **globals**: proporciona listas de variables globales conocidas de entornos como navegador y Node.js. Evita que ESLint marque `window`, `document`, `console` o `process` como variables inexistentes cuando son válidas en su entorno.
- **Prettier**: aplica automáticamente un formato uniforme a JavaScript, Vue, CSS, JSON y Markdown.
- **`eslint-config-prettier`**: desactiva reglas de ESLint que podrían entrar en conflicto con las decisiones de formato de Prettier.

ESLint se ocupa principalmente de la calidad y los posibles errores del código; Prettier se ocupa exclusivamente de su presentación y formato.

## Gestión de dependencias

`package.json` declara las dependencias permitidas por el proyecto. `package-lock.json` registra las versiones exactas instaladas, incluidas las dependencias indirectas, para que todo el equipo obtenga el mismo árbol de paquetes.

Para añadir una dependencia necesaria durante la ejecución:

```bash
npm install nombre-del-paquete
```

Para añadir una herramienta utilizada únicamente durante el desarrollo:

```bash
npm install --save-dev nombre-del-paquete
```

No se debe editar `package-lock.json` manualmente: npm lo crea y actualiza al instalar, actualizar o eliminar paquetes.

## Comprobación antes de entregar cambios

Antes de crear un commit o una pull request se recomienda ejecutar:

```bash
npm run format:check
npm run lint
npm run test:unit -- --run
npm run build
```
