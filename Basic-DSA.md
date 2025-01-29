# **Topics:**

1. **Introduction to DSA** – Basic concepts, importance, and Python’s role.
2. **Arrays & Lists** – Basic operations, searching, and sorting.
3. **Stacks & Queues** – Implementation and applications.
4. **Linked Lists** – Types and operations.
5. **Recursion** – Concept and examples.
6. **Sorting Algorithms** – Bubble, Selection, Insertion, Merge, Quick Sort.
7. **Searching Algorithms** – Linear and Binary Search.
8. **Hashing** – Hash tables and collision handling.
9. **Trees** – Binary Trees and Binary Search Trees (BST).
10. **Graphs** – Basics, DFS, BFS.

---

# `1. **Introduction to DSA** – Basic concepts, importance, and Python’s role.`
## **What is Data?**
Data is any collection of raw facts, numbers, symbols, or characters that represent information. For example:
- A student’s name and roll number.
- A list of products in an online store.
- Temperature readings from a weather station.

Data can be classified into different types:
- **Structured Data** (Databases, Tables)
- **Unstructured Data** (Images, Videos, Text Documents)
- **Semi-structured Data** (JSON, XML)

![image](https://github.com/user-attachments/assets/59190a63-0364-4319-a11e-e84adf53436e)
 

# **2. What is a Data Structure?**
A data structure is a way to organize, manage, and store data efficiently for easy access and modification.

## **Importance of Data Structures**
- **Efficiency**: Helps in faster data retrieval and processing.
- **Organization**: Maintains structured storage for easy management.
- **Scalability**: Helps handle large amounts of data efficiently.
- **Optimization**: Reduces time and space complexity in computations.

## **Real-World Example of Data Structures:**
### **Example: Online Shopping Cart**
- **List:** Stores available products.
- **Queue:** Manages customer service requests.
- **Stack:** Handles undo operations (like removing items from the cart).
- **Hash Table:** Stores user login information.

![image](https://github.com/user-attachments/assets/c205cc4c-0210-4eda-9f28-ff4553f32781)


# **3. What is an Algorithm?**
An algorithm is a step-by-step procedure or a set of rules to perform a task or solve a problem.

## **Characteristics of an Algorithm**
- **Input**: Takes some input.
- **Output**: Produces an output.
- **Definiteness**: Clear and precise steps.
- **Finiteness**: Must terminate after a finite number of steps.
- **Effectiveness**: Every step should be achievable with available resources.

![image](https://github.com/user-attachments/assets/5becc3f8-5bbc-40db-befe-f27a87403a24)


## **Real-World Example of an Algorithm:**
### **Example: ATM Cash Withdrawal**
1. Insert ATM card.
2. Enter PIN.
3. Select withdrawal option.
4. Enter the amount.
5. If the balance is sufficient, dispense cash; otherwise, show an error message.
6. Print receipt and return the card.

# **4. What is Data Structures and Algorithms (DSA)?**
DSA is a combination of:
- **Data Structures**: How data is stored and organized.
- **Algorithms**: How operations are performed on the data.
![image](https://github.com/user-attachments/assets/1263458e-da59-4f0a-934c-eb38baeb17a2)


## **Why Learn DSA?**
- **Optimized Code**: Helps write efficient programs.
- **Problem Solving**: Essential for coding interviews and competitive programming.
- **Real-World Applications**: Used in AI, web development, databases, etc.

# **5. Introduction to Key Data Structures**

## **Arrays & Lists**
- Used to store multiple values in a single variable.
- Example: Managing student records in a classroom.

## **Stacks & Queues**
- **Stack (LIFO – Last In First Out)**: Used for undo features in software.
- **Queue (FIFO – First In First Out)**: Used in call centers for handling service requests.

## **Linked Lists**
- Stores elements dynamically, unlike arrays.
- Example: Music playlist where songs are linked together.

## **Recursion**
- A function that calls itself to solve problems.
- Example: Factorial calculation, Fibonacci series.

## **Sorting Algorithms**
- Used to arrange data systematically.
- Examples: Bubble Sort, Merge Sort (used in e-commerce sites for price sorting).

## **Searching Algorithms**
- Helps find elements in datasets.
- Examples: Linear Search, Binary Search (used in search engines).

## **Hashing**
- Used for quick data retrieval.
- Example: Password storage in databases.

## **Trees & Graphs**
- **Trees**: Used in file system hierarchies.
- **Graphs**: Used in Google Maps for shortest path search.

---


# `2. **Arrays & Lists** – Basic operations, searching, and sorting.`
An **array** or **list** is a collection of elements stored in a sequential order. Lists in Python are dynamic and can hold elements of different data types.

## **Examples of Lists:**
- A list of students in a class.
- A playlist of songs on a music app.
- A queue of orders in a restaurant.

---

# **i. Basic Operations on Lists**
## **Creating a List**
```python
# Creating a list of numbers
numbers = [10, 20, 30, 40, 50]
print(numbers)

# Creating a list with mixed data types
mixed_list = ["Apple", 3.14, 42, True]
print(mixed_list)
```

## **Accessing Elements in a List**
```python
# Accessing elements using indexing
print(numbers[0])  # First element
print(numbers[-1]) # Last element
```

## **Modifying Elements in a List**
```python
# Changing the second element
numbers[1] = 25
print(numbers)
```

## **Adding Elements to a List**
```python
# Using append()
numbers.append(60)
print(numbers)

# Using insert()
numbers.insert(2, 35)
print(numbers)
```

## **Removing Elements from a List**
```python
# Using remove()
numbers.remove(25)  # Removes first occurrence
print(numbers)

# Using pop()
deleted_item = numbers.pop()  # Removes last element
print(deleted_item, numbers)
```

## **Iterating Over a List**
```python
# Using a for loop
for num in numbers:
    print(num)

# Using list comprehension
squared_numbers = [num**2 for num in numbers]
print(squared_numbers)
```

---

# **ii. Searching in Lists**
## **Linear Search**
```python
def linear_search(arr, target):
    for index, value in enumerate(arr):
        if value == target:
            return index
    return -1

numbers = [10, 20, 30, 40, 50]
print(linear_search(numbers, 30))  # Output: 2
```

#### **enumerate:** 
enumerate()function adds a counter to each item in a list or other iterable. It turns the iterable into something we can loop through, where each item comes with its number (starting from 0 by default). We can also turn it into a list of (number, item) pairs using list().

**Syntax of enumerate() method**

```bash
enumerate(iterable, start=0)
```

**Parameters:**
1. **Iterable:** any object that supports iteration
2. **Start:** the index value from which the counter is to be started, by default it is 0

**Return:**
1. Returns an iterator with index and element pairs from the original iterable

**Using a Custom Start Index**

By using enumrate() starts indexing from 0, we can customize this using the start parameter. if want the index to begin at value other than 0.

**example of enumerate:**

```python
a = ["Python", "for", "Everyone"]

# Creating an enumerate object from the list 'a' 
b = enumerate(a)

# This retrieves the first index-element pair from 'b'
nxt_val = next(b)
print(nxt_val)
```

```python
a = ["Python", "for", "Everyone"]

# Iterating list using enumerate to get both index and element
for i, name in enumerate(a):
    print(f"Index {i}: {name}")

# Converting to a list of tuples
print(list(enumerate(a)))
```
```python
a = ["geeks", "for", "geeks"]

#Looping through the list using enumerate
# starting the index from 1
for index, x in enumerate(a, start=1):
    print(index, x)
```

We can use enumerate() in a list comprehension for transformations or filtering.

```python
fruits = ['apple', 'banana', 'cherry']
indexed_fruits = [(i, fruit) for i, fruit in enumerate(fruits)]
print(indexed_fruits)
```
`# Output: [(0, 'apple'), (1, 'banana'), (2, 'cherry')]`

The enumerate() function returns an enumerate object, which is an iterator of tuples containing the index and corresponding item from the iterable.


```python
example = enumerate(['a', 'b', 'c'])
print(list(example))
```
`# Output: [(0, 'a'), (1, 'b'), (2, 'c')]`

## **Binary Search (Only for Sorted Lists)**
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

sorted_numbers = [10, 20, 30, 40, 50]
print(binary_search(sorted_numbers, 40))  # Output: 3
```

---

# **4. Sorting in Lists**
## **Bubble Sort**
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr

unsorted_list = [64, 25, 12, 22, 11]
print(bubble_sort(unsorted_list))
```

## **Selection Sort**
```python
def selection_sort(arr):
    for i in range(len(arr)):
        min_idx = i
        for j in range(i+1, len(arr)):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr

unsorted_list = [64, 25, 12, 22, 11]
print(selection_sort(unsorted_list))
```

## **Insertion Sort**
```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i-1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

unsorted_list = [64, 25, 12, 22, 11]
print(insertion_sort(unsorted_list))
```

## **Merge Sort**
```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]
        merge_sort(left_half)
        merge_sort(right_half)
        i = j = k = 0
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1
        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1
    return arr

unsorted_list = [38, 27, 43, 3, 9, 82, 10]
print(merge_sort(unsorted_list))
```

## **Quick Sort**
```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

unsorted_list = [38, 27, 43, 3, 9, 82, 10]
print(quick_sort(unsorted_list))
```

---
