
## Conexión de PostgreSQL con Django

Para conectar PostgreSQL con Django, puedes cambiar el motor de la base de datos en el archivo `settings.py` de tu proyecto. Aquí tienes un ejemplo de cómo configurarlo:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'adl-test',
        'USER': 'postgres',
        'PASSWORD': '12345',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```

Después de configurar el motor de base de datos, instala el conector PostgreSQL utilizando el siguiente comando en tu terminal con el entorno virtual activo:

```bash
pip install psycopg2
```

## Normalización y Formas Normales

### Primera Forma Normal (1FN)

La 1FN establece que cada columna de una tabla debe contener un solo valor y no debe haber duplicación de datos.

### Segunda Forma Normal (2FN)

La 2FN establece que una tabla debe cumplir con la 1FN y que cada columna no clave (ni pk, ni fk) debe depender completamente de la clave primaria.

### Tercera Forma Normal (3FN)

La 3FN establece que una tabla debe cumplir con la 2FN y que no debe haber dependencias transitivas.

## Transacciones en PostgreSQL

Las transacciones en PostgreSQL garantizan la integridad y consistencia de la base de datos mediante propiedades ACID:

- Atomicidad
- Consistencia
- Aislamiento
- Durabilidad

## DCL (Data Control Language)

El DCL se utiliza en PostgreSQL para controlar los permisos y privilegios en la base de datos:

- `GRANT`: Concede privilegios a los usuarios o roles sobre objetos de la base de datos.
- `REVOKE`: Revoca los privilegios previamente otorgados a los usuarios o roles sobre objetos de la base de datos.

## TCL (Transaction Control Language)

El TCL se utiliza en PostgreSQL para controlar las transacciones y los cambios en la base de datos:

- `BEGIN`: Inicia una transacción explícitamente.
- `COMMIT`: Confirma una transacción, guardando los cambios realizados.
- `ROLLBACK`: Deshace una transacción, revirtiendo los cambios realizados.
- `SAVEPOINT`: Establece un punto de guardado dentro de una transacción.
- `RELEASE SAVEPOINT`: Elimina un punto de guardado previamente establecido.
- `ROLLBACK TO SAVEPOINT`: Deshace los cambios realizados después de un punto de guardado específico.

## Operaciones JOIN en PostgreSQL

- `INNER JOIN`: Combina filas de dos o más tablas en función de una condición de coincidencia.
- `LEFT JOIN`: Combina filas de la tabla izquierda con las filas coincidentes de la tabla derecha.
- `RIGHT JOIN`: Combina filas de la tabla derecha con las filas coincidentes de la tabla izquierda.
- `FULL JOIN`: Combina todas las filas de ambas tablas, incluyendo las filas sin coincidencias.

## Tipos de Datos en PostgreSQL

- `INT`: Números enteros de 4 bytes que pueden tomar valor desde -2147483648 hasta +2147483647.
- `SMALLINT`: Números enteros de 2 bytes que pueden tomar valor desde -32768 hasta +32767.
- `BIGINT`: Números enteros de 8 bytes que pueden tomar valor desde -9223372036854775808 hasta 9223372036854775807.
- `FLOAT`: Números decimales de 32 bits de precisión.
- `DOUBLE`: Números decimales de 64 bits de precisión con hasta 15 dígitos decimales.
- `CHAR`: Cadena de hasta 255 caracteres de longitud fija.
- `VARCHAR`: Cadena de hasta 65535 caracteres de longitud variable.
- `DATE`: Almacena fecha en formato aaaa-mm-dd.
- `TIME`: Almacena el tiempo desde 00:00:00 hasta 24:00:00.
- `TIMESTAMP`: Almacena fecha y hora en formato yyyy-mm-dd hh:mm:ss.
- `BOOLEAN`: Tiene valores posibles como Verdadero, Falso o NULL.

