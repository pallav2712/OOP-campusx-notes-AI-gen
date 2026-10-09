# Python OOP — Complete Beginner-Friendly Notes

**Language:** Simple Hinglish + English technical terms  
**Based on:** The supplied transcript of the Python OOP video  
**Goal:** Understand the concepts, read/write the code, and revise for interviews.

> **Transcript note:** Auto-captions mein speech-to-text errors hain. Notes video ke 21 chapters aur sir ke main example families (OYO/Uber/college social platform, Car, ATM/SBI, Fraction, Customer/Address, Udemy User/Student/Instructor, Phone/Smartphone/Product, Geometry, Indian Rail API) ko follow karte hain. Code ko readable/runnable banane ke liye syntax clean kiya gaya hai. Jahan exact number ya live API detail transcript se confirm nahi hoti, wahan guess ko fact ke roop mein present nahi kiya gaya.

---

## How to study these notes

1. Pehle concept aur example samjho; code ko copy-paste karne se pehle khud type karo.
2. Har example ko run karke output dekho. Phir ek chhota change karke predict karo ki output kya hoga.
3. Ek baar padhne ke baad **Quick Revision**, **Common Mistakes**, aur **Practice Questions** use karo.

## Video chapter map

| Video chapter | Approx. timestamp | Topic |
|---|---:|---|
| 1 | 00:00 | Importance of OOP |
| 2–3 | 10:34–19:55 | Class and object |
| 4–6 | 21:48–56:01 | Practical class/object, `__init__()`, `self` |
| 7 | 1:06:25 | Fraction data type and arithmetic methods |
| 8–11 | 1:23:21–2:11:44 | Encapsulation, references, function arguments, collections of objects |
| 12–13 | 2:17:03–2:31:07 | Static variables/methods and aggregation |
| 14–15 | 2:43:30–2:55:29 | Inheritance and class diagrams |
| 16–19 | 3:01:06–3:28:16 | Polymorphism, `super()`, inheritance types, MRO |
| 20 | 3:35:42 | Method overloading and operator overloading |
| 21 | 3:44:33 | Small railway/IRCTC-style API project |

---

# Chapter 1 — Importance of OOP

## 1.1 OOP ka full form

**OOP = Object-Oriented Programming.** Yeh programming ka ek style/paradigm hai jisme program ko objects aur unke interactions ke around organize kiya jaata hai. Video ka core point: Python ke built-in data types (`int`, `str`, `list`) useful hain, lekin real applications ke liye kabhi-kabhi humein apna meaningful data type banana padta hai.

## 1.2 Sir ke real-world examples: OOP ki zaroorat kyun padi?

Video mein sir everyday problems ko software mein convert karne ke examples dete hain:

- **OYO / hotel booking:** Pehle naye shehar pahunchkar hotel physically dekhna pad sakta tha. Online platform photos/details dikhakar booking easy bana sakta hai.
- **Uber-type ride booking:** Driver ko dhoondhne ya location samajhne ki problem ko app aur GPS-based tracking se handle kiya ja sakta hai.
- **Photo-sharing / Instagram-type platform:** Photos upload karna aur doosre logon ka react karna software features ban sakte hain.
- **LinkedIn jaisa, lekin college students ke liye platform:** Profiles, graduation information, messages aur connections jaise features ek application mein aate hain. Sir ka point yeh hai ki agar har feature ko unstructured tareeke se add karte jao, to code bada aur difficult to maintain ho sakta hai.
- **Kali Linux analogy:** Kisi specific task—jaise penetration testing—ke liye purpose-built environment/tools ek general-purpose setup mein sab kuch manually arrange karne se convenient ho sakte hain. Isi tarah, apni application ke domain ke liye suitable data types banana code ko more expressive bana sakta hai.

OOP har chhote program ke liye mandatory nahi hai. Lekin jab application mein users, profiles, posts, accounts ya trains jaise multiple entities aur unka data/behaviour ho, classes code ko organize karne mein help karti hain.

## 1.3 Apna data type banana: OOP ka central idea

`int`, `str`, `list` Python ke built-in types hain. Lekin `ATM`, `Fraction`, `Customer`, `Address`, `Phone` ya `Train` jaise domain-specific types hum class se define kar sakte hain.

Example: ATM ke paas `pin` aur `balance` jaise data ho sakte hain aur `deposit()`, `withdraw()` aur `check_balance()` jaise behaviours.

## 1.4 Python mein everything is an object

Python mein numbers, strings, lists, aur functions bhi objects hain. `type()` se type check kar sakte ho:

```python
print(type(10))          # <class 'int'>
print(type("hello"))     # <class 'str'>
print(type([1, 2, 3]))    # <class 'list'>
print(type(len))         # built-in function ka type
```

`dir(object)` object ke available attributes/methods explore karne mein help karta hai. Output lamba ho sakta hai.

## 1.5 OOP ke four pillars

Video mein four commonly taught pillars cover hote hain:

1. **Encapsulation:** Data aur related methods ko class mein rakhna aur data access ko controlled rakhna.
2. **Inheritance:** Ek class doosri class ka available behaviour reuse/extend kar sakti hai.
3. **Polymorphism:** Same interface/method call different object types ke liye different behaviour de sakta hai.
4. **Abstraction:** User ko useful interface dikhana aur unnecessary implementation detail hide rakhna.

Aage ATM, `Fraction`, `Customer`, `Address`, `Phone`, `Smartphone` aur railway API ke examples se in concepts ko samjhenge.

> **Yaad rakho:** OOP ka main benefit sirf `class` likhna nahi hai; related data aur behaviour ko aise model karna hai ki real application maintain aur extend karna easier ho.

---

# Chapter 2 — Class

## 2.1 Class kya hoti hai?

**Class ek blueprint/template hai jo define karti hai ki us type ke objects ke paas kaunsa data aur kaunse methods honge.** Jaise car ka blueprint batata hai car ka design kaisa hoga; blueprint khud actual car nahi hai.

## 2.2 Sir ka Car example: attributes aur methods

Car ke possible **data/attributes**:
- number of seats
- colour
- engine type
- brand
- mileage ya current state se related information

Car ke possible **methods/behaviours**:
- calculate mileage
- calculate/display speed
- open airbag (conceptual example)
- GPS navigation

```python
class Car:
    def start(self):
        print("Car started")

    def calculate_mileage(self, distance, fuel_used):
        if fuel_used <= 0:
            raise ValueError("Fuel used must be positive")
        return distance / fuel_used
```

Abhi `Car` class define hui hai. Actual car object banane ke liye class ko call karenge: `car1 = Car()`.

### Class ke do main parts

1. **Attributes / properties / data members:** Object ki information, jaise `colour`, `brand`, `balance`.
2. **Methods / member functions:** Object ka behaviour, jaise `start()`, `deposit()`, `withdraw()`.

## 2.3 Naming conventions

Python mein commonly:
- **Class name:** `PascalCase`, jaise `Car`, `BankAccount`, `Smartphone`.
- **Variable / method name:** `snake_case`, jaise `fuel_used`, `check_balance()`.
- **Constants:** aksar uppercase, jaise `MAX_RETRIES`.

Naming conventions style rules hain, Python syntax restrictions nahi.

## 2.4 Class diagram ka initial idea

UML class diagram mein class name, attributes aur methods ko alag sections mein dikhaya ja sakta hai. Common symbols: `+` public, `-` private, `#` protected. Yeh diagram notation hai; Python mein Java jaisi strict access modifiers syntax nahi hoti. ATM example ke saath Chapter 15 mein diagram dekhenge.

---

# Chapter 3 — Object

