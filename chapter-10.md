# CHAPTER 10 - Namspaces and Scope

**Namespaces**
We know that everything in Python is an object. Strings, lists,
dictionaries, and even functions and modules are objects. All these
objects are identified and accessed by names defined in the program.
As your program grows larger, the number of names in the program
will increase, which increases the chances of name clashes.
Python creates and uses namespaces to manage all the names in a program and avoid any name collisions. It keeps track of all the names by implicitly adding them to different namespaces, mapping each name to its corresponding object. This concept of namespaces allows us to use the same name simultaneously for different objects in different parts of our program, without causing any name conflicts.

You can think of a namespace as just a space for mapping names to
objects. Each name in your program lives inside a specific namespace. These namespaces are automatically created at different
moments during the execution of a program. At any instant, while the
program is running, multiple namespaces can be active. These
namespaces are independent and completely isolated, so we can
have the same name in two or more namespaces without a problem.
Whenever you define a name, Python will store the name object
binding in one of these namespaces, and whenever you use a name
in your program, it will be searched in one of these namespaces.
These namespaces serve as lookup tables for names. All the names in a namespace will be unique, but in different namespaces, names can be the same.

Due to the concept of namespaces, there are very few chances of name clashes, there will be a name clash only if a name appears more than once in the same namespace.

When we define a name, the name object binding will go to a
namespace. The particular name object binding goes to which
namespace will depend on where we have defined the name. Now,
let us see what namespaces Python creates at run time. When the interpreter is invoked, a built-in namespace is created and
it exists until you exit Python. This namespace contains predefined
built-in names such as `print, id, input, int, max` and many builtin
exception names. The built-in namespace exists until the interpreter terminates and this is why we can use these names in our program anytime and anywhere.

When you execute your script, a global namespace is created that
contains all the names that you define at the top level of your
executing script. Some default dunder names are also automatically
included in this namespace by Python. The global namespace also
remains in existence exists until the interpreter is terminated.

Local namespaces are created when functions are called. Each
function call introduces a new local namespace and it exists only till the function is running. The local namespace of a function includes the function’s parameters and any other names that are defined within the body of the function. A local namespace is deleted when the function’s execution is finished, all the name object bindings in it are forgotten. Next time when the function is called, a fresh namespace will be created. So, local namespaces are created when required and are deleted when no longer needed. Note that a local namespace is created when a function is called, not when it is defined.

Each imported module has its own global namespace which is
separate from the global namespace of the main module. If the
importing module needs to use any name from any of these global
namespaces, the name has to be prefixed with the module name. We
have already seen this in the previous chapter. So, there can be many
global namespaces when your program is executing. One global
namespace that will always be there is the namespace corresponding
to the `__main__` module, which is your main module (executing
script), and there may be other global namespaces, each corresponding to an imported module. The namespace that belongs
to your main module is created when the program starts executing,
and a module namespace is created when it is first imported.

We know that the name of the module for our executing script is
`__main__`. Any code that you type at the interactive prompt is also
considered part of the module `__main__` , all names that you define
interactively are global variables that are available in the whole
interactive session. They live in the global namespace of `__main__`
module, when you restart the session, this global namespace will be
recreated. You must have noticed that after we run the program, the
global names of our program are available on the interactive prompt
until we restart.

## Inspecting namespaces

Local and global namespaces are usually implemented through
dictionaries, where names are keys and values are corresponding
objects to which the names are bound. Built-in namespace is
implemented with the help of a module. The built-in names live inside
the standard library module named `builtins`. We can import this
module and use the `dir` function to see all the predefined built-in
names.

```python
import builtins

print(dir(builtins))
```

The `dir` function can be used to get the names in a global or local
namespace. This function gives us just the keys of the dictionary, to
get the full dictionary we can use the `vars` function. Without
arguments, the functions `dir` and `vars` work on the most locally
enclosing scope in which they are executed.

