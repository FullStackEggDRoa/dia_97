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
### 8. Devuelve un listado con el código de cliente de aquellos clientes que realizaron algún pago en 2008. Tenga en cuenta que deberá eliminar aquellos códigos de cliente que aparezcan repetidos. Resuelva la consulta:
o Utilizando la función YEAR de MySQL.
```
SELECT DISTINCT codigo_cliente AS "Código Cliente" FROM pago WHERE YEAR(fecha_pago) = "2008";
+-----------------+
| Código Cliente  |
+-----------------+
|               1 |
|              13 |
|              14 |
|              26 |
+-----------------+
4 rows in set (0,02 sec)
```
o Utilizando la función DATE_FORMAT de MySQL.
```
SELECT DISTINCT codigo_cliente AS "Código Cliente" FROM pago WHERE DATE_FORMAT(fecha_pago,"%Y") = "2008";
+-----------------+
| Código Cliente  |
+-----------------+
|               1 |
|              13 |
|              14 |
|              26 |
+-----------------+
4 rows in set (0,00 sec)
```
o Sin utilizar ninguna de las funciones anteriores.
```
SELECT DISTINCT codigo_cliente AS "Código Cliente" FROM pago WHERE fecha_pago LIKE "%2008%";
+-----------------+
| Código Cliente  |
+-----------------+
|               1 |
|              13 |
|              14 |
|              26 |
+-----------------+
4 rows in set (0,00 sec)
```
### 9. Devuelve un listado con el código de pedido, código de cliente, fecha esperada y fecha de entrega de los pedidos que no han sido entregados a tiempo. 
```
SELECT codigo_pedido AS "Codigo de Pedido", codigo_cliente AS "Codigo Cliente", fecha_esperada AS "Fecha Esperada", fecha_entrega AS "Fecha Entrega" FROM pedido WHERE fecha_entrega > fecha_esperada;
+------------------+----------------+----------------+---------------+
| Codigo de Pedido | Codigo Cliente | Fecha Esperada | Fecha Entrega |
+------------------+----------------+----------------+---------------+
|                9 |              1 | 2008-12-27     | 2008-12-28    |
|               13 |              7 | 2009-01-14     | 2009-01-15    |
|               16 |              7 | 2009-01-07     | 2009-01-15    |
|               17 |              7 | 2009-01-09     | 2009-01-11    |
|               18 |              9 | 2009-01-06     | 2009-01-07    |
|               22 |              9 | 2009-01-11     | 2009-01-13    |
|               28 |              3 | 2009-02-17     | 2009-02-20    |
|               31 |             13 | 2008-09-30     | 2008-10-04    |
|               32 |              4 | 2007-01-19     | 2007-01-27    |
|               38 |             19 | 2009-03-06     | 2009-03-07    |
|               39 |             19 | 2009-03-07     | 2009-03-09    |
|               40 |             19 | 2009-03-10     | 2009-03-13    |
|               42 |             19 | 2009-03-23     | 2009-03-27    |
|               43 |             23 | 2009-03-26     | 2009-03-28    |
|               44 |             23 | 2009-03-27     | 2009-03-30    |
|               45 |             23 | 2009-03-04     | 2009-03-07    |
|               46 |             23 | 2009-03-04     | 2009-03-05    |
|               49 |             26 | 2008-07-22     | 2008-07-30    |
|               55 |             14 | 2009-01-10     | 2009-01-11    |
|               60 |              1 | 2008-12-27     | 2008-12-28    |
|               68 |              3 | 2009-02-17     | 2009-02-20    |
|               92 |             27 | 2009-04-30     | 2009-05-03    |
|               96 |             35 | 2008-04-12     | 2008-04-13    |
|              103 |             30 | 2009-01-20     | 2009-01-24    |
|              106 |             30 | 2009-05-15     | 2009-05-20    |
|              112 |             36 | 2009-04-06     | 2009-05-07    |
|              113 |             36 | 2008-11-09     | 2009-01-09    |
|              114 |             36 | 2009-01-29     | 2009-01-31    |
|              115 |             36 | 2009-01-26     | 2009-02-27    |
|              123 |             30 | 2009-01-20     | 2009-01-24    |
|              126 |             30 | 2009-05-15     | 2009-05-20    |
|              128 |             38 | 2008-12-10     | 2008-12-29    |
+------------------+----------------+----------------+---------------+
32 rows in set (0,00 sec)
```
### 10. Devuelve un listado con el código de pedido, código de cliente, fecha esperada y fecha de entrega de los pedidos cuya fecha de entrega ha sido al menos dos días antes de la fecha esperada.
o Utilizando la función ADDDATE de MySQL.
```
SELECT codigo_pedido AS "Codigo de Pedido", codigo_cliente AS "Codigo Cliente", fecha_esperada AS "Fecha Esperada", fecha_entrega AS "Fecha Entrega" FROM pedido WHERE fecha_entrega >= ADDDATE(fecha_esperada,INTERVAL 2 DAY);
+------------------+----------------+----------------+---------------+
| Codigo de Pedido | Codigo Cliente | Fecha Esperada | Fecha Entrega |
+------------------+----------------+----------------+---------------+
|               16 |              7 | 2009-01-07     | 2009-01-15    |
|               17 |              7 | 2009-01-09     | 2009-01-11    |
|               22 |              9 | 2009-01-11     | 2009-01-13    |
|               28 |              3 | 2009-02-17     | 2009-02-20    |
|               31 |             13 | 2008-09-30     | 2008-10-04    |
|               32 |              4 | 2007-01-19     | 2007-01-27    |
|               39 |             19 | 2009-03-07     | 2009-03-09    |
|               40 |             19 | 2009-03-10     | 2009-03-13    |
|               42 |             19 | 2009-03-23     | 2009-03-27    |
|               43 |             23 | 2009-03-26     | 2009-03-28    |
|               44 |             23 | 2009-03-27     | 2009-03-30    |
|               45 |             23 | 2009-03-04     | 2009-03-07    |
|               49 |             26 | 2008-07-22     | 2008-07-30    |
|               68 |              3 | 2009-02-17     | 2009-02-20    |
|               92 |             27 | 2009-04-30     | 2009-05-03    |
|              103 |             30 | 2009-01-20     | 2009-01-24    |
|              106 |             30 | 2009-05-15     | 2009-05-20    |
|              112 |             36 | 2009-04-06     | 2009-05-07    |
|              113 |             36 | 2008-11-09     | 2009-01-09    |
|              114 |             36 | 2009-01-29     | 2009-01-31    |
|              115 |             36 | 2009-01-26     | 2009-02-27    |
|              123 |             30 | 2009-01-20     | 2009-01-24    |
|              126 |             30 | 2009-05-15     | 2009-05-20    |
|              128 |             38 | 2008-12-10     | 2008-12-29    |
+------------------+----------------+----------------+---------------+
24 rows in set (0,01 sec)
```
o Utilizando la función DATEDIFF de MySQL.
```
SELECT codigo_pedido AS "Codigo de Pedido", codigo_cliente AS "Codigo Cliente", fecha_esperada AS "Fecha Esperada", fecha_entrega AS "Fecha Entrega" FROM pedido WHERE DATEDIFF(fecha_entrega, fecha_esperada) >= 2;
+------------------+----------------+----------------+---------------+
| Codigo de Pedido | Codigo Cliente | Fecha Esperada | Fecha Entrega |
+------------------+----------------+----------------+---------------+
|               16 |              7 | 2009-01-07     | 2009-01-15    |
|               17 |              7 | 2009-01-09     | 2009-01-11    |
|               22 |              9 | 2009-01-11     | 2009-01-13    |
|               28 |              3 | 2009-02-17     | 2009-02-20    |
|               31 |             13 | 2008-09-30     | 2008-10-04    |
|               32 |              4 | 2007-01-19     | 2007-01-27    |
|               39 |             19 | 2009-03-07     | 2009-03-09    |
|               40 |             19 | 2009-03-10     | 2009-03-13    |
|               42 |             19 | 2009-03-23     | 2009-03-27    |
|               43 |             23 | 2009-03-26     | 2009-03-28    |
|               44 |             23 | 2009-03-27     | 2009-03-30    |
|               45 |             23 | 2009-03-04     | 2009-03-07    |
|               49 |             26 | 2008-07-22     | 2008-07-30    |
|               68 |              3 | 2009-02-17     | 2009-02-20    |
|               92 |             27 | 2009-04-30     | 2009-05-03    |
|              103 |             30 | 2009-01-20     | 2009-01-24    |
|              106 |             30 | 2009-05-15     | 2009-05-20    |
|              112 |             36 | 2009-04-06     | 2009-05-07    |
|              113 |             36 | 2008-11-09     | 2009-01-09    |
|              114 |             36 | 2009-01-29     | 2009-01-31    |
|              115 |             36 | 2009-01-26     | 2009-02-27    |
|              123 |             30 | 2009-01-20     | 2009-01-24    |
|              126 |             30 | 2009-05-15     | 2009-05-20    |
|              128 |             38 | 2008-12-10     | 2008-12-29    |
+------------------+----------------+----------------+---------------+
24 rows in set (0,00 sec)
```
### 11. Devuelve un listado de todos los pedidos que fueron rechazados en 2009.
```
SELECT * FROM pedido WHERE estado = "Rechazado" AND YEAR(fecha_pedido) = "2009";
+---------------+--------------+----------------+---------------+-----------+--------------------------------------------------------------------------+----------------+
| codigo_pedido | fecha_pedido | fecha_esperada | fecha_entrega | estado    | comentarios                                                              | codigo_cliente |
+---------------+--------------+----------------+---------------+-----------+--------------------------------------------------------------------------+----------------+
|            14 | 2009-01-02   | 2009-01-02     | NULL          | Rechazado | mal pago                                                                 |              7 |
|            21 | 2009-01-09   | 2009-01-09     | 2009-01-09    | Rechazado | mal pago                                                                 |              9 |
|            25 | 2009-02-02   | 2009-02-08     | NULL          | Rechazado | El cliente carece de saldo en la cuenta asociada                         |              1 |
|            26 | 2009-02-06   | 2009-02-12     | NULL          | Rechazado | El cliente anula la operacion para adquirir mas producto                 |              3 |
|            40 | 2009-03-09   | 2009-03-10     | 2009-03-13    | Rechazado | NULL                                                                     |             19 |
|            46 | 2009-04-03   | 2009-03-04     | 2009-03-05    | Rechazado | NULL                                                                     |             23 |
|            65 | 2009-02-02   | 2009-02-08     | NULL          | Rechazado | El cliente carece de saldo en la cuenta asociada                         |              1 |
|            66 | 2009-02-06   | 2009-02-12     | NULL          | Rechazado | El cliente anula la operacion para adquirir mas producto                 |              3 |
|            74 | 2009-01-14   | 2009-01-22     | NULL          | Rechazado | El pedido no llego el dia que queria el cliente por fallo del transporte |             15 |
|            81 | 2009-01-18   | 2009-01-24     | NULL          | Rechazado | Los producto estaban en mal estado                                       |             28 |
|           101 | 2009-03-07   | 2009-03-27     | NULL          | Rechazado | El pedido fue rechazado por el cliente                                   |             16 |
|           105 | 2009-02-14   | 2009-02-20     | NULL          | Rechazado | el producto ha sido rechazado por la pesima calidad                      |             30 |
|           120 | 2009-03-07   | 2009-03-27     | NULL          | Rechazado | El pedido fue rechazado por el cliente                                   |             16 |
|           125 | 2009-02-14   | 2009-02-20     | NULL          | Rechazado | el producto ha sido rechazado por la pesima calidad                      |             30 |
+---------------+--------------+----------------+---------------+-----------+--------------------------------------------------------------------------+----------------+
14 rows in set (0,00 sec)
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
