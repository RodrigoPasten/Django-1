
## PostgreSQL 8.3 PSQL Cheat Sheet

- PSQL Cheat Sheet: [PostgreSQL 8.3 PSQL Cheat Sheet](http://www.postgresonline.com/special_feature.php?sf_name=postgresql83_psql_cheatsheet)

### Modificar Variables de Entorno

Agrega las siguientes rutas para que la terminal reconozca los comandos `psql`:

```plaintext
C:\Program Files\PostgreSQL\15\bin
C:\Program Files\PostgreSQL\15\lib
```

### Comandos Más Usados

- `PASSWORD`: Asigna una contraseña al usuario creado.
- `ENCRYPTED PASSWORD`: Asigna una contraseña encriptada al usuario creado.
- `UNENCRYPTED PASSWORD`: Asigna una contraseña no encriptada al usuario creado.
- `VALID UNTIL`: La cuenta expirará en la fecha indicada.
- `CREATEDB`: Permite al usuario crear bases de datos.
- `NOCREATEDB`: No permite al usuario crear bases de datos.
- `SUPERUSER`: Puede crear otros usuarios (veremos esto más adelante).
- `NOSUPERUSER`: No puede crear otros usuarios.

### Permisos para los Usuarios

Una vez creados los usuarios, se pueden cambiar los permisos con los siguientes comandos:

- Para dar acceso a todos los privilegios de una base de datos: `GRANT ALL PRIVILEGES ON DATABASE database_name TO nombre_usuario;`
- Quitar privilegios de una base de datos: `REVOKE ALL PRIVILEGES ON DATABASE database_name FROM nombre_usuario;`
- Para dar permiso de creación de una base de datos se usa: `ALTER USER nombre_usuario CREATEDB;`
- Para transformar al usuario en superusuario: `ALTER USER myuser WITH SUPERUSER;`
- Remover el superusuario: `ALTER USER username WITH NOSUPERUSER;`

### Tipos de Datos Más Comunes

#### Enteros:

- `SMALLINT`: Entero de 2 bytes (rango: -32,768 a 32,767)
- `INTEGER`: Entero de 4 bytes (rango: -2,147,483,648 a 2,147,483,647)
- `BIGINT`: Entero de 8 bytes (rango: -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807)
- `SERIAL`: Tipo especial para columna de identidad autoincremental.

#### Números de Punto Flotante:

- `REAL`: Punto flotante de 4 bytes.
- `DOUBLE PRECISION`: Punto flotante de 8 bytes.
- `NUMERIC(p, s)`: Decimal con precisión arbitraria (p) y escala (s).

#### Texto y Caracteres:

- `CHAR(n)`: Cadena de caracteres de longitud fija.
- `VARCHAR(n)`: Cadena de caracteres de longitud variable con límite máximo (n).
- `TEXT`: Cadena de caracteres de longitud variable sin límite máximo.

#### Booleanos:

- `BOOLEAN`: Valor booleano (true o false).

#### Fecha y Hora:

- `DATE`: Fecha (formato: "YYYY-MM-DD").
- `TIME`: Hora sin zona horaria (formato: "HH:MI:SS").
- `TIMESTAMP`: Fecha y hora con zona horaria (formato: "YYYY-MM-DD HH:MI:SS").
- `INTERVAL`: Intervalo de tiempo.

#### Otros Tipos de Datos:

- `UUID`: Identificador único universal.
- `JSON` / `JSONB`: Almacena objetos JSON.
- `ARRAY`: Matriz de valores de un tipo de datos específico.

... (y más tipos de datos y comandos)