## 3.1 Object kya hota hai?

**Object kisi class ka instance hota hai.** Class design batati hai; object us design ka actual instance hota hai. Ek hi class se multiple objects ban sakte hain.

```python
class Car:
    def start(self):
        print("Car started")

car1 = Car()
car2 = Car()

car1.start()
car2.start()
```

`car1` aur `car2` do separate `Car` objects ko refer karte hain. Dono ke methods same class se aate hain, lekin har object ki instance values alag ho sakti hain.

## 3.2 Built-in types bhi classes hain

Video mein sir yeh point dikhate hain ki Python mein list, integer aur string bhi objects hain. Unka type unki class batata hai:

```python
number = 10
name = "Pallav"
numbers = [1, 2, 3]

print(type(number))   # <class 'int'>
print(type(name))     # <class 'str'>
print(type(numbers))  # <class 'list'>
```

Agar `numbers.append(4)` likhte ho, method list object par available hai. Integer par `append()` available nahi, kyunki `int` class ka interface alag hai.

```python
numbers.append(4)
print(numbers)  # [1, 2, 3, 4]

# number.append(4)  # AttributeError: int object has no attribute 'append'
```

## 3.3 Literal syntax

Hum normally list ke liye `[]`, string ke liye quotes aur integer ke liye number likhte hain:

```python
numbers = [1, 2, 3]
name = "Pallav"
count = 10
```

Yeh convenient literal syntax hai. Aksar `list([1, 2, 3])` likhne ki zaroorat nahi hoti.

## 3.4 Class blueprint banati hai; object use karta hai

List class define karti hai ki list object kin operations ko support karega. Jab aap `numbers = [1, 2, 3]` banate ho, to aap actual list object create karte ho. Isi tarah hum `ATM` class define karenge aur `SBI = ATM(...)` jaisa object banayenge.

---

# Chapter 4 — Practical implementation: ATM class and objects

Video mein sir ek simple **ATM machine software** banate hain. Is example mein user PIN enter karta hai aur menu se deposit, withdrawal, balance check ya exit choose karta hai.

## 4.1 ATM class ka data aur behaviour

**Data:** PIN, balance.

**Methods/behaviour:** menu display karna, PIN verify karna, deposit, withdraw, balance check.

## 4.2 Beginner-friendly ATM example

Yeh video ke ATM/SBI example ka cleaned, runnable learning version hai. Financial production system nahi hai.

```python
class ATM:
    def __init__(self, pin, balance=0):
        self.pin = str(pin)
        self.balance = balance

    def verify_pin(self):
        entered_pin = input("Enter your PIN: ")
        return entered_pin == self.pin

    def deposit(self):
        if not self.verify_pin():
            print("Incorrect PIN")
            return

        amount = int(input("Enter deposit amount: "))
        if amount <= 0:
            print("Amount must be positive")
            return

        self.balance += amount
        print("Deposit successful")

    def withdraw(self):
        if not self.verify_pin():
            print("Incorrect PIN")
            return

        amount = int(input("Enter withdrawal amount: "))
        if amount <= 0:
            print("Amount must be positive")
        elif amount > self.balance:
            print("Insufficient funds")
        else:
            self.balance -= amount
            print("Withdrawal successful")

    def check_balance(self):
        if self.verify_pin():
            print(f"Available balance: ₹{self.balance}")
        else:
            print("Incorrect PIN")

    def menu(self):
        while True:
            print("\n1. Deposit")
            print("2. Withdraw")
            print("3. Check balance")
            print("4. Exit")
            choice = input("Choose an option: ")

            if choice == "1":
                self.deposit()
            elif choice == "2":
                self.withdraw()
            elif choice == "3":
                self.check_balance()
            elif choice == "4":
                print("Thank you")
                break
            else:
                print("Invalid option")

SBI = ATM("1234", 10000)
# SBI.menu()  # Uncomment this line to interact with the menu
```

## 4.3 Is code mein class aur objects

- `ATM` class blueprint hai.
- `SBI = ATM("1234", 10000)` SBI account/ATM state ka object create karta hai.
- `SBI.menu()` call karne par menu loop start hota hai.
- `deposit()`, `withdraw()` aur `check_balance()` ATM object ke methods hain.
- `self.balance` ko update karne se isi object ka balance change hota hai.

Agar second object banao, to uska PIN aur balance independently initialize hoga:

```python
BOB = ATM("5678", 5000)
print(SBI.balance)  # 10000
print(BOB.balance)  # 5000
```

**Note:** Chapter 8 mein isi ATM example ko modify karke PIN aur balance ko direct public access se protect karenge. Real banking application mein PIN ko plain text mein store nahi karna chahiye; yahan sirf OOP learning purpose hai.

---

# Chapter 5 — Constructor / `__init__()`

## 5.1 `__init__()` kya karta hai?

Video mein constructor ko special method ke roop mein explain kiya gaya hai jiska code object banne aur initialize hone ke process mein automatically run hota hai. Beginner language mein ise constructor kehna common hai; technically Python mein `__new__()` object create karta hai aur `__init__()` newly created object ko initialize karta hai.

## 5.2 Sir ka pehla demo: `Hello Hello`

```python
class ATM:
    def __init__(self):
        print("Hello Hello")

SBI = ATM()  # object create hote waqt Hello Hello print hoga
```

`SBI = ATM()` par aap `__init__()` ko manually call nahi karte. Python object creation ke process mein ise invoke karta hai.

## 5.3 ATM ko initial PIN aur balance dena

Ab constructor ko parameters dete hain:

```python
class ATM:
    def __init__(self, pin, balance):
        self.pin = str(pin)
        self.balance = balance

SBI = ATM(1234, 10000)
BOB = ATM(5678, 50000)

print(SBI.balance)  # 10000
print(BOB.balance)  # 50000
```

Parameter flow:

- `1234` -> `pin` parameter.
- `10000` -> `balance` parameter.
- `self.pin = str(pin)` -> current object ke andar PIN store karta hai.
- `self.balance = balance` -> current object ke andar balance store karta hai.

`SBI` aur `BOB` same class ke objects hain, lekin unki initial state alag hai.

## 5.4 Default parameter

```python
class ATM:
    def __init__(self, pin, balance=0):
        self.pin = str(pin)
        self.balance = balance

SBI = ATM("1234")          # balance defaults to 0
BOB = ATM("5678", 50000)   # balance is 50000
```

## 5.5 Common mistakes

- Spelling exactly `__init__` rakho: dono sides double underscores.
- Instance method ke first parameter mein `self` likho.
- `__init__()` se custom value return mat karo; initializer ka return value `None` hi hona chahiye.

---

# Chapter 6 — `self` in Python

## 6.1 `self` ka matlab

`self` current object ka reference hota hai. Isi se method identify karta hai ki kis object ka PIN, balance ya doosra attribute use/update karna hai.

```python
class ATM:
    def __init__(self, pin, balance):
        self.pin = str(pin)
        self.balance = balance

    def check_balance(self):
        print(self.balance)

SBI = ATM("1234", 10000)
BOB = ATM("5678", 5000)

SBI.check_balance()  # 10000
BOB.check_balance()  # 5000
```

`SBI.check_balance()` call mein `self` SBI ko refer karta hai. `BOB.check_balance()` call mein `self` BOB ko refer karta hai. Isi wajah se same method different object state ke saath kaam karta hai.

## 6.2 Kya `self` keyword hai?

Nahi. `self` Python reserved keyword nahi, lekin standard convention hai. Normal code mein `self` hi use karo taaki doosre Python developers code easily samajh saken.

## 6.3 `self` manually pass karna hota hai?

