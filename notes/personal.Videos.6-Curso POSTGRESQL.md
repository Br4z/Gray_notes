---
id: 2ypp7tybiju0e2isis2yb0s
title: 6-Curso POSTGRESQL
desc: ''
updated: 1685734390950
playlist_title: ►[ Curso de PostgreSQL ]◄ APRENDE a USAR esta BASE de DATOS desde CERO
date: 2023-06-02
source: https://www.youtube.com/playlist?list=PL8gxzfBmzgex2nuVanqvxoTXTPovVSwi2
---

## 2

- Para crear una base de datos podemos hacer uso de la interfaz gráfica o desde la **query tool** de otra base de datos haciendo uso de la instrucción `CREATE DATABASE <name>`.

## 3

- Para eliminar una base de datos podemos hacer uso de la instrucción `DROP DATABASE IF EXISTS <name>`.

    > Es necesario estar desconectado de la base de datos (la que vamos a eliminar) primero.

## 4

- Para crear una tabla (relación) podemos hacer uso de la **query tool** de la base de datos o la herramienta interactiva en **tables**.

    > Hay que refrescar las tablas luego de crear una.

## 5

- Para insertar datos en una tabla hacemos uso de la instrucción `INSERT INTO <table name>`, que acompañaremos de

    1. `(<attribute 1>, <attribute 2>, <attribute n>) VALUES <tuples>` cuando queremos insertar en el orden que especificamos los atributos (siendo la especificación la parte izquierda).
    2. `VALUES` cuando queremos insertar en el orden con que creamos la tabla.

- Para consultar los datos que tenemos en la base de datos hacemos uso de `SELECT * FROM <table name>`

## 6

- Para actualizar un registro hacemos uso de la instrucción `UPDATE`, un ejemplo con ella podría ser

    ```SQL
    UPDATE <table> SET <modifications>
    WHERE <conditions>

    UPDATE person SET cedula = '1110282760'
    WHERE cedula IS NULL
    ```

## 8

- `SELECT <attributes> FROM <table name>` (podemos usar un asterisco para que nos muestre todos los atributos) nos devolverá los atributos `<attributes>` de la tabla `<table name>`.

    > Podemos usar `AS` para crear alias, por ejemplo `SELECT (name, cedula) AS data FROM person` nos devolverá tuplas de dos elementos en una columna llamada data.

## 9

- El operador `WHERE` sirve para establecer condicionales en las consultas que hacemos con `SELECT` como lo vimos en el ejemplo del video 6.

## 10

- El operador `DELETE` lo podemos usar para eliminar registros:

    ```SQL
    DELETE FROM <table>
    WHERE <conditions>
    ```

## 11

- Tenemos dos opciones para comentar:

    - una línea: `--`
    - múltiples líneas: `/* ... */`.

## 12

- Con el operador `ALTER` podemos modificar una tabla, por ejemplo

    ```SQL
    ALTER TABLE person
    ADD COLUMN test VARCHAR(20)

    ALTER TABLE person
    RENAME COLUMN test to test2

    ALTER TABLE person
    DROP COLUMN test2

    ALTER TABLE <table name>
    <action> ...
    ```

## 13

```SQL
ALTER TABLE person
ADD COLUMN test


SELECT * FROM person
UPDATE test = 'TMY'

ALTER TABLE person
ALTER COLUMN test set NOT NULL

ALTER TABLE person
ALTER COLUMN test TYPE INT -- Nos dará error
```

## 14

```SQL
ALTER TABLE person
ADD PRIMARY KEY (id) -- Esto es recomendable hacerlo en el diseño del esquema, no después
```

## 15

```SQL
CREATE TABLE person(
    id SERIAL PRIMARY KEY NOT NULL,
    name VARCHAR(20),
    phone VARCHAR(20)
)

INSERT INTO person (name, phone) VALUES
    ('Eduardo', '3015088603'),
    ('Pepe', '3015088603'),
    ('Maria', '3015088603')
```

> Un `id SERIAL` se incrementa con cada inserción en la relación.
>
> Si un registro es eliminado, el `id` que tenía no será reutilizado (aunque conceptualmente sea correcto hacerlo).

## 16

### Diferencian entre `DROP` y `TRUNCATE`

