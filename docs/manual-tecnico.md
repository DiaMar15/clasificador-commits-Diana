 Manual técnico

1. Arquitectura

El sistema está compuesto por un cliente, una API REST desarrollada con FastAPI,dos opciones para clasificar los mensajes del commit y una base de datos PostgreSQL donde se guardan las inferencias realixadas durante el mismo.

            Diagrama de arquitectura


                    CLIENTE

              Navegador / Swagger
                     |
                     | HTTP
                     | Puerto 8000
                     v
              +----------------+
              |   FastAPI API  |
              |   0.0.0.0:8000 |
              +----------------+
                /            \
               /              \
              v                v
       +-------------+    +-------------+
       | Motor ECO   |    |   Ollama    |
       | reglas-v1   |    | qwen2.5:0.5b|
       +-------------+    | :11434      |
                          +-------------+
                                |
                                |
                                v
                       +----------------+
                       |   PostgreSQL   |
                       | Docker db-ia   |
                       | Puerto 5432    |
                       +----------------+
                                |
                                v
                         Base de datos
                              iadb


2. Seguridad

Para la base de datos se utilizan dos usuarios principales.

El usuario postgres es el administrador de PostgreSQL y se utiliza para
realizar tareas administrativas y de configuración.

El usuario app_ia es el usuario que utiliza la aplicación. Tiene solamente
los permisos necesarios para trabajar con la tabla inferencias, como
consultar e insertar registros. De esta manera, la aplicación no necesita
utilizar el usuario administrador.

Manejo de contraseñas

Las contraseñas y demás datos sensibles se guardan en el archivo .env.
Este archivo no se sube al repositorio porque está incluido en .gitignore.

De esta forma, las credenciales no quedan escritas directamente en el
código de la aplicación ni se publican en GitHub.

Si una contraseña llegara a filtrarse, se debería cambiar inmediatamente
la contraseña comprometida y actualizar el archivo .env.

También se debería revisar dónde fue expuesta la contraseña y comprobar que
no haya quedado publicada en el repositorio o en su historial.

Después de cambiarla, se deben comprobar nuevamente las conexiones de la
aplicación y de los servicios que utilizaban esa credencial.
