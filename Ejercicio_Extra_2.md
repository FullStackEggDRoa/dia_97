# EJERCICIOS DE APRENDIZAJE
## Ejercicio_Extra_2
 
##Abrir el script de la base de datos llamada “jardineria.sql” y ejecutarlo para crear todas las tablas e insertar datos en las mismas. Deberá obtener un diagrama de entidad relación igual al que se muestra a continuación:

Archivo Diagrama EMR:

### 1. Devuelve un listado con el código de oficina y la ciudad donde hay oficinas.
```
SELECT codigo_oficina AS "Codigo Oficina", ciudad AS "Ciudad" FROM oficina;
+----------------+----------------------+
| Codigo Oficina | Ciudad               |
+----------------+----------------------+
| BCN-ES         | Barcelona            |
| BOS-USA        | Boston               |
| LON-UK         | Londres              |
| MAD-ES         | Madrid               |
| PAR-FR         | Paris                |
| SFC-USA        | San Francisco        |
| SYD-AU         | Sydney               |
| TAL-ES         | Talavera de la Reina |
| TOK-JP         | Tokyo                |
+----------------+----------------------+
```
### 2. Devuelve un listado con la ciudad y el teléfono de las oficinas de España.
```
 SELECT ciudad AS "Ciudad - España", telefono AS "Telefono - España" FROM oficina WHERE pais = "España";
+----------------------+--------------------+
| Ciudad - España      | Telefono - España  |
+----------------------+--------------------+
| Barcelona            | +34 93 3561182     |
| Madrid               | +34 91 7514487     |
| Talavera de la Reina | +34 925 867231     |
+----------------------+--------------------+
```
### 3. Devuelve un listado con el nombre, apellidos y email de los empleados cuyo jefe tiene un código de jefe igual a 7.
```
 SELECT nombre AS "Nombre Empleado", CONCAT(apellido1," ",apellido2) AS "Apellidos", email AS "Correo Electrónico" FROM empleado WHERE codigo_jefe=7;
+-----------------+-------------------+--------------------------+
| Nombre Empleado | Apellidos         | Correo Electrónico       |
+-----------------+-------------------+--------------------------+
| Mariano         | López Murcia      | mlopez@jardineria.es     |
| Lucio           | Campoamor Martín  | lcampoamor@jardineria.es |
| Hilario         | Rodriguez Huertas | hrodriguez@jardineria.es |
+-----------------+-------------------+--------------------------+
```
