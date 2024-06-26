# Consultas Base De Datos Producto - Fabricante

## Insercion De Datos

**1.** Realice la inserccion de los siguientes datos:

```sql
INSERT INTO fabricante VALUES (1, 'Asus'), (2, 'Lenovo'), (3, 'Hewlett-Packard'), (4, 'Samsung'), (5, 'Seagate'), (6, 'Crucial'), (7, 'Gigabyte'), (8, 'Huawei'), (9, 'Xiaomi');

INSERT INTO producto VALUES (1, 'Disco duro SATA3 1TB', 86.99,), (2, 'Memoria RAM DDR4 8GB', 120, 6), (3, 'DISCO SSD 1TB', 150.99, 4), (4, 'GeForce GTX 1050Ti', 185, 7), (5, 'GeForce GTX 180 Xtreme', 755, 6), (6, 'Monitor 24 LED Full HD', 202, 1), (7, 'Monitor 27 LED Full HD', 245.99, 1), (8, 'Portatil Yoga 520', 559, 2), (9, 'Portatil IdeaPad 320', 444, 2), (10, 'Impresora HP DeskJet 3720', 59.99, 3), (11, 'Impresora HP LaserJet Pro M26nw', 180, 3); 
```

---

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

**11.** Lista el identificador de los fabricantes que tienen productos en la tabla producto.

```sql
SELECT codigo_fabricante
FROM fabricante;
```

**12.** Lista el identificador de los fabricantes que tienen productos en la tabla producto, eliminando los identificadores que aparecen repetidos.

```sql
SELECT DISTINCT codigo_fabricante
FROM producto;
```

**13.** Lista los nombres de los fabricantes ordenados de forma ascendente.

```sql
SELECT nombre
FROM fabricante
ORDER BY nombre ASC;
```

**14.** Lista los nombres de los fabricantes ordenados de forma descendente.

```sql
SELECT nombre
FROM fabricante
ORDER BY nombre DESC;
```

**15.** Lista los nombres de los productos ordenados en primer lugar por el nombre de forma ascendente y en segundo lugar por el precio de forma descendente.

```sql
SELECT nombre, precio
FROM producto
ORDER BY nombre ASC, precio DESC;
```

**16.** Devuelve una lista con las 5 primeras filas de la tabla fabricante.

```sql
SELECT codigo, nombre
FROM fabricante LIMIT 0, 5;
```

**17.** Devuelve una lista con 2 filas a partir de la cuarta fila de la tabla fabricante. La cuarta fila también se debe incluir en la respuesta.

```sql
SELECT codigo, nombre
FROM fabricante LIMIT 4, 6;
```

**18.** Lista el nombre y el precio del producto más barato. (Utilice solamente las cláusulas ORDER BY y LIMIT).

```sql
SELECT nombre, precio
FROM producto LIMIT 0, 1
ORDER BY precio ASC;
```

**19.** Lista el nombre y el precio del producto más caro. (Utilice solamente las cláusulas ORDER BY y LIMIT)

```sql
SELECT nombre, precio
FROM producto LIMIT 0, 1
ORDER BY precio DESC;
```

**20.** Lista el nombre de todos los productos del fabricante cuyo identificador de fabricante es igual a 2.

```sql
SELECT codigo_fabricante
FROM producto
WHERE codigo_fabricante = 2;
```

**21. ** Lista el nombre de los productos que tienen un precio menor o igual a 120€.

```sql
SELECT precio
FROM producto
WHERE precio <= 120;
```

**22.** Lista el nombre de los productos que tienen un precio mayor o igual a 400€.

```sql
SELECT precio
FROM producto
WHERE precio >= 400;
```

**23.** Lista el nombre de los productos que no tienen un precio mayor o igual a 400€.

```sql
SELECT precio
FROM producto
WHERE precio < 400;
```

**24.** Lista todos los productos que tengan un precio entre 80€ y 300€. Sin utilizar el operador BETWEEN.

```sql
SELECT precio
FROM producto
WHERE precio <= 80 AND precio >= 300;
```

**25.** Lista todos los productos que tengan un precio entre 60€ y 200€. Utilizando el operador BETWEEN.

```sql
SELECT precio
FROM producto
WHERE precio BETWEEN 60 AND 200;
```

**26.** Lista todos los productos que tengan un precio mayor que 200€ y que el identificador de fabricante sea igual a 6.

```sql
SELECT precio, codigo
FROM producto
WHERE precio > 200 AND codigo = 6;
```

**27.** Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5. Sin utilizar el operador IN.

```sql
SELECT codigo, nombre, precio, codigo_fabricante FROM producto 
WHERE codigo_fabricante = 1 OR codigo_fabricante = 3 OR codigo_fabricante = 5;
```

