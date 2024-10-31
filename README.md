# Prueba tecnica de desarrollador Fullstack Junior - Two to Tango

## Contexto de la Prueba Técnica

La prueba técnica consistió en desarrollar una aplicación web de gestión de tareas que permita a los usuarios registrarse, iniciar sesión y gestionar una lista de tareas. Cada tarea incluye un estado y una fecha de vencimiento, y los usuarios pueden crear, ver, editar y eliminar sus propias tareas. La aplicación se divide en un backend desarrollado con _NestJS_ y _TypeScript, encargado de la autenticación y el manejo de la API, y un frontend construido con \*\*Next.js_ para proporcionar una interfaz sencilla y funcional. Además, se evaluaron aspectos de seguridad, validación y buenas prácticas en la implementación.

### Decisiones Técnicas - Backend

Para la implementación del backend, se optó por estructurar el proyecto en tres módulos principales, dada la no complejidad de la aplicación: un módulo de **usuarios** para gestionar la información de los usuarios, un módulo de **tareas** para la lógica de CRUD de tareas, y un módulo de **autenticación** para el manejo de sesiones y seguridad.

En el módulo de autenticación, se decidió no utilizar la librería **Passport**. En su lugar, se creó una implementación personalizada de autenticación JWT aprovechando las funcionalidades nativas de **NestJS**, lo cual redujo la cantidad de dependencias externas. Para la capa de persistencia, se optó por usar **TypeORM** como ORM, conectado a una base de datos **PostgreSQL**, facilitando el manejo de las conexiones y las operaciones en la base de datos.

### Decisiones Técnicas - Frontend

En el frontend, se optó por **NextAuth** para manejar la autenticación y seguridad. Esta librería proporciona una capa robusta para gestionar autenticación y permisos en aplicaciones de Next.js, y facilita la configuración en proyectos de este tamaño. Además, es flexible y permite incorporar programas de autenticación adicionales en el futuro.

A nivel visual, se utilizó **DAICYUI** para los componentes de interfaz, lo cual agilizó el desarrollo al ofrecer una biblioteca de componentes predefinidos. Para la arquitectura de persistencia, se implementó una estructura donde la lógica de comunicación con el backend está separada en servicios dedicados a interactuar con la API. Además, se usó **TanStack Query** para manejar las peticiones y mutaciones a la API, aprovechando su sistema de caché robusto y la optimización que brinda en las comunicaciones externas.

## Levantamiento del Backend

### Configuración e Inicio del Backend

1. **Clonar el repositorio**

   Una vez clonado este repositorio, nevigate a la carpeta del backend

   ```bash
    cd  test-twototango-backend
   ```

2. **Instalar las dependencias**

   Instala las dependencias del backend:

   ```bash
   npm install
   ```

3. **Configurar las variables de entorno**

En la raíz del proyecto, crea un archivo .env que debe contenedor las variables de entorno para la aplicación. Copia el archivo `.env.example` y renombra el archivo a `.env`. y agrega las variables de entorno correspondientes.

3.1 **(Opcional) Levantar la base de datos con Docker**

En la raíz del proyecto del backend, encontrarás un archivo `docker-compose.yml`, que contiene una configuración básica y rápida para levantar una base de datos **PostgreSQL** con ciertas variables de entorno preconfiguradas. Esto facilita la conexión con el backend sin necesidad de instalar PostgreSQL localmente.

Si tienes Docker instalado en tu computador, puedes ejecutar el siguiente comando para levantar el contenedor:

```bash
docker-compose up -d
```

Una vez levantada la base de datos en PostgreSQL, está configurada con las siguientes variables de entorno, que puedes copiar y reemplazar en tu archivo `.env` para que la aplicación se conecte satisfactoriamente a la base de datos. Las variables de entorno preconfiguradas son:

```yaml
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=twototango
```

4. **Iniciar el backend**
   Para ejecutar el backend, puedes ejecutar el siguiente comando:

   ```bash
   npm run start:dev
   ```

### Configuración e Inicio del Frontend

1. **Navegar al repositorio**

   Una vez clonado este repositorio, nevigate a la carpeta del frontend

   ```bash
    cd  test-twototango-frontend
   ```

2. **Instalar las dependencias**

   Instala las dependencias del frontend:

   ```bash
   npm install
   ```

3. **Configurar las variables de entorno**

En la raíz del proyecto, crea un archivo `.env` que debe contenedor las variables de entorno para la aplicación. Copia el archivo `.example.env` y renombra el archivo a `.env`. y agrega las variables de entorno correspondientes.

Muy importante configurar las variables de entorno de la siguiente manera:

```yaml
NEXT_PUBLIC_BASE_API_URL=http://localhost:3000/api -> url de la API
NEXTAUTH_URL=http://localhost:3000 -> url de la aplicación
NEXTAUTH_SECRET=tus-secret
```

4. **Iniciar el frontend**
   Para ejecutar el frontend, puedes ejecutar el siguiente comando:

   ```bash
   npm run dev
   ```

<br>
<hr/>

Yoyler Mosquera Cordoba

