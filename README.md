# CRUD con Laravel

> **Universidad Tecnológica de Panamá**  
> Facultad de Ingeniería de Sistemas Computacionales

---

## 📋 Descripción

Laboratorio de implementación de un CRUD (Create, Read, Update, Delete) utilizando el framework **Laravel** con base de datos relacional gestionada a través de **phpMyAdmin**, haciendo uso del paquete **Ibex/CRUD** para la generación automática de las vistas y controladores.

---

## 🔗 Enlace al Repositorio

> *(Ver documento original para el enlace al repositorio de GitHub)*

---

## 🚀 Pasos de Implementación

### 1. Creación del proyecto

Se crea el proyecto base de Laravel utilizando Composer o el instalador de Laravel.

### 2. Editar Variables de Entorno

Se configuran las variables de entorno en el archivo `.env` para establecer la conexión con la base de datos:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=nombre_bd
DB_USERNAME=usuario
DB_PASSWORD=contraseña
```

### 3. Crear la Base de Datos en phpMyAdmin

Se crea la base de datos correspondiente desde el panel de **phpMyAdmin** antes de ejecutar las migraciones.

### 4. Asignar Illuminate y Schema para evitar errores de longitud de cadena

Se configura el `AppServiceProvider` para evitar errores relacionados con la longitud de cadenas en versiones antiguas de MySQL:

```php
use Illuminate\Support\Facades\Schema;

public function boot()
{
    Schema::defaultStringLength(191);
}
```

### 5. Creación del modelo Products, creación de datos y migración

Se genera el modelo `Product` junto con su migración y se definen los campos de la tabla:

```bash
php artisan make:model Product -m
```

### 6. Migración de vistas y tablas a la Base de Datos

Se ejecutan las migraciones para crear las tablas en la base de datos:

```bash
php artisan migrate
```

### 7. Generación del paquete Ibex (contiene el paquete CRUD)

Se instala el paquete **Ibex CRUD** a través de Composer:

```bash
composer require ibex/crud-generator --dev
```

### 8. Publicación de archivos con el tag `crud`

Se publican los archivos de configuración del paquete:

```bash
php artisan vendor:publish --tag=crud
```

### 9. Creación de archivos para gestionar la pestaña Products

Se genera el CRUD completo para el modelo `Product`:

```bash
php artisan make:crud products
```

### 10. Copiado de la ruta generada en `web.php`

Se agrega la ruta generada por el paquete en el archivo de rutas `routes/web.php`:

```php
Route::resource('products', ProductController::class);
```

### 11. Uso de `composer dump-autoload`

Se recarga el autoloader de Composer para reconocer las nuevas clases generadas:

```bash
composer dump-autoload
```

### 12. Limpieza de caché e inicio del proyecto

Se limpia la caché de la aplicación y se levanta el servidor de desarrollo:

```bash
php artisan cache:clear
php artisan config:clear
php artisan serve
```

---

## ✅ Registro de Pruebas

Una vez completados los pasos anteriores, se realizaron las siguientes pruebas:

- **Página de productos:** Se verificó que la vista principal del módulo de productos carga correctamente.
- **Registro de productos de prueba:** Se insertaron registros de prueba a través del formulario generado por el CRUD.
- **Verificación en la BD:** Se confirmó que los registros insertados se reflejan correctamente en la base de datos a través de phpMyAdmin.

---

## 🛠️ Tecnologías Utilizadas

| Tecnología | Descripción |
|------------|-------------|
| Laravel | Framework PHP para el desarrollo web |
| PHP | Lenguaje de programación backend |
| MySQL | Motor de base de datos relacional |
| phpMyAdmin | Interfaz gráfica para gestión de la BD |
| Ibex CRUD | Paquete para generación automática de CRUDs |
| Composer | Gestor de dependencias de PHP |

---

## 👤 Información del Estudiante

| Campo | Información |
|-------|-------------|
| Nombre | Luis Jiménez |
| Correo | [luis.jimenez6@utp.ac.pa](mailto:luis.jimenez6@utp.ac.pa) |
| Curso | Desarrollo de Software 7 |
| Fecha de Ejecución del Laboratorio | 13-04-26 |
| Instructor del Laboratorio | Irina Fong |
