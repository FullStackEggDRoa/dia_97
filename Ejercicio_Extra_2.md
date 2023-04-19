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
### 12. Devuelve un listado de todos los pedidos que han sido entregados en el mes de enero de cualquier año.
```
SELECT * FROM pedido WHERE MONTH(fecha_entrega) = "01";
+---------------+--------------+----------------+---------------+-----------+-----------------------------------------------------------+----------------+
| codigo_pedido | fecha_pedido | fecha_esperada | fecha_entrega | estado    | comentarios                                               | codigo_cliente |
+---------------+--------------+----------------+---------------+-----------+-----------------------------------------------------------+----------------+
|             1 | 2006-01-17   | 2006-01-19     | 2006-01-19    | Entregado | Pagado a plazos                                           |              5 |
|            13 | 2009-01-12   | 2009-01-14     | 2009-01-15    | Entregado | NULL                                                      |              7 |
|            15 | 2009-01-09   | 2009-01-12     | 2009-01-11    | Entregado | NULL                                                      |              7 |
|            16 | 2009-01-06   | 2009-01-07     | 2009-01-15    | Entregado | NULL                                                      |              7 |
|            17 | 2009-01-08   | 2009-01-09     | 2009-01-11    | Entregado | mal estado                                                |              7 |
|            18 | 2009-01-05   | 2009-01-06     | 2009-01-07    | Entregado | NULL                                                      |              9 |
|            21 | 2009-01-09   | 2009-01-09     | 2009-01-09    | Rechazado | mal pago                                                  |              9 |
|            22 | 2009-01-11   | 2009-01-11     | 2009-01-13    | Entregado | NULL                                                      |              9 |
|            32 | 2007-01-07   | 2007-01-19     | 2007-01-27    | Entregado | Entrega tardia, el cliente puso reclamacion               |              4 |
|            55 | 2008-12-10   | 2009-01-10     | 2009-01-11    | Entregado | Retrasado 1 dia por problemas de transporte               |             14 |
|            58 | 2009-01-24   | 2009-01-31     | 2009-01-30    | Entregado | Todo correcto                                             |              3 |
|            64 | 2009-01-24   | 2009-01-31     | 2009-01-30    | Entregado | Todo correcto                                             |              1 |
|            75 | 2009-01-11   | 2009-01-13     | 2009-01-13    | Entregado | El pedido llego perfectamente                             |             15 |
|            79 | 2009-01-12   | 2009-01-13     | 2009-01-13    | Entregado | NULL                                                      |             28 |
|            82 | 2009-01-20   | 2009-01-29     | 2009-01-29    | Entregado | El pedido llego un poco mas tarde de la hora fijada       |             28 |
|            95 | 2008-01-04   | 2008-01-19     | 2008-01-19    | Entregado | NULL                                                      |             35 |
|           100 | 2009-01-10   | 2009-01-15     | 2009-01-15    | Entregado | El pedido llego perfectamente                             |             16 |
|           102 | 2008-12-28   | 2009-01-08     | 2009-01-08    | Entregado | Pago pendiente                                            |             16 |
|           103 | 2009-01-15   | 2009-01-20     | 2009-01-24    | Pendiente | NULL                                                      |             30 |
|           113 | 2008-10-28   | 2008-11-09     | 2009-01-09    | Rechazado | El producto ha sido rechazado por la tardanza de el envio |             36 |
|           114 | 2009-01-15   | 2009-01-29     | 2009-01-31    | Entregado | El envio llego dos dias más tarde debido al mal tiempo    |             36 |
|           119 | 2009-01-10   | 2009-01-15     | 2009-01-15    | Entregado | El pedido llego perfectamente                             |             16 |
|           121 | 2008-12-28   | 2009-01-08     | 2009-01-08    | Entregado | Pago pendiente                                            |             16 |
|           123 | 2009-01-15   | 2009-01-20     | 2009-01-24    | Pendiente | NULL                                                      |             30 |
+---------------+--------------+----------------+---------------+-----------+-----------------------------------------------------------+----------------+
24 rows in set (0,00 sec)
```
### 13. Devuelve un listado con todos los pagos que se realizaron en el año 2008 mediante Paypal. Ordene el resultado de mayor a menor.
```
SELECT * FROM pago WHERE forma_pago = "PayPal" AND YEAR(fecha_pago) = "2008" ORDER BY total DESC;
+----------------+------------+----------------+------------+----------+
| codigo_cliente | forma_pago | id_transaccion | fecha_pago | total    |
+----------------+------------+----------------+------------+----------+
|             26 | PayPal     | ak-std-000020  | 2008-03-18 | 18846.00 |
|             14 | PayPal     | ak-std-000015  | 2008-07-15 |  4160.00 |
|             13 | PayPal     | ak-std-000014  | 2008-08-04 |  2246.00 |
|              1 | PayPal     | ak-std-000001  | 2008-11-10 |  2000.00 |
|              1 | PayPal     | ak-std-000002  | 2008-12-10 |  2000.00 |
+----------------+------------+----------------+------------+----------+
5 rows in set (0,00 sec)
```
### 14. Devuelve un listado con todas las formas de pago que aparecen en la tabla pago. Tenga en cuenta que no deben aparecer formas de pago repetidas.
```
 SELECT DISTINCT forma_pago AS "Formas de Pago" FROM pago;
+----------------+
| Formas de Pago |
+----------------+
| PayPal         |
| Transferencia  |
| Cheque         |
+----------------+
3 rows in set (0,00 sec)
```
### 15. Devuelve un listado con todos los productos que pertenecen a la gama Ornamentales y que tienen más de 100 unidades en stock. El listado deberá estar ordenado por su precio de venta, mostrando en primer lugar los de mayor precio.
```
SELECT codigo_producto, nombre, dimensiones, proveedor, cantidad_en_stock, precio_venta, precio_proveedor FROM producto WHERE gama = "Ornamentales" AND cantidad_en_stock > 100 ORDER BY precio_venta DESC;
+-----------------+--------------------------------------------+-------------+------------------+-------------------+--------------+------------------+
| codigo_producto | nombre                                     | dimensiones | proveedor        | cantidad_en_stock | precio_venta | precio_proveedor |
+-----------------+--------------------------------------------+-------------+------------------+-------------------+--------------+------------------+
| OR-115          | Forsytia Intermedia "Lynwood"              | 35-45       | Viveros EL OASIS |               120 |         7.00 |             5.00 |
| OR-116          | Hibiscus Syriacus  "Diana" -Blanco Puro    | 35-45       | Viveros EL OASIS |               120 |         7.00 |             5.00 |
| OR-117          | Hibiscus Syriacus  "Helene" -Blanco-C.rojo | 35-45       | Viveros EL OASIS |               120 |         7.00 |             5.00 |
| OR-118          | Hibiscus Syriacus "Pink Giant" Rosa        | 35-45       | Viveros EL OASIS |               120 |         7.00 |             5.00 |
| OR-112          | Escallonia (Mix)                           | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-113          | Evonimus Emerald Gayeti                    | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-114          | Evonimus Pulchellus                        | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-119          | Laurus Nobilis Arbusto - Ramificado Bajo   | 40-50       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-120          | Lonicera Nitida                            | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-121          | Lonicera Nitida "Maigrum"                  | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-122          | Lonicera Pileata                           | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-123          | Philadelphus "Virginal"                    | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-124          | Prunus pisardii                            | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-125          | Viburnum Tinus "Eve Price"                 | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
| OR-126          | Weigelia "Bristol Ruby"                    | 35-45       | Viveros EL OASIS |               120 |         5.00 |             4.00 |
+-----------------+--------------------------------------------+-------------+------------------+-------------------+--------------+------------------+
15 rows in set (0,00 sec)
```
### 16. Devuelve un listado con todos los clientes que sean de la ciudad de Madrid y cuyo representante de ventas tenga el código de empleado 11 o 30.
```
SELECT * FROM cliente WHERE ciudad = "Madrid" AND codigo_empleado_rep_ventas IN (11,30);
+----------------+-----------------------------+-----------------+-------------------+-----------+-----------+--------------------+------------------+--------+--------+-------+---------------+----------------------------+----------------+
| codigo_cliente | nombre_cliente              | nombre_contacto | apellido_contacto | telefono  | fax       | linea_direccion1   | linea_direccion2 | ciudad | region | pais  | codigo_postal | codigo_empleado_rep_ventas | limite_credito |
+----------------+-----------------------------+-----------------+-------------------+-----------+-----------+--------------------+------------------+--------+--------+-------+---------------+----------------------------+----------------+
|              7 | Beragua                     | Jose            | Bermejo           | 654987321 | 916549872 | C/pintor segundo   | Getafe           | Madrid | Madrid | Spain | 28942         |                         11 |       20000.00 |
|              8 | Club Golf Puerta del hierro | Paco            | Lopez             | 62456810  | 919535678 | C/sinesio delgado  | Madrid           | Madrid | Madrid | Spain | 28930         |                         11 |       40000.00 |
|              9 | Naturagua                   | Guillermo       | Rengifo           | 689234750 | 916428956 | C/majadahonda      | Boadilla         | Madrid | Madrid | Spain | 28947         |                         11 |       32000.00 |
|             10 | DaraDistribuciones          | David           | Serrano           | 675598001 | 916421756 | C/azores           | Fuenlabrada      | Madrid | Madrid | Spain | 28946         |                         11 |       50000.00 |
|             11 | Madrileña de riegos         | Jose            | Tacaño            | 655983045 | 916689215 | C/Lagañas          | Fuenlabrada      | Madrid | Madrid | Spain | 28943         |                         11 |       20000.00 |
|             15 | Jardin de Flores            | Javier          | Villar            | 654865643 | 914538776 | C/ Oña 34          | NULL             | Madrid | Madrid | Spain | 28950         |                         30 |       40000.00 |
|             18 | Naturajardin                | Victoria        | Cruz              | 612343529 | 916548735 | Plaza Magallón 15  | NULL             | Madrid | Madrid | Spain | 28011         |                         30 |        5050.00 |
+----------------+-----------------------------+-----------------+-------------------+-----------+-----------+--------------------+------------------+--------+--------+-------+---------------+----------------------------+----------------+
7 rows in set (0,00 sec)
```

