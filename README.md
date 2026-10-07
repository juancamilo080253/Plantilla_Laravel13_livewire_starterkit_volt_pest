# Los 4 pasos para revivir un proyecto recién clonado de GitHub
Cada vez que clones un proyecto de Laravel de cualquier repositorio, debes ejecutar este "ritual" de 5 comandos en tu terminal dentro de la carpeta del proyecto:

## 🛠️ Requisitos Previos

Asegúrate de tener instalados en tu sistema:
- **PHP** (v8.3 o superior)
- **Composer**
- **Node.js** & **NPM**
- Una base de datos MySQL / PostgreSQL activa (o Laravel Herd / Laragon)

---

### 1. Instalar todas las librerías de PHP (Backend)
Ejecuta esto en tu terminal:
Crea la carpeta `vendor/`: Este comando lee el archivo composer.json de tu proyecto, descarga las versiones exactas que tenías de Laravel.

``` 
composer install
```


### 2. Instalar dependencias de JavaScript y CSS (Frontend)
Crea la carpeta `node_modules/` y descarga herramientas como Vite, Tailwind, Alpine, etc.:

``` 
npm install
```

### 3. Crear tu archivo de entorno .env
El archivo .env tampoco se sube a GitHub por seguridad (porque contiene claves y contraseñas de BD). Tienes que crear uno nuevo copiando la plantilla de ejemplo:

``` 
copy .env.example .env
```
(Si usas Git Bash o PowerShell también puedes hacerlo).

### 4. Generar la clave de encriptación (APP_KEY)
Como vimos antes, el archivo .env nuevo vendrá con la APP_KEY vacía. Genera la tuya con:

``` 
php artisan key:generate
```

### 5. Configurar la base de datos
Abre el archivo:

`.env`

y configura los datos de conexión de tu base de datos.

Por ejemplo:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nombre_de_la_bd
DB_USERNAME=root
DB_PASSWORD=
```

### 5. (Opcional)  Ejecutar las migraciones
Asegúrate de que tu base de datos configurada en el .env exista y corre:

``` 
php artisan migrate
```

### ¡Listo!

### 6. Ejecutar el proyecto
En dos terminales separadas correr:
- Terminal 1 — Laravel: `php artisan serve`.
- Terminal 2 — Vite: `npm run dev`.
