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
### 4. Devuelve el nombre del puesto, nombre, apellidos y email del jefe de la empresa.
```
SELECT puesto AS "Nombre del Puesto", nombre AS "Nombre Empleado", CONCAT(apellido1," ",apellido2) AS "Apellidos", email AS "Correo Electrónico" FROM empleado WHERE codi
go_jefe IS NULL;
+-------------------+-----------------+---------------+----------------------+
| Nombre del Puesto | Nombre Empleado | Apellidos     | Correo Electrónico   |
+-------------------+-----------------+---------------+----------------------+
| Director General  | Marcos          | Magaña Perez  | marcos@jardineria.es |
+-------------------+-----------------+---------------+----------------------+
```
### 5. Devuelve un listado con el nombre, apellidos y puesto de aquellos empleados que no sean representantes de ventas.
```
SELECT nombre AS "Nombre Empleado", CONCAT(apellido1," ",apellido2) AS "Apellidos", email AS "Correo Electrónico" FROM empleado WHERE NOT codigo_jefe=3;
+-----------------+--------------------+---------------------------+
| Nombre Empleado | Apellidos          | Correo Electrónico        |
+-----------------+--------------------+---------------------------+
| Ruben           | López Martinez     | rlopez@jardineria.es      |
| Alberto         | Soria Carrasco     | asoria@jardineria.es      |
| Maria           | Solís Jerez        | msolis@jardineria.es      |
| Mariano         | López Murcia       | mlopez@jardineria.es      |
| Lucio           | Campoamor Martín   | lcampoamor@jardineria.es  |
| Hilario         | Rodriguez Huertas  | hrodriguez@jardineria.es  |
| José Manuel     | Martinez De la Osa | jmmart@hotmail.es         |
| David           | Palma Aceituno     | dpalma@jardineria.es      |
| Oscar           | Palma Aceituno     | opalma@jardineria.es      |
| Lionel          | Narvaez            | lnarvaez@gardening.com    |
| Laurent         | Serra              | lserra@gardening.com      |
| Walter Santiago | Sanchez Lopez      | wssanchez@gardening.com   |
| Marcus          | Paxton             | mpaxton@gardening.com     |
| Lorena          | Paxton             | lpaxton@gardening.com     |
| Narumi          | Riko               | nriko@gardening.com       |
| Takuma          | Nomura             | tnomura@gardening.com     |
| Larry           | Westfalls          | lwestfalls@gardening.com  |
| John            | Walton             | jwalton@gardening.com     |
| Julian          | Bellinelli         | jbellinelli@gardening.com |
| Mariko          | Kishi              | mkishi@gardening.com      |
+-----------------+--------------------+---------------------------+
```
### 6. Devuelve un listado con el nombre de los todos los clientes españoles.
```
 SELECT nombre_cliente AS "Nombre Cliente" FROM cliente WHERE pais = "Spain";
+--------------------------------+
| Nombre Cliente                 |
+--------------------------------+
| Lasas S.A.                     |
| Beragua                        |
| Club Golf Puerta del hierro    |
| Naturagua                      |
| DaraDistribuciones             |
| Madrileña de riegos            |
| Lasas S.A.                     |
| Camunas Jardines S.L.          |
| Dardena S.A.                   |
| Jardin de Flores               |
| Flores Marivi                  |
| Flowers, S.A                   |
| Naturajardin                   |
| Golf S.A.                      |
| Americh Golf Management SL     |
| Aloha                          |
| El Prat                        |
| Sotogrande                     |
| Vivero Humanes                 |
| Fuenla City                    |
| Jardines y Mansiones Cactus SL |
| Jardinerías Matías SL          |
| Agrojardin                     |
| Top Campo                      |
| Jardineria Sara                |
| Campohermoso                   |
| Flores S.L.                    |
+--------------------------------+
```
### 7. Devuelve un listado con los distintos estados por los que puede pasar un pedido.
```
SELECT DISTINCT estado AS "Estado de Pedidos" From pedido;
+-------------------+
| Estado de Pedidos |
+-------------------+
| Entregado         |
| Rechazado         |
| Pendiente         |
+-------------------+
```

## Consultas multitabla (Composición Interna)
### 6. Lista la dirección de las oficinas que tengan clientes en Fuenlabrada
```
SELECT linea_direccion1 FROM oficina INNER JOIN empleado ON oficina.codigo_oficina = empleado.codigo_oficina WHERE codigo_empleado IN (SELECT codigo_empleado_rep_ventas FROM cliente WHERE ciudad = "Fuenlabrada");
+------------------------------+
| linea_direccion1             |
+------------------------------+
| Bulevar Indalecio Prieto, 32 |
| Francisco Aguirre, 32        |
| 5-11 Wentworth Avenue        |
+------------------------------+
```