- `DELETE FROM <table name>` elimina todos los registros de una tabla.
- `DROP TABLE <table name>` elimina una tabla.
- `TRUNCATE TABLE <table name>` elimina la tabla y la vuelve a construir (podríamos decir que vacía la tabla), para reiniciar las `id` (si la habíamos hecho `SERIAL`) al comando anterior le agregamos `RESTART IDENTITY`.

## 17

```SQL
CREATE TABLE person(
    id SERIAL PRIMARY KEY NOT NULL,
    name VARCHAR(20),
    phone VARCHAR(20) default 'unknown' -- Valor por defecto
)

INSERT INTO person (name, phone) VALUES ('Eduardo','3015088603'),

INSERT INTO person (name) VALUES ('Pepe')
```

## 18

```SQL
CREATE TABLE employee(
    id SERIAL PRIMARY KEY NOT NULL,
    name VARCHAR(20),
    salary INT
)

SELECT id, name, salary, (salary + (salary * 0.3)) as 'BOND' FROM employee -- Esto nos da una "vista", por así llamarlo

UPDATE employee set salary = salary + (salary * 0.3)
WHERE id = 1 -- Para cambiarle el salario a un empleado en específico
```

## 19

```SQL
SELECT * FROM employee ORDER BY name ASC -- Podemos ingresar también el número del atributo, además de combinar "órdenes"
```

El primer ordenamiento que hagamos primara sobre los demás, es decir, mientras más a la izquierda este, más prioridad tiene.

## 20

- Para búsquedas más generales (con patrones) usamos el `LIKE`.

    ```SQL
    SELECT * FROM employee
    WHERE name LIKE "%d_" -- El "%" es como el "*" y el "_" es para indicar que hay solo UN carácter, entonces
    -- la consulta busca las personas que en su penúltima letra tengan una letra "d"
    ```

## 21

```SQL
SELECT COUNT(*) FROM employee -- Podemos hacer el conteo restringiéndolos a atributos
WHERE name like "E%"
```

## 22

```SQL
SELECT SUM(salary) FROM employee
WHERE name like "%a%" -- Estamos seleccionando todas las personas que tengan al menos una "a" en el nombre
```

## 23

```SQL
SELECT MIN(salary) FROM employee
SELECT MAX(salary) FROM employee

SELECT name, MAX(salary) FROM employee
GROUP BY name -- Para poder hacer uso del atributo "name" con una función de agregación
```

## 24

```SQL
SELECT AVG(salary) FROM employee -- Obtenemos el promedio de los salarios

SELECT name, AVG(salary) FROM employee
GROUP BY name -- El promedio de cada registro individual es el mismo salario (esto ocurre en los nombres que no se repiten),
-- en el caso de que haya personas con el mismo nombre, estos se agruparan
```

## 25

```SQL
(SELECT name, salary FROM  employee
WHERE name = 'Jose') GROUP BY name, salary HAVING salary > 3000 -- El having vendría siendo el where para el GROUP BY
```

## 26

```SQL
SELECT DISTINCT name FROM employee -- Quitamos los registros que se repiten (en este caso por el nombre)
```

## 27

```SQL
SELECT * FROM employee
WHERE salary BETWEEN 2000 AND 5000 -- También hay NOT BETWEEN
```

## 28

```SQL
ALTER employee
ADD CONSTRAINT uq_salary -- Añadimos una restricción
    UNIQUE(salary) -- Como la llave primaria, este valor en otro registro no se puede repetir, pero varios atributos pueden ser
    -- únicos, a diferencia de una PK
```

## 29

```SQL
ALTER employee
DROP CONSTRAINT uq_salary -- Para eliminar una restricción
```

## 30

```SQL
CREATE TABLE company(
    name VARCHAR(20),
    id SERIAL PRIMARY KEY
)

CREATE TABLE employee(
    name VARCHAR(20),
    id SERIAL PRIMARY KEY,
    id_company INT,
    CONSTRAINT FK_company_employee
        FOREIGN KEY (id_company)
        REFERENCES company (id)
)
```

> Las llaves foráneas las usamos para relacionar dos tablas

## 31

```SQL
CREATE OR REPLACE FUNCTION sum(a INT, b INT) returns INT
AS
$$
SELECT a + b;
$$
LANGUAGE SQL

SELECT sum(10, 20)

CREATE OR REPLACE FUNCTION get_salary(name VARCHAR) returns INT
AS
$$
SELECT salary FROM employee
WHERE name = $1
$$
LANGUAGE SQL

SELECT get_salary('Jose')
```

