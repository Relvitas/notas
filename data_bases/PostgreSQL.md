# PostgreSQL

**PostgreSQL** (también llamado **Postgres**) es un **sistema de gestión de bases de datos relacional (RDBMS)** de código abierto, conocido por su **potencia, flexibilidad y fiabilidad**.

---

## Archivos de configuración

🔥 Ver la ruta donde estan los archivos de ocnfiguración

```sql
SHOW config_file;
```

> Esto nos mostrara una salida como la siguiente:
> 
> -> C:/Program Files/PostgreSQL/17/data/postgresql.conf
> 
> De este solo eliminamos el nombre del archivo y accedemos directamente a la carpeta, que es la que contiene todos los archivos de configuración.
> 
> -> C:/Program Files/PostgreSQL/17/data/

### Archivos

📍 postgresql.conf

> Es el archivo de configuración principal de PostgreSQL, donde se definen parámetros como la memoria, conexiones y registros.

📍pg_hba.conf

> Es el archivo de configuración de autenticación en PostgreSQL, donde se definen las reglas de acceso para usuarios y redes.

📍pg_ident.conf

> Es el archivo de configuración en PostgreSQL que permite mapear nombres de usuario del sistema operativo a nombres de usuario de la base de datos.

---

## Comandos meta

```sql
📍 Muestra una lista de comandos disponibles.
\?

📍 Lita todas las bases de datos disponibles.
\l 

📍 Conectar a una base de datos
\c nom_base_datos

📍 Listar todas las tablas de las base actual.
\d

📍 Mostrar las caracteristicas de una tabla
\d nom_tabla

📍 Listar todas las tablas y sus caracteristicas
\dt

📍 Ejecuta el último comando ingresado en psql
\g

📍 Limpiar la consola
\! cls -> en windows
\! clear -> en linux/macOS

📍 Mostrar el tiempo de ejecución de una consulta.
\timing

📍 Cerrar la consola
\q

📍 Listar todos los comandos disponibles para sql
\h

📍 Ayuda de un comando en especifico
\h <palabra_reservada>
```

---

## Tipos de Datos en PostgreSQL