Normal instance-method call mein Python automatically current object ko first argument ke roop mein pass karta hai:

```python
SBI.check_balance()
```

Conceptually yeh aise samjha ja sakta hai:

```python
ATM.check_balance(SBI)
```

Isliye method definition mein `self` hota hai, lekin normal object call ke andar manually `SBI` pass nahi karna padta.

## 6.4 `self.balance` vs `balance`

```python
def __init__(self, balance):
    self.balance = balance
```

- Right side `balance` constructor ka local parameter hai.
- Left side `self.balance` current object ka attribute hai.

Agar sirf `balance = balance` likh doge, to object ke attribute ko set nahi karoge. `self.` ko yaad rakhna important hai.

---

# Chapter 7 — Apna data type banana: `Fraction`

Video ka practical point: normal Python integers aur strings hain, lekin humein **fraction** ka apna data type chahiye jo numerator/denominator store kare aur addition, subtraction, multiplication aur division support kare.

## 7.1 Fraction mein data kya hai?

- **Numerator:** fraction ka top number.
- **Denominator:** fraction ka bottom number; zero allowed nahi.

Sir ka example `Fraction` class hai. Auto-transcript mein kuch numeric details unclear hain; neeche `2/3` aur `5/6` use karke wahi operations demonstrate kiye gaye hain.

## 7.2 `Fraction` class aur operator methods

```python
class Fraction:
    def __init__(self, numerator, denominator):
        if denominator == 0:
            raise ValueError("Denominator cannot be zero")
        self.numerator = numerator
        self.denominator = denominator

    def __str__(self):
        return f"{self.numerator}/{self.denominator}"

    def __add__(self, other):
        new_num = (
            self.numerator * other.denominator
            + other.numerator * self.denominator
        )
        new_den = self.denominator * other.denominator
        return Fraction(new_num, new_den)

    def __sub__(self, other):
        new_num = (
            self.numerator * other.denominator
            - other.numerator * self.denominator
        )
        new_den = self.denominator * other.denominator
        return Fraction(new_num, new_den)

    def __mul__(self, other):
        return Fraction(
            self.numerator * other.numerator,
            self.denominator * other.denominator,
        )

    def __truediv__(self, other):
        if other.numerator == 0:
            raise ZeroDivisionError("Cannot divide by a zero fraction")
        return Fraction(
            self.numerator * other.denominator,
            self.denominator * other.numerator,
        )

x = Fraction(2, 3)
y = Fraction(5, 6)

print(x)       # 2/3
print(y)       # 5/6
print(x + y)   # 27/18
print(x - y)   # -3/18
print(x * y)   # 10/18
print(x / y)   # 12/15
```

Fractions reduce/simplify automatically nahi ho rahe; example mein `27/18` ko `3/2` simplify kiya ja sakta hai. Simplification ek additional feature hai.

## 7.3 `__str__()` kyun chahiye?

Agar custom object ko `print(x)` karte ho, Python ko pata hona chahiye ki use readable string mein kaise dikhana hai. `__str__()` yeh display rule define karta hai. Iske bina output generally object representation hota hai, jaise class name aur memory-related details.

## 7.4 `+` automatically kaam kyun nahi karta?

Sir pehle point karte hain ki do custom `Fraction` objects ko `x + y` karne par Python ko apne aap fraction-addition ka rule nahi pata hota. `__add__()` us rule ko define karta hai. Isi tarah:

- `__sub__()` -> `-`
- `__mul__()` -> `*`
- `__truediv__()` -> `/`
- `__str__()` -> `print(object)` / `str(object)` ka readable output

Iska broader lesson: OOP se hum apna data type aur uske meaningful operations define kar sakte hain.

---

# Chapter 8 — Encapsulation: ATM ke PIN aur Balance ko protect karna

## 8.1 Video ki problem

ATM example mein agar `SBI.pin` aur `SBI.balance` public hain, to class ke bahar ka code direct balance dekh ya badal sakta hai. Sir demo mein balance ko galat type se assign karne par deposit jaise method ka logic break hone ki problem dikhate hain. Isliye data ko direct open chhodna achhi practice nahi.

**Encapsulation** ka matlab related data/behaviour ko class mein rakhna aur data ko controlled methods ke through read/update karwana.

## 8.2 Single underscore vs double underscore

| Form | Example | Meaning |
|---|---|---|
| Public-style | `balance` | Normal public attribute; direct access available |
| Internal/protected-style convention | `_balance` | Internal use ka hint; strict restriction nahi |
| Private-style name | `__balance` | Python name mangling apply karta hai; accidental access/override se bachata hai |

## 8.3 Sir ke ATM example ka encapsulated version

```python
class ATM:
    def __init__(self, pin, balance):
        self.__pin = str(pin)
        self.__balance = balance

    def get_pin(self):
        return self.__pin

    def set_pin(self, new_pin):
        new_pin = str(new_pin)
        # Video mein PIN ko fixed-length value rakhne ka validation idea hai.
        if new_pin.isdigit() and len(new_pin) == 4:
            self.__pin = new_pin
            print("PIN updated")
        else:
            print("PIN must contain exactly 4 digits")

    def deposit(self, amount):
        if amount <= 0:
            print("Amount must be positive")
            return
        self.__balance += amount
        print("Deposit successful")

    def check_balance(self):
        return self.__balance

SBI = ATM("1234", 10000)
print(SBI.check_balance())  # 10000
SBI.deposit(500)
print(SBI.check_balance())  # 10500
SBI.set_pin("5678")        # PIN updated
SBI.set_pin("5.6")         # invalid PIN
```

`SBI.__pin` aur `SBI.__balance` normal direct attribute names ke roop mein available nahi honge. Isliye class apna internal data expose karne ke bajaye methods provide karti hai.

## 8.4 Double underscore ka actual effect

Python `__pin` ko name-mangle karke internally `_ATM__pin` jaisa naam banata hai. Iska matlab **absolute secrecy nahi**: determined code mangled name access kar sakta hai. Real secrets ko is convention par secure samajhkar store nahi karna chahiye. Iska purpose accidental access/override ko reduce karna hai.

Ek aur subtle point: `SBI.__balance = 1` likhne se normal code mein underlying mangled `_ATM__balance` necessarily update nahi hota; ek alag attribute create ho sakta hai. Isliye direct assignment se bachna chahiye.

## 8.5 Getter/setter aur encapsulation

- **Getter:** controlled way se value read karta hai, jaise `get_pin()`.
- **Setter:** validation ke saath value update karta hai, jaise `set_pin()`.

Har attribute ke liye getter/setter zaroori nahi. Useful tab hota hai jab rules enforce karne hon.

### UML notation

Class diagram mein `+` public aur `-` private ko represent karta hai. ATM diagram Chapter 15 mein diya hai.

---

# Chapter 9 — Reference Variables

## 9.1 Reference variable ka idea

Jab class ka object create hota hai, us object ko variable ke through refer karte hain. Video mein sir explain karte hain ki object banakar uska reference kisi variable mein store karna important hai; variable ke bina object ko baad mein use karna difficult ho sakta hai.

```python
class ATM:
    def __init__(self, pin, balance):
        self.pin = str(pin)
        self.balance = balance

SBI = ATM("1234", 10000)
print(id(SBI))
```

`SBI` object ka reference hold karta hai. `id()` object identity ko inspect karne ka ek tareeqa hai (exact number har run/environment mein alag ho sakta hai).

## 9.2 `second = first` copy nahi banata

```python
first = ATM("1234", 10000)
second = first

print(first is second)  # True
second.balance = 500
print(first.balance)    # 500
```