## Consultas multitabla (Composición Interna)
### 1. Obtén un listado con el nombre de cada cliente y el nombre y apellido de su representante de ventas.
```
SELECT nombre_cliente AS "Nombre Cliente", CONCAT (nombre," ", apellido1," ", apellido2) AS "Representante de Ventas"  FROM cliente INNER JOIN empleado ON cliente.codigo_empleado_rep_ventas = empleado.codigo_empleado;
+--------------------------------+---------------------------------+
| Nombre Cliente                 | Representante de Ventas         |
+--------------------------------+---------------------------------+
| GoldFish Garden                | Walter Santiago Sanchez Lopez   |
| Gardening Associates           | Walter Santiago Sanchez Lopez   |
| Gerudo Valley                  | Lorena Paxton                   |
| Tendo Garden                   | Lorena Paxton                   |
| Lasas S.A.                     | Mariano López Murcia            |
| Beragua                        | Emmanuel Magaña Perez           |
| Club Golf Puerta del hierro    | Emmanuel Magaña Perez           |
| Naturagua                      | Emmanuel Magaña Perez           |
| DaraDistribuciones             | Emmanuel Magaña Perez           |
| Madrileña de riegos            | Emmanuel Magaña Perez           |
| Lasas S.A.                     | Mariano López Murcia            |
| Camunas Jardines S.L.          | Mariano López Murcia            |
| Dardena S.A.                   | Mariano López Murcia            |
| Jardin de Flores               | Julian Bellinelli               |
| Flores Marivi                  | Felipe Rosas Marquez            |
| Flowers, S.A                   | Felipe Rosas Marquez            |
| Naturajardin                   | Julian Bellinelli               |
| Golf S.A.                      | José Manuel Martinez De la Osa  |
| Americh Golf Management SL     | José Manuel Martinez De la Osa  |
| Aloha                          | José Manuel Martinez De la Osa  |
| El Prat                        | José Manuel Martinez De la Osa  |
| Sotogrande                     | José Manuel Martinez De la Osa  |
| Vivero Humanes                 | Julian Bellinelli               |
| Fuenla City                    | Felipe Rosas Marquez            |
| Jardines y Mansiones Cactus SL | Lucio Campoamor Martín          |
| Jardinerías Matías SL          | Lucio Campoamor Martín          |
| Agrojardin                     | Julian Bellinelli               |
| Top Campo                      | Felipe Rosas Marquez            |
| Jardineria Sara                | Felipe Rosas Marquez            |
| Campohermoso                   | Julian Bellinelli               |
| france telecom                 | Lionel Narvaez                  |
| Musée du Louvre                | Lionel Narvaez                  |
| Tutifruti S.A                  | Mariko Kishi                    |
| Flores S.L.                    | Michael Bolton                  |
| The Magic Garden               | Michael Bolton                  |
| El Jardin Viviente S.L         | Mariko Kishi                    |
+--------------------------------+---------------------------------+
36 rows in set (0,00 sec)

```

