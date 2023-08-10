## Uso del ORM de Django
El ORM (Object-Relational Mapping) de Django te permite interactuar con bases de datos relacionales utilizando objetos Python en lugar de SQL directo. A continuación, te mostraré cómo usar el ORM de Django en un entorno de GitHub con formato Markdown:

### Definir un Modelo

1. Crea una aplicación de Django: `python manage.py startapp nombre_app`
2. Define tu modelo en el archivo `models.py` dentro de tu aplicación:

```python
from django.db import models

class Producto(models.Model):
    nombre = models.CharField(max_length=100)
    precio = models.DecimalField(max_digits=10, decimal_places=2)
    categoria = models.ForeignKey('Categoria', on_delete=models.CASCADE)

class Categoria(models.Model):
    nombre = models.CharField(max_length=50)
```

### Migraciones

---

## Ejecutar el comando `makemigrations` en Django

El comando `makemigrations` en Django se utiliza para generar archivos de migración basados en los cambios detectados en los modelos de la aplicación. Estos archivos de migración son esenciales para aplicar cambios en la estructura de la base de datos.

### Sintaxis

```
python manage.py makemigrations [app_label [app_label ...]] [--name NAME]
```

### Parámetros

- `app_label`: (Opcional) Especifica el nombre de una o más aplicaciones para las cuales se generarán las migraciones. Si no se proporciona, se generarán migraciones para todas las aplicaciones en el proyecto.

- `--name NAME`: (Opcional) Permite especificar un nombre personalizado para el archivo de migración que se va a generar.

### Ejemplo

Supongamos que hemos realizado cambios en los modelos de la aplicación `blog` y deseamos generar las migraciones correspondientes:

```
python manage.py makemigrations blog
```

Este comando buscará los cambios en los modelos de la aplicación `blog` y generará archivos de migración en la carpeta `migrations` de dicha aplicación.

Si deseamos generar migraciones para todas las aplicaciones del proyecto, simplemente ejecutamos el comando sin proporcionar ninguna aplicación:

```
python manage.py makemigrations
```

### Crear Migraciones Iniciales

Si tienes modelos y tablas en tu base de datos pero aún no tienes migraciones, puedes crear migraciones iniciales para todas las aplicaciones del proyecto utilizando:

```
python manage.py makemigrations --name initial
```

### Opciones Adicionales para el Comando `makemigrations`

### `--dry-run`

El flag `--dry-run` permite realizar una simulación del proceso de generación de migraciones sin efectuar realmente ningún cambio en los archivos de migración. Esto puede ser útil para verificar los cambios propuestos antes de aplicarlos.

Ejemplo:

```bash
python manage.py makemigrations --dry-run
```

### `--empty`

La opción `--empty` se utiliza para crear una migración vacía. Esto puede ser útil en casos donde se desea registrar manualmente algún cambio en la base de datos que no está relacionado con los modelos.

Ejemplo:

```bash
python manage.py makemigrations app_label --empty
```

## Crear Migraciones para Aplicaciones con Múltiples Bases de Datos

Si tienes una aplicación que utiliza múltiples bases de datos, puedes especificar para qué base de datos deseas generar las migraciones utilizando la opción `--database`.

Ejemplo:

```bash
python manage.py makemigrations app_label --database=db_name
```

## Convertir Modelos en Migraciones

Si tienes modelos definidos en tus aplicaciones pero aún no tienes migraciones, puedes convertir los modelos existentes en archivos de migración utilizando `makemigrations` con el flag `--name`.

Ejemplo:

```bash
python manage.py makemigrations app_label --name=initial
```

Este comando generará migraciones iniciales para los modelos en la aplicación especificada.

## `migrate`: Aplicar Migraciones a la Base de Datos

El comando `migrate` en Django se utiliza para aplicar las migraciones a la base de datos, llevando a cabo los cambios definidos en los modelos en la estructura de la base de datos.

### Uso Básico

El uso más básico del comando `migrate` es simplemente ejecutarlo sin argumentos. Esto aplicará todas las migraciones pendientes en todas las aplicaciones registradas en tu proyecto.

Ejemplo:

```bash
python manage.py migrate
```

### Aplicar Migraciones de una Aplicación Específica

Si solo deseas aplicar las migraciones de una aplicación en particular, puedes especificar la aplicación como argumento.

Ejemplo:

```bash
python manage.py migrate app_label
```

### Aplicar Migraciones de una Versión Específica

Si deseas aplicar migraciones hasta una versión específica, puedes usar la notación `<app_label> <migration_name>`.

Ejemplo:

```bash
python manage.py migrate app_label migration_name
```

### Aplicar Migraciones en una Base de Datos Específica

Si tu proyecto utiliza múltiples bases de datos, puedes especificar en qué base de datos deseas aplicar las migraciones utilizando la opción `--database`.

Ejemplo:

```bash
python manage.py migrate --database=db_name
```

### Estado de las Migraciones

Para verificar el estado de las migraciones, puedes usar:

```bash
python manage.py showmigrations
```

Este comando mostrará un listado de todas las aplicaciones y sus migraciones junto con un indicador del estado (aplicadas o pendientes).

## Revertir Migraciones

### Revertir la Última Migración

Para revertir la última migración aplicada, puedes utilizar:

```bash
python manage.py migrate app_label zero
```

Esto revierte la última migración aplicada en la aplicación especificada, dejando la base de datos en su estado inicial.

### Revertir Todas las Migraciones de una Aplicación

Si deseas deshacer todas las migraciones de una aplicación y volver a un estado vacío, puedes usar:

```bash
python manage.py migrate app_label zero
```



### Crear, Actualizar y Eliminar Registros

```python
# Crear un registro
producto = Producto(nombre="Producto 1", precio=29.99, categoria=categoria_objeto)
producto.save()

# Actualizar un registro
producto = Producto.objects.get(pk=1)
producto.nombre = "Nuevo Nombre"
producto.save()

# Eliminar un registro
producto = Producto.objects.get(pk=1)
producto.delete()
```

### Consultas

```python
# Obtener todos los productos
productos = Producto.objects.all()

# Obtener productos con precio mayor a $20
productos_caros = Producto.objects.filter(precio__gt=20)

# Obtener un producto por su nombre
producto = Producto.objects.get(nombre="Producto 1")

# Conteo de productos por categoría
conteo_por_categoria = Producto.objects.values('categoria__nombre').annotate(conteo=models.Count('categoria'))

# Consulta usando JOIN (relaciones)
productos_categoria = Producto.objects.filter(categoria__nombre="Electrónicos")
```

### Consultas Avanzadas

```python
# Consulta con OR y AND
from django.db.models import Q

productos_filtrados = Producto.objects.filter(Q(precio__gt=10) | Q(categoria__nombre="Ropa"))

# Consulta con JOIN y condiciones complejas
productos_interesantes = Producto.objects.filter(Q(precio__lt=50) & Q(categoria__nombre="Electrónicos"))
```

### Relaciones

- ForeignKey: Para relaciones uno a muchos.
- OneToOneField: Para relaciones uno a uno.
- ManyToManyField: Para relaciones muchos a muchos.

```python
class Orden(models.Model):
    cliente = models.ForeignKey('Cliente', on_delete=models.CASCADE)
    productos = models.ManyToManyField(Producto)

class Cliente(models.Model):
    nombre = models.CharField(max_length=100)
```

Estos son solo ejemplos básicos del uso del ORM de Django. Puedes consultar la [documentación oficial de Django](https://docs.djangoproject.com/en/3.2/topics/db/queries/) para más detalles y ejemplos avanzados.
