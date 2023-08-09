# Django-1



## Ayuda Memoria para Proyecto en Django

### Instalación y Verificación

1. Instalar Django usando pip:

   ```bash
   pip install django=="número de versión"
   ```

2. Verificar la instalación y versión de Django:

   ```bash
   python -m django version
   ```

3. Consultar los comandos disponibles en Django:

   ```bash
   python -m django help
   ```

### Gestión de Dependencias

- Instalar dependencias desde un archivo:

  ```bash
  pip install -r requirements.txt
  ```

- Generar un respaldo de los paquetes instalados en un archivo `requirements.txt`:

  ```bash
  pip freeze > requirements.txt
  ```

- Instalar una versión específica de un paquete, por ejemplo, instalar astral 2.2:

  ```bash
  pip install astral==2.2
  ```

### Creación de un Proyecto Django

1. Crear un proyecto:

   ```bash
   django-admin startproject "Nombre"
   ```

2. Acceder a la carpeta creada y realizar migraciones iniciales:

   ```bash
   python manage.py migrate
   ```

3. Crear una nueva aplicación dentro del proyecto:

   ```bash
   python manage.py startapp web
   ```

4. Agregar la aplicación a la lista de `INSTALLED_APPS` en `settings.py`:

   ```python
   'web.apps.WebConfig',
   ```

5. Si tienes una base de datos existente, puedes generar un modelo a partir de ella:

   ```bash
   python manage.py inspectdb > web\models.py
   ```

### Creación de Vistas y Plantillas

1. Dentro de la carpeta de la aplicación `web`, crea una carpeta `templates`.

2. Dentro de la carpeta `templates`, crea los archivos `index.html`, `about.html` y `welcome.html`.

3. Crea una vista en `views.py` para cada URL deseada, retornando un `render` con los datos necesarios.

4. Registra las vistas en `urls.py` para que correspondan a las rutas `/`, `/acerca` y `/bienvenido`.

5. Crea una plantilla base `base.html` en la carpeta `web/templates`, definiendo la estructura general del sitio.

6. Modifica tus archivos `index.html`, `about.html` y `welcome.html` para extender la plantilla base y definir el contenido específico:

   ```html
   {% extends 'base.html' %}
   {% block content %}
   <div>
       mensaje
   </div>
   {% endblock %}
   ```

### Integración de Bootstrap y Contenido Estático

1. Agrega los archivos CSS y JavaScript de Bootstrap para estilizar tu sitio.

2. Crea una carpeta `static` dentro de la aplicación `web` para alojar contenido estático como imágenes y videos.

3. Asegúrate de agregar la clase `container` a las plantillas para que Bootstrap funcione correctamente.

4. Ejecuta el servidor de desarrollo:

   ```bash
   python manage.py runserver
   ```

### Otras Operaciones Comunes

- Crear un nuevo proyecto Django:

  ```bash
  python -m django startproject "nombre-proyecto"
  ```

- Acceder a la carpeta del proyecto y crear una nueva aplicación:

  ```bash
  python manage.py startapp "nombre-app"
  ```

- Generar archivos de migración:

  ```bash
  python manage.py makemigrations
  ```

- Aplicar las migraciones:

  ```bash
  python manage.py migrate
  ```

- Crear un superusuario:

  ```bash
  python manage.py createsuperuser
  ```

- Ejecutar el proyecto localmente:

  ```bash
  python manage.py runserver
  ```

### Integración con una Base de Datos Existente

1. Genera modelos a partir de una base de datos existente:

   ```bash
   python manage.py inspectdb > web/models.py
   ```

### Trabajo con Formularios y Plantillas

1. Definición de un formulario `Form`:

   ```python
   from django import forms

   class ContactFormForm(forms.Form):
       customer_email = forms.EmailField(label='Correo')
       customer_name = forms.CharField(max_length=64, label='Nombre')
       message = forms.CharField(label='Mensaje')
   ```

2. Definición de un formulario basado en un modelo `ModelForm`:

   ```python
   from django import forms
   from .models import ContactForm

   class ContactFormModelForm(forms.ModelForm):
       class Meta:
           model = ContactForm
           fields = ['customer_email', 'customer_name', 'message']
   ```

3. Procesamiento de formularios en una vista de `views.py`.

### Manejo de Contenido Estático

- Para usar contenido estático en tus archivos HTML, carga la etiqueta `{% load static %}` al inicio.

- Luego, referencia los archivos estáticos usando la etiqueta `{% static "nombre-del-archivo.extensión" %}`.
