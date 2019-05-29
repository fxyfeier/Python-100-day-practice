
## Use of functions and modules

###  Why use functions

To write high-quality code, the first thing to solve is the problem of duplicate code.

### Define function   (def)

In Python you can use the `def` keyword to define functions. Like variables, each function also has a sound name, and the naming convention is the same as the variable naming convention. The parameters passed to the function can be placed in parentheses after the function name. This is very similar to the mathematical function. The parameters of the function in the program are equivalent to the arguments of the function in mathematics. After the function is executed, we can return a value  by the `return` keyword, which is equivalent to the dependent variable of the function in mathematics.

### Function arguments 

In Python, function arguments can have default values and support for variable arguments, so Python doesn't need to be supported like other languages [function overload]

```Python
# The * in front of the args name indicates that args is a variable parameter
# That is, we can pass 0 or more parameters when calling the add function.
def add(*args):
    total = 0
    for val in args:
        total += val
    return total


print(add())
print(add(1))
print(add(1, 2))
print(add(1, 2, 3))
print(add(1, 3, 5, 7, 9))
```
### Using module management functions

For any programming language, names such as variables and functions are a headache, because we encounter embarrassing situations like naming conflicts. The simplest scenario is to define two functions with the same name in the same .py file. Since Python doesn't have the concept of function overloading, the latter definition will override the previous definition, which means that the two functions of the same name are actually only One is there.


```Python
def foo():
    print('hello, world!')


def foo():
    print('goodbye, world!')

# What will the following code output?

foo()
```
The above situation can be easily avoided, but if the project is developed by a multi-person team, there may be multiple programmers in the team who define a function named `foo`, then how to solve this problem? The answer is actually very simple. Every file in Python represents a module. We can have functions with the same name in different modules. When using functions, we can import the specified modules through the `import` keyword. Which module to use is the `foo` function, the code is as follows.

module1.py

```Python
def foo():
    print('hello, world!')
```

module2.py

```Python
def foo():
    print('goodbye, world!')
```

test.py

```Python
from module1 import foo

# output: hello, world!
foo()

from module2 import foo

# Output: goodbye, world!
foo()
```
You can also distinguish which one to use in the way shown below.

test.py

```Python
import module1 as m1
import module2 as m2

m1.foo()
m2.foo()
```
It should be noted that if the module we import has executable code in addition to the definition function, then the Python interpreter will execute the code when importing the module. In fact, we may not want this, so if we are The execution code is written in the module. It is best to put the execution code into the conditions shown below. If the module is run directly, the code under the if condition will not be executed because only the module directly executed The name is "\_\_main\_\_".

module3.py

```Python
def foo():
    pass


def bar():
    pass

# __name__ is an implicit variable in Python which represents the name of the module
# Only the name of the module directly executed by the Python interpreter is __main__
if __name__ == '__main__':
    print('call foo()')
    foo()
    print('call bar()')
    bar()
```

test.py

```Python

As you can see from the above program, when we extract the recurring and relatively independent functions in the code into functions, we can combine these functions to solve more complex problems, which is why we define and use functions. A very important reason.

### Finally, let's discuss the issue of variable scope in Python.

```Python
def foo():
    b = 'hello'

    def bar():  # Python can define functions inside functions
        c = True
        print(a)
        print(b)
        print(c)

    bar()
    # print(c)  # NameError: name 'c' is not defined


if __name__ == '__main__':
    a = 100
    # print(b)  # NameError: name 'b' is not defined
    foo()
```
The above code can execute smoothly and print out 100 and "hello", but we noticed that there are no variables `a` and `b` defined inside the `bar` function, then `a` and `b` Where did it come from? We define a variable `a` in the `if` branch of the above code, which is a global variable, which is global scope because it is not defined in any function. In the `foo` function above we define the variable `b`, which is a local variable defined in the function, which is a local scope and cannot be accessed outside the `foo` function; For the `bar` function inside the `foo` function, the variable `b` belongs to the nested scope, which we can access in the `bar` function. The variable `c` in the `bar` function belongs to the local scope and is inaccessible outside the `bar` function. In fact, Python looks for a variable in the order of "local scope", "nested scope", "global scope" and "built-in scope". The first three are already seen in the above code. By the way, the so-called "built-in scope" is the implicit identifiers `min`, `len`, etc. built into Python are all built-in scopes.

Looking at the code below, we want to modify the value of the global variable `a` through a function call, but in fact the following code can't do it.

```Python
def foo():
    a = 200
    print(a)  # 200


if __name__ == '__main__':
    a = 100
    foo()
    print(a)  # 100
```
After calling the `foo` function, we find that the value of `a` is still 100. This is because when we write `a = 200` in the function `foo`, we redefine a name named `a`. A local variable, which is not the same variable as the `a` of the global scope, because the local scope has its own variable `a`, so the `foo` function no longer searches for `a` in the global scope. If we want to modify `a` in the global scope in the `foo` function, the code looks like this.

```Python
def foo():
    global a
    a = 200
    print(a)  # 200


if __name__ == '__main__':
    a = 100
    foo()
    print(a)  # 200
```
We can use the `global` keyword to indicate that the variable `a` in the `foo` function comes from the global scope. If there is no `a` in the global scope, the code in the following line will define the variable `a` and It is placed in the global scope. Similarly, if we want a function inside a function to modify a variable in a nested scope, we can use the `nonlocal` keyword to indicate that the variable comes from a nested scope.

In development, we should minimize the use of global variables, because the scope and impact of global variables is too broad, and unexpected modifications and uses may occur. In addition, global variables have a longer life than local variables. The cycle may cause the memory occupied by the object to be unavailable for a long time [garbage collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)).

 Reducing the use of global variables means that we should try to make the scope of the variable inside the function, but if we want to extend the life cycle of a local variable , so that it can still be accessed after the function call ends, this time you need to use [closure](https://en.wikipedia.org/wiki/Closure_(computer_programming))

Having said that, the conclusion is very simple. From now on we can write the Python code in the following format. This improvement is actually a huge step on the basis of understanding the function and scope.

```Python
def main():
    # Todo: Add your code here
    pass


if __name__ == '__main__':
    main()
```

### Practice 

#### Exercise 1: Implement a function that calculates the greatest common divisor and the least common multiple.


#### Exercise 2: Implement a function that determines if a number is a palindrome.

#### Exercise 3: Implement a function that determines whether a number is a prime number.

#### Exercise 4: Write a program to determine if the positive integer entered is a palindrome prime. 


