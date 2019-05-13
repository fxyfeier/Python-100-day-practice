
## Day02 - Python elements

#### Instruction and programs

The hardware system of a computer usually consists of five parts, including: Arithmetic Unit, Controller, Memory, Input device and Output decive..Among them, the arithmetic unit and the controller together is what we usually call the central processing unit, which function is to execute all kinds of computation, to control instructions and process the data in the computer software.A program is really a collection of instructions, where we take a series of instructions, put them together in some way, and then use those instructions to control the computer to do what we want it to do. The essential structure of computer is the 'Von Neumann architecture', which has two key points. One is to seperate the storage device from the CPU, and the other is to propose the binary encoding of data(refering to https://en.wikipedia.org/wiki/Von_Neumann_architecture)。

#### Variables and types

In programming, a variable is a carrier for storing data. The variables are actually a block of memory, in which the values of variables can be read and modified. 

There are many types of data that a computer can process, such as a text, graphics, audie, video and so on, There are a lot of data types in Python, and allow us to customize the new data types, so let's start with a few common data types.

*Integer(int): Python can handle any size of an integer (in Python 2.x ,int and long are two types of integers, but this makes little sense to distinguish for Python, so in Python 3 x integers only int this one)
*Float: A floating number is a decimal number, so it is called a floating number because the decimal point of a floating number is variable in scientific notation.
* String: A string enclosed in single or double quotes for any text, such as ` 'hello' ` and ` ` "hello", string representation and the original string, byte string representation, Unicode string representation, and can be written into the form (with three single or double quotation marks the beginning of three single or double quotation marks the end).
*Boolean: the Boolean value only ` True `, ` False ` two values(Pay attention to case)
*The plural form: form such as ` 3 + 5 j `, like math plural said, the only difference is the imaginary part of ` I ` replaced by ` j `

#### Variable naming

In Python, variable naming follows these highly recommended rules:

- Hard and fast rules：
  - Variable names consist of letters(Unicode characters in a broad sence, excluding special characters), numbers, and underscores. Numbers cannot begin.
  - Case-sensitive (uppercase ` a ` and lowercase ` a ` are two different variables).
  - Do not conflict with keywords(special meaning words) and system reserved words (names of functions, modules, etc.).
- PEP 8 requirements：
  - Spell with lowercase letters and connect multiple words with underscores.
  - Protected instance properties begin with a single underscore( _ )  
  - Private instance properties begin with two underscores (__main__)

As a professional programmer, it is also very important to name variables by their meaning.

#### Use of variables

```Python
"""
Variables are used to hold data and perform arithmetic operations

"""

a = 321
b = 123
print(a + b)
print(a - b)
print(a * b)
print(a / b)
print(a // b)
print(a % b)
print(a ** b)

```

"""
Use the input function
Type conversion using int()
A string formatted for output with a placeholder

"""

a = int(input('a = '))
b = int(input('b = '))
print('%d + %d = %d' % (a, b, a + b))
print('%d - %d = %d' % (a, b, a - b))
print('%d * %d = %d' % (a, b, a * b))
print('%d / %d = %f' % (a, b, a / b))
print('%d // %d = %d' % (a, b, a // b))
print('%d %% %d = %d' % (a, b, a % b))
print('%d ** %d = %d' % (a, b, a ** b))

```

```Python

"""
Use type() to check the type of the variable

"""

a = 100
b = 12.345
c = 1 + 5j
d = 'hello, world'
e = True
print(type(a))
print(type(b))
print(type(c))
print(type(d))
print(type(e))

```
We can use Python's built-in functions when converting variable types 

- int()： To convert a numeric value or string to an integer, you can specify a base.
- float()：Converts a string to a floating point number.
- str()：Converts the specified object to a string form, specifying the encoding type.
- chr()：Converts an integer to the corresponding string (one character) for that encoding.
- ord()：Converts a string (one character) to its corresponding encoding (integer).

### The operator

| Operators                                                    | Description                      |
| ------------------------------------------------------------ | ---------------------------------|
| `[]` `[:]`                                                   | Subscript, slice                 |
| `**`                                                         | index                            |
| `~` `+` `-`                                                  | Bitwise negation,  sign          |
| `*` `/` `%` `//`                                             | Multiply, divide, mold, Divisible|
| `+` `-`                                                      | Add, subtract                    |
| `>>` `<<`                                                    | Shift right, left shift          |
| `&`                                                          | Bitwise and                      |
| `^` `|`                                                      | Bitwise XOR, bitwise or          |
| `<=` `<` `>` `>=`                                            |                                  |
| `==` `!=`                                                    | (not)Equal to                    |
| `is`  `is not`                                               | Identity operator                |
| `in` `not in`                                                | Member operator                  |
| `not` `or` `and`                                             | Logical Operators                |
| `=` `+=` `-=` `*=` `/=` `%=` `//=` `**=` `&=` `|=` `^=` `>>=` `<<=`|Compound assignment operator|

>**Note：** In actual development, if we don't know the priority, we can use parentheses to ensure the order of execution of the operation.

"""
Use of operators

"""

a = 5
b = 10
c = 3
d = 4
e = 5
a += b
a -= c
a *= d
a /= e
print("a = ", a)

flag1 = 3 > 2
flag2 = 2 < 1
flag3 = flag1 and flag2
flag4 = flag1 or flag2
flag5 = not flag1
print("flag1 = ", flag1)
print("flag2 = ", flag2)
print("flag3 = ", flag3)
print("flag4 = ", flag4)
print("flag5 = ", flag5)
print(flag1 is True)
print(flag2 is not False)

```

### Practice

#### Practice1：Fahrenheit temperature is changed to Celsius.

```Python
"""

F = 1.8C + 32

"""

f = float(input('Input Fahrenheit temperature:'))
c = (f - 32) / 1.8
print('%.1f Fahrenheit temperature = %.1f Celsius' % (f, c))

```

#### Practice2： Enter the radius of the circle to calculate the perimeter and area.

```Python
"""
Enter the radius of the circle to calculate the perimeter and area.

"""

import math

radius = float(input('Input the radius of the circle: '))
perimeter = 2 * math.pi * radius
area = math.pi * radius * radius
print('Perimeter: %.2f' % perimeter)
print('Area: %.2f' % area)

```

#### Practice3：Enter the year to determine if it is a leap year.

```Python
"""
Enter the year If it is a leap year output True, otherwise output False

"""

year = int(input('Input year: '))
# If the code is too long to write in a line, it is not easy to read. We can use \ or () to break the line.
is_leap = (year % 4 == 0 and year % 100 != 0 or
           year % 400 == 0)
print(is_leap)
```
