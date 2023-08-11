
## Paso a Paso: Proyecto Django - Creación de un Sistema de Laboratorios

### 1. Crear la Base de Datos

1.1 Abrir PG Admin
   - Acceder con el usuario y contraseña de administrador.
   - Crear un nuevo usuario: 
     ```sql
     CREATE USER userdjango WITH PASSWORD 'userdjango';
     ```
   - Crear una nueva base de datos llamada 'practica_final_orm_django', asignando el usuario 'userdjango'.

1.2 Configuración del Proyecto en PyCharm

1.2.1 Crear un nuevo proyecto Django
   - Ubicación: C:\PycharmProjects\practica_final_orm_django
   - Entorno virtual: Virtualenv, Python 3.11
   - Nombre de la aplicación: laboratorio

1.2.2 Instalar paquetes requeridos
   - Django (framework)
   - psycopg2 (conector de PostgreSQL)

1.2.3 Inicializar el proyecto y la aplicación
   ```bash
   cd C:\PycharmProjects\practica_final_orm_django
   django-admin startproject config
   cd config
   django-admin startapp laboratorio
   ```

1.2.4 Registrar la aplicación en `settings.py`
   ```python
   INSTALLED_APPS = [
       ...
       'laboratorio.apps.LaboratorioConfig',
   ]
   ```

1.2.5 Configurar la base de datos en `settings.py`
   ```python
   DATABASES = {
       "default": {
           "ENGINE": "django.db.backends.postgresql",
           "NAME": "practica_final_orm_django",
           "USER": "userdjango",
           "PASSWORD": "userdjango",
           "HOST": "127.0.0.1",
           "PORT": "5432",
       }
   }
   ```

1.2.6 Realizar migraciones y crear el superusuario
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   python manage.py createsuperuser
   ```

1.3 Ejecutar el proyecto
   ```bash
   python manage.py runserver
   ```

### 2. Crear el Modelo

2.1 Crear los modelos en `models.py` (Ejemplo)

```python
from datetime import date
from django.core.validators import MinValueValidator
from django.db import models

class Laboratorio(models.Model):
    nombre = models.CharField(max_length=20)

    def __str__(self):
        return self.nombre

class DirectorGeneral(models.Model):
    nombre = models.CharField(max_length=200)
    laboratorio = models.OneToOneField(Laboratorio, on_delete=models.CASCADE)

    def __str__(self):
        return self.nombre

class Producto(models.Model):
    nombre = models.CharField(max_length=40)
    laboratorio = models.ForeignKey(Laboratorio, on_delete=models.CASCADE)
    f_fabricacion = models.DateField(validators=[MinValueValidator(limit_value=date(2015, 1, 1))])
    p_costo = models.DecimalField(max_digits=10, decimal_places=2)
    p_venta = models.DecimalField(max_digits=10, decimal_places=2)

    def __str__(self):
        return self.nombre
```

2.2 Realizar migraciones y actualizar la base de datos

```bash
python manage.py makemigrations
python manage.py migrate
```

2.3 Registrar los modelos en `admin.py`

```python
from django.contrib import admin

class LaboratorioAdmin(admin.ModelAdmin):
    list_display = ('id', 'nombre')

class DirectorGeneralAdmin(admin.ModelAdmin):
    list_display = ('id', 'nombre', 'laboratorio')

class ProductoAdmin(admin.ModelAdmin):
    list_display = ('id', 'nombre', 'format_date', 'p_costo', 'p_venta')

    def format_date(self, obj):
        return obj.f_fabricacion.strftime('%Y')

    format_date.short_description = 'F FABRICACION'

admin.site.register(Laboratorio, LaboratorioAdmin)
admin.site.register(DirectorGeneral, DirectorGeneralAdmin)
admin.site.register(Producto, ProductoAdmin)
```

2.4 Realizar migraciones y ejecutar el servidor

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```

2.5 Acceder al sitio de administración de Django

   - Abrir la URL: http://127.0.0.1:8000/admin
   - Iniciar sesión con el usuario y contraseña del superusuario

2.6 Añadir usuarios, laboratorios y productos a través del Admin
   - Realizar los cambios y guardarlos

### 3. Realizar Consultas

3.1 Ingresar a la Shell de Python

```bash
python manage.py shell
```

3.2 Importar Modelos

```python
from laboratorio.models import Laboratorio, DirectorGeneral, Producto
```

3.3 Realizar Consultas (Ejemplo)

```python
laboratorios = Laboratorio.objects.all()
print('\n'.join(str(lab.nombre) for lab in laboratorios))
```

### 4. Realizar Cambios al Modelo

4.1 Guardar una nueva migración con un alias específico

```bash
python manage.py makemigrations --name actualizado_campos
python manage.py migrate
```

4.2 Consultar las migraciones existentes

```bash
python manage.py showmigrations
```

### 5. CRUD (Create, Read, Update, Delete)

5.1 Crear carpetas de plantillas
   - Crear la carpeta `templates` en el directorio de la aplicación

5.2 Configurar URLs

En `config/urls.py`:

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('laboratorio/', include('laboratorio.urls')),
    path('', include('laboratorio.urls'))
]
```

5.3 Crear archivos `laboratorio/urls.py` y `laboratorio/views.py`

5.4 Crear controladores en `views.py` para las vistas del CRUD

```python
from django.shortcuts import render
from .models import Laboratorio

# Controladores-vistas para CRUD
def listar_labs(request):
    laboratorios = Laboratorio.objects.all()
    return render(request, 'listar.html', {'laboratorios': laboratorios})
```

---

