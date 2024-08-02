# CHAPTER 9 - Module and Packages

- **Modules**
  Any file with the .py extension is considered a module, there is no special syntax required to make it a module. The file can contain any valid Python code, but it mostly contains functions, class definitions, and global variables.
  To import a module, we write the `import` keyword followed by the module name. The name of the module is the name of the file without the `.py` extension.

  - **Types of Modules**

    - User defined modules
      User defined modules are the modules that are written by the programmer for their requirements.
    - Standard modules
      There are many standard modules available with Python that you can use in your main script or in any of your own modules. The term ‘Batteries included’ is often used for Python because it comes with this standard library of modules that can be used to perform different types of tasks. There are many standard modules that perform generic programming tasks specific to the web, GUI, files, text pattern matching, and more.
    - Third-party modules
      Third-party modules are available from external sources, and they must be installed before they can be imported and used in our programs. For example, `numpy`, `pandas` and `matplotlib` are packages that need to be installed separately.

    To see the list of modules available, you can write this on the interactive prompt: `help('modules')`

    ## Exploring modules

    To see what a module offers, you can import it in interactive shell and use the built-in dir function or help function. This way you can explore any user defined or predefined module in the interactive mode.
    `help(module_name) or dir(module_name)`.
    The function dir returns a sorted list of strings that contains all the names defined at the top level in a module. It also contains the default Python attributes associated with a module. After viewing the names, if you want to know more about a particular item in the module, you can call the help function for the same.

    ## Creating and naming a new module

    To create a module, you do not have to do anything special. Just create a `.py` file and place your code in it. Any Python file with a `.py` extension is already a module. While creating a module, you should keep in mind that the module name should be a valid Python name.

    ## Importing a module

    We have seen that a program needs to use the `import` statement to get access to the code inside the module. The general syntax of `import` statement is to write the `import` keyword followed by the module name.
    Syntax: `import module_name`.
    This will import the entire module which means that any name defined at the top level of the module is available for use as long as that name is prefixed with the module name.
    We can write these `import` statements anywhere inside the file, even inside functions or if statements, but it is customary to place them at the top of the file.
    After importing the modules, we can use the functions defined in these modules. To use any name that is defined inside the module, we need to prefix it with the module name and a dot.

    ## Importing all names from a module

    The from statement is a variation of the import statement, it allows any program to access the names defined in the imported module directly without prefixing with the module name. If we want to access all the names of a module, then we can write this form of from statement.
    Syntax: `from module_name import *` (Not recommend to import modules this way)
    All the names defined at the top level of the imported module become available in the global scope of the importing module.

    This form of import seems more convenient as it requires less typing but it can cause name conflict with names defined in this program or with built-in names and names imported from other modules. We know that if there are two objects bound to the same name, Python does not show any error, it just rebinds the name. So, if there is a function in your program that has the same name as a function that is imported, then whichever name is encountered later will overwrite the previous one.

  ## Importing individual names from a module

  If you want to import only some names from the module, then after the import keyword you can specify a comma separated list of names that you want to import.
  Suntax: `from module import name1, name2, ……`

  This from statement has specific names instead of the wildcard character `*`. So instead of importing everything from the module, we can import just one or more names which we intend to use. The names are directly accessible in the importing module.

  ## Using an alias while importing

  When we import an entire module using the `import module_name` syntax, we need to prefix the names with the module name which can be cumbersome if the module name is long. In such cases, we can rename the module to a shorter name while importing. This can be done by using the `as` keyword in the import statement. For example, the following statement imports our numerals module with the alias num: `import numerals as num`
  Any user-defined module, standard module or third-party module can be imported using an alias.

  ## Documenting a module

  It is good to document a module if it is going to be used by other programmers who were not involved in the development of the module. To document a module, you can add a docstring in the beginning of the module. It is a string enclosed in triple quotes and is used to give information about the module and its contents. The first line of the docstring should generally state the purpose of the module and after that you can document other things that the user should know about the module. This docstring is available to any importing file in the form of attribute `__doc__`. It also shows up when `help()` function is called with the module name after importing.

  ## Module Object

  When Python finds an imported module, a module object is created in memory and the code inside the module is executed. The module object is analogous to a function object that is created when a function is executed. A module object has named attributes that you can bind and reference. So, like all other things in Python, modules are also objects. A module is a first-class object and can be bound to
  a variable. It can be an item of a container or an attribute of an object. It can be passed as argument to a function, or can be returned from a function call.
  When you write an `import` statement like import numerals, Python looks for the file `numerals.py`, and it creates a module object and binds the name `numerals` to that object in the current scope. We can use the `dir` function to see all the names in the current scope. The `dir` function when used without arguments gives an alphabetically sorted list of names in the current scope.

  ```python
  import numerals
  print(dir())
  ```

  ## Byte compiled version of a module

  When you import a module, Python will create a .pyc file for the module which is the compiled Python file. It is the byte compiled version of the module and you can generally see this file in `__pycache__` subdirectory which is created in the same directory as the `.py` file. This bytecode version is created and stored only for imported modules and not for the main script. Python creates this byte compiled version so that it does not have to compile the file every time the module is loaded by different programs. If an up-todate
  `.pyc` file exists for a module, Python will use that for loading the module instead of the `.py` file. If the .pyc does not exist or is out of date or was created from a different version then Python will load the module from the .py file and regenerate and save the new compiled version. This is an automatic process and is done to speed up any loading of modules required in future. You can see the `__pycache__` subdirectory in the library directories also, it contains the compiler version of library modules.

  ## Reloading a module

  Each module is loaded into memory only once during an interpreter session or during a program run, regardless of the number of times it is imported into a program. If multiple imports occur, the module’s code will not be executed again and again.
  Suppose during an interactive session, you have imported a module, and the code of the module is changed while you are using these modules. You might want to use the updated module code by importing it again, but this is not possible since any imports that are done after the first import just use the already loaded module object, the module is not reloaded and its code is not executed again. You have to restart the interpreter session or execute the program again
  to reload the module. However, you can force a reload by using the reload function from the importlib module. This way we can get the updated version of the already loaded module without exiting the interpreter session.

  ```python
  import module1
  from importlib import reload
  reload(module1)
  ```

  ## Scripts and modules

  The script (application file or main module) contains the main control flow of your application, it is the file that you run to start your application.
  So, when you launch your application using the command
  line or using the IDLE Run Module menu or F5, this is the file that will be executed from top to bottom. This top-level file or the script uses the code defined in other modules by importing them. A module in turn can import other modules also. For example, `module1` is importing `module2` and `module4`. The standard library modules and the third-party modules can also be used by the main script or any of the modules.

  A module is just an ordinary Python file, so it can be imported as well as executed directly.

  A module generally contains reusable code in the form of function and class definitions, but it may contain other runnable code too. There can be situations when you want to
  use the same file as an executable script and an importable module. An example of this is testing, you might want to run a module as a script to test the functions inside it.

  We have seen earlier that the module object has some built in
  attributes, which includes `__name__` that represents the name of the module. Python will set the value of this variable depending on how the code of the module is executed. If the module’s code is executed because it has been imported, Python initializes `__name__` with the
  name of the module and if a module is run as a standalone script, `__name__` is initialized to `__main__`.

  ```python
  if __name__ == "__main__":
    run()

  ```

  When our file `prime.py` is executed as a standalone script,
  `__name__` is equal to `__main__`, the `if` condition is `True` and so the print calls execute. When the file `prime.py` is used for importing, `__name__` is equal to prime, the if condition is False and so anything written inside the if construct will not execute. Anything that is at the top level of the file and not inside this if construct, will
  always be executed whether the file is imported or executed. So, the function definitions that we have in our file `prime.py` will be executed whether the file is executed as a script or imported as a module.

  So, if you want to place any testing code that should not be executed when the module is imported, you can place it at the bottom of the file inside the `if` statement with condition `__name__ == '__main__':`. This idiom is commonly applied when you want to use a Python file both as an importable module and an executable script. You do not need to write a separate file for testing the module. It is also a common pattern to define a function that contains all the
  testing code, and call that function inside the if statement.

