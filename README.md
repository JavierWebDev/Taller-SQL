# Consultas Base De Datos Producto - Fabricante

## Insercion De Datos

**1.** Realice la inserccion de los siguientes datos:

```sql
INSERT INTO fabricante VALUES (1, 'Asus'), (2, 'Lenovo'), (3, 'Hewlett-Packard'), (4, 'Samsung'), (5, 'Seagate'), (6, 'Crucial'), (7, 'Gigabyte'), (8, 'Huawei'), (9, 'Xiaomi');

INSERT INTO producto VALUES (1, 'Disco duro SATA3 1TB', 86.99,), (2, 'Memoria RAM DDR4 8GB', 120, 6), (3, 'DISCO SSD 1TB', 150.99, 4), (4, 'GeForce GTX 1050Ti', 185, 7), (5, 'GeForce GTX 180 Xtreme', 755, 6), (6, 'Monitor 24 LED Full HD', 202, 1), (7, 'Monitor 27 LED Full HD', 245.99, 1), (8, 'Portatil Yoga 520', 559, 2), (9, 'Portatil IdeaPad 320', 444, 2), (10, 'Impresora HP DeskJet 3720', 59.99, 3), (11, 'Impresora HP LaserJet Pro M26nw', 180, 3); 
```

## Consultas Sobre Una Tabla

**1.** Lista el nombre de todos los productos que hay en la tabla producto.

```sql
SELECT id, nombre
FROM producto;
```

**2.** Lista los nombres y los precios de todos los productos de la tabla producto.

```sql
SELECT id, nombre, precio
FROM producto;
```

**3.**  Lista todas las columnas de la tabla producto.

```sql
SELECT id, nombre, precio, codigo, codigo_fabricante
FROM producto;
```

**4.** Lista el nombre de los productos, el precio en euros y el precio en dólares estadounidenses (USD).

```sql
SELECT nombre, precio, (precio * 0.94)
FROM producto;
```

**5.**  Lista el nombre de los productos, el precio en euros y el precio en dólares estadounidenses (USD).

```sql
SELECT nombre as nombre_de_producto, precio as euros, (precio * 0.94) as dolares
FROM producto;
```

**6.** Lista los nombres y los precios de todos los productos de la tabla producto, convirtiendo los nombres a mayúscula.

```sql
SELECT UPPER(nombre), precio
FROM producto;
```

**7.** Lista los nombres y los precios de todos los productos de la tabla producto, convirtiendo los nombres a minúscula.

```sql
SELECT LOWER(nombre), precio
FROM producto;
```

**8.**  Lista el nombre de todos los fabricantes en una columna, y en otra columna obtenga en mayúsculas los dos primeros caracteres del nombre del fabricante.

```sql
SELECT nombre as nombre, LEFT(UPPER(nombre), 2) as COD
FROM producto;
```

**9.** Lista los nombres y los precios de todos los productos de la tabla producto, redondeando el valor del precio.

```sql
SELECT nombre as NOMBRE, ROUND(precio) as PRECIO
FROM producto;
```

**10.** Lista los nombres y los precios de todos los productos de la tabla producto, truncando el valor del precio para mostrarlo sin ninguna cifra decimal.

```sql
SELECT nombre as NOMBRE, TRUNCATE(precio) as PRECIO
FROM producto;
```