`first` aur `second` same ATM object ko refer kar rahe hain. Isliye ek reference se state change karne par doosre reference se bhi updated state dikhegi.

Independent object banana ho to class ko dobara call karo:

```python
SBI = ATM("1234", 10000)
BOB = ATM("5678", 5000)
print(SBI is BOB)  # False
```

## 9.3 Unassigned temporary object

```python
ATM("9999", 100)  # object creation expression, but reference store nahi kiya
```

Expression execute hota hai, lekin us object ko baad ke statements mein refer karne ke liye koi named variable nahi rakha. Practical programs mein object ka reference save karna generally useful hota hai.

## 9.4 `is` vs `==`

- `is`: kya same object hai?
- `==`: kya values/content equal hain? Iska behaviour class define kar sakti hai.

```python
a = [1, 2, 3]
b = a
c = [1, 2, 3]

print(a is b)  # True: same object
print(a == c)  # True: same content
print(a is c)  # False: separate list objects
```

Custom classes mein `==` content compare kare, yeh automatically guaranteed nahi. `__eq__()` implement karne par equality ka rule define kiya ja sakta hai.

---

# Chapter 10 — Objects ko functions mein pass karna

Video is topic ko “pass by reference” ke naam se discuss karta hai. Python ke liye zyada precise description **call by object sharing / pass by assignment** hai. Practical result yeh hai ki function ko object milta hai; object ke mutable attributes ko change karoge to caller ko bhi change dikhega.

## 10.1 Sir ka `Customer` example

```python
class Customer:
    def __init__(self, name, gender=None):
        self.name = name
        self.gender = gender

def greet(customer):
    print(f"Hello, {customer.name}")

customer1 = Customer("Nitesh", "Male")
greet(customer1)  # Hello, Nitesh
```

Custom class ka object bhi function ko argument ke roop mein pass ho sakta hai—bilkul string, integer ya list ki tarah.

## 10.2 Function ke andar object mutate karna

```python
def update_customer(customer):
    customer.name = "Ankita"

customer1 = Customer("Nitesh", "Male")
update_customer(customer1)
print(customer1.name)  # Ankita
```

`update_customer()` ne existing object ka `name` attribute badla. Caller ka `customer1` ab bhi usi object ko refer karta hai, isliye outside function bhi updated name milta hai. Object ki identity change nahi hui; uski state change hui.

## 10.3 Parameter ko reassign karna alag hai

```python
def replace_customer(customer):
    customer = Customer("New Customer", "Female")

customer1 = Customer("Nitesh", "Male")
replace_customer(customer1)
print(customer1.name)  # Nitesh
```

Function ke andar `customer` local parameter ko naye object se bind kiya gaya. Caller ke `customer1` variable ki binding change nahi hui.

## 10.4 Mutable lists aur immutable tuples

Sir is baat ko list ke example se bhi samjhate hain:

```python
def add_five(items):
    items.append(5)

album = [1, 2, 3, 4]
add_five(album)
print(album)  # [1, 2, 3, 4, 5]
```

Agar original list ko mutate hone se bachana ho, copy pass kar sakte ho:

```python
original = [1, 2, 3, 4]
add_five(original.copy())
print(original)  # [1, 2, 3, 4]
```

Tuple immutable hota hai, isliye tuple ko list jaisa in-place append nahi kar sakte. Lekin variable ko reassign kiya ja sakta hai; immutability ka matlab variable ko hamesha ke liye lock karna nahi hai.

### Revision line

**Shared object ko mutate karna** aur **function ke local parameter ko reassign karna** alag cheezein hain.

---

# Chapter 11 — Collection of Objects

Ek collection—jaise list, tuple, set ya dictionary—ke andar custom class ke multiple objects store kiye ja sakte hain. Sir ka example `Customer` class aur customers ki list hai.

```python
class Customer:
    def __init__(self, name):
        self.name = name

    def intro(self):
        print(f"Hello friends, I am {self.name}")

c1 = Customer("Nitesh")
c2 = Customer("Ajay")
c3 = Customer("Ankit")

customers = [c1, c2, c3]

for customer in customers:
    customer.intro()
```

Output:

```text
Hello friends, I am Nitesh
Hello friends, I am Ajay
Hello friends, I am Ankit
```

## 11.1 Objects ko list/dictionary se manage karna

List mein objects ke references hain; loop har object par method call karta hai. Aap methods ke through object ka data read/update kar sakte ho.

```python
customers_by_id = {
    101: Customer("Nitesh"),
    102: Customer("Ajay"),
}

customers_by_id[101].intro()
```

Isi tarah tuple ya set bhi objects hold kar sakte hain, subject to unki ordering/mutability rules.

## 11.2 Object ko `print()` karna vs method call

Agar `Customer` class mein `__str__()` nahi hai, to `print(c1)` se generally default object representation milega; aapka custom intro message automatically print nahi hoga. `c1.intro()` explicitly intro method call karta hai. Readable `print(c1)` output chahiye to `__str__()` implement karo, jaise `Fraction` chapter mein kiya.

**Key idea:** Custom objects ko collection mein rakhna aur un par loop chalana bilkul normal strings/numbers ki list ki tarah hota hai.

---

# Chapter 12 — Static Variables and Methods

## 12.1 Sir ka example: har `Customer` ka serial number

Requirement: first customer ka serial number `1`, second ka `2`, third ka `3`—automatically assign ho. Agar counter har object ke andar instance variable hota, to har object ka counter separately start hota. Humein ek shared counter chahiye jo sab customers ke liye common ho.

```python
class Customer:
    __counter = 0  # class/static variable: shared counter

    def __init__(self, name):
        self.name = name
        Customer.__counter += 1
        self.__serial_number = Customer.__counter  # per-object value

    def display(self):
        print(self.__serial_number, self.name)

    @staticmethod
    def get_counter():
        return Customer.__counter

c1 = Customer("Nitesh")
c2 = Customer("Ajay")
c3 = Customer("Ankit")

c1.display()  # 1 Nitesh
c2.display()  # 2 Ajay
c3.display()  # 3 Ankit
print(Customer.get_counter())  # 3
```

- `__counter` **class variable** hai—sab objects ke liye shared.
- `__serial_number` **instance variable** hai—har customer ka apna number.
- `Customer.get_counter()` static method ko class name se call karta hai; object banana necessary nahi.

## 12.2 Instance variable vs class variable

| Instance variable | Class variable |
|---|---|
| Har object ki separate value | Class ke liye shared value |
| Example: customer ka PIN/balance/name | Example: customers ka common serial counter |
| Usually `self.value` | Class body mein defined, yahan `Customer.__counter` |

## 12.3 Static method ka meaning

`@staticmethod` method ko class ke namespace mein rakhta hai, lekin Python first argument ke roop mein automatic `self` ya `cls` nahi deta. Isliye `get_counter()` class variable ko `Customer.__counter` ke through access karta hai.

Agar static method ko class/subclass ke saath dynamic tareeke se kaam karna ho, to `@classmethod` with `cls` better fit ho sakta hai. Video ke main concept ke liye: static method ko object banaye bina class se call kar sakte ho.

## 12.4 Important gotcha

Class variable ko object ke through assign karna—jaise `c1.counter = 100`—instance attribute create kar sakta hai jo class variable ko shadow karega. Shared counter update karne ke liye class-level access use karo. Real multi-threaded apps mein aisa counter concurrency ke liye additional design maang sakta hai.

---

# Chapter 13 — Class Relationship: Aggregation

## 13.1 HAS-A relationship

