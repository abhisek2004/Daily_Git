# Q1. Different String Formats in Python

Python supports different types of strings.

1. **Single Quote String**
   Written inside single quotes.
   Example: `'Hello'`

2. **Double Quote String**
   Written inside double quotes.
   Example: `"Hello"`

3. **Triple Quote String**
   Used for multi-line string.
   Example: `'''Hello'''`

4. **Raw String**
   Backslash is treated as normal character.
   Example: `r"C:\file"`

5. **Byte String**
   Used for bytes data.
   Example: `b"Hello"`

6. **f-String**
   Used for formatting values.
   Example: `f"My age is {20}"`

---

# Q2. int(), float(), str(), chr(), complex()

1. **int()**
   Converts value into integer.
   Example: `int(5.6)=5`

2. **float()**
   Converts value into decimal number.
   Example: `float(5)=5.0`

3. **str()**
   Converts value into string.
   Example: `str(10)="10"`

4. **chr()**
   Returns character from ASCII value.
   Example: `chr(65)=A`

5. **complex()**
   Creates complex number.
   Example: `complex(2,3)=2+3j`

---

# Q3. ord(), hex(), oct(), complex(), float()

1. **ord()**
   Returns ASCII value of character.
   Example: `ord('A')=65`

2. **hex()**
   Converts number into hexadecimal.
   Example: `hex(10)=0xa`

3. **oct()**
   Converts number into octal.
   Example: `oct(8)=0o10`

4. **complex()**
   Used for complex number.
   Example: `3+4j`

5. **float()**
   Converts value into float.
   Example: `5 = 5.0`

---

# Q4. is / is not, type(), Dynamic and Strongly Typed

1. **is Operator**
   Checks both variables are same object.
   Example: `a is b`

2. **is not Operator**
   Checks variables are different object.
   Example: `a is not b`

3. **type()**
   Returns data type of variable.
   Example: `type(5)=int`

4. **Dynamic Typed Language**
   Variable type can change.
   Example: `x=5`, later `x="Hello"`

5. **Strongly Typed Language**
   Different data types cannot mix directly.
   Example: `"5"+5` gives error.

---

# Q5. What is Python? Features and Applications

**Python** is a high-level, interpreted programming language created by Guido van Rossum.

## Features

1. Easy language
2. Simple syntax
3. Object oriented
4. Portable
5. Free and open source
6. Large library support

## Applications

1. Web Development
2. Data Science
3. AI and Machine Learning
4. Automation
5. Game Development

---

# Q6. Difference Between List and Tuple

| List            | Tuple              |
| --------------- | ------------------ |
| Uses []         | Uses ()            |
| Mutable         | Immutable          |
| Can change data | Cannot change data |
| Slower          | Faster             |

Example:
List = `[1,2,3]`
Tuple = `(1,2,3)`

---

# Q7. Type Conversion and Type Casting

## Type Conversion

Automatic conversion by Python.

Example:
`5 + 2.0 = 7.0`

## Type Casting

Manual conversion by user.

Examples:

`int(5.9)=5`
`float(5)=5.0`
`str(10)="10"`

---

# Q8. Identity and Membership Operators

## Identity Operators

1. **is** → same object
2. **is not** → different object

Example:
`a is b`

## Membership Operators

1. **in** → checks present
2. **not in** → checks absent

Example:

`"a" in "apple"` = True
`5 in [1,2,5]` = True

---

Best of luck for your exam today 🍀

# Q1. Reverse Each Word in File

```python
f=open("secret_societies.txt","r")
for line in f:
    words=line.split()
    for w in words:
        print(w[::-1],end=" ")
```

---

# Q2. Count Words in File

```python
f=open("quotes.txt","r")
data=f.read()
words=data.split()
print("Total Words =",len(words))
```

---

# Q3. Longest Word in File

```python
name=input("Enter file name:")
f=open(name,"r")
data=f.read()
words=data.split()
long=max(words,key=len)
print("Longest Word =",long)
```

---

# Q4. Regex Methods

**search()** → finds first match anywhere in string

**match()** → checks from starting only

**findall()** → returns all matches

Example:

```python
import re
s="abc123xyz"

print(re.search("\d+",s))
print(re.match("abc",s))
print(re.findall("\d+",s))
```

---

# Q5. Extract Email from File

```python
import re
f=open("email.txt","r")
for line in f:
    x=re.findall('\S+@\S+',line)
    if x:
        print(x)
```

---

# Q6. Need of try and except

Used to handle errors in program.
It stops program crash.

Example:

```python
try:
    a=10/0
except:
    print("Error")
```

Advantages:

1. Handles error
2. Prevent crash
3. Easy debugging

---

# Q7. Arc Length Using Class

Formula = radius × angle(in radian)

