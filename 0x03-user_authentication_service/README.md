0x03. User authentication service

In the industry, you should not implement your own authentication system and use a module or framework that doing it for you (like in Python-Flask: Flask-User). Here, for the learning purpose, we will walk through each step of this mechanism to understand it by doing.

Learning Objectives
At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

How to declare API routes in a Flask app
How to get and set cookies
How to retrieve request form data
How to return various HTTP status codes

Requirements
Allowed editors: vi, vim, emacs
All your files will be interpreted/compiled on Ubuntu 18.04 LTS using python3 (version 3.7)
All your files should end with a new line
The first line of all your files should be exactly #!/usr/bin/env python3
A README.md file, at the root of the folder of the project, is mandatory
Your code should use the pycodestyle style (version 2.5)
You should use SQLAlchemy 1.3.x
All your files must be executable
The length of your files will be tested using wc
All your modules should have a documentation (python3 -c 'print(__import__("my_module").__doc__)')
All your classes should have a documentation (python3 -c 'print(__import__("my_module").MyClass.__doc__)')
All your functions (inside and outside a class) should have a documentation (python3 -c 'print(__import__("my_module").my_function.__doc__)' and python3 -c 'print(__import__("my_module").MyClass.my_function.__doc__)')
A documentation is not a simple word, it’s a real sentence explaining what’s the purpose of the module, class or method (the length of it will be verified)
All your functions should be type annotated
The flask app should only interact with Auth and never with DB directly.
Only public methods of Auth and DB should be used outside these classes
Setup
You will need to install bcrypt

pip3 install bcrypt

Tasks
0. User model
mandatory
In this task you will create a SQLAlchemy model named User for a database table named users (by using the mapping declaration of SQLAlchemy).

The model will have the following attributes:

id, the integer primary key
email, a non-nullable string
hashed_password, a non-nullable string
session_id, a nullable string
reset_token, a nullable string

1. create user
mandatory
In this task, you will complete the DB class provided below to implement the add_user method.

2. Find user
mandatory
In this task you will implement the DB.find_user_by method. This method takes in arbitrary keyword arguments and returns the first row found in the users table as filtered by the method’s input arguments. No validation of input arguments required at this point.

Make sure that SQLAlchemy’s NoResultFound and InvalidRequestError are raised when no results are found, or when wrong query arguments are passed, respectively.

Warning:

NoResultFound has been moved from sqlalchemy.orm.exc to sqlalchemy.exc between the version 1.3.x and 1.4.x of SQLAchemy - please make sure you are importing it from sqlalchemy.orm.exc

In this task, you will implement the DB.update_user method that takes as argument a required user_id integer and arbitrary keyword arguments, and returns None.

The method will use find_user_by to locate the user to update, then will update the user’s attributes as passed in the method’s arguments then commit changes to the database.

If an argument that does not correspond to a user attribute is passed, raise a ValueError.

