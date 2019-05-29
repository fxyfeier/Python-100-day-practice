
## Strings and common data structures

### Using strings

The Second World War prompted the birth of modern electronic computers. The original idea was simple. It used computers to calculate the missile's trajectory. So in the era when the computer was just born, the information processed by computers was mainly numerical, and the world’s number An electronic computer ENIAC can perform about 5,000 floating point operations per second. Over time, although numerical operations are still one of the most important things in the daily work of computers, today's computers process more data in the form of textual information, and Python represents the way text information is used. We said it a long time ago, that is the string type. The so-called **string** is a finite sequence of zero or more characters, generally recorded as [$${\displaystyle s=a_{1}a_{2}\dots a_{n}(0\leq n \leq \infty)}$$](https://wikimedia.org/api/rest_v1/media/math/render/svg/e29bf631b090323edd6889f810e6cff29538b161).

We can use the following code to understand the use of strings.


```Python
def main():
    str1 = 'hello, world!'
    # Calculate the length of a string by the len function
    print(len(str1))  # 13
    # Get a copy of the first letter of the string capitalized
    print(str1.capitalize())  # Hello, world!
    # Get a copy of string letters uppercase
    print(str1.upper())  # HELLO, WORLD!
    # Find the location of the substring from the string
    print(str1.find('or'))  # 8
    print(str1.find('shit'))  # -1
    # An exception is thrown when similar to find but the substring is not found
    print(str1.index('or'))
    print(str1.index('shit'))
    # Check if the string starts with the specified string
    print(str1.startswith('He'))  # False
    print(str1.startswith('hel'))  # True
    # Check if the string ends with the specified string
    print(str1.endswith('!'))  # True
    #  Centers the string at the specified width and fills the specified characters on both sides
    print(str1.center(50, '*'))
    # Place the string to the right of the specified width to the left to fill the specified character
    print(str1.rjust(50, ' '))
    str2 = 'abc123456'
    # Take the character at the specified position from the string (subscript operation)
    print(str2[2])  # c
    # String slice (from the specified start index to the specified end index)
    print(str2[2:5])  # c12
    print(str2[2:])  # c123456
    print(str2[2::2])  # c246
    print(str2[::2])  # ac246
    print(str2[::-1])  # 654321cba
    print(str2[-3:-1])  # 45
    # Check if the string is composed of numbers
    print(str2.isdigit())  # False
    # Check if the string is composed of letters
    print(str2.isalpha())  # False
    # Check if the string is composed of number and letters
    print(str2.isalnum())  # True
    str3 = '  jackfrued@126.com '
    print(str3)
    # Get a copy of string trim left and right spaces
    print(str3.strip())


if __name__ == '__main__':
    main()
```
In addition to strings, Python also has built in many types of data structures. If you want to save and manipulate data in your program, you can use existing data structures most of the time. The most common ones include lists, tuples, collections, and dictionary.

