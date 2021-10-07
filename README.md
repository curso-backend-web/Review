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
  
