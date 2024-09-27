# Python Lesson: Lists, Tuples, Dictionaries, and Loops

## Overview

This lesson introduces fundamental data structures and control flow concepts in Python, with comparisons to JavaScript. It covers lists, tuples, dictionaries, and loops, providing a solid foundation for working with collections and iterating over data in Python. 

## Lesson Objectives

By the end of this lesson, you should be able to:

1. Create and manipulate lists in Python
2. Understand list methods and how they compare to JavaScript array methods
3. Use list slicing and list comprehensions effectively
4. Create and work with tuples, understanding their immutable nature
5. Differentiate between when to use lists versus tuples in Python
6. Implement various types of loops in Python, including for loops
7. Understand the differences between Python and JavaScript loops
8. Utilize `range()`, `enumerate()`, and indexing in loops
9. Create and manipulate dictionaries in Python
10. Compare dictionary methods to JavaScript object methods
11. Recognize the similarities and differences between Python's data structures and their JavaScript counterparts

## Lists in Python

Lists in Python are similar to arrays in JavaScript. They are ordered, mutable collections that can contain elements of different types. Lists are defined using square brackets `[]` and elements are separated by commas.

### Creating Lists

```python
# Creating a list
fruits = ["apple", "banana", "cherry"]
print(fruits)

# Lists can contain different types
mixed_list = [1, "two", 3.0, True]
print(mixed_list)
```

### Indexing and Slicing

Python uses zero-based indexing, just like JavaScript. 
Additionally, Python supports negative indexing, which allows you to access elements from the end of the list. When using negative indexing, the index starts at -1 for the last element, -2 for the second last, and so on.


```python
# Indexing
print(fruits[0])  # First item
print(fruits[-1])  # Last item
print(fruits[2])  # Third item  
print(fruits[-2])  # Second last item
```

### Slicing

Slicing in Python allows you to access a subset of elements from a list. The syntax for slicing is `list[start:stop:step]`, where `start` is the index to begin the slice, `stop` is the index to end the slice (exclusive), and `step` is the interval between elements in the slice. All three parameters are optional.

- `start`: The beginning index of the slice. If omitted, the slice starts from the beginning of the list.
- `stop`: The ending index of the slice (exclusive). If omitted, the slice goes until the end of the list.
- `step`: The step size or interval between elements. If omitted, the default step size is 1.

Examples:

```python
fruits = ["apple", "banana", "cherry", "date", "elderberry"]



# Slicing
print(fruits[1:3])  # From index 1 to 2 (exclusive of 3)
print(fruits[:3])  # From start to index 2
print(fruits[2:])  # From index 2 to end
print(fruits[::2])  # Every second item

```
One fun slice trick to remember is how to reverse a list:

```python
print(fruits[::-1])  # Reverse the list
```

### Common List Methods

Python list methods are similar to JavaScript array methods, but there are some differences. 

### Append Method
Python lists have the `append` method, which is similar to JavaScript's `push` method, but Python does not have a direct equivalent to JavaScript's `shift` and `unshift` methods. Additionally, Python lists use `remove` to delete the first occurrence of a value, whereas JavaScript arrays use `splice` to remove elements at a specific index.


Example:


```python
fruits = ["apple", "banana", "cherry"]

# Append (similar to JavaScript push)
fruits.append("date")
print(fruits)
# output: ['apple', 'banana', 'cherry', 'date']

# Equivalent in JavaScript:
# fruits.push("date");
# console.log(fruits);  
#output: ['apple', 'banana', 'cherry', 'date']

```
### Extend Method

The `extend` method in Python is used to add multiple elements to the end of a list. It takes an iterable (such as a list, tuple, or string) as an argument and appends each element of the iterable to the list. This is similar to using the `+=` operator with lists.

```python
# Extend (add multiple elements)
fruits.extend(["elderberry", "fig"])
print(fruits)
# output: ['apple', 'banana', 'cherry', 'date', 'elderberry', 'fig']

    # Equivalent in JavaScript:
    # fruits.push("elderberry", "fig");
    # console.log(fruits);  
    # output: ['apple', 'banana', 'cherry', 'date', 'elderberry', 'fig']
```

### Insert Method

The `insert` method in Python is used to insert an element at a specific position in the list. It takes two arguments: the index at which to insert the element and the element to be inserted.

```python
# Insert
fruits.insert(1, "apricot")
print(fruits)
# output: ['apple', 'apricot', 'banana', 'cherry', 'date', 'elderberry', 'fig']

# Equivalent in JavaScript:
# fruits.splice(1, 0, "apricot");
# console.log(fruits);  
# output: ['apple', 'apricot', 'banana', 'cherry', 'date', 'elderberry', 'fig']
```