**28.** Lista todos los productos donde el identificador de fabricante sea 1, 3 o 5. Utilizando el operador IN.

```sql
SELECT codigo, nombre, precio, codigo_fabricante FROM producto 
WHERE codigo_fabricante IN (1,3,5);
```

**29.** Lista el nombre y el precio de los productos en céntimos (Habrá que multiplicar por 100 el valor del precio). Cree un alias para la columna que contiene el precio que se llame céntimos.

```sql
SELECT  nombre, precio * 100 AS centimos FROM producto;
```

**30.** Lista los nombres de los fabricantes cuyo nombre empiece por la letra S.

```sql
SELECT nombre
FROM fabricante
WHERE nombre LIKE 'S%';
```

**31.** Lista los nombres de los fabricantes cuyo nombre termine por la vocal e.

```sql
SELECT nombre
FROM fabricante
WHERE nombre LIKE '%e';
```

**32.** Lista los nombres de los fabricantes cuyo nombre contenga el carácter w.

```sql
SELECT nombre
FROM fabricante
WHERE nombre LIKE '%w%';
```

**33.** Lista los nombres de los fabricantes cuyo nombre sea de 4 caracteres.

```sql
SELECT nombre
FROM fabricante
WHERE nombre LIKE '____';
```

**34.** Devuelve una lista con el nombre de todos los productos que contienen la cadena Portátil en el nombre.

```sql
SELECT nombre
FROM producto
WHERE nombre LIKE '%portatil%';
```

**35.** Devuelve una lista con el nombre de todos los productos que contienen la cadena Monitor en el nombre y tienen un precio inferior a 215 €.

```sql
SELECT nombre
FROM producto
WHERE nombre LIKE '%Monitor%' AND precio < 215;
```

**36.** Lista el nombre y el precio de todos los productos que tengan un precio mayor o igual a 180€. Ordene el resultado en primer lugar por el precio (en orden descendente) y en segundo lugar por el nombre (en orden
ascendente).

```sql
SELECT nombre
FROM producto
WHERE nombre LIKE '%Monitor%' AND precio < 215;
```

---

## Consultas Multitabla

**1.** Devuelve una lista con el nombre del producto, precio y nombre de fabricante de todos los productos de la base de datos.

```sql
SELECT p.nombre, p.precio, f.nombre
FROM producto as p, fabricante as f;
```

**2.** Devuelve una lista con el nombre del producto, precio y nombre de fabricante de todos los productos de la base de datos. Ordene el resultado por el nombre del fabricante, por orden alfabético.

```sql
SELECT PRODUCTO.nombre, PRODUCTO.precio, FABRICANTE.nombre
FROM producto as PRODUCTO, fabricante as FABRICANTE
ORDER BY FABRICANTE.nombre ASC;
```

**3.** Devuelve una lista con el identificador del producto, nombre del producto, identificador del fabricante y nombre del fabricante, de todos los productos de la base de datos.

```sql
SELECT PRODUCTO.nombre, PRODUCTO.precio, FABRICANTE.nombre, FABRICANTE.codigo
FROM producto as PRODUCTO, fabricante as FABRICANTE;
```

**4.** Devuelve el nombre del producto, su precio y el nombre de su fabricante, del producto más barato.

```sql
SELECT p.nombre, MIN(p.precio), p.codigo_fabricante
FROM producto as p;
```

**5.** Devuelve el nombre del producto, su precio y el nombre de su fabricante, del producto más caro.

```sql
SELECT p.nombre, MAX(p.precio), p.codigo_fabricante
FROM producto as p;
```

**6.** Devuelve una lista de todos los productos del fabricante Lenovo.

```sql
SELECT codigo_fabricante
FROM producto
WHERE codigo_fabricante = 2;
```

**7.** Devuelve una lista de todos los productos del fabricante Crucial que tengan un precio mayor que 200€.

```sql
SELECT codigo_fabricante, precio
FROM producto
WHERE codigo_fabricante = 6 AND precio > 200;
```

**8.** Devuelve un listado con todos los productos de los fabricantes Asus, Hewlett-Packardy Seagate. Sin utilizar el operador IN.

```sql
SELECT codigo_fabricante
FROM producto
WHERE codigo_fabricante = 1 AND codigo_fabricante = 3 AND codigo_fabricante = 5;
```

**9.** Devuelve un listado con todos los productos de los fabricantes Asus, Hewlett-Packardy Seagate. Utilizando el operador IN.

```sql
SELECT codigo_fabricante
FROM producto
WHERE codigo_fabricante IN (1,3,5);
```

**10.** Devuelve un listado con el nombre y el precio de todos los productos de los fabricantes cuyo nombre termine por la vocal e.

```sql
SELECT nombre, precio
FROM producto
WHERE nombre LIKE '%e'
```