Documentación por PostgreSQL [link]([PostgreSQL: Documentation: 11: Chapter 8. Data Types](https://www.postgresql.org/docs/11/datatype.html))

| Tipo de Dato       | Tamaño (bytes) | Valor Mínimo                           | Valor Máximo                           |
| ------------------ | -------------- | -------------------------------------- | -------------------------------------- |
| **Enteros**        |                |                                        |                                        |
| `smallint`         | 2              | -32,768                                | 32,767                                 |
| `integer (int)`    | 4              | -2,147,483,648                         | 2,147,483,647                          |
| `bigint`           | 8              | -9,223,372,036,854,775,808             | 9,223,372,036,854,775,807              |
| **Decimales**      |                |                                        |                                        |
| `decimal`          | Variable       | Dependiendo de la precisión            | Dependiendo de la precisión            |
| `numeric`          | Variable       | Igual que `decimal`                    | Igual que `decimal`                    |
| `real`             | 4              | ~ -3.4 × 10³⁸                          | ~ 3.4 × 10³⁸                           |
| `double precision` | 8              | ~ -1.8 × 10³⁰⁸                         | ~ 1.8 × 10³⁰⁸                          |
| **Caracteres**     |                |                                        |                                        |
| `char(n)`          | Variable       | Cadena de longitud fija                | Cadena de longitud fija                |
| `varchar(n)`       | Variable       | Cadena de longitud variable (límite n) | Cadena de longitud variable (límite n) |
| `text`             | Variable       | Cadena de longitud ilimitada           | Cadena de longitud ilimitada           |
| **Booleano**       |                |                                        |                                        |
| `boolean`          | 1              | `FALSE` (0)                            | `TRUE` (1)                             |
| **Fechas y Horas** |                |                                        |                                        |
| `date`             | 4              | 4713 AC                                | 5874897 DC                             |
| `timestamp`        | 8              | 4713 AC                                | 294276 DC                              |
| `timestamptz`      | 8              | 4713 AC                                | 294276 DC                              |
| `time`             | 8              | 00:00:00                               | 24:00:00                               |
| `timetz`           | 12             | 00:00:00+TZ                            | 24:00:00+TZ                            |
| `interval`         | 16             | -178,000,000 años                      | 178,000,000 años                       |
| **Otros Tipos**    |                |                                        |                                        |
| `bytea`            | Variable       | Datos binarios                         | Datos binarios                         |
| `uuid`             | 16             | 00000000-0000-0000-0000-000000000000   | ffffffff-ffff-ffff-ffff-ffffffffffff   |
| `json`             | Variable       | JSON válido                            | JSON válido                            |
| `jsonb`            | Variable       | JSON binario optimizado                | JSON binario optimizado                |
| `xml`              | Variable       | XML válido                             | XML válido                             |
| `cidr`             | Variable       | Dirección IP                           | Dirección IP                           |
| `inet`             | Variable       | Dirección IP con máscara               | Dirección IP con máscara               |
| `macaddr`          | 6              | Dirección MAC                          | Dirección MAC                          |

---

## Restricciones Especiales en PostgreSQL

| Restricción     | Descripción                                                                                                                                           |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **PRIMARY KEY** | Garantiza que la columna (o combinación de columnas) tenga valores únicos y no nulos. Es la clave primaria de la tabla.                               |
| **UNIQUE**      | Asegura que los valores en una columna (o conjunto de columnas) sean únicos en la tabla. Se pueden tener varias restricciones `UNIQUE`.               |
| **NOT NULL**    | Indica que la columna no puede contener valores `NULL`. Se usa para garantizar que siempre se almacene un valor válido.                               |
| **CHECK**       | Define una condición que los valores deben cumplir antes de insertarse o actualizarse. Ejemplo: `CHECK (edad >= 18)`.                                 |
| **DEFAULT**     | Especifica un valor por defecto si no se proporciona un valor en la inserción. Ejemplo: `fecha TIMESTAMP DEFAULT now()`.                              |
| **FOREIGN KEY** | Define una relación con otra tabla, asegurando la integridad referencial. Se usa con `REFERENCES`.                                                    |
| **SERIAL**      | No es una restricción, sino un tipo especial que define un campo auto-incremental, equivalente a `INTEGER NOT NULL DEFAULT nextval('sequence_name')`. |
| **IDENTITY**    | Alternativa moderna a `SERIAL`. Se define como `GENERATED { ALWAYS                                                                                    |
| **EXCLUSION**   | Permite restricciones más avanzadas que `UNIQUE`, utilizando operadores personalizados para evitar valores duplicados bajo ciertas condiciones.       |

### Explicacion:

📍 `PRIMARY KEY` (Clave primaria)

```sql
CREATE TABLE usuarios (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL
);
```

> El campo `id` será único y no podrá ser `NULL`.

📍 `UNIQUE` (Valor Único)

```sql
CREATE TABLE empleados (
    email VARCHAR(100) UNIQUE
);
```

> El campo `id` será único y no podrá ser `NULL`.

📍 `NOT NULL` (Obligatorio)

```sql
CREATE TABLE clientes (
    nombre VARCHAR(50) NOT NULL
);
```

> El campo `nombre` siempre debe tener un valor.

📍 `CHECK` (Condición personalizada)

```sql
CREATE TABLE productos (
    precio DECIMAL(10,2) CHECK (precio > 0)
);
```

> No se podrán insertar precios negativos.

📍 `DEFAULT` (Valor por defecto)

```sql
CREATE TABLE pedidos (
    fecha TIMESTAMP DEFAULT now()
);
```

> Si no se proporciona una fecha, se usará la actual.

📍 `FOREIGN KEY` (Clave foránea)

```sql
CREATE TABLE ventas (
    cliente_id INT REFERENCES clientes(id)
);
```

> El `cliente_id` debe existir en la tabla `clientes`.

📍 `SERIAL` (Auto-incremento)

```sql
CREATE TABLE facturas (
    id SERIAL PRIMARY KEY
);
```

> `id` se generará automáticamente con un número secuencial.

📍 `IDENTITY` (Nueva alternativa a `SERIAL`)

```sql
CREATE TABLE productos (
    id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY
);
```

> Hace lo mismo que `SERIAL`, pero con mejor control.

📍 `EXCLUSION` (Evitar solapamientos personalizados)

```sql
CREATE TABLE reservas (
    id SERIAL PRIMARY KEY,
    habitacion INT,
    fecha_inicio DATE,
    fecha_fin DATE,
    EXCLUDE USING gist (habitacion WITH =, daterange(fecha_inicio, fecha_fin, '[]') WITH &&)
);
```

> Evita reservas que se solapen en la misma habitación.

---

🔥 Crear Roles

```sql
CREATE ROLE nombre_usuario WITH permiso1 permiso2;
```

> De esta forma creamos un usuario/rol en base de datos.

📍 Tabla de permisos

| **Permiso**     | **Descripción**                                                                                          |
| --------------- | -------------------------------------------------------------------------------------------------------- |
| **SUPERUSER**   | Concede todos los privilegios sin restricciones. Puede administrar cualquier objeto en la base de datos. |
| **CREATEDB**    | Permite crear nuevas bases de datos.                                                                     |
| **CREATEROLE**  | Permite crear, modificar y eliminar roles, pero no asignar permisos superiores a los propios.            |
| **INHERIT**     | Permite heredar permisos de roles a los que pertenece.                                                   |
| **LOGIN**       | Permite que el rol inicie sesión en la base de datos (necesario para usuarios).                          |
| **REPLICATION** | Permite el acceso a la replicación de base de datos (usado en configuraciones de alta disponibilidad).   |
| **BYPASSRLS**   | Permite omitir las políticas de seguridad a nivel de fila (`Row Level Security - RLS`).                  |

📍 Agregar permisos al rol ya existente

```sql
ALTER ROLE nombre_usuario WITH permiso1 permiso2;
```

📍 Asignar contraseña a usuario

```sql
ALTER ROLE nombre_usuario WITH PASSWORD 'contraseña';
```

📍 Eliminar un usuario

```sql
DROP ROLE nombre_usuario;
```

📍 Remover permisos

```sql
ALTER ROLE nombre_usuario NOPERMISO;
```

📍 Listar todos los roles

```sql
\dg
```

📍 Documentación del comando

```sql
\h CREATE ROLE
```

🔥 Asignar privilegios al usuario

```sql
GRANT PRIVILEGIO1, PRIVELEGIO2, ON objeto TO nombre_usuario;
```

> privilegio -> Permiso a otorgar
> 
> objeto -> Puede ser una tabla, esquema, base de datos etc.
> 
> usuario -> Nombre de usuario/rol que recibe los permisos.

📍 Tabla de privilegios

| **Privilegio** | **Descripción**                                                             |
| -------------- | --------------------------------------------------------------------------- |
| **SELECT**     | Permite leer datos de una tabla o vista.                                    |
| **INSERT**     | Permite agregar nuevos registros a una tabla.                               |
| **UPDATE**     | Permite modificar registros existentes en una tabla.                        |
| **DELETE**     | Permite eliminar registros de una tabla.                                    |
| **TRUNCATE**   | Permite eliminar todos los registros de una tabla de forma rápida.          |
| **REFERENCES** | Permite crear claves foráneas que hagan referencia a la tabla.              |
| **TRIGGER**    | Permite crear triggers (disparadores) en una tabla.                         |
| **CREATE**     | Permite crear nuevos objetos dentro de una base de datos o esquema.         |
| **CONNECT**    | Permite a un usuario conectarse a una base de datos.                        |
| **TEMPORARY**  | Permite crear tablas temporales en la base de datos.                        |
| **EXECUTE**    | Permite ejecutar funciones almacenadas.                                     |
| **USAGE**      | Permite acceder a objetos como esquemas, dominios y tipos sin modificarlos. |
| **ALL**        | Otorga todos los privilegios posibles sobre un objeto.                      |

📍 Remover privilegios

```sql
REVOKE privilegio, privilegio ON objeto FROM usuario;
```

---

🔥 Operadores

📍 Aritméticos

| Operador | Descripción                | Ejemplo                |
| -------- | -------------------------- | ---------------------- |
| `+`      | Suma                       | `SELECT 5 + 3;` → `8`  |
| `-`      | Resta                      | `SELECT 10 - 4;` → `6` |
| `*`      | Multiplicación             | `SELECT 6 * 7;` → `42` |
| `/`      | División                   | `SELECT 10 / 2;` → `5` |
| `%`      | Módulo (resto de división) | `SELECT 10 % 3;` → `1` |
| `^`      | Potencia                   | `SELECT 2 ^ 3;` → `8`  |
| `        | /`                         | Raíz cuadrada          |
| `!`      | Factorial                  | `SELECT 5!;` → `120`   |
| `@`      | Valor absoluto             | `SELECT @ -10;` → `10` |

📍 Comparación

| Operador      | Descripción              | Ejemplo                                   |
| ------------- | ------------------------ | ----------------------------------------- |
| `=`           | Igual a                  | `SELECT 10 = 10;` → `TRUE`                |
| `!=` o `<>`   | Diferente de             | `SELECT 10 <> 5;` → `TRUE`                |
| `>`           | Mayor que                | `SELECT 10 > 5;` → `TRUE`                 |
| `<`           | Menor que                | `SELECT 10 < 5;` → `FALSE`                |
| `>=`          | Mayor o igual            | `SELECT 10 >= 10;` → `TRUE`               |
| `<=`          | Menor o igual            | `SELECT 10 <= 5;` → `FALSE`               |
| `BETWEEN`     | Dentro de un rango       | `SELECT 10 BETWEEN 5 AND 15;` → `TRUE`    |
| `IN`          | Dentro de una lista      | `SELECT 'A' IN ('A', 'B', 'C');` → `TRUE` |
| `IS NULL`     | Verifica si es `NULL`    | `SELECT NULL IS NULL;` → `TRUE`           |
| `IS NOT NULL` | Verifica si NO es `NULL` | `SELECT 'Texto' IS NOT NULL;` → `TRUE`    |

📍 Lógicos

| Operador | Descripción                      | Ejemplo                            |
| -------- | -------------------------------- | ---------------------------------- |
| `AND`    | Se cumplen ambas condiciones     | `SELECT TRUE AND FALSE;` → `FALSE` |
| `OR`     | Se cumple al menos una condición | `SELECT TRUE OR FALSE;` → `TRUE`   |
| `NOT`    | Niega una condición              | `SELECT NOT TRUE;` → `FALSE`       |

📍 Texto

| Operador     | Descripción                                   | Ejemplo                                  |
| ------------ | --------------------------------------------- | ---------------------------------------- |
| `\|          | `                                             | Concatenación                            |
| `LIKE`       | Búsqueda con patrón (sensible a mayúsculas)   | `SELECT 'Hola' LIKE 'H%';` → `TRUE`      |
| `ILIKE`      | Búsqueda con patrón (no distingue mayúsculas) | `SELECT 'hola' ILIKE 'H%';` → `TRUE`     |
| `SIMILAR TO` | Comparación con expresiones regulares SQL     | `SELECT 'abc' SIMILAR TO 'a%'`; → `TRUE` |

📍 JSON/JSONB

| Operador | Descripción                      | Ejemplo                                        |
| -------- | -------------------------------- | ---------------------------------------------- |
| `->`     | Obtiene un campo JSON como JSON  | `SELECT '{"a":1}'::json->'a';` → `1`           |
| `->>`    | Obtiene un campo JSON como texto | `SELECT '{"a":1}'::json->>'a';` → `'1'`        |
| `#>`     | Obtiene un valor anidado JSON    | `SELECT '{"a":{"b":2}}'::json#>'{a,b}';` → `2` |

📍 Array

| Operador | Descripción               | Ejemplo                                        |
| -------- | ------------------------- | ---------------------------------------------- |
| `@>`     | Contiene                  | `SELECT '{1,2,3}'::int[] @> '{2}';` → `TRUE`   |
| `<@`     | Está contenido en         | `SELECT '{2}'::int[] <@ '{1,2,3}';` → `TRUE`   |
| `&&`     | Tienen elementos en común | `SELECT '{1,2,3}'::int[] && '{2,4}';` → `TRUE` |

📍 Rango

| Operador | Descripción                     | Ejemplo                                          |
| -------- | ------------------------------- | ------------------------------------------------ |
| `&&`     | Se solapan dos rangos           | `SELECT '[1,5]'::int4range && '[3,7]';` → `TRUE` |
| `@>`     | Un rango contiene otro          | `SELECT '[1,5]'::int4range @> '[2,4]';` → `TRUE` |
| `<@`     | Un rango está contenido en otro | `SELECT '[2,4]'::int4range <@ '[1,5]';` → `TRUE` |

📍 Redes IP

| Operador | Descripción       | Ejemplo                                                       |
| -------- | ----------------- | ------------------------------------------------------------- |
| `>>`     | Contiene          | `SELECT '192.168.1.0/24'::cidr >> '192.168.1.1/32';` → `TRUE` |
| `<<`     | Está contenido en | `SELECT '192.168.1.1/32'::inet << '192.168.1.0/24';` → `TRUE` |

📍 Bit a Bit

| Operador | Descripción                   | Ejemplo                 |
| -------- | ----------------------------- | ----------------------- |
| `&`      | AND bit a bit                 | `SELECT 5 & 3;` → `1`   |
| `\|`     | OR bit a bit                  | `SELECT 5 \| 3;` → `7`  |
| `#`      | XOR bit a bit                 | `SELECT 5 # 3;` → `6`   |
| `~`      | NOT bit a bit                 | `SELECT ~5;` → `-6`     |
| `<<`     | Desplazamiento a la izquierda | `SELECT 5 << 1;` → `10` |
| `>>`     | Desplazamiento a la derecha   | `SELECT 5 >> 1;` → `2`  |

---

## 

## Sintaxis

```plsql
SELECT curso, nombre, FROM alumno WHERE asignatura = "mate"
verbo | nombre_columnas | clausula | nombre_tabla | palabra_resevada | expresion 
```

---

🔥 Conocer la version de postgres instalada

```plsql
SELECT version();
```

---

:fire: **sudo -i -u postgres**

Con este comando accederemos a postgres en usuarios ubuntu dado a que el metodo de autenticacion configurado en pg_hba.conf puede ser md5 o peer. Lo que requerie una contraseña o que el usuario coicida con el de linux.

:fire: **psql**

Ejecutamos a la ves este comando para acceder a postgresql.

---

🔥 Crear una base de datos

```sql
CREATE DATABASE nom_base_datos
```

🔥 Eliminar una base de datos

```sql
DROP DATABASE nom_base_datos
```

---

🔥 Crear una tabla

```sql
CREATE TABLE nombre_tabla(
    nombre_campo tipo_dato [restriccion_especial]
);
```

- Asignar llave primaria
  
  ```sql
  CREATE TABLE nombre_tabla(
      nombre_campo tipo_dato [restriccion_especial],
      CONSTRAINT pk_nombre_llave PRIMARY KEY (campoPK)
  );
  ```
* Asignar llave foranea
  
  ```sql
  CREATE TABLE nombre_tabla(
      nombre_campo tipo_dato [restriccion_especial],
      CONSTRAINT fk_nombre_llave 
      FOREIGN KEY (campoFkDeEstaTabla) 
      REFERENCES nombre_tabla_2(campoPKTabla2)
      ON DELTE accion
      ON UPDATE accion
  );
  ```
  
  Acciones referenciales:
  
  | **Opción**    | **Descripción**                                                                                                                            |
  | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
  | `CASCADE`     | Si el registro padre es eliminado (`ON DELETE`) o actualizado (`ON UPDATE`), los registros hijos se eliminan o actualizan automáticamente. |
  | `SET NULL`    | Si el registro padre es eliminado o actualizado, la clave foránea en la tabla hija se establece en `NULL`.                                 |
  | `SET DEFAULT` | Si el registro padre es eliminado o actualizado, la clave foránea en la tabla hija se establece en su valor por defecto.                   |
  | `RESTRICT`    | Impide la eliminación o actualización si hay registros relacionados en la tabla hija.                                                      |
  
  * Agregar llave foranea a tabla ya creada con campo fk
    
    ```sql
    ALTER TABLE nombre_tabla
    ADD CONSTRAINT fk_nombre_llave
    FOREIGN KEY (campoFKDeTabla)
    REFERENCES nom_tabla_padre(campoPK)
    ON DELETE accion
    ON UPDATE accion;
    ```
  
  * Agregar llave forane sin campo fk existente
    
    ```sql
    ALTER TABLE nombre_tabla
    ADD COLUMN nombre_campo tipo_dato
    ADD CONSTRAINT fk_nombre_llave
    FOREIGN KEY (campoFKDeTabla)
    REFERENCES nom_tabla_padre(campoPK)
    ON DELETE accion
    ON UPDATE accion;
    ```

🔥 Eliminar una tabla

```sql
DROP TABLE nombre_tabla;
```

---

🔥 Insertar datos en una tabla

```sql
INSERT INTO
  pasajero(campo, campo2)
VALUES
  (valor, 'valor');
```

🔥 Eliminar dato de una tabla

```sql
DELETE FROM
  nombre_tabla
WHERE
  nombre_campo = 'valor';
```

🔥 Acutalizar datos en una tabla

```sql
UPDATE
    nombre_tabla
SET
    nombre_campo = 'nuevo_valor',
    nombre_campo = 'nuevo_valor'
WHERE
    < condicion >;
```

---

🔥 Cambiar tipo de dato de un campo

📍 Primer metodo

```sql
ALTER TABLE nombre_tabla ALTER COLUMN nombre_campo TYPE tipodato;
```

> Tener encuenta que el tipo de dato debe estar en el mismo rango, es decir que si es numerico no se puede cambiar a texto.

📍 Segundo metodo

```sql
ALTER TABLE
  nombre_tabla
ALTER COLUMN
  nombre_campo TYPE TIPODATO USING nombre_tabla :: tipo_dato;
```

---

🔥 Agregar un nuevo campo de tabla

```sql
ALTER TABLE
  nombre_tabla
ADD
  COLUMN nombre_campo tipo_dato [restriccione_especial];
```

🔥 Eliminar un campo de tabla

```sql
ALTER TABLE
  nombre_tabla DROP COLUMN nombre_tabla;
```

---

🔥 JOINS

📍 INNER JOIN

```sql
SELECT columnas
FROM tabla1
INNER JOIN tabla2 ON tabla1.columna_clave = tabla2.columna_clave;
```

> Devuelve solo las filas donde hay una coincidencia en ambas tablas, basándose en la condición especificada en `ON`.

📍 LEFT JOIN

```sql
SELECT columnas
FROM tabla1
LEFT JOIN tabla2 ON tabla1.columna_clave = tabla2.columna_clave;
```

> Devuelve todas las filas de la tabla1 (la tabla de la izquierda) y las filas coincidentes de la tabla2 (la tabla de la derecha). Si no hay coincidencia en la tabla2 para una fila de la tabla1, se devuelven valores `NULL` para las columnas de la tabla2.

📍 RIGHT JOIN

```sql
SELECT columnas
FROM tabla1
RIGHT JOIN tabla2 ON tabla1.columna_clave = tabla2.columna_clave;
```

> Es similar a `LEFT JOIN`, pero devuelve todas las filas de la tabla2 (la tabla de la derecha) y las filas coincidentes de la tabla1 (la tabla de la izquierda). Si no hay coincidencia en la tabla1 para una fila de la tabla2, se devuelven valores `NULL` para las columnas de la tabla1.

📍 FULL OUTER JOIN

```sql
SELECT columnas
FROM tabla1
FULL OUTER JOIN tabla2 ON tabla1.columna_clave = tabla2.columna_clave;
```

> Devuelve todas las filas de ambas tablas. Si no hay coincidencia en una tabla para una fila de la otra, se devuelven valores `NULL` para las columnas de la tabla sin coincidencia.

---

🔥 Instrucciones adicionales

📍 Cláusulas para modificar resultados

| Instrucción  | Descripción                                                                 |
| ------------ | --------------------------------------------------------------------------- |
| **ORDER BY** | Ordena los resultados en **ascendente (ASC)** o **descendente (DESC)**.     |
| **LIMIT**    | Restringe el número de filas devueltas en una consulta.                     |
| **OFFSET**   | Omite un número específico de filas antes de empezar a devolver resultados. |
| **FETCH**    | Alternativa a `LIMIT`, permite especificar cuántas filas traer.             |
| **DISTINCT** | Elimina filas duplicadas en los resultados de una consulta.                 |

✔ Ejemplo:

```sql
SELECT * FROM empleados
ORDER BY salario DESC
LIMIT 10 OFFSET 5;
```

📍 Cláusulas para el manejo de datos

✔ ON CONFILCT

La función `ON CONFLICT` en PostgreSQL es una herramienta poderosa que te permite manejar de manera elegante y eficiente los conflictos que puedan surgir al insertar o actualizar datos en una tabla. Estos conflictos suelen ocurrir cuando intentas insertar una fila que viola una restricción única (como una clave primaria o una restricción `UNIQUE`) o una restricción de exclusión.

En lugar de simplemente generar un error y detener la operación, `ON CONFLICT` te permite definir acciones alternativas que se ejecutarán en caso de conflicto. Esto te brinda un mayor control sobre el comportamiento de tu base de datos y te permite implementar lógicas de negocio más complejas.

```sql
INSERT INTO tabla (columna1, columna2, ...)
VALUES (valor1, valor2, ...)
ON CONFLICT [conflicto_objetivo] [DO acción];
```

> - **`ON CONFLICT`**: La cláusula que define la acción a realizar en caso de conflicto.
> - **`conflicto_objetivo`**: Especifica el objetivo del conflicto, es decir, la restricción que podría generar el conflicto. Puede ser el nombre de una restricción única o de exclusión, o una lista de columnas que forman parte de una restricción única o de exclusión. Si se omite, PostgreSQL intentará inferir el objetivo del conflicto.
> - **`DO acción`**: Especifica la acción a realizar en caso de conflicto. Puede ser `DO NOTHING` (no hacer nada) o `DO UPDATE` (actualizar la fila existente).

✔ Ejemplo:

```sql
INSERT INTO productos (codigo, nombre, precio)
VALUES ('ABC-123', 'Producto Nuevo', 99.99)
ON CONFLICT (codigo) DO UPDATE SET nombre = EXCLUDED.nombre, precio = EXCLUDED.precio;
```

✔ RETURNING

La cláusula `RETURNING` en SQL es una herramienta muy útil que te permite obtener información sobre las filas que han sido afectadas por una instrucción SQL, como `INSERT`, `UPDATE` o `DELETE`. En otras palabras, te permite "devolver" valores de las filas que han sido modificadas.

```sql
INSERT INTO tabla (columna1, columna2, ...)
VALUES (valor1, valor2, ...)
RETURNING columna1, columna2, ...;
```

> **`RETURNING columna1, columna2, ...`**: La cláusula que especifica las columnas cuyos valores se van a devolver.

📍 Consultas avanzadas

| Instrucción   | Descripción                                                                                               |
| ------------- | --------------------------------------------------------------------------------------------------------- |
| **GROUP BY**  | Agrupa los resultados según un campo. Se usa con funciones de agregación como `COUNT`, `SUM`, `AVG`, etc. |
| **HAVING**    | Filtra los grupos creados con `GROUP BY` según una condición. Similar a `WHERE`, pero aplicado a grupos.  |
| **UNION**     | Combina los resultados de dos o más consultas `SELECT`, eliminando duplicados.                            |
| **UNION ALL** | Similar a `UNION`, pero conserva los valores duplicados.                                                  |
| **INTERSECT** | Devuelve solo las filas que existen en ambas consultas `SELECT`.                                          |
| **EXCEPT**    | Devuelve las filas de la primera consulta `SELECT` que no están en la segunda.                            |

✔ Ejemplo:

```sql
SELECT departamento, AVG(salario) AS salario_promedio
FROM empleados
GROUP BY departamento
HAVING AVG(salario) > 3000;
```

---

🔥 Funciones

📍 COALESCE

```sql
SELECT campo, COALESCE(campo, 'valor_si_es_null') AS nombre_campo
FROM tabla;
```

> Puedes usar `COALESCE` para asignar un valor por defecto cuando un campo es `NULL`.

📍 NULLIF

```sql
SELECT nombre, NULLIF(rol, 'invitado') AS rol_real FROM usuarios;
```

> `NULLIF` es una función de **control de flujo** en PostgreSQL que compara dos valores y devuelve `NULL` si son iguales. Si los valores son diferentes, devuelve el primer valor.

📍 GREATEST

```sql
SELECT GREATEST(10, 25, 5, 40, 30);
```

> `GREATEST` es una función de **comparación** en PostgreSQL que devuelve el valor **más alto** de una lista de expresiones

📍 LEAST

```sql
SELECT LEAST(10, 25, 5, 40, 30);
```

> `LEAST` es la función opuesta a `GREATEST`. Devuelve el **valor más pequeño** de una lista de expresiones.

---

🔥 Bloques anonimos

**`CASE WHEN THEN END`** en SQL se usa para evaluar condiciones y devolver valores basados en esas condiciones. Es como una estructura `if-else` en otros lenguajes de programación.

```sql
SELECT 
CASE 
WHEN condición1 THEN resultado1
 WHEN condición2 THEN resultado2
 ELSE resultado_por_defecto
 END AS nombre_columna
FROM tabla;
```

> - CASE: Indica el inicio de la estructura de decisión.
> - WHEN: Especifica una condición a evaluar.
> - THEN: Define qué resultado devolver si la condición es verdadera.
> - ELSE (opcional): Especifica un valor por defecto si ninguna condición se cumple.
> - END: Finaliza la estructura CASE.
> - AS nombre_columna: Opcional, le da un nombre a la columna en la consulta.

✔ Ejemplo:

```sql
SELECT nombre, precio,
 CASE 
WHEN precio < 50 THEN 'Barato'
 WHEN precio BETWEEN 50 AND 100 THEN 'Normal'
 ELSE 'Caro'
 END AS categoria
FROM productos;
```

```sql
SELECT nombre, precio
FROM productos
ORDER BY 
    CASE 
        WHEN precio > 100 THEN 1  -- Los caros primero
        WHEN precio BETWEEN 50 AND 100 THEN 2  -- Luego los normales
        ELSE 3  -- Los baratos al final
    END;
```

---

## VISTAS

:fire: Vista: volatil

Una vista volatil es aquella que siempre realizara la consulta a la base de datos, pues la información de esta no se almacena en memoria.

```sql
CREATE VIEW v_nombre_vista AS
SELECT ...
```

> AS -> Estaria tomando la consulta como v_nombre_vitas.

:eye: Invocar una vita

```sql
SELECT * FROM v_nombre_vista;
```

:fire: Vista materializada: persistente

Una **vista materializada** es una vista especial que **almacena los resultados de una consulta** en la base de datos, en lugar de ejecutarla cada vez que se accede. Esto mejora el rendimiento en consultas pesadas, pero los datos **no se actualizan automáticamente**.

```sql
CREATE MATERIALIZED VIEW vm_nombre_vitas AS
SELECT ...
```

:eye: Invocar vista materializada

```sql
SELECT * FROM vm_nombre_vista;
```

:arrows_counterclockwise: Actualizar/refrescar vista materializada

Como los datos **no cambian automáticamente**, si la tabla `ventas` recibe nuevos registros, la vista debe actualizarse manualmente:

```sql
REFRESH MATERIALIZED VIEW vm_nombre_vista;
```

:arrows_counterclockwise: Actualizar consulta de la vista

```sql
CREATE OR REPLACE VIEW vm_nombre_vista AS
SELECT ...
```

:wastebasket: Eliminar una vista materializada

```sql
DROP MATERIALIZED VIEW vm_nombre_vista;
```

---

## 

## PARTICIONES

Las **particiones** en PostgreSQL son una técnica para **dividir una tabla grande en múltiples partes más pequeñas**, llamadas **particiones**, con el objetivo de mejorar el rendimiento y la administración de datos.

Cada partición se comporta como una subtabla de la tabla principal (*tabla padre*), pero los datos se almacenan en las particiones en función de una regla definida, como **rango de fechas, valores específicos o un hash**.

📍 **Tipos de particiones**

| **Tipo de Partición** | **Descripción**                                                                                                    |
| --------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Rango (`RANGE`)**   | Los datos se dividen en función de un rango de valores, como fechas o números.                                     |
| **Lista (`LIST`)**    | Los datos se separan en función de un conjunto de valores específicos, como países o categorías.                   |
| **Hash (`HASH`)**     | Los datos se dividen de manera automática utilizando una función hash, útil para distribuir datos equitativamente. |

Ejemplo de cada particion:

📍 Particionamiento por Rango (`RANGE`)

1. Una tabla de pedidos particionada por año.
   
   ```sql
   CREATE TABLE pedidos (
       id SERIAL PRIMARY KEY,
       fecha DATE NOT NULL,
       total DECIMAL(10,2)
   ) PARTITION BY RANGE (fecha);
   ```
   
   1. Se crea particiones por fecha
      
      ```sql
      CREATE TABLE pedidos_2023 
      PARTITION OF pedidos FOR 
      VALUES FROM ('2023-01-01') TO ('2024-01-01');
      
      CREATE TABLE pedidos_2024 
      PARTITION OF pedidos FOR 
      VALUES FROM ('2024-01-01') TO ('2025-01-01');
      ```
      
      > Crea las particiones permitiendo insertar datos en un rago de fecha especifico.
   
   2. Buscar datos
      
      ```sql
      SELECT * FROM pedidos WHERE fecha = '2023-02-01'
      ```
      
      > PostgreSQL se encargará de consultar solo la partición relevante. Esto se llama **"partition pruning"** (*poda de particiones*), lo que significa que el motor de la base de datos **solo escanea las particiones necesarias** en función de la consulta.

📍 Particionamiento por Lista (`LIST`)

1. Una tabla de clientes particionada por país
   
   ```sql
   CREATE TABLE clientes (
       id SERIAL PRIMARY KEY,
       nombre VARCHAR(50),
       pais TEXT NOT NULL
   ) PARTITION BY LIST (pais);
   ```
   
   1. Se crea particiones por pais
      
      ```sql
      CREATE TABLE clientes_mexico 
      PARTITION OF clientes FOR 
      VALUES IN ('México');
      
      CREATE TABLE clientes_usa 
      PARTITION OF clientes FOR 
      VALUES IN ('USA');
      
      CREATE TABLE clientes_otro 
      PARTITION OF clientes DEFAULT;
      ```
      
      > Se pueden manejar regiones específicas de manera más eficiente.

📍 Particionamiento por Hash (`HASH`)

1. Una tabla de usuarios distribuida en 4 particiones con `HASH`
   
   ```sql
   CREATE TABLE usuarios (
       id SERIAL PRIMARY KEY,
       nombre VARCHAR(50)
   ) PARTITION BY HASH (id);
   ```
   
   1. Se crea particiones con mod 4
      
      ```sql
      CREATE TABLE usuarios_p0 PARTITION OF usuarios FOR 
      VALUES
          WITH (MODULUS 4, REMAINDER 0);
      
      CREATE TABLE usuarios_p1 PARTITION OF usuarios FOR 
      VALUES
          WITH (MODULUS 4, REMAINDER 1);
      
      CREATE TABLE usuarios_p2 PARTITION OF usuarios FOR 
      VALUES
          WITH (MODULUS 4, REMAINDER 2);
      
      CREATE TABLE usuarios_p3 PARTITION OF usuarios FOR 
      VALUES
          WITH (MODULUS 4, REMAINDER 3);
      ```
      
      > Distribuye datos equitativamente en varias particiones para mejorar la velocidad de inserción y búsqueda.

---

## PL/PSQL

PL/pgSQL (**Procedural Language/PostgreSQL**) es un **lenguaje de procedimientos** que permite escribir **funciones y bloques de código** dentro de PostgreSQL, similar a los procedimientos almacenados en otros motores de bases de datos.

Es una extensión de SQL que **añade control de flujo, variables, estructuras condicionales y loops**, lo que permite escribir lógica compleja dentro de la base de datos.

```sql
DO $$
DECLARE
    nombre_var TIPODATO; -- declaracion de variable
    nombre_var TIPODATO := 'valor'; -- declaracion e inicializacion
BEGIN
    nombre_var := 'valor'; -- inicializacion de variable
    -- Cuerpo pl
END $$;
```

> Este no se crea al momento de ejecutar.

:new: Al macenar pl/psql dentro de una funcion

Esto lo realizamos si queremos usar el pl solo con invocacion de lo contrario nos toca ejecutar todo el codigo del pl de manera manual.

```sql
CREATE FUNCTION pl_nombre_procedmiento (
    nombre_variable TIPODATO,
    nombre_variable TIPODATO
) RETURNS TIPODATO AS $$ -- tipo de dato que se retorna
BEGIN
    -- Cuerpo pl
    RETURN nombre_variable;
END;
$$ LANGUAGE plpgsql; -- tipo de lenguaje soportado
```

:eye: Invocar la funcion del pl

```sql
SELECT pl_nombre_procedimiento(args);
```

:arrows_counterclockwise: Actualizar pl

```sql
CREATE OR REPLACE FUNCTION pl_nombre_procedimiento(
    nombre_varaible TIPODATO
) RETURNS TIPODATO AS $$
BEGIN
    -- Nuevo cuerpo o actualizacion
END;
$$ LANGUAGE pspsql;
```

> Si tenemos algun problema, lo mejor es eliminar el procedimiento y recrearlo.

:wastebasket: Eliminiar pl

```sql
DROP FUNCTION pl_nombre_procedimiento;
```

:pushpin: Funciones y caracteristicas del PL/pgSQL

| **Funcionalidad**          | **Descripción**                                                                   |
| -------------------------- | --------------------------------------------------------------------------------- |
| **Declarar Variables**     | Permite definir variables dentro del bloque.                                      |
| **Estructuras de Control** | `IF`, `CASE`, `LOOP`, `WHILE`, `FOR`.                                             |
| **Manejo de Errores**      | `EXCEPTION` para capturar errores.                                                |
| **Cursores**               | Para recorrer resultados de consultas.                                            |
| **Transacciones**          | `BEGIN`, `COMMIT`, `ROLLBACK`.                                                    |
| **Ejecución Dinámica**     | `EXECUTE` para consultas dinámicas.                                               |
| **Operaciones con Tablas** | `SELECT`, `INSERT`, `UPDATE`, `DELETE`.                                           |
| **Triggers**               | Funciones que se ejecutan automáticamente.                                        |
| **Uso de Arrays**          | `FOREACH` para recorrer listas de datos.                                          |
| **Retorno de Resultados**  | `RETURN` para devolver valores o `RETURN QUERY` para devolver conjuntos de datos. |

---

## 

## TRIGGERS

Un **Trigger** es un **disparador automático** en PostgreSQL que **ejecuta una función cuando ocurre un evento en una tabla**.

`INSERT` `UPDATE` `DELETE` `TRUNCATE`

```sql
CREATE TRIGGER trigger_nombre_triger
TIPOTRIGER EVENTO ON nombre_tabla
FOR EACH ROW
EXECUTE FUNCTION nombre_funcion_registro();
```

:pushpin: Tipos de triggers en postgresql

| **Tipo de Trigger** | **Descripción**                                                                                                                |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| **BEFORE**          | Se ejecuta antes de que ocurra la operación (`INSERT`, `UPDATE`, `DELETE`). Puede modificar los datos antes de que se guarden. |
| **AFTER**           | Se ejecuta después de que se haya completado la operación. Se usa comúnmente para auditoría o registros.                       |
| **INSTEAD OF**      | Se usa en **vistas** para reemplazar la operación original con una personalizada.                                              |
| **ROW LEVEL**       | Se ejecuta una vez **por cada fila** afectada en la tabla.                                                                     |
| **STATEMENT LEVEL** | Se ejecuta **una sola vez por instrucción**, sin importar cuántas filas se afecten.                                            |

:bulb: Ejemplo:

```sql
-- 1. Crear la tabla de logs
CREATE TABLE log_cambios (
    id SERIAL PRIMARY KEY,
    accion TEXT,
    fecha TIMESTAMP DEFAULT now()
);

-- 2. Crear la función que se ejecutará con el Trigger
CREATE FUNCTION log_insert() RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO log_cambios (accion, fecha) 
    VALUES ('Se insertó un usuario', now());
    RETURN NEW; -- OLD "antes del cambio", NEW "despues del cambio"
END;
$$ LANGUAGE plpgsql;

-- 3. Crear el Trigger que ejecuta la función después de un INSERT
CREATE TRIGGER trigger_insert_usuario
AFTER INSERT ON usuarios
FOR EACH ROW -- Por cada fila
EXECUTE FUNCTION log_insert();
```

:wastebasket: Eliminar un trigger

Si tenemos un trigger llamado `trigger_insert_usuario` en la tabla `usuarios`, lo eliminamos con:

```sql
DROP TRIGGER trigger_insert_usuario ON usuarios;
```

**Esto elimina el Trigger**, pero **no la función** asociada. Si también quieres eliminar la función, usa:

```sql
DROP FUNCTION log_insert();
```

---

## 

## TRANSACCIONES

Una **transacción** en PostgreSQL es un conjunto de operaciones SQL que se ejecutan como **una sola unidad de trabajo**. Se asegura de que todas las operaciones se completen correctamente o que ninguna de ellas tenga efecto en caso de error (**atomicidad**).

```sql
BEGIN;
    -- cuerpo transaccion
COMMIT;
```

:pushpin: Tipo de transacciones

| **Comando**                       | **Descripción**                                                  |
| --------------------------------- | ---------------------------------------------------------------- |
| `BEGIN;`                          | Inicia una transacción.                                          |
| `COMMIT;`                         | Confirma los cambios y los hace permanentes.                     |
| `ROLLBACK;`                       | Deshace todos los cambios de la transacción.                     |
| `SAVEPOINT nombre;`               | Crea un punto de guardado dentro de la transacción.              |
| `ROLLBACK TO nombre;`             | Revierte hasta un `SAVEPOINT`, sin cancelar toda la transacción. |
| `SET TRANSACTION ISOLATION LEVEL` | Define el nivel de aislamiento de la transacción.                |

:pushpin: Modos de transaccion

| **Nivel de Aislamiento** | **Descripción**                                                           |
| ------------------------ | ------------------------------------------------------------------------- |
| `READ COMMITTED`         | Lecturas pueden ver solo cambios confirmados. (Por defecto)               |
| `REPEATABLE READ`        | Las consultas dentro de la transacción ven la misma instantánea de datos. |
| `SERIALIZABLE`           | Garantiza la ejecución de transacciones como si fueran secuenciales.      |

:bulb: Ejemplos:

```sql
BEGIN;

UPDATE cuentas SET saldo = saldo - 100 WHERE id = 1;
SAVEPOINT sp1;  -- Guarda el estado actual

UPDATE cuentas SET saldo = saldo + 100 WHERE id = 2;

ROLLBACK TO sp1;  -- Revierte cambios después del SAVEPOINT

COMMIT;  -- Guarda los cambios restantes
```

```sql
BEGIN;
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
-- Consultas SQL
COMMIT;
```

---

## 

## BACKUPS Y RESTAURACION

:round_pushpin: Copia de seguridad

`pg_dump` es una herramienta de línea de comandos en PostgreSQL utilizada para realizar copias de seguridad (**backups**) de bases de datos. Permite exportar datos y estructura en varios formatos

```sql
pg_dump -U usuario -d base_de_datos modo_exportacion -f "ruta/nombre.sql"
```

> **`-U usuario`** → Especifica el usuario con permisos.  
> **`-d base_de_datos`** → Nombre de la base de datos a respaldar.  
> **`-f backup.sql`** → Archivo donde se guardará la copia.

:pushpin: Modos de exportacion

| **Modo de Exportación**    | **Descripción**                                                                                   |
| -------------------------- | ------------------------------------------------------------------------------------------------- |
| `--schema-only`            | Exporta solo la estructura (DDL) de la base de datos sin incluir datos.                           |
| `--data-only`              | Exporta solo los datos de las tablas, omitiendo la estructura.                                    |
| `--create`                 | Incluye la sentencia `CREATE DATABASE` en el dump.                                                |
| `--clean`                  | Agrega `DROP` antes de las sentencias `CREATE`, eliminando objetos existentes antes de restaurar. |
| `--if-exists`              | Se usa con `--clean` para evitar errores si los objetos no existen.                               |
| `--no-owner`               | Excluye la información del propietario de los objetos en el dump.                                 |
| `--no-privileges`          | No incluye los permisos (`GRANT` y `REVOKE`) en el backup.                                        |
| `--no-comments`            | Excluye los comentarios de los objetos en el backup.                                              |
| `--no-publications`        | No exporta las publicaciones de replicación.                                                      |
| `--no-subscriptions`       | No exporta las suscripciones de replicación.                                                      |
| `--exclude-table=tabla`    | Excluye una tabla específica del backup.                                                          |
| `--exclude-schema=esquema` | Excluye un esquema específico del backup.                                                         |
| `-t nombre_tabla`          | Exporta solo la estructura y datos de una tabla específica.                                       |
| `-Fc`                      | Exporta en formato comprimido (`custom`), útil para `pg_restore`.                                 |
| `-Fd`                      | Exporta en formato de directorio, permitiendo una restauración paralela.                          |
| `-Ft`                      | Exporta en formato `tar`, compatible con `pg_restore`.                                            |
| `-f archivo.sql`           | Guarda el backup en un archivo con el nombre especificado.                                        |

:round_pushpin: Restablecer copia de seguridad

`pg_restore` es una herramienta utilizada para restaurar backups creados con `pg_dump` en formatos **personalizado** (`-Fc`) o **directorio** (`-Fd`).

```bash
pg_restore -U usuario -d nueva_base opc_importacion 'ruta/backup.dump'
```

:file_folder: Formatos soportados en pg_restore

| **Modo de Exportación** | **Descripción**                                                | Cómo Restaurar                                     |
| ----------------------- | -------------------------------------------------------------- | -------------------------------------------------- |
| Personalizado (-Fc)     | Backup comprimido y optimizado para restauraciones selectivas. | pg_restore -U usuario -d base_de_datos backup.dump |
| Directorio (-Fd)        | Copia en varios archivos, útil para grandes bases de datos.    | pg_restore -U usuario -d base_de_datos backup_dir/ |
| TAR (-Ft)               | Archivo en formato tar, permite restauración selectiva.        | pg_restore -U usuario -d base_de_datos backup.tar  |

:pushpin: Opciones principales

| **Opción**         | **Descripción**                                          |
| ------------------ | -------------------------------------------------------- |
| `-U usuario`       | Especifica el usuario de conexión.                       |
| `-h host`          | Define el servidor donde se restaurará la base de datos. |
| `-p puerto`        | Especifica el puerto de conexión.                        |
| `-d base_de_datos` | Nombre de la base de datos donde se restaurará.          |
| `-f archivo`       | Ruta y nombre del archivo de salida.                     |
| `-C`               | Crea la base de datos antes de restaurarla.              |
| `-j N`             | Usa **N** hilos para la restauración (solo para `-Fd`).  |
| `--schema=schema`  | Restaura solo un esquema específico.                     |
| `--table=tabla`    | Restaura solo una tabla específica.                      |
| `--list`           | Muestra el contenido del backup sin restaurarlo.         |
| `--clean`          | Elimina objetos antes de restaurarlos.                   |
| `--if-exists`      | Ignora errores si un objeto no existe.                   |

---

## DBLINK

`dblink` es una **extensión** en PostgreSQL que permite conectar y ejecutar consultas en **bases de datos remotas o diferentes dentro del mismo servidor**.

:pushpin: Antes de usar dblink, primero debemos verificar que la extension este habilidata.

```sql
CREATE EXTENSION dblink;
```

:hammer: Connectar a una base de datos remota

```sql
SELECT * FROM
dblink ('
    dbname=nombre_db_remota
    port=puerto_db_remota 
    host=direccion/host 
    user=usuario con el que accedemos remotamente
    password=clave_de_usuario',
    'select ... consulta remota'
) AS nombre_para_tabla_generada (nombre_campo tipodato);
```

---

## 

## REPLICAS

La **replicación** en PostgreSQL es el proceso de copiar datos de una base de datos principal (**Primary**) a una o más bases de datos secundarias (**Replicas**). Esto se hace para mejorar el rendimiento, disponibilidad y tolerancia a fallos.

:warning: Son servidores diferentes, cada servidor tiene instalado su gestor de base de datos.

:pushpin: Tipos de replicas

| **Tipo de Replicación**    | **Descripción**                                                                                                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Replicación Física**     | Copia byte a byte del archivo WAL (*Write-Ahead Logging*). Se usa para **alta disponibilidad** y recuperación ante fallos.                                                                 |
| **Replicación Lógica**     | Permite replicar **tablas específicas** en lugar de toda la base de datos. Es útil para migraciones o integraciones entre sistemas.                                                        |
| **Streaming Replication**  | Replica en tiempo real mediante el flujo de los WAL logs. La réplica puede ser de solo lectura.                                                                                            |
| **Asíncrona vs. Síncrona** | - **Asíncrona:** La réplica puede estar desactualizada unos segundos.  <br>- **Síncrona:** La transacción se confirma solo cuando la réplica la recibe, garantizando sincronización total. |

:hammer_and_wrench: Configuracion

1. Archivo de la base primaria
   
   `C:\Program Files\PostgreSQL\<version>\data\postgresql.conf`
   
   ```bash
   # los archivos de bitacora se comparten como hot standby
   # es decir mantiene los archivos hasta que las replicas los utilizen
   wal_level = hot_standby
   
   # Este valor corresponde a la cantidad de replicas que vamos a tener
   max_wal_senders = 1
   
   # Como trataremos los archivos de bitacora, los archivaremos para que los puedan leer lar replicas
   archive_mode = on
   
   # Se especifica un comando de linux para copiar los archivos
   archive_command = 'cp %p /tmp/%f'
   ```

2. Agregar ip al archivo pg_hba.conf
   
   `C:\Program Files\PostgreSQL\data\pg_hba.conf`
   
   ```bash
   host    replication all         direccion_ip/32         trust
   ```

3. Reiniciamos el servicio en la base primaria
   
   ```bash
   sudo systemctl restart postgresql
   ```

4. Detenemos el servicio de la replica
   
   ```bash
   sudo service postgresql stop
   ```

5. Borramos datos locales de replica
   
   ```bash
   rm -rf /var/lib/pgsql/data/*
   ```

6. Copiamos de db_principal a replica
   
   ```bash
   pg_basebackup -U $user_de_master -R -D /var/lib/pgsql/data/ --host=$host_de_master_db --port=$puerto_de_la_master_db
   ```

7. Modificamos archivo postgres.conf de replica
   
   ```bash
   # Esto define este postgres como una base de datos de replica
   hot_standby = on
   ```

8. Reiniciamos el servicio de replica
   
   ```bash
   sudo service postgresql start
   ```

A partir de ahora las configuraciones se han guardado y ya funcionan en modo de master y replica

incluso la contraseña del servicio **replica** ahora sera la misma del servicio **master**

a partir de ahora todos los cambios hechos en master se recrean en replica, y cualquier cambio hecho en replica no se ejecutara ya que estara en modo de solo lectura.

---

## 

## DOCUMENTACION

1. [Extensiones]([PostgreSQL: Documentation: 11: Appendix F. Additional Supplied Modules](https://www.postgresql.org/docs/11/contrib.html))