## 32

```SQL
CREATE OR REPLACE FUNCTION insert_employees() returns VOID
AS
$$
INSERT INTO employee('David', 1, 6500) -- Esquema (name, id, salary)
INSERT INTO employee('Brandon', 2, 3500) -- Esquema (name, id, salary)
INSERT INTO employee('Deivid', 3, 10500) -- Esquema (name, id, salary)
$$
LANGUAGE SQL

SELECT insert_employee(10, 20)

CREATE OR REPLACE FUNCTION get_employee(INT) returns employee -- Cuando queremos que nos devuelva el registro ponemos que retorna
-- el nombre de la relación
AS
$$
SELECT * FROM employee
WHERE id = $1
$$
LANGUAGE SQL

SELECT get_employee(1)
```

## 33

```SQL
SELECT * FROM employee LIMIT 5 -- Muestra los primeros 5 registros
```

## 34

> La relacion `employee_log` tiene los mismos atributos que `employee`.

```SQL
CREATE FUNCTION test() RETURN TRIGGER
AS
$$
BEGIN

INSERT INTO employee_log VALUES (OLD.name, OLD.id, OLD.salary);

return NEW;

END
$$
LANGUAGE PLPGSQL;

CREATE TRIGGER trigger BEFORE UPDATE ON employee
FOR EACH ROW -- Para cada registro que fue actualizado
EXECUTE PROCEDURE test();


UPDATE employee SET
name = 'Eduardo',
id = '11',
salary = '6000'
WHERE name = 'Eduardo'
```

## 35

> La relacion `employee_log` tiene los mismos atributos que `employee` más tres campos (`user`, `date` y `time`).

```SQL
CREATE FUNCTION test() RETURN TRIGGER
AS
$$
DECLARE

user VARCHAR(250) := User
date DATE := current_date
time time := current_time

BEGIN

INSERT INTO employee_log VALUES (NEW.name, NEW.id, NEW.salary, user, date, time);

return NEW;

END
$$
LANGUAGE PLPGSQL;

CREATE TRIGGER trigger AFTER UPDATE ON employee
FOR EACH ROW
EXECUTE PROCEDURE test();

INSERT INTO employee VALUES ('Greg', '12', '8500')
```

## 36

```SQL
SELECT * FROM employee
where id = '2' or id = '3' or id = '11'

SELECT * FROM employee
where id IN ('2', '3', '11')
```

## 37

```SQL

SELECT * FROM employee LIMIT 3 OFFSET 4 -- Mostrar 3 registros a partir del cuarto [start = OFFSET, end = OFFSET + LIMIT]
```

## 38

```SQL
CREATE VIEW employee_view
AS SELECT name, id FROM employee;

SELECT * FROM employee_view
```

Podriamos verlo como crear una relacion a partir de otra (la creada depende de la orginal, es dcir, es dinamica).

## 39

```SQL
SELECT name, id, 'employee' as origin FROM employee
UNION ALL -- Para mostrar todos
SELECT name, id, 'person' from person
```

> Los campos unidos debes ser del mismo tipo.

## 40

```SQL
SELECT * from employee
INNER JOIN person
ON employee.id = person.id
```

## 41

```SQL
SELECT * from employee
LEFT JOIN person
ON employee.id = person.id
```

Le da prioridad a la primera tabla (`employees`), es decir, solo se adjuntarán los datos (en los campos que corresponda) de la segunda tabla, si la condición se cumple (tienen "relación"), en caso contrario dejarán en `null`.

## 42

```SQL
SELECT * from employee
RIGHT JOIN person
ON employee.id = person.id
```

> A diferencia del video anterior, la tabla que tiene prioridad es la segunda (`person`).

## 43

```SQL
SELECT * from employee
FULL JOIN person
ON employee.id = person.id
```

> Aqui ninguna tabla tiene prioridad, por lo que las tablas que no tengan relacion tendran campos en `null`.

## 44

```SQL
SELECT * from employee
CROSS JOIN person
```

Relaciona todos (de la primera tabla) con todos (de la segunda).

> Por eso no es necesario especificar una condición.

## 46

```SQL
CREATE VIEW my_view AS
SELECT * FROM person
WHERE country = "Costa Rica"
WITH CHECK OPTION -- Obliga que los registros insertados cumplan con la condición de la vista

INSERT INTO my_view VALUES (345634, 'Luis', 'Solano', 'Colombia', 13) -- Dará error
```

