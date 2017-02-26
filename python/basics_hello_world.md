#### True or False
```python
In [4]: True
Out[4]: True

In [5]: False
Out[5]: False

In [6]: True + True
Out[6]: 2

In [7]: bool(True)
Out[7]: True

In [8]: bool(False)
Out[8]: False

In [9]: bool(0)
Out[9]: False

In [10]: bool([])
Out[10]: False

In [11]: bool("")
Out[11]: False

In [12]: bool("Treehouse")
Out[12]: True

In [13]: bool([1,2,3])
Out[13]: True

In [14]: bool(None)
Out[14]: False

```
#### Comparisons
```python
In [15]: 5 == 5
Out[15]: True

In [16]: 5 == 7
Out[16]: False

In [17]: 5 !=7
Out[17]: True

In [18]: 5 < 7
Out[18]: True

In [19]: 5 > 7
Out[19]: False

In [20]: 5 <= 7
Out[20]: True

In [21]: 5 >= 7
Out[21]: False

In [22]: 5 is 5
Out[22]: True

In [23]: a = 5

In [24]: b = 5

In [25]: a is b
Out[25]: True

In [26]: c = []

In [27]: d = []

In [28]: c == d
Out[28]: True

In [29]: c is d
Out[29]: False

In [30]: e = None

In [31]: e is None
Out[31]: True

In [32]: e == None
Out[32]: True

```
#### If, Elif, Else
```python
In [33]: if 5 > 2:
    ...:     print("Well, yeah")
    ...:     
Well, yeah

In [34]: age = 34 * 365

In [35]: if age > 10000:
    ...:     print("Wow, over 10,000 days old!")
    ...:     
Wow, over 10,000 days old!

In [36]: age = 5000

In [37]: if age > 10000:
    ...:     print("Wow, over 10,000 days old!")
    ...: else:
    ...:     print("Keep going! You'll get there!")
    ...:     
Keep going! You'll get there!

In [38]: age = 22000

In [39]: if age > 20000:
    ...:     print('Time to retire!')
    ...: elif age > 10000:
    ...:     print('Lots of time left!')
    ...: else:
    ...:     print('Time to get started!')
    ...:     
Time to retire!

In [40]: if not age > 25000:
    ...:     print("Whippersnapper")
    ...:     
Whippersnapper

```
#### Containment(in)
```python
In [41]: "cheese" in "cheeseshop"
Out[41]: True

In [42]: cheeseshop = []

In [43]: "cheese" in cheeseshop
Out[43]: False

In [44]: days_open = ['Monday', 'Tuesday', 'Wednesday', 'Thursd
    ...: ay']

In [45]: today = 'Tuesday'

In [46]: if today in days_open:
    ...:     print("Come on in!")
    ...:     
Come on in!

In [47]: today = "Saturday"

In [48]: if today in days_open:
    ...:     print("Come on in!")
    ...: else:
    ...:     print("Sorry, we're closed")
    ...:     
Sorry, we're closed

In [49]: if today not in days_open:
    ...:     print("Sorry, we're closed")
    ...:     
Sorry, we're closed
```

#### Around and Around(for, while)
```python
In [50]: my_list = ['hello', 'how', 'are', 'you']

In [51]: for word in my_list:
    ...:     print(word)
    ...:     
hello
how
are
you

In [52]: for letter in 'abcdefghijklmnopqrstuvwxyz':
    ...:     print(letter.upper())
    ...:     
A
B
C
D
E
F
G
H
I
J
K
L
M
N
O
P
Q
R
S
T
U
V
W
X
Y
Z

In [53]: for num in [1, 2, 3, 4]
  File "<ipython-input-53-ed4a31c5102d>", line 1
    for num in [1, 2, 3, 4]
                           ^
SyntaxError: invalid syntax


In [54]: for num in [1, 2, 3, 4]:
    ...:     if num % 2 == 0:
    ...:         print(num)
    ...:         
2
4

In [55]: start = 10

In [56]: while start:
    ...:     print(start)
    ...:     start -= 1
    ...:     
10
9
8
7
6
5
4
3
2
1

In [57]: names = ['Kenneth', 'Amy', 'Andrew', 'QUIT', 'Lacey']

In [58]: for name in names:
    ...:     if name == 'QUIT':
    ...:         break
    ...:     print(name)
    ...:     
Kenneth
Amy
Andrew

In [59]: for name in names:
    ...:     if name == 'QUIT':
    ...:         continue
    ...:     print(name)
    ...:     
Kenneth
Amy
Andrew
Lacey

```

#### Having a Conversation
```python
In [60]: input("What's your age?")
What's your age?34
Out[60]: '34'

In [61]: age = input("What's your age? ")
What's your age? 34

In [62]: age
Out[62]: '34'

In [63]: age + 1
---------------------------------------------------------------
TypeError                     Traceback (most recent call last)
<ipython-input-63-87804d39a9ea> in <module>()
----> 1 age + 1

TypeError: Can't convert 'int' object to str implicitly

In [64]: int(age)
Out[64]: 34

In [65]: age + 1
---------------------------------------------------------------
TypeError                     Traceback (most recent call last)
<ipython-input-65-87804d39a9ea> in <module>()
----> 1 age + 1

TypeError: Can't convert 'int' object to str implicitly

In [66]: b = int(age)

In [67]: b + 1
Out[67]: 35

In [68]: age = int(input("What's your age? "))
What's your age? 35

In [69]: age
Out[69]: 35

In [70]: age += 10

In [71]: age
Out[71]: 45
```
#### Fully Functional
```python
def hows_the_parrot():
    print("He's pining for the fjords!")

hows_the_parrot()

def lumberjack(name):
    if name.lower() == 'kenneth':
        print("Kenneth's is a lumberjack and he's OK!")
    else:
        print("{} sleeps all night and {} works all day!".format(name, name))

lumberjack("Kenneth")
lumberjack("Peter")

/home/pt/.pyenv/versions/3.4.3/bin/python /home/pt/tree-house-pycharm/functions.py
He's pining for the fjords!
Kenneth's is a lumberjack and he's OK!
Peter sleeps all night and Peter works all day!

Process finished with exit code 0


def hows_the_parrot():
    print("He's pining for the fjords!")

hows_the_parrot()

def lumberjack(name, pronoun):
        print("{}'s a lumberjack and {} OK!".format(name, pronoun))

lumberjack("Kenneth", "he's")
lumberjack("Lacey", "she's")
lumberjack("Sam", "they're")
lumberjack()

/home/pt/.pyenv/versions/3.4.3/bin/python /home/pt/tree-house-pycharm/functions.py
Traceback (most recent call last):
He's pining for the fjords!
  File "/home/pt/tree-house-pycharm/functions.py", line 12, in <module>
    lumberjack()
TypeError: lumberjack() missing 2 required positional arguments: 'name' and 'pronoun'
Kenneth's a lumberjack and he's OK!
Lacey's a lumberjack and she's OK!
Sam's a lumberjack and they're OK!


def average(num1, num2):
    return (num1 + num2) / 2

avg = average(2, 8)
print(avg)

/home/pt/.pyenv/versions/3.4.3/bin/python /home/pt/tree-house-pycharm/functions.py
5.0

Process finished with exit code 0
```

#### The Exception to the Rule
```python
try:
    count = int(input("Give me a number: "))
except ValueError:
    print("That's not a number!")
else:
    print("Hi " * count)
```