### 2. Muestra el nombre de los clientes que hayan realizado pagos junto con el nombre de sus representantes de ventas.
```
SELECT nombre_cliente AS "Nombre Cliente", CONCAT (nombre," ", apellido1," ", apellido2) AS "Representante de Ventas"  FROM cliente INNER JOIN empleado ON cliente.codigo_empleado_rep_ventas = empleado.codigo_empleado WHERE codigo_cliente IN (SELECT DISTINCT codigo_cliente FROM pago);
+--------------------------------+---------------------------------+
| Nombre Cliente                 | Representante de Ventas         |
+--------------------------------+---------------------------------+
| Jardineria Sara                | Felipe Rosas Marquez            |
| Flores Marivi                  | Felipe Rosas Marquez            |
| Dardena S.A.                   | Mariano López Murcia            |
| Camunas Jardines S.L.          | Mariano López Murcia            |
| Jardinerías Matías SL          | Lucio Campoamor Martín          |
| Jardines y Mansiones Cactus SL | Lucio Campoamor Martín          |
| Naturagua                      | Emmanuel Magaña Perez           |
| Beragua                        | Emmanuel Magaña Perez           |
| Sotogrande                     | José Manuel Martinez De la Osa  |
| Golf S.A.                      | José Manuel Martinez De la Osa  |
| Gardening Associates           | Walter Santiago Sanchez Lopez   |
| GoldFish Garden                | Walter Santiago Sanchez Lopez   |
| Tendo Garden                   | Lorena Paxton                   |
| Gerudo Valley                  | Lorena Paxton                   |
| Agrojardin                     | Julian Bellinelli               |
| Jardin de Flores               | Julian Bellinelli               |
| El Jardin Viviente S.L         | Mariko Kishi                    |
| Tutifruti S.A                  | Mariko Kishi                    |
+--------------------------------+---------------------------------+
18 rows in set (0,00 sec)
```
### 3. Muestra el nombre de los clientes que no hayan realizado pagos junto con el nombre de sus representantes de ventas.
```
SELECT nombre_cliente AS "Nombre Cliente", CONCAT (nombre," ", apellido1," ", apellido2) AS "Representante de Ventas"  FROM cliente INNER JOIN empleado ON cliente.codigo_empleado_rep_ventas = empleado.codigo_empleado WHERE codigo_cliente NOT IN (SELECT DISTINCT codigo_cliente FROM pago);
+-----------------------------+---------------------------------+
| Nombre Cliente              | Representante de Ventas         |
+-----------------------------+---------------------------------+
| Lasas S.A.                  | Mariano López Murcia            |
| Club Golf Puerta del hierro | Emmanuel Magaña Perez           |
| DaraDistribuciones          | Emmanuel Magaña Perez           |
| Madrileña de riegos         | Emmanuel Magaña Perez           |
| Lasas S.A.                  | Mariano López Murcia            |
| Flowers, S.A                | Felipe Rosas Marquez            |
| Naturajardin                | Julian Bellinelli               |
| Americh Golf Management SL  | José Manuel Martinez De la Osa  |
| Aloha                       | José Manuel Martinez De la Osa  |
| El Prat                     | José Manuel Martinez De la Osa  |
| Vivero Humanes              | Julian Bellinelli               |
| Fuenla City                 | Felipe Rosas Marquez            |
| Top Campo                   | Felipe Rosas Marquez            |
| Campohermoso                | Julian Bellinelli               |
| france telecom              | Lionel Narvaez                  |
| Musée du Louvre             | Lionel Narvaez                  |
| Flores S.L.                 | Michael Bolton                  |
| The Magic Garden            | Michael Bolton                  |
+-----------------------------+---------------------------------+
18 rows in set (0,00 sec)
```
### 4. Devuelve el nombre de los clientes que han hecho pagos y el nombre de sus representantes junto con la ciudad de la oficina a la que pertenece el representante.
```
ELECT nombre_cliente AS "Nombre Cliente", CONCAT (nombre," ", apellido1," ", apellido2) AS "Representante de Ventas", (SELECT ciudad FROM oficina WHERE oficina.codigo_oficina = empleado.codigo_oficina) AS "Ciudad Oficina" FROM cliente INNER JOIN empleado ON cliente.codigo_empleado_rep_ventas = empleado.codigo_empleado WHERE codigo_cliente IN (SELEC
T DISTINCT codigo_cliente FROM pago);
+--------------------------------+---------------------------------+----------------------+
| Nombre Cliente                 | Representante de Ventas         | Ciudad Oficina       |
+--------------------------------+---------------------------------+----------------------+
| Jardineria Sara                | Felipe Rosas Marquez            | Talavera de la Reina |
| Flores Marivi                  | Felipe Rosas Marquez            | Talavera de la Reina |
| Dardena S.A.                   | Mariano López Murcia            | Madrid               |
| Camunas Jardines S.L.          | Mariano López Murcia            | Madrid               |
| Jardinerías Matías SL          | Lucio Campoamor Martín          | Madrid               |
| Jardines y Mansiones Cactus SL | Lucio Campoamor Martín          | Madrid               |
| Naturagua                      | Emmanuel Magaña Perez           | Barcelona            |
| Beragua                        | Emmanuel Magaña Perez           | Barcelona            |
| Sotogrande                     | José Manuel Martinez De la Osa  | Barcelona            |
| Golf S.A.                      | José Manuel Martinez De la Osa  | Barcelona            |
| Gardening Associates           | Walter Santiago Sanchez Lopez   | San Francisco        |
| GoldFish Garden                | Walter Santiago Sanchez Lopez   | San Francisco        |
| Tendo Garden                   | Lorena Paxton                   | Boston               |
| Gerudo Valley                  | Lorena Paxton                   | Boston               |
| Agrojardin                     | Julian Bellinelli               | Sydney               |
| Jardin de Flores               | Julian Bellinelli               | Sydney               |
| El Jardin Viviente S.L         | Mariko Kishi                    | Sydney               |
| Tutifruti S.A                  | Mariko Kishi                    | Sydney               |
+--------------------------------+---------------------------------+----------------------+
18 rows in set (0,00 sec)
```
### 5. Devuelve el nombre de los clientes que no hayan hecho pagos y el nombre de sus representantes junto con la ciudad de la oficina a la que pertenece el representante.
```
SELECT nombre_cliente AS "Nombre Cliente", CONCAT (nombre," ", apellido1," ", apellido2) AS "Representante de Ventas", codigo_oficina AS "Ciudad Oficina"  FROM cliente INNER JOIN empleado ON cliente.codigo_empleado_rep_ventas = empleado.codigo_empleado WHERE codigo_cliente NOT IN (SELECT DISTINCT codigo_cliente FROM pago);
+-----------------------------+---------------------------------+----------------+
| Nombre Cliente              | Representante de Ventas         | Ciudad Oficina |
+-----------------------------+---------------------------------+----------------+
| Lasas S.A.                  | Mariano López Murcia            | MAD-ES         |
| Club Golf Puerta del hierro | Emmanuel Magaña Perez           | BCN-ES         |
| DaraDistribuciones          | Emmanuel Magaña Perez           | BCN-ES         |
| Madrileña de riegos         | Emmanuel Magaña Perez           | BCN-ES         |
| Lasas S.A.                  | Mariano López Murcia            | MAD-ES         |
| Flowers, S.A                | Felipe Rosas Marquez            | TAL-ES         |
| Naturajardin                | Julian Bellinelli               | SYD-AU         |
| Americh Golf Management SL  | José Manuel Martinez De la Osa  | BCN-ES         |
| Aloha                       | José Manuel Martinez De la Osa  | BCN-ES         |
| El Prat                     | José Manuel Martinez De la Osa  | BCN-ES         |
| Vivero Humanes              | Julian Bellinelli               | SYD-AU         |
| Fuenla City                 | Felipe Rosas Marquez            | TAL-ES         |
| Top Campo                   | Felipe Rosas Marquez            | TAL-ES         |
| Campohermoso                | Julian Bellinelli               | SYD-AU         |
| france telecom              | Lionel Narvaez                  | PAR-FR         |
| Musée du Louvre             | Lionel Narvaez                  | PAR-FR         |
| Flores S.L.                 | Michael Bolton                  | SFC-USA        |
| The Magic Garden            | Michael Bolton                  | SFC-USA        |
+-----------------------------+---------------------------------+----------------+
18 rows in set (0,01 sec)
```
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
