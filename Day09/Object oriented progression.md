
## Object oriented progression

### @property decorator

We talked about attributes and method access in Python, although we do not recommend setting the property to private, it's also problematic to expose properties directly to the outside. For example, there is no way to check that the value assigned to an attribute is valid. Our previous recommendation was to start the name of the property with a single underscore to indicate that the property is protected and direct access is not recommended. If we want to access a property, we can do so through the getter and setter methods of the property. To do this, consider using the @property wrapper to decorator's getters and setters, making access to properties secure and convenient, and the code is shown below:

``` Python
class Person(object):

    def __init__(self, name, age):
        self._name = name
        self._age = age
        
    #getter method
    @property
    def name(self):
        return self._name
    
    @property
    def age(self):
        return self._age 
    
    #setter method
    @age.setter
    def age(self, age):
        self._age = age
        
    def play(self):
        if self._age <= 16:
            print('%s is playing airplane chess' % self._name)
        else:
            print('%s is playing cat' % self._name)
            

def main():
    person = Person('Phil', 12)
    person.play()
    person.age = 22
    person.play()
#     person.name = 'Eva'   # AttributeError: can't set attribute
#     person.play()

if __name__ == '__main__':
    main()

```

### \_\_slots\_\_ magic

Python is a dynamic language that allows us to bind or unbind new properties or methods to objects while the program is running. However, if we need to qualify objects of a custom type to bind only certain properties, 
we can use \_\_slots\_\_ in the class.

It is important to note that \_\_slots\_\_ only restrict the current class, not to the subclasses. 


### Static methods and class methods

Previously, the methods we defined is belonged to object methods, meaning these methods used to send message to the object. In fact, the methods in a class don't have to be all object methods. For example, we define a triangle class, by passing in three sides to construct a triangle, and provide methods to calculate its perimeter and area. But the incoming three sides are not necessarily construct triangle, so we can write a method to verify whether three sides can form a triangle. This method is obviously not an object method,
for the triangle object was not created when this method was called. So this method belongs to the triangle class but not to the triangle object, hence we can use static methods to solve this kind of problem. The code is as follows:

```Python
import math

class Triangle(object):
    
    def __init__(self, a, b, c):
        self._a = a
        self._b = b
        self._c = c
        
    @staticmethod
    def is_valid(a, b, c):
        return a + b > c and a + c > b and b + c > a
    
    def perimeter(self):
        return self._a + self._b + self._c
    
    def area(self):
        half = self.perimeter() / 2
        return math.sqrt(half * (half - self._a) * (half - self._b) * (half - self._c))
    
    
def main():
    a, b, c = 3, 4, 1
    #Both static method and object method are called by sending message to  the class
    if Triangle.is_valid(a, b, c):
        t = Triangle(a, b, c)
        print(t.perimeter())
        print(t.area())
        #You can also call an object method by sending a message to the class /
        #by passing in the object that receives the message as a parameter
        # print(Triangle.perimeter(t))
        # print(Triangle.area(t))
    else:
        print('Cannot construct a triangle.')
        

if __name__ == '__main__':
    main()   
```
Similar to static methods, is Class methods. Its first parameter convention is called cls, which represents the object of the information related to the current class (the class itself is also an object, sometimes called the metadata object of the class), through which we can obtain the information related to the class and create the object of the class, as shown below:

### Relationships between classes

Simply put, there are three kinds of relationships between classes :is-a has-a and use-a.



































