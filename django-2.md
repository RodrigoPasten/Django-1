
## Configuración de Proyecto Django con PostgreSQL

### Instalación de PostgreSQL y pgAdmin

1. Instala PostgreSQL como base de datos.

2. Instala pgAdmin como gestor de base de datos.

### Creación y Configuración de Base de Datos

1. Crea una base de datos en PostgreSQL:

   ```sql
   CREATE DATABASE db_practica_orm;
   ```

2. Crea un usuario y contraseña:

   ```sql
   CREATE USER user_db WITH PASSWORD 'user_db';
   ```

3. Asigna permisos al usuario:

   ```sql
   GRANT ALL PRIVILEGES ON DATABASE db_practica_orm TO postgres;
   GRANT ALL PRIVILEGES ON DATABASE db_practica_orm TO user_db;
   ```


### Configuración de la Base de Datos

1. Instala el conector para PostgreSQL:

   ```bash
   pip install psycopg2
   ```

2. En `config/settings.py`, agrega la configuración de la base de datos:

   ```python
   DATABASES = {
       'default': {
           'ENGINE': 'django.db.backends.postgresql',
           'NAME': 'db_practica_orm',
           'USER': 'postgres',
           'PASSWORD': 'admin',
           'HOST': '127.0.0.1',
           'PORT': '5432',
       }
   }
   ```

### Creación de Modelos y Migraciones

1. Crea los modelos para la aplicación.

2. Genera los archivos de migración:

   ```bash
   python manage.py makemigrations
   ```

3. Aplica las migraciones:

   ```bash
   python manage.py migrate
   ```

### Creación de Vistas y Plantillas

1. Crea las vistas para listar y agregar productos en `producto/views.py`.

2. Crea una carpeta `templates` dentro de la aplicación `producto`.

3. Crea archivos HTML para listar, agregar, editar y eliminar productos.

### Creación de Formularios

1. Crea un archivo `forms.py` en la aplicación `producto`.

2. Define los formularios necesarios en `forms.py`.

### Configuración de URLs

1. Crea un archivo `urls.py` en la aplicación `producto`.

2. Define las URLs y asócialas a las vistas correspondientes.

### Comandos Adicionales

- `python manage.py shell`: Inicia una sesión interactiva de Django shell.
- `python manage.py dbshell`: Accede a la consola interactiva de la base de datos.
- `python manage.py showmigrations`: Muestra el estado de las migraciones.
- `python manage.py dumpdata`: Exporta los datos de la base de datos.
- `python manage.py test`: Ejecuta pruebas unitarias en tu proyecto.