```python
import math

class Arc:
    def __init__(self,r,a):
        self.r=r
        self.a=a

    def show(self):
        x=self.r*math.radians(self.a)
        print("Arc Length =",x)

obj=Arc(7,60)
obj.show()
```

---

# Q8. Arc Length Program

```python
import math
r=7
a=60
l=r*math.radians(a)
print(l)
```

---

# Q9. Bank Account Program

```python
class Bank:
    def __init__(self,b=0):
        self.b=b

    def deposit(self,a):
        self.b=self.b+a

    def withdraw(self,a):
        self.b=self.b-a

    def balance(self):
        print(self.b)

x=Bank(1000)
x.deposit(500)
x.withdraw(200)
x.balance()
```

---

# Q10. Check Collinear Points

```python
x1,y1=1,1
x2,y2=2,2
x3,y3=3,3

area=x1*(y2-y3)+x2*(y3-y1)+x3*(y1-y2)

if area==0:
    print("Collinear")
else:
    print("Not Collinear")
```

---

# Q11. Inheritance and super()

Inheritance means child class gets parent properties.

```python
class A:
    def show(self):
        print("Parent")

class B(A):
    def show2(self):
        super().show()
        print("Child")

x=B()
x.show2()
```

---

# Q12. Method Overriding

Same method in parent and child class.

```python
class A:
    def show(self):
        print("Parent")

class B(A):
    def show(self):
        print("Child")

x=B()
x.show()
```

---

# Q13. Multiple Inheritance

One child gets properties of many parents.

```python
class A:
    def a(self):
        print("A")

class B:
    def b(self):
        print("B")

class C(A,B):
    pass

x=C()
x.a()
x.b()
```

---

# Q14. Point Inside Circle

```python
import math

x=3
y=4
r=5

d=math.sqrt(x*x+y*y)

if d<r:
    print("Inside")
elif d==r:
    print("On Circle")
else:
    print("Outside")
```

---

# Q15. Multiple Inheritance with Overriding

```python
class A:
    def show(self):
        print("A")

class B:
    def show(self):
        print("B")

class C(A,B):
    def show(self):
        print("C")

x=C()
x.show()
```

---

# Q16. Operator Overloading

```python
class Num:
    def __init__(self,x):
        self.x=x

    def __add__(self,o):
        return self.x+o.x

a=Num(5)
b=Num(3)
print(a+b)
```

---

# Q17. move_rectangle()

```python
class Rect:
    def __init__(self,x,y):
        self.x=x
        self.y=y

def move_rectangle(r,dx,dy):
    r.x=r.x+dx
    r.y=r.y+dy

r=Rect(2,3)
move_rectangle(r,4,5)
print(r.x,r.y)
```

---

# Q18. What is Exception?

Exception means error during program execution.

Examples:

1. ZeroDivisionError
2. ValueError
3. NameError

Example:

```python
try:
    print(10/0)
except:
    print("Error")
```

Used to control errors and continue program.

# Q1. Overlapping Circles 30 Degree

```python
import turtle
t=turtle.Turtle()

for i in range(12):
    t.circle(100)
    t.left(30)

turtle.done()
```

---

# Q2. Logo Design with Turtle

```python
import turtle
t=turtle.Turtle()

t.color("blue")
t.begin_fill()
t.circle(50)
t.end_fill()

t.penup()
t.goto(-30,-80)
t.pendown()
t.write("PYTHON")

turtle.done()
```

---

# Q3. Multiplication Table of 5 and 7 Using Thread

```python
import threading

def table(n):
    for i in range(1,11):
        print(n,"x",i,"=",n*i)

t1=threading.Thread(target=table,args=(5,))
t2=threading.Thread(target=table,args=(7,))

t1.start()
t2.start()
```

---

# Q4. What is Thread

A thread is a small unit of program execution.
It runs tasks at same time.

Advantages:

1. Fast execution
2. Saves time
3. Multiple tasks together
4. Better performance

Example:

```python
import threading

def show():
    print("Thread Running")

t=threading.Thread(target=show)
t.start()
```

---

# Q5. What is Synchronization

Synchronization means controlling threads to use shared data safely.

Used to avoid data conflict.

Example:

```python
import threading

lock=threading.Lock()

def show():
    lock.acquire()
    print("Running")
    lock.release()

t1=threading.Thread(target=show)
t1.start()
```

---

# Q6. Pen Control Methods in Turtle

1. penup() → lift pen
2. pendown() → put pen down
3. pensize() → set pen size
4. pencolor() → set color
5. speed() → set speed
6. clear() → clear screen

Example:

```python
import turtle
t=turtle.Turtle()

t.pencolor("red")
t.pensize(5)
t.forward(100)

turtle.done()
```

---

# Q7. Pattern Using Turtle

```python
import turtle
t=turtle.Turtle()

for i in range(5):
    t.forward(100)
    t.right(144)

turtle.done()
```

---

Best of luck for exam today 🍀
