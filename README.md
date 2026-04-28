# CRUD con Laravel

> **Universidad Tecnológica de Panamá**  
> Facultad de Ingeniería de Sistemas Computacionales

---

## Descripción

Laboratorio de implementación de un CRUD (Create, Read, Update, Delete) utilizando el framework **Laravel** con base de datos relacional gestionada a través de **phpMyAdmin**, haciendo uso del paquete **Ibex/CRUD** para la generación automática de las vistas y controladores.

---

## 🚀 Pasos de Implementación

### 1. Creación del proyecto

Se crea el proyecto base de Laravel utilizando Composer o el instalador de Laravel.
<img width="572" height="390" alt="image" src="https://github.com/user-attachments/assets/88dd21c4-a8b2-4679-9f2c-dc23f3661316" />

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
<img width="921" height="161" alt="image" src="https://github.com/user-attachments/assets/cc079c23-819e-48f9-a483-9ea729e697a8" />

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
<img width="921" height="151" alt="image" src="https://github.com/user-attachments/assets/f3466236-d6ec-48f7-81c5-1a177267c755" />
<img width="921" height="250" alt="image" src="https://github.com/user-attachments/assets/e20724c6-bb3f-4327-bf8e-f15d8c97d2a3" />

### 6. Migración de vistas y tablas a la Base de Datos

Se ejecutan las migraciones para crear las tablas en la base de datos:

```bash
php artisan migrate
```
<img width="921" height="249" alt="image" src="https://github.com/user-attachments/assets/8c168a18-1b4f-4d4c-9be0-eb6489c33375" />

### 7. Generación del paquete Ibex (contiene el paquete CRUD)

Se instala el paquete **Ibex CRUD** a través de Composer:

```bash
composer require ibex/crud-generator --dev
```
<img width="921" height="179" alt="image" src="https://github.com/user-attachments/assets/21951990-2978-44b6-9715-2d0ebcceaa3a" />

### 8. Publicación de archivos con el tag `crud`

Se publican los archivos de configuración del paquete:

```bash
php artisan vendor:publish --tag=crud
```
<img width="913" height="111" alt="image" src="https://github.com/user-attachments/assets/c180f87e-db3b-4a7d-9783-e7dd06b808ea" />

### 9. Creación de archivos para gestionar la pestaña Products

Se genera el CRUD completo para el modelo `Product`:

```bash
php artisan make:crud products
```
<img width="921" height="155" alt="image" src="https://github.com/user-attachments/assets/58dc77b7-8294-42a2-9472-a7ffc445de0e" />

### 10. Copiado de la ruta generada en `web.php`

Se agrega la ruta generada por el paquete en el archivo de rutas `routes/web.php`:

```php
Route::resource('products', ProductController::class);
```
<img width="921" height="116" alt="image" src="https://github.com/user-attachments/assets/0fca793f-6f1a-4a87-b45d-e09aa45c1d43" />

### 11. Uso de `composer dump-autoload`

Se recarga el autoloader de Composer para reconocer las nuevas clases generadas:

```bash
composer dump-autoload
```
<img width="917" height="169" alt="image" src="https://github.com/user-attachments/assets/3d394c80-c7d8-48bb-ac96-68f81fe9eb4a" />

### 12. Limpieza de caché e inicio del proyecto

Se limpia la caché de la aplicación y se levanta el servidor de desarrollo:

```bash
php artisan cache:clear
php artisan config:clear
php artisan serve
```

---

## Registro de Pruebas

Una vez completados los pasos anteriores, se realizaron las siguientes pruebas:

- **Página de productos:** Se verificó que la vista principal del módulo de productos carga correctamente.
<img width="921" height="224" alt="image" src="https://github.com/user-attachments/assets/7cc00a10-bfda-4103-9e45-5dff19d0a28c" />
- **Registro de productos de prueba:** Se insertaron registros de prueba a través del formulario generado por el CRUD.
<img width="921" height="292" alt="image" src="https://github.com/user-attachments/assets/2ab13348-e893-4123-a766-0881440b0800" />

<img width="921" height="296" alt="image" src="https://github.com/user-attachments/assets/a25c0590-90b2-404c-8857-7d501637eade" />

<img width="921" height="312" alt="image" src="https://github.com/user-attachments/assets/66722cac-5731-48c8-b6de-738ad716987d" />

<img width="921" height="331" alt="image" src="https://github.com/user-attachments/assets/4153bd37-190f-4253-a356-68b085906d56" />

- **Verificación en la BD:** Se confirmó que los registros insertados se reflejan correctamente en la base de datos a través de phpMyAdmin.
<img width="921" height="113" alt="image" src="https://github.com/user-attachments/assets/b5a620a5-901d-48fe-8652-eca2a40600f0" />
---

## Tecnologías Utilizadas

| Tecnología | Descripción |
|------------|-------------|
| Laravel | Framework PHP para el desarrollo web |
| PHP | Lenguaje de programación backend |
| MySQL | Motor de base de datos relacional |
| phpMyAdmin | Interfaz gráfica para gestión de la BD |
| Ibex CRUD | Paquete para generación automática de CRUDs |
| Composer | Gestor de dependencias de PHP |

---

## Información del Estudiante

| Campo | Información |
|-------|-------------|
| Nombre | Luis Jiménez |
| Correo | [luis.jimenez6@utp.ac.pa](mailto:luis.jimenez6@utp.ac.pa) |
| Curso | Desarrollo de Software 7 |
| Fecha de Ejecución del Laboratorio | 24-04-26 |
| Instructor del Laboratorio | Irina Fong |
