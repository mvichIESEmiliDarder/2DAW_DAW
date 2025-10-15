
Esta guía utiliza el estándar de la comunidad para la instalación de proyectos Laravel sin necesidad de instalar PHP o Composer directamente en Ubuntu, usando contenedores de Docker.

## 1. Preparación del Entorno

Asegúrate de que **Docker Desktop está iniciado y en ejecución** en tu sistema Ubuntu.

1. **Navega al directorio** donde deseas alojar tus proyectos (ej: `~/proyectos`).
    
    Bash
    
    ```
    cd ~/Documentos/proyectos-web
    ```
    

---

## 2. Creación del Proyecto Laravel

Utilizaremos la imagen oficial de Composer dentro de Docker para crear el proyecto. El _flag_ `--rm` asegura que el contenedor se elimine inmediatamente después de crear el proyecto.

1. **Crea el proyecto `hola-laravel`:**
    
    Bash
    
    ```
    docker run --rm \
        -v "$(pwd)":/app \
        composer/composer create-project laravel/laravel hola-laravel
    ```
    
    - **Explicación:** Mapea tu directorio actual (`$(pwd)`) al directorio de trabajo del contenedor (`/app`), permitiendo que Composer escriba los archivos del proyecto directamente en tu Ubuntu.
        
2. **Accede al nuevo directorio:**
    
    Bash
    
    ```
    cd hola-laravel
    ```
    

---

## 3. Instalación y Configuración de Laravel Sail

Laravel Sail proporciona el archivo `docker-compose.yml` para definir los servicios de desarrollo (PHP, MySQL, Nginx, Redis).

1. Instala los archivos de Sail (docker-compose.yml):
    
    Ejecutamos el comando artisan sail:install dentro de un contenedor temporal de PHP, ya que no tienes PHP instalado localmente.
    
    Bash
    
    ```
    docker run --rm \
        -u "$(id -u):$(id -g)" \
        -v "$(pwd):/var/www/html" \
        -w /var/www/html \
        laravelsail/php83-composer:latest \
        php artisan sail:install --with=mysql,redis
    ```
    
2. Configura el Alias sail (Opcional, pero vital):
    
    Esto simplifica la ejecución de todos los comandos de Artisan, Composer y PHP.
    
    Bash
    
    ```
    echo 'alias sail="bash vendor/bin/sail"' >> ~/.bashrc
    source ~/.bashrc
    ```
    

---

## 4. Primer Arranque del Entorno de Desarrollo

El siguiente comando inicia los contenedores persistentes que usarás para el desarrollo local.

1. **Levanta los contenedores:**
    
    Bash
    
    ```
    sail up -d
    ```
    
    - **Explicación:** El _script_ `sail` llama a Docker Compose, que lee el `docker-compose.yml` y lanza los servicios en segundo plano (`-d`).
        
2. Inicializa la base de datos (Migraciones):
    
    Esto crea las tablas necesarias, resolviendo el error de "table not found" que ocurre al visitar la página por primera vez.
    
    Bash
    
    ```
    sail artisan migrate
    ```
    
3. Verificación Final:
    
    Abre tu navegador y navega a http://localhost. Deberías ver la página de bienvenida de Laravel.
    

---

## 5. Uso Diario para el Desarrollo

Una vez que el entorno está levantado, todos los comandos relacionados con PHP deben ejecutarse a través del alias `sail`.

|Acción|Comando|
|---|---|
|**Crear un Controlador**|`sail artisan make:controller PostController`|
|**Instalar un paquete**|`sail composer require laravel/ui`|
|**Ejecutar pruebas**|`sail artisan test`|
|**Acceder al bash del contenedor**|`sail bash`|
|**Detener el entorno**|`sail down`|
|**Reiniciar el entorno**|`sail up -d`|