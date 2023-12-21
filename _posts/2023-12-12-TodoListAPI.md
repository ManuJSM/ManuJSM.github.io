---
layout: single
title: TodoListDocumentation
date: 2023-12-12
classes: wide
excerpt: Esta es la documentación de la API que estoy desarrollando en .NET
header:
  teaser: #/assets/images/API.png
  teaser_home_page: true
categories:
  - API
  - Documentacion
tags:
  - Asp.NET core
  - EntityFramework
---


## Introducción

Aquí dejo la documentación de TodoListAPI, un proyecto diseñado para la gestion de tareas, hecha para aprender las bases del CRUD y los patrones de diseño mas usados.

## Link al repositorio de GitHub

[/ManuJSM/ToDoListAPI](https://github.com/ManuJSM/ToDoListAPI)


## Características principales
- Crear y borrar listas de tareas
- Crear,borrar y modificar tareas 
- Marcar cuando has terminado una tarea

## Tecnologías Usadas
- C# (Backend)
- ASP.NET Core (Framework)
- Entity Framework Core (Database ORM)
- SQL Server (Database)


## Estructura Del Proyecto

```
TodoListAPI/
|-- Controllers/
|-- Models/
|-- Dtos/
|-- Data/
|-- Mappers/
|-- Repositories/
|-- Interfaces/
```

## Controlador De Listas
### Get ALL Lists

Muestra Todas las listas de tareas que Existen

**URL** : `/api/TodoList/`

**Method** : `GET`

### Success Responses

**Code** : `200 OK`

**Content** : `{[]}`

```json
[
  {
    "id": 1,
    "title": "Comprar"
  },
  {
    "id": 2,
    "title": "Limpiar"
  }
]
```
### GetById

Muestra una lista concreta con sus items introduciendo el {id} de una de las 
listas anteriores

**URL** : `/api/TodoList/{id}`

**Method** : `GET`

### Success Responses

**Code** : `200 OK`

**Content** : `{[]}`

```json
{
  "id": 1,
  "title": "Comprar",
  "items": [
    {
      "id": 1,
      "title": "Chocolate",
      "isCompleted": false
    },
    {
      "id": 2,
      "title": "Pan",
      "isCompleted": true
    },
    {
      "id": 3,
      "title": "Patatas",
      "isCompleted": false
    }
  ]
}
```

### CreateTodoList

Crea una lista de Tareas con un titulo dado.

**URL** : `/api/TodoList/`

**Method** : `POST`

**Data constraints**

La lista necesita un Nombre para ser almacenada en la base de datos

```json
{
    "Title": "String"
}
```

**Data example** 

```json
{
    "title": "Comprar"
}
```

### Success Responses

**Code** : `201 Created`

**Content** : `{[]}`

```json
[
  {
    "id": 1,
    "title": "Comprar"
  }
]
```
### DeleteList

Borra una Lista con todos sus items dado el Id de la lista.

**URL** : `/api/TodoList/{id}`

**Method** : `DELETE`

### Success Response

**Condition** : Si la lista existe.

**Code** : `204 NO CONTENT`


### Error Responses

**Condition** : Si no hay una lista con este Id.

**Code** : `404 NOT FOUND`


### Update 

Actualiza una Lista entera 

**URL** : `/api/TodoList/{id}`

**Method** : `PUT`

**Data constraints**

```json
{
  "title": "String",
  "items": [
    {
      "title": "String",
      "isCompleted": "bool"
    }
  ]
}
```

**Data example** 

```json
{
  "title": "Comprar",
  "items": [
    {
      "title": "Chocolate",
      "isCompleted": false
    },
    {
      "title": "Pan",
      "isCompleted": true
    },
    {
      "title": "Patatas",
      "isCompleted": false
    }
  ]
}
```

### Success Response

**Condition** : Si la lista existe.

**Code** : `200 OK`

```json
{
  "id": 1,
  "title": "Comprar",
  "items": [
    {
      "id": 1,
      "title": "Chocolate",
      "isCompleted": false
    },
    {
      "id": 2,
      "title": "Pan",
      "isCompleted": true
    },
    {
      "id": 3,
      "title": "Patatas",
      "isCompleted": false
    }
  ]
}
```

### Error Responses

**Condition** : Si no hay una lista con este Id.

**Code** : `404 NOT FOUND`

**Content** : `{}`


## Controlador De Items

### AddToList

Añade un elemento a la lista con el id dado

**URL** : `/api/TodoItem/{id}`

**Method** : `POST`

**Data constraints**

El nuevo elemento necesita un Nombre para ser almacenado.

```json
{
    "Title": "String"
}
```

**Data example** 

```json
{
    "title": "filete de pollo"
}
```

### Success Response

**Condition** : Si la lista existe se crea un nuevo elemento y llama al controlador de Lista para mostrar toda la lista actualizada con el nuevo elemento, el campo isCompleted sera puesto automaticamente a falso.

**Code** : `201 Created`

**Content** : `{[]}`

```json
{
  "id": 1,
  "title": "Comprar",
  "items": [
    {
      "id": 1,
      "title": "Chocolate",
      "isCompleted": false
    },
    {
      "id": 2,
      "title": "Pan",
      "isCompleted": true
    },
    {
      "id": 3,
      "title": "Patatas",
      "isCompleted": false
    },
    {
      "id": 4,
      "title": "filete de pollo",
      "isCompleted": false
    }
  ]
}
```


### Error Responses

**Condition** : Si no hay una lista con este Id.

**Code** : `404 NOT FOUND`



### DeleteItem

Borra un Item de la lista sabiendo el ID de ese Item

**URL** : `/api/TodoItem/{id}`

**Method** : `DELETE`

### Success Response

**Condition** : Si el elemento existe.

**Code** : `204 NO CONTENT`


### Error Responses

**Condition** : Si no hay un elemento con este Id.

**Code** : `404 NOT FOUND`



### UpdateItem

Actualiza un elemento concreto dado su Id

**URL** : `/api/TodoItem/{id}`

**Method** : `PUT`

**Data constraints**

```json

{
  "title": "String",
  "isCompleted": "bool"
}
  
```

**Data example** 

```json

{
  "title": "lavar las sábanas",
  "isCompleted": "True"
}
  
```

### Success Response

**Condition** : Si la lista existe.

**Code** : `200 OK`

```json
{
  "id": 10,
  "title": "lavar las sábanas",
  "isCompleted": "True"
}
```

### Error Responses

**Condition** : Si no hay un Item con ese Id

**Code** : `404 NOT FOUND`

**Content** : `{}`