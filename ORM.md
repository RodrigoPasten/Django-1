## Uso del ORM de Django en Markdown

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

1. Crea migraciones para aplicar los cambios al esquema de la base de datos: `python manage.py makemigrations`
2. Aplica las migraciones: `python manage.py migrate`

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
