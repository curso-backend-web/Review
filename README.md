# Review curso de Back-End Web

## OBJETIVO
Saber construir una API (REST o GRAPHQL) conectada a una BBDD (Relacional o NoSQL) y puesta en producción.

## LENGUAJE DE PROGRAMACIÓN
JavaScript - ES6 --> TypeScript (superset JavaScript) | php

## BBDD
Diseño de BBDD (Modelos de Entidad-Relación), SQL, SGBDR (MySQL o PostGreSQL) y NoSQL(MongoDB)

## Y otros
Testing (Unit Testing), CI/CD (Jenkins, Circle, Travis), Contenedores Docker

## Herramientas de Desarrollo
Slack --> Comunicación del equipo
GitHub --> Compartir ejercicios y Git (Gestión Versiones)
IDE --> VisualStudioCode (VSCode)

## Documentación
http://bcncodes-academy-lessons.web.app
http://github.com/curso-backend-web


## Bitácora

### Día 1

Instalamos VSCode, Node.js (instalamos vía nvm), git

- holaMundo.js
- servidorHttp.js
- utilizamos el terminal para lanzar comandos.   

### Día 2

Testing -- Fundamentos
Ejercicio de testing con validación de Password.

Pasó el tiempo.....
#############################################

APIRest con authentication
0. Planficamos lo que queremos hacer. Aquí se hace un kanban con todas las tareas 
1. Arquitectura: Crear los directorios y ficheros principales
  |_ Controller
  |_ Model
  |_ Routes
  |_ app.js
  |_ server.js
  
2. configurar app.js
  - Montamos los handlers de cada ruta
  - Añadimos los middlewares de terceros...P.ej: express.json()
  - exportamos app y lo importamos en server.js

3.  Empezamos a construir por ruta:
  - Routes: construir el router de la ruta
      - subrutas y métodos asociados a controllers. Método a método.
  - Controller: crear el controlador asociado al método.
      - procesamiento de la request.
      - pedir los datos al model.
      - devolver la respuesta.
  - Model: creamos el método de la clase que recupera los datos.
  (si fuera necesario se crea directorio data con los datos) 
  - SE PRUEBA mediante cliente REST.
4. Incorporamos middleware.
  Incorporar los middleware de autenticación y gestión de errores requiere modificar los controladores añadiendo el parámetro next.
  - Middleware de errores
  - Middleware de auth...
5. Otras funcionalidades:
  ...temas de seguridad, temas caché, temas de cors...
  
  
# Día 1 -- BBDD

Las bbdd están dentro de los SGBD (RDMS). Un software que gestiona los datos, el acceso a los datos, la seguridad de los datos, el rendimiento.

Las bbdd relacionales: almacena datos relacionados entre si, con una estructura en tablas con filas y columnas.
Las bbdd noSQL no utilizan sql para explotar los datos: documentos, clave-valor, texto, ...

- Físico: el almacenamiento de los datos,
- Lógico: modelo de relación de los datos almacenados
- Conceptual: traducción del mundo real al mundo conceptos, base para el modelo lógico.

**El modelo conceptual**
Se genera un diagrama E/R (entidad-relación) 
  - Entidades, relaciones y atributos
 
 -Entdades: Los objetos de la vida real que queremos modelar. Sustantivos de las frases que recogemos de los requerimientos.
 -Relaciones: serían los verbos de las frases.
 -Palabras tales como mucho, al menos, solo uno,... cardinalidad
 
 Traducir o trasladar el modelo conceptual al modelo lógico-relacional.
 
 
# Día 2 -- CONSULTAS

-> SQL embebido en el código.
-> ORM para comunicarnos en la bbdd.

SQL
___

__qué queremos obtener__: SELECT tabla1.columna1, funcion(tabla2.column2),...
__de dónde__: FROM tabla1, tabla2, (select otracosa from otra tabla where condicion)
__con qué condiciones__: WHERE tabla1.columna1 like 'F%'
__otras cláusulas__: información agrupada con GROUP BY, ordenada con ORDER BY, 
__últimas condiciones__ con HAVING



Consultas de combinaciones de varias tablas.
**JOINS**
SELECT t1.nom_col1, t2.nom_col2 from table1 t1, table2 t2 where t1.id = t2.id;
SELECT t1.nom_col1, t2.nom_col2 from table1 t1 JOIN t2 ON t1.id = t2.id;
                                from table1 t1 JOIN t2 USING (id);

-INNER-JOIN, LEFT OUTER JOIN, RIGHT OUTER JOIN, EQUI-JOIN, NON-EQUI-JOIN, FULL-JOIN, CROSS-JOIN, NATURAL-JOIN

**UNION**
select 1 UNION
select 2

**SUBQUERIES**
- Aggregated
- Correlated

referencia: https://mysqltutorial.org


# Día 3 -- Diseño de la bbd

1. De la idea al papel:
  - Identificación de entidades, relaciones, atributos, restricciones, etc.
  - Diseño del modelo lógico-relacional: Pintamos tablas con PK, FK y relaciones.
2. Generamos scripts de tablas.
3. Preparamos los datos de partida para ser cargados: json, csv, xml, ... Y se cargan en tablas de preparación.
4. Preparamos los scripts de carga en las tablas definitivas. Para ello tenemos que relacionar las tablas de preparacións con las tablas que vamos generando con los id definitivos.
5. Diseño e implementación del resto de artefactos de la bbdd (procedures, triggers, funciones, índices, etc.)

# Día 4 -- Conexión de la aplicación a la bbdd

- Las aplicaciones se conectan a las bbdd mediante __drivers__, puente de conexión entre ambos sistemas. Estos drivers son programas que implementan el estándar ODBC, entre otros. Dependiendo del lenguaje de programación usaremos un driver en ese lenguaje. 

- Con MySQL usamos la librería mysql2 que complementa a la librería mysql.

1. Instalación: 
```bash
npm i mysql2
```

2. configuración de la conexión:
```js
db = {
  hostname:'',
  database:'',
  user:'',
  password:''
}

mysql.createConnection(db);

``` 
3. Lanzamos las queries con el comando:
- `mysql.query();`
- `mysql.execute(sql,params);`

4. Preparación los modelos
  - Uno por objeto o funcionalidad.

Tasks:
- register -- llamar al proc insert user
- login -- llamar a la función check_user
- getAllMovies -- select * // sustituir el * por los nombres de cols
- getMovieById -- select con condición where
- setMovie -- insert one movie
- updateMovie -- update con condición where
- deleteMovie -- delete con condición where
- getAllUsers -- select where 
- deleteUser -- delete user condición where


USUARIO de acceso:
escritura, lectura, ejecución sobre las tablas de la db. 
sin permisos de ddl: eliminar tablas, alter tablas, 



  





  
