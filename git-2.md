
## Comandos de Git

1. `git status`: Ver el estado del repositorio.
2. `git config --global user.name "nombreUsuario"`: Configurar el nombre de usuario.
3. `git config --global user.email "tucorreo@gmail.com"`: Configurar el correo electrónico.
4. `git config --list`: Listar la configuración de Git.
5. `git init`: Inicializar un repositorio.
6. `git add index.html`: Añadir un archivo al área de preparación.
7. `git add .`: Añadir todos los archivos al área de preparación.
8. `git rm --cached index.html`: Retirar un archivo del área de preparación.
9. `git commit -m "comentario"`: Realizar un commit con un comentario.
10. `git log --oneline`: Ver la estructura de comentarios y ramas.
11. `git branch -m main`: Cambiar el nombre de la rama principal.
12. `git branch -m nombreRama nombreNuevo`: Cambiar el nombre de una rama.
13. `git checkout numeroComentario`: Ir a un comentario específico.
14. `git checkout nombreRama`: Cambiar a una rama específica.
15. `git reset --soft HEAD~`: Regresar al último commit sin perder cambios.
16. `git remote add origin https://github.com/{usuario}/{repo}.git`: Agregar un repositorio remoto.
17. `git remote set-url origin git@github.com:adrianedutecno/iguanapage.git`: Cambiar la URL de un repositorio remoto.
18. `git remote rename nombreActual nombreNuevo`: Renombrar un repositorio remoto.
19. `git remote -v`: Visualizar repositorios remotos.
20. `git remote show`: Visualizar información sobre un repositorio remoto.
21. `git config --global init.defaultBranch nombreRama`: Configurar la rama por defecto.
22. `git remote rm nombreRepositorio`: Eliminar un repositorio remoto.
23. `git branch`: Ver en qué rama estamos ubicados.
24. `git branch nombreRama`: Crear una nueva rama.
25. `git merge nombreRamaDatosNuevos`: Realizar un merge o unión de datos entre ramas.
26. `git checkout -b nombreRama`: Crear y cambiar a una nueva rama.

## Comandos de Git para Llaves SSH y GitHub

1. `ls -la ~/.ssh`: Verificar si existe una llave SSH en tu PC.
2. `ssh-keygen -t rsa -b 4096 -C "tucorre@gmail.com"`: Crear una llave SSH.
3. `eval "$(ssh-agent -s)"`: Activar el agente SSH.
4. `ssh-add ~/.ssh/id_rsa`: Añadir una clave privada al agente.
5. `cat ~/.ssh/id_rsa.pub`: Leer la llave pública dentro de la terminal.
6. Ir a GitHub, luego a "Settings" > "SSH and GPG keys" para agregar la llave.

## Comandos de Terminal (Unix/Linux)

1. `pwd`: Mostrar el directorio actual.
2. `cd /directorio`: Cambiar al directorio especificado.
3. `cd ..`: Ir al directorio padre.
4. `ls -la`: Listar carpetas, permisos y archivos ocultos.
5. `ls`: Listar carpetas y archivos.
6. `mkdir nombreCarpeta`: Crear una nueva carpeta o directorio.
7. `touch index.html`: Crear un archivo con una extensión.
8. `cp nombreArchivo carpeta/nombreArchivoCopia`: Copiar un archivo a otra carpeta.
9. `rm index.html`: Eliminar un archivo.
10. `mv index.html carpetaDestino/`: Mover un archivo a otra carpeta.
11. `rm -rf nombreDirectorio`: Eliminar una carpeta y su contenido.
12. `mv nombreArchivoActual nombreArchivoNuevo`: Cambiar el nombre de un archivo.