There are two `built-in` functions called `locals` and `globals`
that can be used to examine the names contained in local and global
namespaces. `globals()` returns a dictionary that contains names in
the global namespace of the module and `locals()`, when placed
inside a function, returns a dictionary that contains local names
accessible from that function.

If `locals()` is called outside a function at the top level of the
program, it behaves like the `globals()` function. If `globals()` is
called inside a function, it returns a dictionary that contains all names that can be accessed globally from that function. If the function is defined in a separate module, it gives the global names of the module where the function was defined and not the global names of the module where the function is called.

## Scopes

A name cannot be accessed from just anywhere inside a program.
Every name-object binding has a scope and this scope determines
the part of the program where you can access that particular name
without using any prefix. Scope of a name depends on where it has
been defined inside the file. Names that are assigned outside all
functions, at the top level of a file, have global scope and they can be accessed throughout the file. Names that are assigned inside a
function have local scope, and these names can be accessed only
inside the function in which they are defined.

## Name resolution

When we use a name inside the program, Python needs to look for that name in the appropriate namespace and fetch the object that it is referring to. Python uses the concept of scope to search the namespaces. Scope determines the namespaces that are accessible for searching. If a name has local scope, then it will be searched in its own local namespace or the local namespaces of enclosing functions, or in global and built-in namespaces. If a name has global scope, then it will be searched in global and built-in namespaces. This process is called **name resolution**.
Python follows a rule for name resolution commonly known as **LEGB** rule. This rule specifies the order in which namespaces are searched while looking for a name.

- L : Local namespace
- E : Enclosing local namespaces(if any)
- G : Global namespace
- B : Built in namespace

If the name that you are using
has local scope, then Python first looks for the name in its own local
namespace, then in the local namespaces of the enclosing functions
starting from the nearest enclosing function (if there are any),
followed by the global namespace of the current module, and then
finally in the built-in namespace. It stops the search at the first place where the name is found. If the name has a global scope, it is first searched in global namespace and then in the built-in namespace. If the name is not found in any of the namespaces, then a `NameError`
is raised.
A consequence of this rule is that local names can mask global
and built-in names and global names can mask built-in names. If you
reassign any of the built-in names in your program then you will lose
the original functionality of that name.

## `global` statement

The global statement allows you to create or change a global
variable from within a function.

The global declaration is a namespace declaration which indicates
that the specified name lives in the global namespace and should be
rebound there instead of introducing a new name in the local
namespace. It is possible to specify more than one global variable by using the same global statement. So, we could specify more global variables by using a comma. `global x, y, z`

You can freely use a global name inside a function, but if you want to
reassign a global variable inside a function, you need to declare it
global by writing the global statement. Without the global declaration, the assignment will create a new local variable. This requirement of a global declaration for reassigning a global variable is actually good, otherwise you might unknowingly change a global variable leading to problems. This could happen if you are unaware of a global variable that has the same as the local variable that you are creating inside the function, you would think that a local is being created but actually it will the reassign the global variable. The global declaration is required only if you have to reassign the global variable; a mutable global variable can be changed in-place inside the function without the global declaration.

## `nonlocal` statement

There is a similar statement that uses the keyword `nonlocal` and it allows us to reassign names that are in the enclosing function scope. Like global statement, `nonlocal` statement is also a namespace declaration which indicates that the specified variable lives in some enclosing function scope.
To prevent the creation of a new local variable, we need to declare the variable as nonlocal by writing the `nonlocal` statement.

There are two differences between the `global` statement and
`nonlocal` statement:

- The first difference is that in a `global` statement you can write a variable name even if it does not exist in the global space, while in a `nonlocal` statement you cannot write a variable name that does not exist in an enclosing function.

- The other difference between `global` and `nonlocal` statement is related to the searching of name. If a name is declared global, then the search for it starts at the global scope and continues in the builtin scope. If a name is declared `nonlocal`, search is not done in the `global` or built in scopes. It is searched only in the enclosing function scopes.

## The End
