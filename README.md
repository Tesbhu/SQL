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

- SELECT: Se utiliza para recuperar datos de una tabla o vista.

```sql
Ejemplo: Seleccionar todos los registros de una tabla
SELECT * FROM tabla;
INSERT: Se utiliza para insertar nuevos registros en una tabla.
```
- INSERT: Se utiliza para insertar nuevos registros en una tabla

```sql
Ejemplo: Insertar un nuevo registro en una tabla
INSERT INTO tabla (columna1, columna2, ...) VALUES (valor1, valor2, ...);
```

- UPDATE: Se utiliza para actualizar registros existentes en una tabla.

```SQL
-- Ejemplo: Actualizar un valor en una tabla
UPDATE tabla SET columna = nuevo_valor WHERE condición;
```

- DELETE: Se utiliza para eliminar registros de una tabla.

```SQL
-- Ejemplo: Eliminar registros que cumplan una condición en una tabla
DELETE FROM tabla WHERE condición;
```


- WHERE: Se utiliza para filtrar registros basados en una condición.

```SQL
-- Ejemplo: Seleccionar registros que cumplan una condición específica
SELECT * FROM tabla WHERE condición;
```

- ORDER BY: Se utiliza para ordenar los resultados en función de una o varias columnas.

```SQL
-- Ejemplo: Ordenar los registros por una columna en orden ascendente
SELECT * FROM tabla ORDER BY columna ASC;
```

- GROUP BY: Se utiliza para agrupar registros basados en el valor de una columna.

```SQL
-- Ejemplo: Agrupar registros y calcular la suma de una columna
SELECT columna, SUM(otra_columna) FROM tabla GROUP BY columna;
```

- JOIN: Se utiliza para combinar registros de dos o más tablas en función de una condición.

```SQL
-- Ejemplo: Realizar un join entre dos tablas basado en una condición
SELECT * FROM tabla1 JOIN tabla2 ON tabla1.columna = tabla2.columna;
```
-------------
# Consultas intermedias

- Consulta con subconsulta: Utilizando una subconsulta para filtrar los resultados.
```SQL
-- Ejemplo: Seleccionar los empleados que tienen un salario mayor al promedio de la empresa
SELECT * FROM empleados WHERE salario > (SELECT AVG(salario) FROM empleados);
```


-------------
# Consultas avanzadas 
- **Consulta con JOIN y subconsulta**: Combinando JOIN y subconsultas para obtener resultados más complejos.
```SQL
-- Ejemplo: Obtener los empleados y su salario promedio en comparación con el salario promedio de su departamento
SELECT e.empleado_id, e.nombre, e.salario, d.salario_promedio
FROM empleados e
JOIN (SELECT departamento_id, AVG(salario) AS salario_promedio FROM empleados GROUP BY departamento_id) d
ON e.departamento_id = d.departamento_id
WHERE e.salario > d.salario_promedio;
```

- **Consulta con funciones de ventana**: Utilizando funciones de ventana para realizar cálculos avanzados dentro de grupos de datos.

```SQL
-- Ejemplo: Obtener la clasificación de los empleados basada en su salario dentro de cada departamento
SELECT empleado_id, nombre, salario, departamento_id,
    ROW_NUMBER() OVER (PARTITION BY departamento_id ORDER BY salario DESC) AS clasificacion
FROM empleados;
```

- **Consulta con operaciones de conjunto**: Utilizando operaciones de conjunto como UNION, INTERSECT o EXCEPT para combinar o comparar conjuntos de resultados.

```SQL
-- Ejemplo: Obtener los empleados que trabajan en el departamento de Ventas y Marketing, pero no en el departamento de Finanzas
SELECT empleado_id, nombre
FROM empleados
WHERE departamento_id = 1
UNION
SELECT empleado_id, nombre
FROM empleados
WHERE departamento_id = 2
EXCEPT
SELECT empleado_id, nombre
FROM empleados
WHERE departamento_id = 3;
```

- **Consulta con subconsultas correlacionadas**: Utilizando subconsultas correlacionadas para realizar operaciones basadas en los resultados de una consulta externa.

```SQL
-- Ejemplo: Obtener los empleados cuyo salario es mayor al salario promedio de su departamento
SELECT empleado_id, nombre, salario
FROM empleados e
WHERE salario > (SELECT AVG(salario) FROM empleados WHERE departamento_id = e.departamento_id);

```
---------

## Clausula WHEN y CASE
- Consulta con cláusula WHEN en una declaración SELECT:
```SQL
-- Ejemplo: Mostrar el nombre de un producto y su categoría basado en el precio
SELECT nombre_producto,
       CASE
           WHEN precio > 1000 THEN 'Alto'
           WHEN precio > 500 THEN 'Medio'
           ELSE 'Bajo'
       END AS categoria
FROM productos;
```

- Consulta con cláusula CASE en una declaración GROUP BY:
```SQL
-- Ejemplo: Obtener el conteo de empleados por rango de salarios
SELECT CASE
           WHEN salario > 5000 THEN 'Alto'
           WHEN salario > 3000 THEN 'Medio'
           ELSE 'Bajo'
       END AS rango_salario,
       COUNT(*) AS cantidad_empleados
FROM empleados
GROUP BY rango_salario;
```
---------
## Consultas inteligentes