### Remove Method

The `remove` method in Python is used to remove the first occurrence of a value from the list.

```python
# Remove (removes first occurrence)
fruits.remove("banana")
print(fruits)
# output: ['apple', 'apricot', 'banana', 'cherry', 'date', 'elderberry', 'fig']

# Equivalent in JavaScript:
# fruits.splice(fruits.indexOf("banana"), 1);
# console.log(fruits);  
# output: ['apple', 'apricot', 'cherry', 'date', 'elderberry', 'fig']
```

### Pop Method

The `pop` method in Python is used to remove and return an item at a specific index from the list. If no index is specified, it removes and returns the last item from the list. If you set a variable to the `pop` method, it will return the popped item just like in JavaScript.

```python
# Pop (removes and returns item at index, default is last item)
popped = fruits.pop()
print(f"Popped: {popped}")
# output: "Popped: fig"
print(fruits)
# output: ['apple', 'apricot', 'banana', 'cherry', 'date', 'elderberry']

```

### Sort Method

The `sort` method in Python is used to sort the list in ascending order.

```python
# Sort (in-place sorting)
fruits.sort()
print(fruits)
# output: ['apple', 'apricot', 'banana', 'cherry', 'date', 'elderberry']
```
To sort numbers you do not need to use the callback function with the subtraction trick as you do in JavaScript, Python can sort numbers just fine.

```python
numbers = [5, 2, 8, 1, 3, 11]
numbers.sort()
print(numbers)
# output: [1, 2, 3, 5, 8, 11]
```

### Reverse Method

The `reverse` method in Python is used to reverse the list in place. This is similar to JavaScript's `reverse` method.

```python
# Reverse
fruits.reverse()
print(fruits)
# output: ['fig', 'elderberry', 'date', 'cherry', 'banana', 'apricot', 'apple']
```

### List Comprehensions

List comprehensions are a powerful feature in Python, not present in JavaScript. They provide a concise way to create lists based on existing lists. You can also incorporate loops within list comprehensions to generate lists dynamically. For example, you can use a for loop inside a list comprehension to iterate over a range or another list and apply an expression to each item. Additionally, you can include conditional statements to filter items within the loop.

```python
# Create a list of squares
squares = [x**2 for x in range(10)]
print(squares)
# output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Create a list of even numbers
evens = [x for x in range(20) if x % 2 == 0]
print(evens)
# output: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

## Tuples in Python

Tuples are sequences in Python. They are similar to lists but cannot be changed after creation. Tuples are immutable, which means their contents cannot be changed once they are created. This immutability can be a significant advantage in situations where you need to ensure that the data remains constant. For example, when representing coordinates, dates, or other fixed data structures, tuples can provide a clear and efficient way to handle the data.

### Creating Tuples

Tuples are defined using parentheses `()` and elements are separated by commas.
```python
# Creating a tuple
coordinates = (10, 20)
print(coordinates)
# output: (10, 20)
```
Note: For single element tuples you need to include the comma otherwise Python will not recognize it as a tuple.
# Single-element tuple (note the comma)
single_element = (5,)
print(single_element)
# output: (5,)
```
Tuple packing is the process of assigning multiple values to a single variable in a single statement.

```python
# Tuple packing
person = "John", 30, "New York"
print(person)
# output: ('John', 30, 'New York')
```


```python
### Tuple Immutability

Tuples are immutable, which means their contents cannot be changed once they are created. This immutability can be a significant advantage in situations where you need to ensure that the data remains constant. For example, when representing coordinates, dates, or other fixed data structures, tuples can provide a clear and efficient way to handle the data.
```python
coordinates = (10, 20)
try:
    coordinates[0] = 15  # This will raise a TypeError
except TypeError as e:
    print(f"Error: {e}")

#output: Error: 'tuple' object does not support item assignment
```
However, you can reassign the entire tuple.

```python
coordinates = (15, 25)
print(coordinates)
# output: (15, 25)
```

Also, similar to array destructuring in JavaScript, you can destructure tuples
x, y = coordinates
print(x, y)
# output: 15 25

JavaScript equivalent:

```javascript
const coordinates = [15, 25];
const [x, y] = coordinates;
console.log(x, y);
// output: 15 25
```

## Loops in Python

Python's loop syntax is quite different from JavaScript's, but the concepts are similar.

### For Loops

The `for...in` loop in Python is used to iterate over a sequence (such as a list, tuple, or string) and execute a block of code for each item in the sequence. 

```python
# Iterating over a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Equivalent in JavaScript:
# for (let fruit of fruits) {
#     console.log(fruit);
# }

