
## Entornos Virtuales en Python

Para trabajar con entornos virtuales en Python, puedes seguir estos pasos:

### Instalación de `virtualenv` y `virtualenvwrapper`

1. Verificar la versión de Python: `python -V`
2. Verificar la versión de `pip`: `pip -V`
3. Instalar `virtualenvwrapper`: `pip install virtualenvwrapper`
4. Instalar `virtualenv`: `pip install virtualenv`

### Creación de un Entorno Virtual

- Crear un entorno virtual: `virtualenv nombre_entorno`
  Ejemplo: `virtualenv django_env`

### Activación del Entorno Virtual

- PowerShell:
  - `.\<nombre_entorno>\Scripts\activate.ps1`

- Command Prompt (CMD):
  - `<nombre_entorno>\Scripts\activate.ps1`

- Unix (Linux/Mac):
  - `source <nombre_entorno>/bin/activate`

### Desactivación del Entorno Virtual

- `deactivate`

### Solución para Restricciones de Ejecución en PowerShell

Si encuentras el error sobre las políticas de ejecución en PowerShell, sigue estos pasos:

1. Obtener la política actual de ejecución: `Get-ExecutionPolicy`
2. Desactivar la política de ejecución: `Set-ExecutionPolicy RemoteSigned`

### Uso de `virtualenvwrapper`

- Instalar `virtualenvwrapper`: `pip3 install virtualenvwrapper`
- Configurar variables de entorno (Unix/Linux):
  ```
  export WORKON_HOME=$HOME/.virtualenvs
  export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
  export PROJECT_HOME=$HOME/Devel
  source /usr/local/bin/virtualenvwrapper.sh
  source ~/.bashrc
  ```
- Comandos útiles:
  - `deactivate`: Salir del entorno virtual actual.
  - `workon`: Listar entornos virtuales disponibles.
  - `workon nombre_del_entorno`: Activar un entorno virtual específico.
  - `rmvirtualenv nombre_del_entorno`: Eliminar un entorno virtual.

### Creación de Entorno Virtual embebido en Python - Linux

1. Instalar `virtualenv`: `pip install virtualenv`
2. Crear el ambiente: `python3 -m venv Nombre_Ambiente`
   Ejemplo: `python3 -m venv onlyflans`
3. Activar el ambiente: `source Nombre_Ambiente/bin/activate`
4. Desactivar el ambiente: `deactivate`

