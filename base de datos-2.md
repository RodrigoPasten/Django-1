
## Comandos PostgreSQL

- `\c nombre_base`: Conectarse a una base de datos específica.
- `\l`: Listar todas las bases de datos existentes.
- `\?`: Mostrar ayuda.
- `\du`: Listar todos los usuarios en el motor.
- `\dt`: Listar todas las relaciones (o tablas) existentes en una base de datos específica.
- `\q`: Salir de la consola de PostgreSQL.
- `\!`: Obtener información del sistema y salir sin cerrar la shell de psql.
- `\h`: Mostrar la lista de comandos disponibles.
- `\conninfo`: Mostrar detalles del usuario conectado.

### Usuarios

- Crear un usuario: `CREATE USER nombre_usuario WITH PASSWORD passworrd_asignado;`
- Eliminar usuarios: `DROP USER nombre_usuario;`
- Ver los usuarios existentes en la base de datos: `\du`
- Cambiar contraseña de usuario: `\password "nombre de usuario"`
- Usuarios que tienen acceso a la base de datos: `SELECT nombre_usuario FROM pg_user;`
- Limitar a un usuario: `CREATE USER nombre_usuario WITH comando_opcional;`

### Conexiones

- Conectarse desde cualquier consola a una base de datos: `psql -U username -W -d database_name`

### Administración de la Base de Datos

- Iniciar la base de datos cambiando de usuario: `sudo su -l postgres`
- Entrar a la base de datos mediante la terminal: `psql`
- Crear base de datos: `CREATE DATABASE nombre;`
- Crear título de base de datos: `\C POST`
- Crear tablas: `CREATE TABLE POST ();`
- Ver tabla creada: `SELECT * FROM post;`
- Modificar tabla, agregando una columna: `ALTER TABLE "nombre base de datos" ADD "nombre nuevo atributo" "Tipo de datos";`
- Agregar datos a columna creada: `UPDATE "nombre base de datos" SET "nombre columna creada" = 'dato' WHERE "especificar identificador como id=1";`
- Eliminar usuario: `DELETE FROM "nombre base" WHERE "especificar identificador como id=1";`
- Eliminar base de datos: `DROP DATABASE "nombre";`
- Vincular 2 tablas de una base de datos: `CREATE TABLE "nombre tabla" (id_comentario SERIAL, id_post INT, fecha_creacion TIMESTAMP, contenido VARCHAR(255), FOREIGN KEY(id_post) REFERENCES post(id));`


## Manipulación de Datos y Administración en PostgreSQL

### Creación de Tablas

```sql
-- Creación de una tabla
CREATE TABLE nombre_tabla (columnas);

-- Ver la estructura de la tabla
SELECT * FROM nombre_tabla;
```

### Inserción de Datos en una Tabla

```sql
-- Inserción de datos
INSERT INTO nombre_tabla (columna1, columna2, columna3) VALUES (valor1, valor2, valor3);
```

### Actualización de Registros

```sql
-- Actualización de registros
UPDATE nombre_tabla SET columna1 = valor_nuevo WHERE condicion;
```

### Eliminación de Registros

```sql
-- Eliminar toda la tabla
DELETE FROM tabla;

-- Seleccionar qué registros queremos borrar
DELETE FROM tabla WHERE condicion;
```

### Restricciones

- `NOT NULL`: La columna no puede tener valores NULL.
- `UNIQUE`: Todos los valores de la columna deben ser diferentes entre sí.
- `SERIAL`: Restringe el valor numérico para que sea autoincremental.
- `PRIMARY KEY`: Define la clave primaria.
- `FOREIGN KEY`: Enlaza dos tablas, normalmente referente a una clave primaria.
- `CHECK`: Todos los valores de una columna deben satisfacer una condición específica.
- `DEFAULT`: Asigna un valor por defecto a los registros sin valor asignado.
- `INDEX`: Crea y recupera datos de forma rápida.

### Transacciones

```sql
-- Inicio de una transacción
BEGIN o START;

-- Guardar los cambios de la transacción
COMMIT;

-- Revertir los cambios realizados
ROLLBACK;

-- Guardar el punto de partida para aplicar ROLLBACK
SAVEPOINT;

-- Asignar nombre a la transacción
SET TRANSACTION;

-- Desactivar AUTOCOMMIT
\set AUTOCOMMIT off;

-- Comprobar si AUTOCOMMIT está activado
\echo :AUTOCOMMIT;
```

### Exportación y Restauración

```bash
# Exportar una base de datos
pg_dump -U nombre_usuario nombre_db > db.sql

# Exportar todas las bases de datos
sudo su - postgres
pg_dumpall > /directorio/dumpall.sql

# Restaurar una base de datos
sudo su - postgres
psql -U postgres nombredb < archivo_restauracion.sql

# Restaurar todas las bases de datos
sudo su - postgres
psql -f /var/lib/pgsql/backups/dumpall.sql mydb
```