# Using range()
for i in range(5):
    print(i)

# Equivalent in JavaScript:
# for (let i = 0; i < 5; i++) {
#     console.log(i);
# }

Different from JavaScript, you can use the `enumerate` function to get the index of the item in the list.

# Using enumerate()
for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")

# Equivalent in JavaScript:
# fruits.forEach((fruit, index) => {
#     console.log(`Index ${index}: ${fruit}`);
# });
```

### Loop Control Statements
You can loop based on a range of numbers, but you can also loop based on a range of numbers in reverse.

Both break and continue work the same way they do in JavaScript.
```python
# break and continue
for i in range(10):
    if i == 3:
        continue  # Skip 3
    if i == 7:
        break  # Stop at 7
    print(i)

# Reverse loop
for i in range(10, 0, -1):
    print(i)
```
notice that you can use break and continue in a for loop just like in JavaScript.

## Dictionaries in Python

Dictionaries in Python are similar to objects in JavaScript. They store key-value pairs.

### Creating and Using Dictionaries

Dictionaries are defined using curly braces `{}` and keys and values are separated by commas similar to how you would define an object in JavaScript.
```python
# Creating a dictionary
person = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

You can access the values in a dictionary using the keys.
# Accessing values
print(person["name"])
# output: John

The preferred method to access dictionary values is using the `get` method. This method is safer because it will not raise an error if the key does not exist.
print(person.get("age"))  # Safer method if key might not exist
# output: 30

You cannot use dot notation to access dictionary values in Python, you must use bracket notation.

### Adding and Modifying Dictionary Values
In order to add or modify a value in a dictionary you can use the same bracket notation.

```python
# Adding or modifying entries
person["job"] = "Developer"
person["age"] = 31

# Deleting entries
del person["city"]

print(person)
#output: {'name': 'John', 'age': 31, 'job': 'Developer'}
```
Or you can use the `update` method.

```python
    # Using the update method
person.update({"height": 180, "weight": 75})
print(person)
#output: {'name': 'John', 'age': 31, 'job': 'Developer', 'height': 180, 'weight': 75}
```

### Dictionary Methods

The `keys`, `values`, and `items` methods are used to get the keys, values, and items (key-value pairs) of a dictionary similar to Object.keys(), Object.values(), and Object.entries() in JavaScript.

```python
# Keys, values, and items
print(person.keys())

#ouput: dict_keys(['name', 'age', 'city', 'job', 'height', 'weight'])

print(person.values())
#ouput: dict_values(['John', 30, 'New York', 'Developer', 180, 75])

print(person.items())

#ouput: dict_items([('name', 'John'), ('age', 30), ('city', 'New York'), ('job', 'Developer'), ('height', 180), ('weight', 75)])   
```

### Iterating Over Dictionaries

You can iterate over a dictionary using a for loop and a for loop with the `items` method. The items method is the most efficient way to iterate over a dictionary.

```python
# Python
person = {
    "name": "John",
    "age": 30
}

# Iterating over a dictionary
for key in person:
    print(f"{key}: {person[key]}")
#output:
# name: John
# age: 30
```
You can also use the `items` method to iterate over a dictionary. The `items` method returns a view object that displays a list of a dictionary's key-value tuple pairs.

```python
# Items method for key-value pairs
for key, value in person.items():
    print(f"{key}: {value}")

#output:
# name: John
# age: 30
# name: John
# age: 30
```

## Summary

This lesson provided an overview of Python's data structures and control flow concepts, with comparisons to JavaScript. It covered lists, tuples, dictionaries, and loops, providing a solid foundation for working with collections and iterating over data in Python.

Now it's time to start building!

## Materials

- [Python Lists - Official Documentation](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
- [Python Tuples - Official Documentation](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences)
- [Python for Loops - Real Python](https://realpython.com/python-for-loop/)
- [Python Lists - GeeksforGeeks](https://www.geeksforgeeks.org/python-lists/)
- [Python Tuples - GeeksforGeeks](https://www.geeksforgeeks.org/tuples-in-python/)
- [Python For Loops - GeeksforGeeks](https://www.geeksforgeeks.org/python-for-loop/)
- [List Comprehensions in Python - Real Python](https://realpython.com/list-comprehension-python/)
- [Python Dictionaries - Official Documentation](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)
- [Python Dictionaries - Real Python](https://realpython.com/python-dicts/)
- [Python Dictionaries - GeeksforGeeks](https://www.geeksforgeeks.org/python-dictionary/)
