![Hbnb](https://i.ibb.co/tzWhF53/65f4a1dd9c51265f49d0.png)

# HolbertonBnB
## Cloning of AirBnB Website

The goal of the project is to deploy on my server a simple copy of the AirBnB website
A complete web application composed by:
	- A command interpreter, similar to that found in a Shell, that allows data manipulation without a visual user interface; ideal for debugging and development
	- A front-end website that displays the finished product to all users: both inert and elastic
	- An API that acts as a conduit for data (upload, update, remove, and retrieve) between the front end and your database.

# What’s a command interpreter?
Do you remember the Shell? It’s exactly the same but limited to a specific use-case. In our case, we want to be able to manage the objects of our project:

  - Create a new object (ex: a new User or a new Place)
  - Retrieve an object from a file, a database etc…
  - Do operations on objects (count, compute stats, etc…)
  - Update attributes of an object
  - Destroy an object


# Execution

The shell should work like this in interactive mode:

```
$ ./console.py
(hbnb) help

Documented commands (type help <topic>):
========================================
EOF  help  quit

(hbnb) 
(hbnb) 
(hbnb) quit
$
```

But also in non-interactive mode: (like the Shell project in C)

```
$ echo "help" | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
$ cat test_help
help
$
$ cat test_help | ./console.py
(hbnb)

Documented commands (type help <topic>):
========================================
EOF  help  quit
(hbnb) 
$
```
# Steps
## Each step will link to a concept:


# The console

  - create your data model
  - manage (create, update, destroy, etc) objects via a console / command interpreter
  - store and persist objects to a file (JSON file)

Using a strong storage system is the first step. We will be able to abstract from "My object" and "How they are stored and persisted" thanks to this storage engine. This implies that you won't have to worry about how your objects are stored from your console code (the command interpreter itself), from the front-end you will create later, or from the RestAPI.

This abstraction will also allow you to change the type of storage easily without updating all of your codebase.

The console will be a tool to validate this storage engine

![img](https://i.ibb.co/287QnyQ/815046647d23428a14ca.png)


# Web static

  - learn HTML/CSS
  - create the HTML of your application
  - create template of each object

![img](https://i.ibb.co/k4PN9jC/87c01524ada6080f40fc.png)


# MySQL storage

  - replace the file storage by a Database storage
  - map your models to a table in database by using an O.R.M.

![img](https://i.ibb.co/sqqFdgb/5284383714459fa68841.png)


# Web framework - templating

  - create your first web server in Python
  - make your static HTML file dynamic by using objects stored in a file or database

![img](https://i.ibb.co/YWxd2hz/cb778ec8a13acecb53ef.png)


# RESTful API

  - expose all your objects stored via a JSON web interface
  - manipulate your objects via a RESTful API

![img](https://i.ibb.co/SyyCv5S/06fccc41df40ab8f9d49.png)


# Web dynamic

  - learn JQuery
  - load objects from the client side by using your own RESTful API

![img](https://i.ibb.co/4PSRhvD/d2d06462824fab5846f3.png)


# Files and Directories

  - models directory will contain all classes used for the entire project. A class, called “model” in a OOP project is the representation of an object/instance.
  - tests directory will contain all unit tests.
  - console.py file is the entry point of our command interpreter.
  - models/base_model.py file is the base class of all our models. It contains common elements: 
    - attributes: id, created_at and updated_at
    - methods: save() and to_json()
  - models/engine directory will contain all storage classes (using the same prototype). For the moment you will have only one: file_storage.py.


# Storage

It is imperative that a web application be persistent. This implies that every time your program runs, all of the objects from a previous run are loaded into memory. All of the work completed in an earlier execution will not be preserved and will be lost without persistence.

You will work with both file and database storage in this project. You will concentrate on file for the time being.

Why are "model" and "storage management" different? The goal is to create autonomous and modular models. With this architecture, changing your storage system is simple and doesn't require rewriting any code.

For every object, you will always use the class attributes. As opposed to instance attributes, why not? For three reasons:

  - Provide easy class description: everybody will be able to see quickly what a model should contain (which attributes, etc…)
  - Provide default value of any attribute
  - In the future, provide the same model behavior for file storage or database storage
