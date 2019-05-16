
## Day03 - Branch structure

### Application scenario

Different from the sequential structure. For example, if we design a game, the first pass condition of the game is that the player gets 1000 points. After completing this game, we have to decide whether to enter the second level or tell the player "Game Over" according to the player's score. Two branches are generated, and only one of the two branches will be executed. This is the branch structure in the program.

#### if statement

if...elif...else

```Python
"""
User authentication

"""

username = input('User name:')
password = input('Password:')
#If we don't want an  echo from the back end when we enter a password, we can use the getpass function of the getpass module.
# import getpass
# password = getpass.getpass('Password: ')
if username == 'admin' and password == '123456':
	print('Successful authentication!')
else:
	print('Unsuccessful authentication!')

If we want to construct more branches, we can use the `if...elif...else...` structure, such as the following piecewise function to evaluate.

$$f(x)=\begin{cases} 3x-5&\text{(x>1)}\\x+2&\text{(-1}\leq\text{x}\leq\text{1)}\\5x+3&\text {(x<-1)}\end{cases}$$

```Python

        3x - 5  (x > 1)
f(x) =  x + 2   (-1 <= x <= 1)
        5x + 3  (x < -1)
"""

x = float(input('x = '))
if x > 1:
    y=3 * x -5
elif x >= -1:
    y = x + 2
else:
    y = 5 * x + 3
print('f(%.2f) = %.2f'%(x,y))


Of course, according to the needs of actual development, the branch structure can be nested, and the above code can alsi be written as follows:

```Python

x = float(input('x = '))
if x > 1:
    y = 3 * x - 5
else:
    if x >= -1:
        y = x + 2
    else:
        y = 5 * x + 3
print('f(%.2f) = %.2f' % (x, y))
```
> **Note：**In the Python zen we mentioned at Day01, there is such a sentence "Flat is better than nested." The reason for this is because the nested structure will have a serious impact on the readability of the code. If we can use a flat structure, don't use nesting, so the previous one is better.

### Day03 practice:

#### Practice 1: Interchange between imperial units and metric units.

#### Practice 2: Rolling the dice to decide what to do.

> **Hint：** Using the random module's randint function to generate a random number of the specified range to simulate the dice.

#### Practice 3: Conversion between percentage score and grade.

90 points or more    --> A
80~89 points         --> B
70~79 points	     --> C
60~69 points         --> D
60 points or less    --> E

#### Practice 4: Enter the length of the three sides. If can be form a triangle, calculate the perimeter and area.

> **Hint：** Using the `sqrt` function of the `math` module to calculate the square root. The formula for calculating the area of a triangle by the side length is called [Helen's formula] (https://en.wikipedia.org/wiki/Heron%27s_formula)

#### Practice 5: Personal income tax calculator

> **Hint：** Using Python's built-in `abs()` function to take absolute values to handle `-0` issues.



