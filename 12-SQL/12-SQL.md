# Structured Query Language (SQL)

- Es un lenguaje diseñado para acceder y manipular bases de datos **relacionales** (RDBMS-Relational Data Base Management System).
- A pesar de ser un lenguaje estándar ANSI/ISO, existen diferentes versiones de SQL, cada una con pequeñas variaciones según el motor de base de datos que se esté utilizando.

## Gestores de base de datos relacionales (RDBMS)

- Se les llama gestores de base de datos a aquellos sistemas encargados en mantener las relaciones presentes y su mantención en una base de datos.
- Los gestores relacionales son aquellos que internamente almacenan sus datos utilizando un modelo relacional. Este organiza los datos de la siguiente manera:
    - Los datos se almacenan en una o más tablas (relaciones)
    - Cada tabla contiene una o más filas y columnas
    - Cada fila representa un registro, las cuales contienen un identificador único.
    - Cada columna representa los atributos (características de los datos almacenados)
- Existen múltiples gestores de base de datos relacionales. Entre ellos:
    - MySQL
    - MariaDB
    - SQLite
    - PostgreSQL
    - SQLServer
    - Oracle
    - Un largo etc.
- Por su simplicidad, en el presente curso utilizaremos SQLite


## Lenguaje SQL

### Sentencias básicas SQLite

Referencia: https://www.sqlite.org/lang.html

#### **Insert**

```sql
insert into nombre_tabla (columna1, columna2, columna3) values (valor1, valor2, valor3);
```

Ejemplo: 

```console
sqlite> insert into Cliente (nombre, run, dv) values ('Patricio', 11111111, 1), ('Juan', 2222222, 2);
```

#### **Select**

```sql
select columna1, columna2 from nombre_tabla where condición;
```

Ejemplo:

```console
sqlite> select run from Cliente where nombre="Patricio";
```

#### **Update**

```sql
update nombre_tabla set columna1=valor1, columna2=valor2 where columna3=valor3;

```

Ejemplo: 

```console
sqlite> update Cliente set nombre="Patricio Olivares" where run=11111111;
sqlite> select * from Cliente;
```


#### **Delete**

```sql
delete from nombre_tabla where condicion;

```

Ejemplo: 

```console
sqlite> delete from Cliente where run=11111111;
sqlite> select * from Cliente;
```

### Sentencias auxiliares

#### **Order by**
Permite ordenar elementos bajo un criterio. Se puede indicar si el orden es ascendente o descendente a través de las palabras reservadas *asc* o *desc* respectivamente.

Ejemplo:

```console
sqlite> select * from Cliente order by nombre asc;
```

#### **Limit**
Limita la cantidad de registros obtenidos

Ejemplo:

```console
sqlite> select * from Cliente limit 2;
```

#### **Métodos de agregación**
Existen múltiples métodos que entregan información agregada sobre los datos resultantes de una consulta. Entre ellas tenemos:

- **AVG:** Promedio
- **SUM:** Suma
- **MIN:** Valor mínimo
- **MAX:** Valor máximo
- **COUNT:** Conteo de elementos

Ejemplo:

```console
sqlite> select count(*) from Cliente;
```

#### **Alias**
Permite cambiar los nombres con los que ciertas columnas y tablas pueden ser accedidas. Particularmente cuando los nombres de columnas o tablas son extensos, complicados o se repiten en diferentes tablas dentro de una misma query.

Ejemplo:

```console
sqlite> select nombre as n from Cliente where n="Patricio";
```

#### **Group by**
Permite agrupar los datos resultantes de una query bajo un cierto criterio.

Ejemplo:

```console
sqlite> select nombre, count(*) from Cliente group by nombre;
```

#### **Having**
Permite filtrar los datos obtenidos desde funciones agregadas (similar al where).

Ejemplo:

```console
sqlite> select nombre, count(*) from Cliente group by nombre having run>33333333;
```

#### **Join**

Join permite combinar datos entre tablas que tengan una o más columnas en común. El Join puede ser de tipo

1. **Inner Join:** Devuelve los datos que se encuentren en ambas columnas (intersección)
2. **Left Join:** Agrega a la tabla de la izquierda la información contenida en la tabla derecha.
3. **Right Join:** Agrega a la tabla de la detecha la información contenida en la tabla izquierda.

Ejemplo:

```console
sqlite> insert into Cliente (nombre, run, dv) values ('Alfonso', 33333333, 3), ('Constanza', 44444444, 4);
sqlite> insert into Cuenta (n_cuenta, saldo, person_id) values (1, 10000, 2), (2, 10000, 2), (3, 50000, 3);
sqlite> select nombre, run, n_cuenta, saldo from Cliente join Cuenta on Cliente.id=person_id;
sqlite> select nombre, run, n_cuenta, saldo from Cliente left join Cuenta on Cliente.id=person_id;

```

# Referencias
- https://www.w3schools.com/sql/
- https://en.wikipedia.org/wiki/Relational_database#Relational_model