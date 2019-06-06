
## Object-oriented programming

What's the 'object-oriented programming':

> * Take a set of data structures and methods that process them and make them into a (project), 
* To classify objects that behave in the same way as (classes),
* Through the (encapsulation) to hide internal details,
* Through the (inheritance) to implement classes' (specialization) and (generalization),
* Dynamic allocation based on object types is implemented by (polymorphism). 

Before we said that the program is a set of instructions, the statements that we write in a program become one or more instructions and are executed by the CPU. To simplify the program, we introduced the concept of function, and we put relatively independent and frequently resued code into a function. So we just call function when we need to use them. If a function is too complex and bloated, we can further divide the function into sub-functions to reduce the complexity of the system.

The beginnings of Object-oriented programming can be traced back to the eariler Simular language.

### Classes and objects

Simple put, a class is a blueprint and template for an object, and an object is an instance of a class.

#### Definning class

Use the 'class' keyword to define classes in Python, and then define methods in the class using funtions, in this way we can describe the dynamic characteristics of the object. The code is shown below:

```Python

class student(object):
    #__init__ is an special method used to initialize an object when it is created.
    #In this way, we can bind the name and age  properties for the object of student 
    #PEP 8 requires that identifier's name be all lowercase and multiple words are underlined.

    def __init__(self, name, age):
	self.name = name
	self.age = age

    def study(self, course_name):
	print('%s, it's time to study %s.' %(self.name, course_name))

    def read(self):
	if self.age < 18:
	    print('%s can only read <Python Code>.' % self.name)
	else:
	    print('%s can choosed any book you like.' % self.name)
	
    
```
> **Note**： Funtions written in a class, called methods, are the messages an boject can receive.

#### Create and use an object

Once we have definded a class, we can creare an object and send a message to it.
``` python

def main():
    # Create a student object and specify the name and age
    stu1 = student('Phil', 33)
    # Send a study notice to the object
    stu1.study('Python')
    # Send a reading notice to the object
    stu1.read()
    stu2 = student('Philip' 15)
    stu2.study('English')
    stu2.read()

if __name__ == '__main__':
    main()

```
#### Access visibility

For the above code, the programmer with Java, c #, c + + programming experience may ask, we give a ` student ` object binding ` name ` and ` age ` properties exactly is how to access (also known as visibility) because in many object-oriented programming language, we usually sets the attributes of the object to a private or protected. In Python, there are only two kinds of access for attributes and methods, public and private. If we want the property to be private, we can start naming the property with two underscores. 


```Python
class Test:

    def __init__(self, foo):
        self.__foo = foo

    def __bar(self):
        print(self.__foo)
        print('__bar')


def main():
    test = Test('hello')
    # AttributeError: 'Test' object has no attribute '__bar'
    test.__bar()
    # AttributeError: 'Test' object has no attribute '__foo'
    print(test.__foo)


if __name__ == "__main__":
    main()
```

However, Python does not syntactically strictly guarantee the privacy of a private property or method, It just names private properties and methods to block access to them, in fact, if you know the rules of change the name still can access to them, the following code can verify this set, so you can use such words to explain, is 'We are all consenting adults here' because most programmers agree that openness is better than closure, and programmers are responsible for their own behavior.


```Python
class Test:

    def __init__(self, foo):
        self.__foo = foo

    def __bar(self):
        print(self.__foo)
        print('__bar')


def main():
    test = Test('hello')
    test._Test__bar()
    print(test._Test__foo)


if __name__ == "__main__":
    main()
```

###  Pillars of Object orientation 

Object orientation has three pillars: encapsulation inheritance and polymorphism.
The understanding of encapsulation is to hide any implementation details that can be hidden, exposing (providing) only simple programming interfaces to the outside world. The way we define methods in a class is to encapsulate the data and the operations on the data, and after we create the object, we only need to send a message to the object (calling the method) to execute the code in the method, which means we only need to know the name of the method and the parameters passed in (external view of the method), but not the implementation details inside the method (internal view of the method).

###  Practice

#### Exercise 1: Define a class that describes the digital clock

#### Exercise 2: define a class that describes a point on a plane and provides methods for moving the point and calculating the distance to another point