Son las consultas que un cientifico de datos requiere para la construcción de sus modelos, pues sin los datos precisos los modelos NO sirven

```SQL
-- Consulta de ventas por categoría de productos y mes
SELECT YEAR(fecha_venta) AS año, MONTH(fecha_venta) AS mes, categoria_producto, SUM(cantidad) AS total_ventas
FROM ventas
JOIN productos ON ventas.producto_id = productos.producto_id
GROUP BY año, mes, categoria_producto;

-- Consulta de clientes con mayor número de compras
SELECT cliente_id, COUNT(*) AS total_compras
FROM pedidos
GROUP BY cliente_id
ORDER BY total_compras DESC
LIMIT 5;

-- Consulta de productos más vendidos en un período de tiempo
SELECT producto_id, SUM(cantidad) AS total_vendido
FROM ventas
WHERE fecha_venta BETWEEN '2022-01-01' AND '2022-12-31'
GROUP BY producto_id
ORDER BY total_vendido DESC
LIMIT 10;

-- Consulta de ingresos totales por región y año
SELECT YEAR(fecha_venta) AS año, region, SUM(total) AS ingresos_totales
FROM ventas
JOIN clientes ON ventas.cliente_id = clientes.cliente_id
GROUP BY año, region;

-- Consulta de empleados con mejor desempeño en ventas
SELECT empleado_id, SUM(total) AS total_ventas
FROM ventas
GROUP BY empleado_id
ORDER BY total_ventas DESC
LIMIT 3;

```
-------------
## Las fechas son importantes 

Los modelos de series de tiempo son muy usados por ejemplo en caso de estudiar fraudes nos interesa saber las transacciones por ejemplo de un mes y de ellos datos para prevenir futuros fraudes
```SQL
SELECT *
FROM transacciones
WHERE cliente_id IN (
    SELECT DISTINCT cliente_id
    FROM transacciones
    WHERE fecha_transaccion >= DATE_SUB(CURDATE(), INTERVAL 1 MONTH)
    LIMIT 100
);
```
Explicación de la consulta:

La subconsulta interna SELECT DISTINCT cliente_id selecciona los 100 primeros cliente_id que han realizado transacciones en el último mes utilizando la función DATE_SUB(CURDATE(), INTERVAL 1 MONTH) para obtener la fecha límite de un mes atrás desde la fecha actual.

La consulta principal selecciona todas las transacciones de la tabla transacciones donde el cliente_id está en la lista de los 100 clientes obtenidos en la subconsulta interna.

Asegúrate de ajustar el nombre de la tabla y los campos según la estructura de tu base de datos.

Ten en cuenta que esta consulta asume que tienes una tabla llamada "transacciones" que contiene información sobre las transacciones realizadas por los clientes, y que tiene una columna "cliente_id" que identifica a cada cliente. También asume que tienes una columna "fecha_transaccion" que registra la fecha de cada transacciónes

---------------------

## Automatizar consultas y reportes

Para automatizar la consulta en SQL y generar un informe diario sobre el nivel del inventario, puedes seguir estos pasos:

1. Crea una consulta SQL que calcule el nivel del inventario y obtenga los resultados deseados. Por ejemplo:
```SQL
SELECT producto, cantidad
FROM inventario
WHERE cantidad < cantidad_minima;
```
Esta consulta selecciona los productos y las cantidades en el inventario donde la cantidad es menor que la cantidad mínima establecida.

2. Guarda esta consulta en un archivo SQL, por ejemplo, "consulta_inventario.sql".

3. Configura una tarea programada (cron job) en tu sistema operativo para ejecutar la consulta automáticamente a diario. Puedes utilizar comandos como cron en sistemas Unix/Linux o la herramienta "Programador de tareas" en Windows.

4. En la tarea programada, especifica el comando para ejecutar la consulta SQL utilizando tu cliente de base de datos. Por ejemplo:
Por ejemplo, puedes redirigir la salida de la consulta a un archivo CSV utilizando el siguiente comando:

```SQL
mysql -u usuario -pcontraseña -h servidor -D basededatos -e "SELECT producto, cantidad FROM inventario WHERE cantidad < cantidad_minima" > ruta/reporte_inventario.csv
```
También puedes utilizar herramientas adicionales o lenguajes de programación para procesar los resultados y enviarlos por correo electrónico a la persona adecuada.

Al automatizar la consulta en SQL y la generación del informe, podrás recibir regularmente información actualizada sobre el nivel del inventario y tomar acciones en consecuencia. Asegúrate de adaptar los pasos según tu entorno y las herramientas que estés utilizando.

Ten en cuenta que el enfoque puede variar dependiendo del sistema operativo y el cliente de base de datos que estés utilizando. Asegúrate de consultar la documentación correspondiente para obtener información detallada sobre cómo programar tareas y ejecutar consultas en tu entorno específico.