## 47, 48 y 49

- `ABS`: valor absoluto.
- `CBRT`: raíz cúbica.
- `CEILING`: techo.
- `FLOOR`: piso.
- `POWER(x, y)`: potencia ($x^y$).
- `ROUND(x, y)`: redondeo de $x$ con $y$ decimales (con las reglas convencionales).
- `SIGN`
    - 1: si el número es positivo.
    - -1: si el número es negativo.
    - 0: si el número es cero.
- `SQRT`: raíz cuadrada.
- `MOD(x, y)`: módulo ($x % y$).
- `PI`: número $\pi$.
- `RANDOM`: valor aleatorio entre 0 y 1.
- `TRUNC(x, y)`: número $x$ con $y$ decimales.

```SQL
ABS(-5) -- 5
CBRT(9) -- 2
CEILING(5.6) -- 6
FLOOR(6.5) -- 6
POWER(2, 4) -- 16
ROUND(24.827, 2) -- 24.83
SIGN(-232) -- -1
SQRT(9) -- 3
```

## 50, 51 y 52

- `CHAR_LENGHT`: tamaño de una cadena (string).
- `UPPER`: mayúscula.
- `LOWER`: minúscula.
- `POSITION(x in y)`: siendo $x$ y $y$ un string, nos devuelve la posición donde comienza $x$ en $y$.

    > La indexación comienza en 1 y si $x$ no se encuentra en $y$, nos devuelve 0.

- `SUBSTRING(x FROM y FOR z)`: siendo $y$ y $z$ enteros, devuelve el substring `S[y,..., y + (z - 1)]`.

- `TRIM(<LEADING, TRILING or BOTH> x from y)`: elimina los caracteres $x$ consecutivos, según el modo que especifiquemos:

    - `LEADING`: principio.
    - `TRILING`: final.
    - `BOTH`: ambos lados.

- `LFTRIM(x, y)`: eliminará los caracteres consecutivos $y$ que haya en el lado izquierdo de $x$.
    > Si no se le especifica $y$, po defecto este será `' '`.
    >
    > Podriamos considerarlo como un `TRIM(LEADING x from y)`.

- `RTRIM(x, y)`: funciona de forma análoga al de arriba, con la única diferencia que este actúa sobre el lado derecho.

    > Podríamos considerarlo como un `TRIM(TRAILING x from y)`.

- `SUBSTR(x, y, z)`: siendo $x$ un string y $y$ y $z$ números enteros, retorna el string `S[y, ..., y + (z - 1)]`.

    > Podríamos considerarlo como un `SUBSTRING(x FROM y FOR z)`.
    >
    > Si no se le especifica $z$, por defecto es el tamaño del string.

- `LPAD(x, y, z)`: rellena el string $x$ con un número de caracteres $z$ en el lado izquierdo, tal que la longitud del string retornado sea $y$.

- `RPAD(x, y, z)`: funciona de forma análoga al de arriba, con la única diferencia de que esté rellena el lado derecho.

```SQL
CHAR_LENGHT('Hello world') -- 11
UPPER('Hello world') -- HELLO WORLD
LOWER('HELLO WORLD') -- hello world
POSITION('world' in 'Hello world') -- 7
POSITION('World' in 'Hello world') -- 0
SUBSTRING('Hello world' from 1 for 5) - Hello
TRIM(LEADING '-' FROM '--Hello world--') -- Hello world --
TRIM(TRAILING '-' FROM '--Hello world--') -- --Hello world
TRIM(BOTH '-' FROM '--Hello world--') -- Hello world
RTRIM('--Hello world--', '-') -- Hello world--
LTRIM('--Hello world--', '-') -- --Hello world
SUBSTR('Hello world', 7, 5) -- world
LPAD('Hello world', 15, '-') -- ----Hello world
RPAD('Hello world', 15, '-') -- Hello world----
```

## 53

- `CURRENT_DATE`
- `CURRENT_TIME`
- `CURRENT_TIMESTAMP`: fecha y hora actual.
- `EXTRACT(<CENTURY, QUARTER, YEAR, MONTH, DAY, HOUR ...> FROM y)`: extrae el campo especificado de $y$ (si este lo contiene).

