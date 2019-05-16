
## Day04 - Loop structure

### Application area

If we need to repeatedly execute a certain instruction in the program, such as using the program to control the robot to play football, if the robot holds the ball and has not entered the range of the shot, then we must always send instructions to let the robot run toward the goal. We may have noticed that the description just mentioned is not only the action that needs to be repeated, but also the branch structure we talked about in the previous chapter. To give a simple example, in our program to print a string such as &quot;hello, world&quot; on the screen every 1 second and last for an hour, we certainly can't `print('hello , world') ` 3,600 times. If we really need to do this, the programming work is too boring. Therefore, we need to understand the loop structure. With the loop structure, we can easily control something to repeat, repeat, and repeat. There are two ways to construct a loop structure in Python, one is a `for-in` loop, and the other is a `while` loop.

#### for-in

```Python
"""
Use the for loop to achieve 1~100 summation

"""

sum = 0
for x in range(101):
    sum += x
print(sum)
```

> **Notice：** the `range` type in the above can be used to generate a constant sequence of values, and this sequence is usually used in loops, for example:

- `range(101)` can produce a sequence of integers from 0 to 100.
- `range(1, 100)` can produce a sequence of integers from 1 to 99.
- `range(1, 100, 2)` can produce an odd sequence of 1 to 99, where 2 

Knowing this, we can use the following code to achieve an even sum between 1 and 100.

```Python

sum = 0
for x in range(2, 101, 2):
    sum += x
print(sum)

```

The same functionality can also be achieved by using a branching structure in the loop, as shown below.

```Python

sum = 0
for x in range(1, 101):
    if x % 2 == 0:
        sum += x
print(sum)
```

#### while loop

If we want to construct a loop structure that doesn't know the exact number of loops, we recommend using a `while` loop, which controls the loop with an expression that produces or converts a `bool` value. If the value of the expression is `True`, the loop continues and the value of the expression ends with the `False`. Below we pass a small game of "guess the number" (the computer gives a random number between 1 and 100, the person enters the number that he guessed, the computer gives the corresponding prompt information, until the person guesses the number from the computer) See how to use the `while` loop

```Python
"""
Guess the number game
The computer has a random number between 1 and 100.
The computer gives a hint bigger/smaller/Bingo! based on the number guessed by the person.

"""

import random

answer = random.randint(1, 100)
counter = 0
while True:
    counter += 1
    number = int(input('Enter number: '))
    if number < answer:
        print('Bigger')
    elif number > answer:
        print('Smaller')
    else:
        print('Bingo!')
        break
print('You guessed %d times in total' % counter)
if counter > 7:
    print(' Your IQ balance is obviously insufficient ')
```

```Python
"""
Output multiplication table (99 table)

"""

for i in range(1, 10):
    for j in range(1, i + 1):
        print('%d*%d=%d' % (i, j, i * j), end='\t')
    print()
```

### Day04 practice:

#### Practice 1: Enter a number to determine if it is a prime number.

#### Practice 2: Enter two positive integers to calculate the greatest common divisor and the least common multiple.

#### Practice 3: Print a triangle pattern.

"""
*
**
***
****
*****

    *
   **
  ***
 ****
*****

    *
   ***
  *****
 *******
*********
"""