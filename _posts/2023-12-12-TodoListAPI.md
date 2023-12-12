---
layout: single
title: TodoListDocumentation(En Desarrollo)
date: 2023-12-12
classes: wide
excerpt: Esta es la documentación de la API que estoy desarrollando en .NET
header:
  teaser: /assets/images/API.png
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

## Usage Examples
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