Video mein sir e-commerce example se samjhate hain ki badi application mein `Product`, `Customer`, `Address`, `Review` jaise multiple classes ho sakti hain. **Aggregation** ko beginner level par **HAS-A** relationship samjho: ek class ka object doosri class ke object ka reference apne attribute mein rakhta hai.

Sir ka practical example: **Customer has an Address**. Address mein city, pin code aur state hain; customer mein name/gender aur address ka reference hai.

```python
class Address:
    def __init__(self, city, pincode, state):
        self.city = city
        self.pincode = pincode
        self.state = state

class Customer:
    def __init__(self, name, gender, address):
        self.name = name
        self.gender = gender
        self.address = address

    def display_profile(self):
        print(self.name, self.gender)
        print(self.address.city, self.address.pincode, self.address.state)

    def edit_profile(self, name=None, city=None, pincode=None, state=None):
        if name is not None:
            self.name = name
        if city is not None:
            self.address.city = city
        if pincode is not None:
            self.address.pincode = pincode
        if state is not None:
            self.address.state = state

address1 = Address("Kolkata", 700001, "West Bengal")
customer1 = Customer("Nitesh", "Male", address1)

print(customer1.address.city)  # Kolkata
customer1.edit_profile(name="Ankit", city="Gurgaon", pincode=122001, state="Haryana")
customer1.display_profile()
```

Yahan `customer1.address.city` ke through nested object ka city access ho raha hai. Customer object khud city, pin code aur state ko duplicate attributes mein store nahi kar raha; woh Address object ko use kar raha hai.

## 13.2 Aggregation se fayda

- Har class ki responsibility clear rehti hai.
- Address ka data/logic `Address` class mein rehta hai.
- Customer ko address-related operations doosre object ke through milte hain.
- `edit_profile()` ka logic update details ko manage karta hai; omitted values (`None`) hone par old values unchanged rehti hain.

## 13.3 Aggregation vs inheritance

