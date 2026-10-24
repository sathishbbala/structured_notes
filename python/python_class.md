
# Lists
In Python, a list is an ordered, changeable (mutable) collection of items that allows duplicate values. Lists are the most versatile and widely used data structure in Python, written using square brackets [].
Think of a list like a dynamic shopping list: you can keep adding items, crossing items out, rearranging them, or changing them at any point.

``` python
# 1. Creating a list (allows different data types and duplicates)
shopping_list = ["Milk", "Eggs", "Bread", "Milk"]

# 2. Accessing elements using zero-based indexing
print(shopping_list[0])  # Output: Milk
print(shopping_list[-1]) # Output: Milk (Negative index reads from the end)

# 3. Modifying an item (Lists are mutable)
shopping_list[2] = "Croissant"
print(shopping_list)    # Output: ['Milk', 'Eggs', 'Croissant', 'Milk']

# 4. Adding new items
shopping_list.append("Apples")  # Adds to the very end
shopping_list.insert(1, "Butter") # Inserts "Butter" at index 1
print(shopping_list)    # Output: ['Milk', 'Butter', 'Eggs', 'Croissant', 'Milk', 'Apples']

# 5. Removing items
shopping_list.remove("Milk")  # Removes the FIRST occurrence of "Milk"
popped_item = shopping_list.pop() # Removes and returns the last item ("Apples")
print(shopping_list)    # Output: ['Butter', 'Eggs', 'Croissant', 'Milk']

# Slicing (Extracting parts of a list)
numbers = [10, 20, 30, 40, 50]
print(numbers[1:4])  # Output: [20, 30, 40] (Starts at index 1, stops before 4)

# Checking for an item:python
print("Eggs" in shopping_list)  # Output: True

# Sorting a list:python
numbers.sort(reverse=True)
print(numbers)  # Output: [50, 40, 30, 20, 10]
```

# Tuples (Immutable)

``` python
student_info = ("John Doe", 20, "Computer Science", 3.8)
# Accessing elements of the tuple
print("Name:", student_info[0])
print("Age:", student_info[1])
print("Major:", student_info[2])

#show the immutable nature of a tuple
try:
    student_info[1] = 21  # Attempting to change the age   
except TypeError as e:
    print("Error:", e)  # This will raise a TypeError since tuples are immutable
```
``` Error
Error: 'tuple' object does not support item assignment
```

## Named Tuple
Named tuple, which is part of the `collections` module. A named tuple is a subclass of tuples that allows you to access its elements using named fields instead of just index positions. This makes your code more readable and self-documenting. You can create a named tuple using the `namedtuple` factory function from the `collections` module. Here's an example of how to create and use a named tuple:

```python
from collections import namedtuple 
Transaction = namedtuple("Transaction", ["date", "amount", "category", "merchant"])

namedtuple_a = Transaction("2026-10-05", 250.0, "food", "swiggy")
namedtuple_b = Transaction("2026-10-06", 100.0, "transport", "uber")
    
print(namedtuple_a.merchant)      # 'swiggy'  (readable!)
print(namedtuple_a[3])          # 'swiggy'  (still works like a tuple)
```

## Common Use Case: De-duplication

If you have a list with duplicate entries and want to clean it instantly, you can typecast it into a set and back into a list:
```python
numbers = [1, 2, 2, 3, 3, 3, 4]
unique_numbers = list(set(numbers))
print(unique_numbers)  # Output: [1, 2, 3, 4]
```

## Dictionary
In Python, a dictionary is an ordered (as of Python 3.7) collection of data stored in key-value pairs. Instead of accessing items using an index number (like 0 or 1), you access them using a unique key. Dictionaries are written using curly braces with colons {key: value}. Think of a dictionary exactly like its real-world counterpart: you look up a specific word (the key) to find its definition (the value).

``` python
# 1. Creating a dictionary (Keys must be unique; values can be anything)
user_profile = {
    "username": "coder123",
    "followers": 1250,
    "is_active": True,
    "languages": ["Python", "JavaScript"]
}

# 2. Accessing values using their keys
print(user_profile["username"])   # Output: coder123
# Safely access using .get() (Returns None instead of crashing if key doesn't exist)
print(user_profile.get("email"))  # Output: None

# 3. Modifying a value
user_profile["followers"] = 1251
print(user_profile["followers"])  # Output: 1251

# 4. Adding a new key-value pair
user_profile["location"] = "India"

# 5. Removing a key-value pair
del user_profile["is_active"]
# Or use .pop() to remove and get the value back
followers_count = user_profile.pop("followers") 
```

You can iterate through keys, values, or both simultaneously using specific dictionary methods:

``` python
car = {"brand": "Ford", "model": "Mustang", "year": 1964}

# Loop through keys only
for key in car:
    print(key)  # Output: brand, model, year

# Loop through values only
for value in car.values():
    print(value)  # Output: Ford, Mustang, 1964

# Loop through both keys and values using .items()
for key, value in car.items():
    print(f"{key}: {value}")
# Output:
# brand: Ford
# model: Mustang
# year: 1964
```

##   Two Golden Rules of Dictionaries

1. Keys must be unique: If you try to add a duplicate key, Python will simply overwrite the old value with the new one.
2. Keys must be immutable: You can use strings, numbers, or tuples as keys. You cannot use lists or sets as keys because they can change.


# Class 

In Python, a class is a blueprint or a template used to create objects. It allows you to group data (attributes) and behaviors (methods) together into a single, reusable package.
To understand it easily, think of a class like a blank credit card application form. The form itself doesn't hold any actual money or belong to anyone; it just defines what information 
a credit card must have (like a cardholder name, credit limit, and balance). When a customer fills out the form, they create a unique object (or instance) of that card.

## Core Concepts

1. The Blueprint (Class): The template that defines the structure (e.g., class BankAccount:).
2. The Object (Instance): The actual, real-world entity created using the template (e.g., alice_account).
3. Attributes: Variables inside the class that hold specific data (e.g., balance = 5000).
4. Methods: Functions inside the class that define what the object can do (e.g., withdraw()).

Here is how you define a financial account class and use it to manage unique customer accounts:

``` python
class BankAccount:
    # The __init__ method acts as the constructor to set up each new account
    def __init__(self, account_holder, initial_balance):
        self.holder = account_holder      # Attribute: Stores the name
        self.balance = initial_balance    # Attribute: Stores the money

    # A method defining how to deposit money
    def deposit(self, amount):
        self.balance += amount
        return f"Deposited ₹{amount:,.2f}. Current balance: ₹{self.balance:,.2f}"

# -------------------------------------------------------------
# Creating unique objects (instances) from our BankAccount blueprint
# -------------------------------------------------------------

account_a = BankAccount("Alice Sharma", 50000.00)
account_b = BankAccount("Bob Patel", 1200.00)

# Accessing attributes and running methods
print(account_a.holder)          # Output: Alice Sharma
print(account_a.deposit(5000))   # Output: Deposited ₹5,000.00. Current balance: ₹55,000.00
print(account_b.balance)         # Output: 1200.0 (Bob's balance remains unchanged)
```

## Why Use Classes?

1. Data Isolation: As shown above, modifying Alice's balance has absolutely no effect on Bob's balance. Each object maintains its own private state.
2. Organization: It keeps related financial math and customer data locked safely in one clean place rather than scattering variables all over your code.
3. Reusability: You can write the rules for a BankAccount once and seamlessly spin up millions of unique accounts for a banking application.

## why "__repr__" and "__eq__" are needed?
To understand why "__repr__" and "__eq__" are needed, you have to look at what Python does under the hood when they are missing. By default, Python doesn't know what is inside your custom object, so it falls back to basic language defaults.

When you create a custom class, Python's default behavior is to print the class name and its memory address hex code.
1. Without __repr__: Python outputs <__main__.Transaction object at 0x7f81b0>. This tells you where the object lives in your computer's RAM, but absolutely nothing about the actual transactional data inside it. This makes debugging your code incredibly difficult.
   
2. With __repr__: You override the default behavior to return a clean, readable string representation of the object's actual state (e.g., Transaction(date='2026-10-05', amount=250.0...)).

NOTE: Python has two formatting methods: __str__ (for clean user-facing text) and __repr__ (for an unambiguous developer-facing representation). If you only define __repr__, Python will use it for both print(a) and when viewing objects inside lists or containers.

When you write a == b, Python invokes the __eq__ method behind the scenes. 
1. Without __eq__: Python checks for Identity. It evaluates a is b—meaning it returns True only if both variables point to the exact same spot in memory. Even if two transactions have identical dates, amounts, and merchants, Python treats them as entirely different entities because they are separate objects in memory.
   
2. With __eq__: You teach Python how to check for Equality (Value comparison). You write the logic that says: "Two transactions are equal if their dates, amounts, categories, and merchants match.

``` python
class Transaction:
    def __init__(self, date, amount, category, merchant):
        self.date = date
        self.amount = amount
        self.category = category
        self.merchant = merchant
    def __repr__(self):
        return f"Transaction(date={self.date}, amount={self.amount}, category={self.category}, merchant={self.merchant})"
    def __eq__(self, other):
        if isinstance(other, Transaction):
            return (self.date == other.date and
                    self.amount == other.amount and
                    self.category == other.category and
                    self.merchant == other.merchant)
        return False


a = Transaction("2026-10-05", 250.0, "food", "swiggy")
print(a)
print(a == Transaction("2026-10-05", 250.0, "food", "swiggy"))
```
```
Output:
Transaction(date=2026-10-05, amount=250.0, category=food, merchant=swiggy)
True
```