```SQL
CURRENT_DATE -- 2023-05-30T00:00:00.000Z
CURRENT_TIME -- 02:42:28.156056+00
CURRENT_TIMESTAMP -- 2023-05-30T02:44:12.392Z
EXTRACT(YEAR FROM CURRENT_TIMESTAMP) -- 2023
```

## 54

```SQL
SELECT * FROM person
WHERE country IS NOT NULL
```

## 55

```SQL
CREATE SEQUENCE index
START WITH 1
INCREMENT BY 20
MINVALUE 1
MAXVALUE 100
CYCLE; -- Si se alcanza el valor máximo la cuenta vuelve a comenzar, si no
-- se especifica dará error al alcanzar el límite

SELECT * FROM index
SELECT NEXTVAL('index')
```

> Una vez creada la secuencia, podemos modificarla con `ALTER`.

## 56

```SQL
SELECT name, last_name, coutry,
(SELECT MAX(price) AS "Maximum price" FROM prices WHERE person.country = prices.country)
FROM person
```

> Subconsulta como atributo.

## 57

```SQL
SELECT name, last_name, coutry FROM person
WHERE country = (SELECT country FROM prices ORDER BY price LIMIT 1 OFFSET 14)
```

> Subconsulta en un `WHERE`.

## 58

```SQL
SELECT name, last_name, coutry FROM person
WHERE person.country = (SELECT country FROM prices WHERE prices.country LIKE '%C%')
```

## 59

```SQL
UPDATE person SET
country = (SELECT country FROM prices ORDER BY price LIMIT 1 OFFSET 64)
WHERE country is NULL

UPDATE person SET visa = true
WHERE country in (SELECT country FROM prices where country LIKE '%os%')

DELETE person SET visa = true
WHERE country in (SELECT country FROM prices where country LIKE '%gol%')
```

## 60

```SQL
INSERT INTO maximum_price
SELECT country, MAX(price) FROM prices
GROUP BY country
```

## 61

```SQL
DO

$$
DECLARE x INT := 50;
        y INT := 500;
        z INT;

BEGIN

z := x * y;

RAISE NOTICE 'The value of the z variable is %', z;

END
$$
```

## 62

```SQL
DO

$$
BEGIN

IF EXISTS(SELECT country FROM prices WHERE country = 'Iraq') THEN

DELETE FROM prices WHERE country = 'Iraq';
RAISE NOTICE 'The country has been found';

ELSE

RAISE NOTICE 'The country has not been found';

END IF

END
$$
```

## 63

```SQL
DO

$$
DECLARE x INT := (SELECT COUNT("id") FROM prices);
        y INT := 0;

BEGIN

WHILE (y < x)
LOOP

RAISE NOTICE 'y = %', y;
y := y + 1;

END LOOP;

END
$$
```

## 64

```SQL
SELECT country, price,
    CASE WHEN country = 'Turkey' THEN 'Flight with layovers'
         WHEN country = 'Spain' THEN 'Delayed flight'
         ELSE 'Normal flight'
    END AS flight_status
FROM prices
```

## 67

```SQL
DO

$$
DECLARE register RECORD;
        prices_cursor CURSOR FOR (SELECT * FROM prices ORDER BY country);

BEGIN

OPEN prices_cursor;

FETCH prices_cursor INTO register;

RAISE NOTICE 'Country: %, Price: %'. register.country, register.price;

FETCH prices_cursor INTO register;

RAISE NOTICE 'Country: %, Price: %'. register.country, register.price;

END
$$
LANGUAGE PLPGSQL;
```

## 68

```SQL
DO

$$
DECLARE register RECORD;
        prices_cursor CURSOR FOR (SELECT * FROM prices ORDER BY country);

BEGIN

OPEN prices_cursor;
FETCH prices_cursor INTO register;

WHILE (FOUND) LOOP

RAISE NOTICE 'Country: %, Price: %'. register.country, register.price;

FETCH prices_cursor INTO register;

END LOOP;

END
$$
LANGUAGE PLPGSQL;



DO

$$
DECLARE register RECORD;
        prices_cursor CURSOR FOR (SELECT * FROM prices ORDER BY country);

BEGIN

FOR register IN prices_cursor LOOP

RAISE NOTICE 'Country: %, Price: %'. register.country, register.price;

END LOOP;

END
$$
LANGUAGE PLPGSQL;
```
