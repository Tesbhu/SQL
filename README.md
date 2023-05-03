# SQL
Fuente de código de consultas básicas, avanzadas y aplicadas a la inteligencia de negocios con Python

------------------------------------------------------------------------------------------------------

El lenguaje de consultas estructuras (SQL) es un software muy popular para hacer consultas (querys) en bases de datos. Su historia se remonta a los años 70's , hoy en día (abril 2023) existen muchas maneras de aprender a usarlo con distintos editores, el más popular sigue siendo SQL server, es preciso mencionar de manera temprana que hay lenguajes **NoSQL** no quiere decir que sea lo contrario, es decir que soporta las consultas SQL y las que no lo son, no te preocupes daré las definiciones de ambas, sólo es importante decirlo pues seguramente en una vacante de trabajo has visto que se requiere un conocimiento en **Mongo** esto quiere decir que la empresa requiere que sepas algo sobre lenguajes NoSQL y de Java pues Mongo se interpreta con códigos de Java es decir son formatos tipo Json, Python tienen la opción de leerlos y si en algún momento lo has usado eso quiere decir que ya has tenido contacto con algo NoSQL.

--------------------------------------------------------------------------------------------------------

## SQL ¿Fácil?

Hay muchos videos por ahí donde dicen "Aprende SQL en 10 minutos" quizas se refieran sólo a la definicion pues para un programa de 50 años que ha recibido muchisismo dinero para su desarrollo e implementación y me atrevo a decir que diariamente alguna persona en el mundo implementa nuevas herramientas, por lo que aprendo a nivel experto sería propio de un profesional dedicado a la gestión de la base de datos es decir crearlas, revisar los servidores, estas tareas son titanicas y de alto valor, para un banco tener sus cifras en orden es más que fundamental. Entonces SQL es un mundo en si mismo pues en la interfaz que uno eliga puede crear nuevas funciones, automatizar procesos entre otras acciones, este repositorio tienen como meta mostrar las consultas avanzadas para la inteligencia de negocios las cuales sse caracterizan por la extracción de información de bases ya dadas y planificar que información es relevante para un posterior análisis.

## Matemáticas

En el curso [Managing Big Data with MySQL](https://www.coursera.org/learn/analytics-mysql/home/week/1) ofrecido por la universidad de Duke se comienza con la idea que las bases de datos tienen una conexión con la terío de conjuntos.

---------------------------------------------------------------------------------------------------------------------

## Diagramas 

Los diagramas como el siguiente:


son clave tanto si eres estudiante o un administrador de base de datos con 30 años de experiencia pues asociar una imagén visual  nos permite pensar en distinos caminos a la solución de nuestras consultas 


----

## Consultas básicas

SELECT: Se utiliza para recuperar datos de una tabla o vista.

```sql
Ejemplo: Seleccionar todos los registros de una tabla
SELECT * FROM tabla;
INSERT: Se utiliza para insertar nuevos registros en una tabla.
```
INSERT: Se utiliza para insertar nuevos registros en una tabla

```sql
Ejemplo: Insertar un nuevo registro en una tabla
INSERT INTO tabla (columna1, columna2, ...) VALUES (valor1, valor2, ...);
```

UPDATE: Se utiliza para actualizar registros existentes en una tabla.

sql

-- Ejemplo: Actualizar un valor en una tabla
UPDATE tabla SET columna = nuevo_valor WHERE condición;
DELETE: Se utiliza para eliminar registros de una tabla.

sql
e
-- Ejemplo: Eliminar registros que cumplan una condición en una tabla
DELETE FROM tabla WHERE condición;
WHERE: Se utiliza para filtrar registros basados en una condición.

sql

-- Ejemplo: Seleccionar registros que cumplan una condición específica
SELECT * FROM tabla WHERE condición;
ORDER BY: Se utiliza para ordenar los resultados en función de una o varias columnas.

sql

-- Ejemplo: Ordenar los registros por una columna en orden ascendente
SELECT * FROM tabla ORDER BY columna ASC;
GROUP BY: Se utiliza para agrupar registros basados en el valor de una columna.

sql

-- Ejemplo: Agrupar registros y calcular la suma de una columna
SELECT columna, SUM(otra_columna) FROM tabla GROUP BY columna;

JOIN: Se utiliza para combinar registros de dos o más tablas en función de una condición.

sql

-- Ejemplo: Realizar un join entre dos tablas basado en una condición
SELECT * FROM tabla1 JOIN tabla2 ON tabla1.columna = tabla2.columna;