- **Customer HAS-A Address** -> aggregation.
- **Smartphone IS-A Phone** (video's inheritance example) -> inheritance.

Har relationship ko inheritance se represent mat karo. UML diagrams mein aggregation ko generally hollow diamond se represent kiya jaata hai, aksar containing/aggregate class ke side par.

---

# Chapter 14 — Inheritance

## 14.1 Inheritance ka real application example: Udemy-type platform

Video mein website/platform example hai jahan do type ke users hain: **Student** aur **Instructor**.

Dono ke common features:
- Login
- Register

Student-specific features:
- Course mein enroll karna
- Course review karna

Instructor-specific features:
- Course create karna
- Questions answer karna

Agar `Student` aur `Instructor` mein login/register ka same code copy-paste karoge, to duplication hoga. Sir ka point DRY principle (**Don't Repeat Yourself**) hai. Common functionality ko `User` parent class mein rakhkar dono specialized classes usse inherit kar sakti hain.

```python
class User:
    def login(self):
        print("User logged in")

    def register(self):
        print("User registered")

class Student(User):
    def enroll(self, course):
        print(f"Enrolled in {course}")

    def review_course(self, course):
        print(f"Reviewing {course}")

class Instructor(User):
    def create_course(self, course):
        print(f"Created course: {course}")

    def answer_question(self, question):
        print(f"Answered: {question}")

student = Student()
instructor = Instructor()

student.login()                 # inherited from User
student.enroll("Python OOP")
instructor.register()           # inherited from User
instructor.create_course("Python OOP")
```

`class Student(User)` Python ko batata hai ki `Student` class `User` se inherit karti hai.

## 14.2 Inheritance mein kya reuse hota hai?

Child class parent ke accessible attributes aur methods ko use kar sakti hai. Agar child class apna same-name method define kare, to overriding ke rules apply hote hain (Chapter 16).

Inheritance direction parent se child ki taraf hoti hai: `Student` `User` ke common features inherit kar sakta hai, lekin `User` automatically `Student` ke course-enrollment features inherit nahi karta.

## 14.3 Private-style attributes ka note

Python mein parent class ke `__private` style attributes name-mangling hote hain. Isliye child class unhe parent ke original `__name` ke naam se normally access nahi kar sakti. Yeh “private members bilkul exist nahi karte” jaisa nahi; actual detail name mangling aur access pattern se related hai.

## 14.4 Inheritance kab use karein?

Use it where a real **IS-A** relationship exists and common behaviour naturally share hota hai. Sir ke next examples mein isi idea ko `Product -> Phone -> Smartphone` hierarchy se dekhenge. HAS-A relationship, jaise Customer aur Address, ke liye aggregation zyada suitable hai.

---

# Chapter 15 — Class Diagram (UML Basics)

Class diagram code likhne se pehle class ka structure communicate karne ka visual tareeqa hai. Video mein sir ATM class ke attributes/methods ko diagram mein represent karte hain.

## 15.1 ATM class ka diagram

```text
+--------------------------------------+
| ATM                                  |
+--------------------------------------+
| - __pin: str                         |
| - __balance: float                   |
+--------------------------------------+
| + __init__(pin, balance)             |
| + menu()                             |
| + deposit(amount)                    |
| + withdraw(amount)                   |
| + check_balance()                    |
| + get_pin()                          |
| + set_pin(new_pin)                   |
+--------------------------------------+
```

- Top section: class ka naam.
- Middle section: attributes/data members.
- Bottom section: methods/operations.
- `-` private-style member ko show karta hai.
- `+` public member ko show karta hai.

Diagram mein PIN aur balance private-style dikhaye hain kyunki Chapter 8 mein hum direct access avoid karna chahte hain. Public methods controlled interaction dete hain.

## 15.2 Common UML symbols

| Symbol | UML meaning |
|---|---|
| `+` | Public |
| `-` | Private |
| `#` | Protected |
| Hollow triangle arrow | Inheritance; triangle parent/base class ki taraf |
| Hollow diamond | Aggregation; aggregate/containing class ki side |

Yeh **UML notation** hai, Python syntax nahi. Python mein `_name` convention aur `__name` name mangling use hote hain; Python classes Java-style `public/private/protected` keywords declare nahi karti.

## 15.3 Diagram code se kaise help karta hai?

Team member diagram dekhkar class ki responsibilities, available methods, attributes aur relationships samajh sakta hai, bhale hi har method ka internal logic diagram mein na likha ho.

---

# Chapter 16 — Polymorphism: Method Overriding

## 16.1 Meaning

**Polymorphism** ka literal meaning hai “many forms”. Video mein sir kehte hain ki same method name different classes mein ho sakta hai, aur object ke actual class ke according relevant implementation run hota hai.

## 16.2 Sir ka `Phone` aur `Smartphone` example

```python
class Phone:
    def buy(self):
        print("Buying a phone")

class Smartphone(Phone):
    def buy(self):
        print("Buying a smartphone")

phone = Phone()
samsung = Smartphone()

phone.buy()    # Buying a phone
samsung.buy()  # Buying a smartphone
```

`Smartphone` ne parent `Phone` ke `buy()` method ka apna implementation define kiya. Isko **method overriding** kehte hain. Jab `samsung.buy()` call hota hai, child class ka version run hota hai.

## 16.3 Override kyun useful hai?

Parent common behaviour define karta hai, lekin child class apni specialized behaviour provide kar sakti hai. Real-world analogy mein same family business ko continue karne ke bajaye child apna different career choose kar sakta hai; software mein child class inherited behaviour ko reuse bhi kar sakti hai aur replace bhi.

## 16.4 Polymorphism ke forms jo video mein naam se cover hain

- **Method overriding:** Child class same method name ka implementation replace karti hai.
- **Method overloading:** Same method name ko different argument patterns ke liye use karna; Python mein iska handling Java jaisa nahi (Chapter 20).
- **Operator overloading:** `+`, `-`, `*`, `/` jaise operator ko custom objects ke liye define karna (Fraction example).

## 16.5 Private member ka inheritance example

Video mein sir ek parent/child situation se yeh bhi dikhate hain ki name-mangled `__attribute` ko child object se parent ke same written name ke roop mein access nahi kar sakte. Python ka `__name` strict security boundary nahi hai, lekin normal attribute lookup mein `_Parent__name` ban jaata hai. Public/protected conventions aur methods ke through intended access design karna chahiye.

## 16.6 Duck typing

Python mein similar behaviour ke liye inheritance mandatory nahi. Agar objects ek expected method provide karte hain, to calling code unhe common interface se use kar sakta hai. Isse duck typing kehte hain. Video ka main practical overriding example phir bhi `Phone`/`Smartphone` hai.

---

# Chapter 17 — `super()` ka use

## 17.1 Sir ka `Phone` / `Smartphone` example

Jab child method apna behaviour run karne ke baad parent ka method bhi reuse karna chahe, to `super()` useful hota hai.

```python
class Phone:
    def buy(self):
        print("Buying a phone")

class Smartphone(Phone):
    def buy(self):
        print("Buying a smartphone")
        super().buy()

samsung = Smartphone()
samsung.buy()
```

Output:

```text
Buying a smartphone
Buying a phone
```

Execution order:

1. `samsung.buy()` child `Smartphone.buy()` run karta hai.
2. Child print karta hai `Buying a smartphone`.
3. `super().buy()` parent `Phone.buy()` ko invoke karta hai.
4. Parent print karta hai `Buying a phone`.

Agar child mein `buy()` define hi na hota, to normal lookup inherited parent method ko use karta.

## 17.2 Parent constructor reuse karna

Sir ka next design example: brand aur camera jaise common attributes phone ke paas hain, jabki operating system aur RAM smartphone-specific hain. Common setup parent constructor mein rakh sakte hain.

```python
class Phone:
    def __init__(self, brand, camera):
        self.brand = brand
        self.camera = camera

    def buy(self):
        print("Buying a phone")

class Smartphone(Phone):
    def __init__(self, brand, camera, operating_system, ram):
        super().__init__(brand, camera)
        self.operating_system = operating_system
        self.ram = ram

    def buy(self):
        print("Buying a smartphone")
        super().buy()

samsung = Smartphone("Samsung J1", "5 MP", "Android", "1 GB")
print(samsung.brand)
print(samsung.camera)
print(samsung.operating_system)
print(samsung.ram)
samsung.buy()
```

`super().__init__(brand, camera)` parent ka common initialization reuse karta hai. Child ko common attributes dobara likhne ki zaroorat nahi; woh sirf smartphone-specific attributes set karta hai.

## 17.3 `super()` object ka normal attribute nahi

`super()` ko method/class definition ke andar use karte hain. `samsung.super` likhna intended syntax nahi. `super()` MRO (Method Resolution Order) ke next implementation ko access karta hai; multiple inheritance mein yeh sirf hard-coded direct parent ko select karne ka shortcut nahi hai.

---

# Chapter 18 — Types of Inheritance

Video mein sir inheritance structures ko `Phone`, `Smartphone`, `FeaturePhone` aur `Product` jaise classes ke through explain karte hain.

## 18.1 Single inheritance

Ek child ek parent class se inherit karti hai.

```python
class Phone:
    def buy(self):
        print("Buying a phone")

class Smartphone(Phone):
    pass

samsung = Smartphone()
samsung.buy()  # inherited Phone.buy()
```

Diagram: `Phone <- Smartphone`.

## 18.2 Multilevel inheritance

Inheritance chain banti hai: child parent se, aur parent kisi aur base class se inherit karta hai.

```python
class Product:
    def review(self):
        print("Product review")

class Phone(Product):
    def buy(self):
        print("Buying a phone")

class Smartphone(Phone):
    pass

samsung = Smartphone()
samsung.buy()     # Phone se
samsung.review()  # Product se
```

Diagram: `Product <- Phone <- Smartphone`. Smartphone inherited Phone aur Product ke available methods use kar sakta hai.

## 18.3 Hierarchical inheritance

Ek parent se multiple child classes inherit karti hain.

```python
class Phone:
    def call(self):
        print("Calling")

class Smartphone(Phone):
    pass

class FeaturePhone(Phone):
    pass

Smartphone().call()
FeaturePhone().call()
```

Diagram: `Phone` parent hai aur `Smartphone`/`FeaturePhone` children hain.

## 18.4 Multiple inheritance

Ek child multiple parent classes se inherit karti hai. Video mein `Smartphone` ko `Phone` aur `Product` dono se inherit karne ka example use hota hai.

```python
class Product:
    def review(self):
        print("Product review")

class Phone:
    def buy(self):
        print("Buying a phone")

class Smartphone(Phone, Product):
    pass

samsung = Smartphone()
samsung.buy()     # Phone se
samsung.review()  # Product se
```

`class Smartphone(Phone, Product)` mein base classes ka order bhi important ho sakta hai; Chapter 19 MRO explain karta hai.

## 18.5 Hybrid inheritance

Hybrid inheritance multiple patterns ka combination hota hai. Misal ke liye ek hierarchy mein `Phone` se `Smartphone` aur `FeaturePhone` derive hon, aur `Smartphone` kisi independent `Product` class se bhi inherit kare. Hybrid pattern ka fixed one-line syntax nahi; class graph dekhkar identify kiya jaata hai.

### Quick memory aid

- Single: one parent, one child.
- Multilevel: parent-child chain.
- Hierarchical: one parent, multiple children.
- Multiple: one child, multiple parents.
- Hybrid: above patterns ka combination.

---

# Chapter 19 — MRO (Method Resolution Order)

## 19.1 MRO kyun chahiye?

Multiple inheritance mein agar same method `Phone` aur `Product` dono mein defined ho, to Python ko decide karna hota hai ki kaunsa method pehle search hoga. **MRO** wahi ordered search path hai.

## 19.2 Sir ka `Product` + `Phone` + `Smartphone` example

```python
class Product:
    def buy(self):
        print("Product buy method")

    def review(self):
        print("Product review method")

class Phone:
    def buy(self):
        print("Phone buy method")

class Smartphone(Phone, Product):
    pass

samsung = Smartphone()
samsung.buy()       # Phone buy method
samsung.review()    # Product review method
print(Smartphone.mro())
```

`Smartphone` mein apna `buy()` nahi hai. Bases `Phone, Product` is order mein likhe hain, isliye Python MRO mein `Phone` pehle search karta hai aur `Phone.buy()` execute karta hai. `review()` Phone mein nahi milta, isliye Product se milta hai.

Agar declaration reverse kar do:

```python
class Smartphone(Product, Phone):
    pass
```

Aur dono parent classes mein `buy()` hi rahe, to `Product.buy()` pehle mil sakta hai. Base-class order behaviour change karta hai.

## 19.3 MRO inspect karna

```python
print(Smartphone.mro())
print(Smartphone.__mro__)
```

Typical first example ka order `Smartphone -> Phone -> Product -> object` hoga. Python C3 linearization use karta hai; beginner ke liye sabse important baat: multiple inheritance mein method ko guess nahi, MRO se check karo.

## 19.4 `self.method()` se accidental recursion

Video ek tricky case bhi discuss karta hai: agar child ke `m1()` method ke andar `self.m1()` call kar diya, to child object ke through wahi child method phir se call ho sakta hai. Base method call karna intended ho to `super().m1()` use hota hai.

```python
class Parent:
    def m1(self):
        print("Parent m1")

class Child(Parent):
    def m1(self):
        print("Child m1")
        super().m1()

Child().m1()
```

Output:

```text
Child m1
Parent m1
```

Agar `super().m1()` ki jagah `self.m1()` likh diya, to repeated recursive calls aur finally `RecursionError: maximum recursion depth exceeded` ho sakta hai.


---

# Chapter 20 — Method Overloading and Operator Overloading

## 20.1 Method overloading: sir ka `Geometry.area()` example

Sir ka example: shape ka area calculate karna hai. Circle ke liye ek input—radius—chahiye; rectangle ke liye do inputs—length aur width. Idea yeh hai ki method name `area` same rahe, input pattern ke hisaab se behaviour choose ho.

### Why this direct Java-style code doesn't work in Python

```python
class Geometry:
    def area(self, radius):
        return 3.14 * radius * radius

    def area(self, length, width):
        return length * width
```

Python mein class ke andar same naam se second `def area` likhne par pehli definition overload-list mein preserve nahi hoti; second definition pehli ko replace kar deti hai. Isliye `Geometry().area(5)` par missing `width` ki error aayegi.

### Python mein similar behaviour ka practical solution

```python
class Geometry:
    def area(self, a, b=None):
        if b is None:
            # One argument: circle radius
            return 3.14 * a * a
        # Two arguments: rectangle length and width
        return a * b

shape = Geometry()
print(shape.area(5))     # 78.5: circle radius 5
print(shape.area(4, 6))  # 24: rectangle 4 x 6
```

Yeh signature-based method overloading nahi hai; optional parameter aur condition se similar functionality implement ki gayi hai. Zaroorat ho to separate names (`circle_area`, `rectangle_area`) readability aur bhi improve kar sakte hain.

## 20.2 Operator overloading: `Fraction` example

Normally `+` numbers add karta hai. Lekin do `Fraction` objects ke liye Python ko addition rule chahiye. Chapter 7 mein humne `Fraction.__add__()` define karke rule diya:

```python
class Fraction:
    def __init__(self, numerator, denominator):
        self.numerator = numerator
        self.denominator = denominator

    def __str__(self):
        return f"{self.numerator}/{self.denominator}"

    def __add__(self, other):
        numerator = (
            self.numerator * other.denominator
            + other.numerator * self.denominator
        )
        denominator = self.denominator * other.denominator
        return Fraction(numerator, denominator)

x = Fraction(2, 3)
y = Fraction(5, 6)
print(x + y)  # 27/18
```

`x + y` par Python `x.__add__(y)` ka logic use karta hai. Is example mein result ek naya `Fraction` object hai.

Other common special methods:

| Python operation | Special method |
|---|---|
| `a + b` | `__add__()` |
| `a - b` | `__sub__()` |
| `a * b` | `__mul__()` |
| `a / b` | `__truediv__()` |
| `print(obj)` / `str(obj)` | `__str__()` |
| `len(obj)` | `__len__()` |
| `a == b` | `__eq__()` |

## 20.3 Magic / dunder methods

Special methods ke naam aam taur par double underscore se start aur end hote hain—jaise `__init__`, `__str__`, `__add__`. Python inhe specific operations/protocols ke dauraan call karta hai. Sirf kisi normal method ka naam apni marzi se `__something__` rakh dene se woh automatically meaningful built-in protocol nahi ban jaata; Python ke defined special-method names use karne hote hain.

---

# Chapter 21 — Mini Project: Indian Rail API / IRCTC-Style App

Video ke final project ka aim ek train-information application banana hai jo external **Indian Rail API** se information fetch kare. Menu-based program mein user train number ya PNR jaise input se railway details request kar sakta hai.

## 21.1 Video mein dikhaye gaye features

- Train number se train schedule/route dekhna.
- PNR se related information request karna.
- Kisi station par trains ke baare mein information lena.
- Train ki seat availability/fare jaise data ke options discuss karna.

Video mein schedule example ke liye train number **12222** dikhaya gaya hai; narration ise Howrah se Pune jaane wali Duronto Express se relate karti hai. Ek aur sample train number **20965** use hota hai, jiske sample route ko Ajmer se Agra ke roop mein discuss kiya jaata hai. Ye video ke examples hain—not a promise that live route/schedule data aaj bhi same hai.

## 21.2 API kya hai?

API (Application Programming Interface) ek defined way hai jisse ek program doosri service se data/functionality request kar sakta hai. Video mein sir Indian Rail API website par account banakar API key lene, train number ko URL mein dene, aur browser se JSON response dekhne ka process dikhate hain.

Typical flow:

1. API provider par account banao.
2. Provider ke dashboard se API key lo.
3. Correct endpoint/URL mein API key aur train number do.
4. HTTP response receive karo.
5. JSON response parse karo.
6. Response mein `route` jaise list/fields ko traverse karke station/time display karo.

> **Current-service warning:** Video ka provider/endpoint old ho sakta hai. Account, API key, URL pattern, response fields, quotas aur access current provider documentation se verify karna hoga. Neeche wala pattern learning scaffold hai, guaranteed current endpoint nahi.

## 21.3 JSON structure ko samajhna

JSON response browser mein raw text ke roop mein aa sakta hai. Video mein JSON formatter/tool se structure readable banaya jaata hai. Parsed JSON Python mein generally dictionaries aur lists banta hai.

Simplified example (actual fields/provider response vary kar sakte hain):

```json
{
  "response_code": 200,
  "status": "success",
  "message": null,
  "route": [
    {
      "station_name": "Howrah",
      "arrival_time": "Source-provided time",
      "departure_time": "Source-provided time",
      "distance": 0
    },
    {
      "station_name": "Tatanagar",
      "arrival_time": "Source-provided time",
      "departure_time": "Source-provided time",
      "distance": 250
    }
  ]
}
```

- Outer JSON object -> Python dictionary.
- `route` -> list.
- List ka har station entry -> dictionary.
- Ek station ka naam access karne ke liye `route[0]["station_name"]` jaisa nested lookup use hota hai.

## 21.4 Python se API request ka conceptual skeleton

```python
import os
import requests

API_KEY = os.environ["INDIAN_RAIL_API_KEY"]


def fetch_train_schedule(train_number):
    # Video-era endpoint pattern; verify the provider's current docs first.
    url = (
        "https://indianrailapi.com/api/v2/TrainSchedule/"
        f"apikey/{API_KEY}/TrainNumber/{train_number}/"
    )
    response = requests.get(url, timeout=10)
    response.raise_for_status()
    return response.json()


def display_route(data):
    # Key names depend on the actual provider response.
    route = data.get("route", data.get("Route", []))
    for stop in route:
        station = stop.get("station_name", stop.get("StationName", "Unknown station"))
        arrival = stop.get("arrival_time", stop.get("ArrivalTime", "N/A"))
        departure = stop.get("departure_time", stop.get("DepartureTime", "N/A"))
        print(station, arrival, departure)

# Example usage after setting INDIAN_RAIL_API_KEY:
# data = fetch_train_schedule("12222")
# display_route(data)
```

Important: API key ko code/GitHub mein hard-code nahi kiya; environment variable se read kiya hai. Actual API may use different URL fields/header/query parameters, so current docs ke according update karna hoga.

## 21.5 Is project mein OOP kahan fit hota hai?

Video ka main flow API aur JSON par focus karta hai; ise class ke roop mein organize bhi kar sakte hain. Example: `RailwayApp` configuration hold kar sakti hai aur `fetch_train_schedule()` / `display_route()` methods provide kar sakti hai. Is tarah fetching, parsing aur presentation ki responsibilities separate reh sakti hain.

## 21.6 Good practices

- API key ko public source code mein expose mat karo.
- `timeout` set karo, kyunki network request fail/slow ho sakti hai.
- `raise_for_status()` aur exception handling se HTTP failures handle karo.
- JSON field missing ho sakta hai; `.get()` ya validation use karo.
- API provider ke terms, rate limits aur current documentation check karo.

---

# Quick Revision — Core Concepts at a Glance

| Concept | Beginner-friendly meaning | Example / signal |
|---|---|---|
| OOP | Program ko objects aur unke behaviour ke around organize karna | OYO/Uber/college platform problems |
| Class | Object banane ka blueprint | `class ATM:` / `class Car:` |
| Object | Class ka actual instance | `SBI = ATM("1234", 10000)` |
| Attribute | Object/class se associated data | `self.name` |
| Method | Class ke andar defined function | `student.introduce()` |
| `__init__()` | Object ki initial state set karta hai | `self.name = name` |
| `self` | Current instance ka reference | `self.balance` |
| Encapsulation | Data/behaviour ko organize aur access ko control karna | Validation methods, `_name`, `__pin` |
| Reference | Variable object ko refer karta hai | `b = a` |
| Mutation | Existing object ko change karna | `items.append(1)` |
| Class variable | Class ke saath associated shared data | `Customer.__counter` |
| Static method | Class namespace mein method jise automatic `self`/`cls` nahi milta | `@staticmethod` |
| Aggregation | HAS-A relationship | Customer has an Address |
| Inheritance | Child class parent ka behaviour inherit karti hai | `Student(User)` / `Smartphone(Phone)` |
| Overriding | Child same-name method ka implementation replace karti hai | `Student.login()` |
| Polymorphism | Same interface, different behaviour | `Phone.buy()` vs `Smartphone.buy()` |
| `super()` | MRO ke next implementation tak access | `super().__init__()` |
| MRO | Method lookup ka order | `MyClass.mro()` |
| Method overloading (Python) | Same name/variants ko defaults/dispatch se emulate karna | `width=None` |
| Operator overloading | Custom object ke operators ka behaviour define karna | `__add__()` |
| Special method | Python protocol se linked method | `__str__`, `__len__` |

---

# Common Beginner Mistakes

1. **Class aur object ko same samajhna.** Class blueprint hai; object instance hai.
2. **`self` bhool jaana.** Instance methods ki definition mein `self` first parameter rakho.
3. **`__init__` ki spelling galat likhna.** Dono sides double underscore hain.
4. **`self.name` aur `name` confuse karna.** Ek object attribute hai; doosra local parameter ho sakta hai.
5. **Sochna ki `b = a` automatically copy banata hai.** Assignment often same object ka another reference banata hai.
6. **`is` ko content equality ke liye use karna.** Identity ke liye `is`; equality ke liye generally `==`.
7. **Mutate aur reassign ko same samajhna.** Shared list modify karna caller ko affect kar sakta hai; parameter reassign karna caller's variable ko reassign nahi karta.
8. **Har field ko class variable bana dena.** Per-object information normally instance attributes mein honi chahiye.
9. **Python `private` ko secure secret storage samajhna.** Double underscore name mangling hai, security barrier nahi.
10. **Har HAS-A relation ke liye inheritance use karna.** Address customer ka part/relationship hai; usually Customer ko Address se inherit nahi karna chahiye.
11. **Child `__init__()` likhkar parent initialization bhool jaana.** Zaroorat ho to `super().__init__(...)` call karo.
12. **Multiple inheritance mein method lookup guess karna.** `ClassName.mro()` inspect karo.
13. **Expect karna ki Python C++/Java jaisi signature-based method overloading automatically karega.** Python mein repeated same-name definitions previous definition ko replace kar deti hain.
14. **Custom operators define karte waqt invalid inputs ignore karna.** Real classes mein type checks/meaningful errors ka design zaroor socho.
15. **API endpoint aur API key ko permanent maan lena.** External service ka contract/documentation verify karna hota hai.

---

# Practice Questions

Pehle khud solve karne ki koshish karo; phir hints/answers dekho.

## Questions

1. Sir ke `Car` example ko implement karo: brand/colour attributes aur `start()` method add karo.
2. Sir ke `Geometry.area()` example ko implement karo: one argument par circle area, two arguments par rectangle area.
3. Sir ke `ATM` example mein `deposit()`, `withdraw()` aur `check_balance()` methods likho. Negative amount aur insufficient balance handle karo.
4. `a = [1, 2]`, `b = a` aur `c = a.copy()` ke baad `b.append(3)` karoge to `a`, `b`, `c` mein kya hoga?
5. `self` kya represent karta hai? Kya `self` reserved keyword hai?
6. Udemy-style example mein `User` parent, `Student` aur `Instructor` child classes banao. Common `login()`/`register()` reuse karo.
7. Ek class variable `total_created` se count karo ki kitne objects create hue.
8. `Customer` objects ki list banao aur loop mein sabka name print karo.
9. Aggregation aur inheritance ke liye ek-ek real-world example do.
10. Sir ke `Fraction` example ke liye `__add__()` implement karo taaki `Fraction(2, 3) + Fraction(5, 6)` meaningful result de.

## Short answers / hints

1. `Car` class mein `brand` aur `colour` attributes store karo; `start()` method se message print karo.
2. Circle area = `3.14 * radius * radius`; rectangle area = `length * width`.
3. Deposit amount positive hona chahiye. Withdrawal se pehle check karo `amount <= balance`.
4. `a` aur `b` same list refer karte hain, to dono ` [1, 2, 3]` dikhayenge. `c` independent shallow copy hai, so it remains `[1, 2]`.
5. `self` current instance ko refer karta hai; yeh reserved keyword nahi, convention hai.
6. `class Student(User): ...`; student ke apne `__init__()` mein parent initialization chahiye ho to `super().__init__(...)` use karo.
7. Class body mein `total_created = 0`; `__init__()` mein `ClassName.total_created += 1` ya suitable `type(self)` logic use karo.
8. `for customer in customers: print(customer.name)`.
9. Aggregation: `Customer` has an `Address`. Inheritance: `Student` is a type of `User`.
10. `__add__()` fraction formula se numerator/denominator calculate karke new `Fraction` object return kare.

---

# Final Mental Model

OOP ko is sequence mein yaad rakho:

1. **Class** define karti hai ki objects ka data/behaviour kya hoga.
2. **Object** us class ka instance hai.
3. **Attributes** object ki state rakhte hain; **methods** operations define karte hain.
4. `__init__()` initial state set karta hai; `self` current instance ko refer karta hai.
5. **Encapsulation** internal implementation/data ko organize aur controlled access dene mein help karti hai.
6. **References** samjhate hain ki multiple variables same object ko refer kar sakte hain.
7. **Aggregation** objects ko HAS-A relation se jodti hai; **inheritance** IS-A relation se behaviour reuse/extend karti hai.
8. **Polymorphism** ek common interface ko different implementations ke saath use karne deta hai.
9. `super()` aur **MRO** inherited methods ke lookup/coordination ko explain karte hain.
10. **Special methods** se Python operators aur built-in operations ko apni classes ke liye meaningful banaya ja sakta hai.

Best revision method: notes padhne ke baad `ATM`, `Fraction`, `Customer` + `Address`, `User`/`Student`/`Instructor`, `Phone`/`Smartphone`/`Product`, aur `Geometry` examples ko bina dekhe khud implement karo. Agar tum code ko apni language mein explain kar paate ho, to concept ratne ke bajaye samajh aa raha hai.