- **Packages**

  A package is just a directory that contains modules and a file called `__init__.py`.

  A package can contain other packages also which are sometimes referred to as subpackages. The file `__init__.py` may be empty or it can contain some comments or initialization code for the package. This file will be executed when the package or its contents are imported. To define a package, create a directory that has the same name as the package and then create a file `__init__.py` in that directory. You can place your modules in this directory. The name of the package should be a valid Python identifier.

  ## Subpackages

  A hierarchical structure of packages and subpackages can help you to organize modules of your project and avoid import name conflicts. Here is the hierarchy of a package that contains two subpackages. Each package and subpackage contains the file `__init__.py`.

## Relative imports

The importing that we have done till now is absolute importing.
When we have a complex package with a hierarchical structure that
includes many subpackages and modules, we can use relative
importing in the from statement to import modules that are a part of the same package.

Relative imports can be done only for importing inside a package and can be applied only to the from statement, they cannot be applied to import statements. The main module that is intended to be executed as script should always use absolute imports because its name is `__main__`, and in relative imports the importing is done based on the name of the current module.

> Absolute imports are more readable and descriptive but tend to become lengthy and verbose in complex packages. By using relative imports, you can do intra-package accessing without hardcoding the package name. This can be beneficial if in future the top-level package name is changed or the structure is reorganised. If you have some code, like function definitions or constants that need to be used by all modules in the package, you can make a common module that contain all these objects that have to be shared. This file can be imported in all the modules of the package.

## The End
