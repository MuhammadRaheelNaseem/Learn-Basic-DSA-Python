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
# `1. Introduction to DSA – Basic concepts, importance, and Python’s role.`
---

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
---

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

# **3. Stacks & Queues** – Implementation and applications.
---

Stacks and Queues are fundamental data structures used for storing and managing data efficiently. These structures follow specific order mechanisms to retrieve and store data.

## **Real-World Examples:**
- **Stacks:**
  - Undo/Redo functionality in a text editor.
  - Browser back and forward navigation.
  - Call stack in recursion.
- **Queues:**
  - Printer job scheduling.
  - Customer service call handling.
  - Process scheduling in operating systems.


# **i. Stack (LIFO – Last In, First Out)**
A stack follows the **LIFO (Last In, First Out)** principle, meaning the last added element is the first one to be removed.


```python
# Stack Implementation using a list

# Step 1: Initialize an empty stack
stack = []

# Step 2: Push elements onto the stack
stack.append(10)  # Push 10
stack.append(20)  # Push 20
stack.append(30)  # Push 30

# Step 3: Display the current stack
print("Current Stack:", stack)  # Output: [10, 20, 30]
```

---

#### ii. Stack Pop Operation

**Concept**: The pop operation removes the top element from the stack.

```python
# Stack Pop Operation

# Step 1: Initialize the stack
stack = [10, 20, 30]

# Step 2: Pop the top element from the stack
popped_item = stack.pop()  # Removes 30

# Step 3: Display the popped item and the current stack
print("Popped Item:", popped_item)  # Output: 30
print("Stack after popping:", stack)  # Output: [10, 20]
```

---

#### 3. Stack Peek Operation

**Concept**: The peek operation allows you to see the top element without removing it.

```python
# Stack Peek Operation

# Step 1: Initialize the stack
stack = [10, 20, 30]

# Step 2: Peek at the top element
if stack:  # Check if the stack is not empty
    top_item = stack[-1]  # Get the last item
    print("Top Item (Peek):", top_item)  # Output: 30
else:
    print("Stack is empty")
```

---

#### 4. Stack Size Operation

**Concept**: The size operation returns the number of elements in the stack.

```python
# Stack Size Operation

# Step 1: Initialize the stack
stack = [10, 20, 30]

# Step 2: Get the size of the stack
stack_size = len(stack)

# Step 3: Display the size
print("Size of Stack:", stack_size)  # Output: 3
```

---

#### 5. Check if Stack is Empty

**Concept**: This operation checks whether the stack has any elements.

```python
# Check if Stack is Empty

# Step 1: Initialize the stack
stack = []

# Step 2: Check if the stack is empty
is_empty = len(stack) == 0

# Step 3: Display the result
print("Is Stack Empty?", is_empty)  # Output: True
```

---

#### 6. Stack LIFO Concept

**Concept**: Demonstrating the Last In, First Out behavior of stacks.

```python
# Stack LIFO Concept

# Step 1: Initialize the stack
stack = []

# Step 2: Push more items onto the stack
stack.append(10)
stack.append(20)
stack.append(30)

# Step 3: Display the stack
print("Stack after pushing 10, 20, 30:", stack)  # Output: [10, 20, 30]

# Step 4: Pop items and show LIFO behavior
print("Popped Item (should be 30):", stack.pop())  # Output: 30
print("Popped Item (should be 20):", stack.pop())  # Output: 20
```

---

### Queues

#### 7. Basic Queue Implementation

**Concept**: A queue is a collection of elements that follows the First In, First Out (FIFO) principle.

```python
# Queue Implementation using a list

# Step 1: Initialize an empty queue
queue = []

# Step 2: Enqueue elements into the queue
queue.append(10)  # Enqueue 10
queue.append(20)  # Enqueue 20
queue.append(30)  # Enqueue 30

# Step 3: Display the current queue
print("Current Queue:", queue)  # Output: [10, 20, 30]
```

---

#### 8. Queue Dequeue Operation

**Concept**: The dequeue operation removes the front element from the queue.

```python
# Queue Dequeue Operation

# Step 1: Initialize the queue
queue = [10, 20, 30]

# Step 2: Dequeue the front element from the queue
dequeued_item = queue.pop(0)  # Removes  10

# Step 3: Display the dequeued item and the current queue
print("Dequeued Item:", dequeued_item)  # Output: 10
print("Queue after dequeuing:", queue)  # Output: [20, 30]
```

---

#### 9. Queue Enqueue Operation

**Concept**: The enqueue operation adds an element to the back of the queue.

```python
# Queue Enqueue Operation

# Step 1: Initialize the queue
queue = [20, 30]

# Step 2: Enqueue a new element
queue.append(40)  # Enqueue 40

# Step 3: Display the current queue
print("Queue after enqueuing 40:", queue)  # Output: [20, 30, 40]
```

---

#### 10. Queue Size Operation

**Concept**: The size operation returns the number of elements in the queue.

```python
# Queue Size Operation

# Step 1: Initialize the queue
queue = [20, 30, 40]

# Step 2: Get the size of the queue
queue_size = len(queue)

# Step 3: Display the size
print("Size of Queue:", queue_size)  # Output: 3
```

---

#### 11. Check if Queue is Empty

**Concept**: This operation checks whether the queue has any elements.

```python
# Check if Queue is Empty

# Step 1: Initialize the queue
queue = []

# Step 2: Check if the queue is empty
is_empty = len(queue) == 0

# Step 3: Display the result
print("Is Queue Empty?", is_empty)  # Output: True
```

---

#### 12. Queue FIFO Concept

**Concept**: Demonstrating the First In, First Out behavior of queues.

```python
# Queue FIFO Concept

# Step 1: Initialize the queue
queue = [10, 20, 30]

# Step 2: Display the queue
print("Queue before dequeuing:", queue)  # Output: [10, 20, 30]

# Step 3: Dequeue items and show FIFO behavior
print("Dequeued Item (should be 10):", queue.pop(0))  # Output: 10
print("Dequeued Item (should be 20):", queue.pop(0))  # Output: 20
print("Queue after dequeuing:", queue)  # Output: [30]
```

---

 # other way of understanding:
 
### **3. Stacks & Queues – Implementation and Applications**

---

#### **1. Stack Implementation**

```python
# Stack Implementation using a List (LIFO - Last In, First Out)

stack = []

# Push Operation (Add an item to the stack)
stack.append(10)  # Push 10
stack.append(20)  # Push 20
stack.append(30)  # Push 30
print(f"Stack after push operations: {stack}")

# Pop Operation (Remove the top item from the stack)
popped_item = stack.pop()  # Pops 30
print(f"Popped item: {popped_item}")
print(f"Stack after pop operation: {stack}")

# Peek Operation (View the top item without removing it)
top_item = stack[-1] if stack else None
print(f"Top item (Peek): {top_item}")

# Check if the Stack is Empty
is_empty = len(stack) == 0
print(f"Is the stack empty? {is_empty}")
```

**Explanation:**
- **Push**: `append()` is used to add items to the list, simulating the push operation.
- **Pop**: `pop()` removes the last item.
- **Peek**: By accessing the last index `[-1]`, we can view the top item without removing it.
- **Empty Check**: We check if the stack is empty by verifying if the length of the stack is zero.

---

#### **2. Queue Implementation (Without Classes)**

```python
# Queue Implementation using a List (FIFO - First In, First Out)

queue = []

# Enqueue Operation (Add an item to the queue)
queue.append(10)  # Enqueue 10
queue.append(20)  # Enqueue 20
queue.append(30)  # Enqueue 30
print(f"Queue after enqueue operations: {queue}")

# Dequeue Operation (Remove the front item from the queue)
dequeued_item = queue.pop(0)  # Pops 10 (front of the queue)
print(f"Dequeued item: {dequeued_item}")
print(f"Queue after dequeue operation: {queue}")

# Front Operation (View the front item without removing it)
front_item = queue[0] if queue else None
print(f"Front item: {front_item}")

# Check if the Queue is Empty
is_empty = len(queue) == 0
print(f"Is the queue empty? {is_empty}")
```

**Explanation:**
- **Enqueue**: `append()` adds items to the end of the list, simulating the enqueue operation.
- **Dequeue**: `pop(0)` removes the first item in the list, simulating FIFO.
- **Front**: Accessing `queue[0]` gives us the front item without removing it.
- **Empty Check**: Like the stack, we check if the queue is empty by checking the list's length.

---

#### **3. Reverse a List Using Stack**

This example uses the stack to reverse the elements of a list.

```python
# Reversing a list using a Stack

def reverse_list(lst):
    stack = []
    # Push all elements to the stack
    for item in lst:
        stack.append(item)
    
    # Pop all elements from the stack and store them back in the list
    reversed_lst = []
    while stack:
        reversed_lst.append(stack.pop())
    
    return reversed_lst

# Example usage
original_list = [1, 2, 3, 4, 5]
reversed_list = reverse_list(original_list)
print(f"Original List: {original_list}")
print(f"Reversed List: {reversed_list}")
```

**Explanation:**
- We push each element of the list into the stack.
- By popping elements from the stack, we reverse the order of the elements in the original list.

---

#### **4. Check for Balanced Parentheses Using Stack**

This is a common problem where we check if parentheses are balanced using a stack.

```python
# Check if parentheses are balanced using a Stack

def is_balanced(expression):
    stack = []
    # Traverse the expression
    for char in expression:
        if char == "(":
            stack.append(char)  # Push open parenthesis to stack
        elif char == ")":
            if not stack:  # If stack is empty, there's no matching '('
                return False
            stack.pop()  # Pop matching '(' from stack
    
    # If stack is empty, parentheses are balanced
    return len(stack) == 0

# Example usage
expression = "(a + b) * (c + d)"
print(f"Is the expression balanced? {is_balanced(expression)}")
```

**Explanation:**
- We use the stack to push opening parentheses `(`.
- When we encounter a closing parenthesis `)`, we check if there’s a matching opening parenthesis in the stack.
- If the stack is empty at the end, it means all parentheses are balanced.

---

#### **5. Implement a Queue Using Two Stacks**

We can simulate a queue using two stacks. Here's how we do it:

```python
# Queue implementation using two stacks

stack1 = []
stack2 = []

# Enqueue operation (Add an item to the queue)
def enqueue(item):
    stack1.append(item)

# Dequeue operation (Remove the front item from the queue)
def dequeue():
    if not stack2:
        if not stack1:
            print("Queue is empty!")
            return None
        while stack1:
            stack2.append(stack1.pop())  # Move elements from stack1 to stack2
    return stack2.pop()

# Example usage
enqueue(10)
enqueue(20)
enqueue(30)
print(f"Dequeued item: {dequeue()}")  # Output: 10
print(f"Dequeued item: {dequeue()}")  # Output: 20
```

**Explanation:**
- **Enqueue**: Push items to `stack1`.
- **Dequeue**: If `stack2` is empty, transfer all elements from `stack1` to `stack2`, then pop from `stack2` to simulate the queue.

---

#### **6. Reverse a Queue Using Stack**

This program reverses the order of elements in a queue using a stack.

```python
# Reverse a Queue using a Stack

def reverse_queue(queue):
    stack = []
    
    # Push all elements of the queue to the stack
    while queue:
        stack.append(queue.pop(0))  # Dequeue from the front
    
    # Push all elements back to the queue from the stack
    while stack:
        queue.append(stack.pop())  # Enqueue to the back
    
    return queue

# Example usage
queue = [1, 2, 3, 4, 5]
reversed_queue = reverse_queue(queue)
print(f"Reversed Queue: {reversed_queue}")
```

**Explanation:**
- We dequeue all elements from the queue and push them to the stack.
- Then, we pop from the stack and enqueue them back to the queue, reversing the order.

---

### **Key Concepts Recap**
- **LIFO (Last In, First Out)**: Stacks are based on this principle.
- **FIFO (First In, First Out)**: Queues are based on this principle.

---

### Additional Simple Programs for Practice:

#### **7. Check Palindrome Using Stack**
```python
def is_palindrome(word):
    stack = []
    for char in word:
        stack.append(char)
    
    reversed_word = ''.join([stack.pop() for _ in range(len(stack))])
    return word == reversed_word

print(is_palindrome("madam"))  # Output: True
```

#### **8. Implement a Circular Queue Using a List**
```python
queue = []
front = -1
rear = -1
MAX_SIZE = 5

def enqueue(item):
    global front, rear
    if (rear + 1) % MAX_SIZE == front:
        print("Queue is full!")
    else:
        if front == -1:
            front = 0
        rear = (rear + 1) % MAX_SIZE
        queue.append(item)

def dequeue():
    global front, rear
    if front == -1:
        print("Queue is empty!")
    else:
        item = queue.pop(0)
        if front == rear:
            front = rear = -1
        else:
            front = (front + 1) % MAX_SIZE
        return item
```

---

### **4. Linked Lists – Types and Operations**

---

#### **1. Singly Linked List: Basic Implementation**

In a singly linked list, each node contains two parts: data and a reference (or link) to the next node.

```python
# Node class for Singly Linked List
class Node:
    def __init__(self, data):
        self.data = data  # Store the data
        self.next = None  # Initialize the next pointer to None

# Function to print the Linked List
def print_list(head):
    current = head
    while current:
        print(current.data, end=" -> ")
        current = current.next
    print("None")

# Creating nodes
head = Node(10)  # First node
second = Node(20)  # Second node
third = Node(30)  # Third node

# Linking nodes
head.next = second
second.next = third

# Printing the Linked List
print_list(head)
```

**Explanation:**
- **Node**: Each node contains `data` and a `next` pointer, which points to the next node in the list.
- **Print function**: Traverses the list and prints the data in each node.

---

#### **2. Inserting a Node at the Beginning**

Inserting a node at the beginning of the list involves creating a new node and adjusting the head of the list.

```python
# Function to insert a node at the beginning
def insert_at_beginning(head, data):
    new_node = Node(data)  # Create a new node
    new_node.next = head  # Point new node to the current head
    head = new_node  # Make new node the new head
    return head

# Example usage
head = Node(10)
head = insert_at_beginning(head, 5)
print_list(head)
```

**Explanation:**
- **Insert at beginning**: The new node is placed at the start, and the head pointer is updated to the new node.

---

#### **3. Inserting a Node at the End**

To insert a node at the end, we traverse the list until we reach the last node and then insert the new node.

```python
# Function to insert a node at the end
def insert_at_end(head, data):
    new_node = Node(data)  # Create a new node
    if not head:  # If the list is empty, make the new node the head
        head = new_node
        return head
    current = head
    while current.next:  # Traverse to the last node
        current = current.next
    current.next = new_node  # Link the new node at the end
    return head

# Example usage
head = Node(10)
head = insert_at_end(head, 20)
head = insert_at_end(head, 30)
print_list(head)
```

**Explanation:**
- **Insert at end**: The list is traversed until the last node, and the new node is added at the end.

---

#### **4. Deleting a Node (By Value)**

Deleting a node involves searching for the node by its value and adjusting the pointers accordingly.

```python
# Function to delete a node by value
def delete_node(head, value):
    if not head:  # If the list is empty
        print("List is empty")
        return head
    if head.data == value:  # If the head is the node to delete
        return head.next
    current = head
    while current.next:
        if current.next.data == value:  # Node found to delete
            current.next = current.next.next
            return head
        current = current.next
    print("Node not found")
    return head

# Example usage
head = Node(10)
head = insert_at_end(head, 20)
head = insert_at_end(head, 30)
head = delete_node(head, 20)
print_list(head)
```

**Explanation:**
- **Delete by value**: The list is traversed, and if the value is found, the node is removed by changing the `next` pointer of the previous node.

---

#### **5. Searching for an Element in a Linked List**

This function searches for a specific element in the list and returns `True` if found.

```python
# Function to search for a value in the linked list
def search(head, value):
    current = head
    while current:
        if current.data == value:
            return True
        current = current.next
    return False

# Example usage
head = Node(10)
head = insert_at_end(head, 20)
head = insert_at_end(head, 30)
print("Is 20 in the list?", search(head, 20))  # Output: True
print("Is 40 in the list?", search(head, 40))  # Output: False
```

**Explanation:**
- **Search**: The list is traversed node by node, checking if the value matches the node’s data.

---

#### **6. Reversing a Singly Linked List**

To reverse the linked list, we need to adjust the `next` pointers of each node.

```python
# Function to reverse the linked list
def reverse_list(head):
    prev = None
    current = head
    while current:
        next_node = current.next  # Store next node
        current.next = prev  # Reverse the current node's pointer
        prev = current  # Move prev to the current node
        current = next_node  # Move to the next node
    return prev  # New head after reversal

# Example usage
head = Node(10)
head = insert_at_end(head, 20)
head = insert_at_end(head, 30)
head = reverse_list(head)
print_list(head)
```

**Explanation:**
- **Reverse**: We iterate through the list, reversing the `next` pointers as we go.

---

#### **7. Finding the Length of a Linked List**

This function counts how many nodes are in the list.

```python
# Function to find the length of the linked list
def length(head):
    count = 0
    current = head
    while current:
        count += 1
        current = current.next
    return count

# Example usage
head = Node(10)
head = insert_at_end(head, 20)
head = insert_at_end(head, 30)
print(f"Length of the list: {length(head)}")
```

**Explanation:**
- **Length**: This function counts each node by traversing the entire list.

---

### **Types of Linked Lists**

---

#### **8. Doubly Linked List (With Two Pointers)**

In a doubly linked list, each node contains three parts: data, a pointer to the next node, and a pointer to the previous node.

```python
# Node class for Doubly Linked List
class DoublyNode:
    def __init__(self, data):
        self.data = data  # Store the data
        self.next = None  # Pointer to the next node
        self.prev = None  # Pointer to the previous node

# Function to print the Doubly Linked List in forward direction
def print_forward(head):
    current = head
    while current:
        print(current.data, end=" <-> ")
        current = current.next
    print("None")

# Function to print the Doubly Linked List in reverse direction
def print_reverse(tail):
    current = tail
    while current:
        print(current.data, end=" <-> ")
        current = current.prev
    print("None")

# Creating doubly linked nodes
head = DoublyNode(10)
second = DoublyNode(20)
third = DoublyNode(30)

# Linking nodes (forward and backward)
head.next = second
second.prev = head
second.next = third
third.prev = second

# Printing the doubly linked list
print_forward(head)
print_reverse(third)
```

**Explanation:**
- **Doubly Linked List**: Each node points both to the next node and to the previous node, allowing traversal in both directions.

---

#### **9. Circular Linked List**

In a circular linked list, the last node points back to the head instead of `None`.

```python
# Node class for Circular Linked List
class CircularNode:
    def __init__(self, data):
        self.data = data
        self.next = None

# Function to print a circular linked list
def print_circular_list(head):
    if not head:
        return "List is empty"
    current = head
    while True:
        print(current.data, end=" -> ")
        current = current.next
        if current == head:  # Loop back to the head
            break
    print("... (circular)")

# Creating circular linked nodes
head = CircularNode(10)
second = CircularNode(20)
third = CircularNode(30)

# Linking nodes
head.next = second
second.next = third
third.next = head  # Points back to head

# Printing the circular linked list
print_circular_list(head)
```

**Explanation:**
- **Circular Linked List**: The last node points back to the first node, creating a circular structure.




### **5. Recursion – Concept and Examples**

---

#### **1. What is Recursion?**

Recursion is a technique where a function calls itself in order to break a problem down into smaller, more manageable subproblems. A recursive function typically has two main components:

1. **Base Case**: The condition under which the function stops calling itself.
2. **Recursive Case**: The part where the function calls itself to solve a smaller problem.

---

#### **2. Basic Recursion Example: Factorial**

The **Factorial** of a number `n` is the product of all positive integers less than or equal to `n`. For example, the factorial of 5 (`5!`) is `5 * 4 * 3 * 2 * 1 = 120`.

```python
# Recursive function to calculate factorial
def factorial(n):
    if n == 0 or n == 1:  # Base case: factorial of 0 or 1 is 1
        return 1
    else:
        return n * factorial(n - 1)  # Recursive case

# Example usage
print(factorial(5))  # Output: 120
```

**Explanation:**
- **Base Case**: When `n` is 0 or 1, the function stops and returns 1.
- **Recursive Case**: The function calls itself with a smaller value of `n`.

---

#### **3. Recursion Example: Fibonacci Sequence**

The **Fibonacci Sequence** is a series of numbers where each number is the sum of the two preceding ones. The sequence starts as `0, 1, 1, 2, 3, 5, 8, 13, ...`.

```python
# Recursive function to calculate Fibonacci sequence
def fibonacci(n):
    if n == 0:  # Base case: Fibonacci(0) = 0
        return 0
    elif n == 1:  # Base case: Fibonacci(1) = 1
        return 1
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)  # Recursive case

# Example usage
print(fibonacci(5))  # Output: 5 (Fibonacci sequence: 0, 1, 1, 2, 3, 5)
```

**Explanation:**
- **Base Cases**: Fibonacci(0) = 0, Fibonacci(1) = 1.
- **Recursive Case**: Calls itself to sum the two previous numbers in the sequence.

---

#### **4. Recursion Example: Sum of Natural Numbers**

The sum of natural numbers up to `n` can be calculated recursively. The formula is `n + (n-1) + (n-2) + ... + 1`.

```python
# Recursive function to calculate sum of natural numbers
def sum_natural_numbers(n):
    if n == 1:  # Base case: sum of 1 is 1
        return 1
    else:
        return n + sum_natural_numbers(n - 1)  # Recursive case

# Example usage
print(sum_natural_numbers(5))  # Output: 15 (1 + 2 + 3 + 4 + 5)
```

**Explanation:**
- **Base Case**: When `n` is 1, the sum is 1.
- **Recursive Case**: The function calls itself with `n - 1`, adding each value until it reaches 1.

---

#### **5. Recursion Example: Reverse a String**

You can use recursion to reverse a string by splitting the string into smaller substrings and swapping them.

```python
# Recursive function to reverse a string
def reverse_string(s):
    if len(s) == 0:  # Base case: empty string
        return s
    else:
        return reverse_string(s[1:]) + s[0]  # Recursive case

# Example usage
print(reverse_string("hello"))  # Output: "olleh"
```

**Explanation:**
- **Base Case**: When the string is empty, return the empty string.
- **Recursive Case**: Calls itself with the substring `s[1:]` and appends the first character `s[0]` at the end.

---

#### **6. Recursion Example: Finding the Greatest Common Divisor (GCD)**

The **GCD** of two numbers is the largest number that divides both of them. A recursive approach uses the Euclidean algorithm.

```python
# Recursive function to calculate GCD of two numbers
def gcd(a, b):
    if b == 0:  # Base case: if b is 0, return a as the GCD
        return a
    else:
        return gcd(b, a % b)  # Recursive case: Euclidean algorithm

# Example usage
print(gcd(48, 18))  # Output: 6 (Greatest common divisor of 48 and 18)
```

**Explanation:**
- **Base Case**: When `b` is 0, the GCD is `a`.
- **Recursive Case**: The function calls itself with `b` and the remainder of `a` divided by `b`.

---

#### **7. Recursion Example: Binary Search**

Binary search works by repeatedly dividing the search interval in half. If the value is equal to the middle element, we return the index; otherwise, we search in the left or right half recursively.

```python
# Recursive function to perform binary search
def binary_search(arr, target, low, high):
    if low > high:  # Base case: element not found
        return -1
    mid = (low + high) // 2  # Find the middle index
    if arr[mid] == target:  # Base case: element found
        return mid
    elif arr[mid] > target:
        return binary_search(arr, target, low, mid - 1)  # Search left half
    else:
        return binary_search(arr, target, mid + 1, high)  # Search right half

# Example usage
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(binary_search(arr, 5, 0, len(arr) - 1))  # Output: 4 (5 is at index 4)
```

**Explanation:**
- **Base Case**: If the search interval is invalid (`low > high`), return `-1`. If the element is found, return the index.
- **Recursive Case**: Adjust the search range by narrowing it to the left or right half based on comparison with the middle element.

---

#### **8. Recursion Example: Tower of Hanoi Problem**

The **Tower of Hanoi** is a classic problem where we need to move disks from one peg to another, following certain rules.

```python
# Recursive function to solve the Tower of Hanoi problem
def tower_of_hanoi(n, source, auxiliary, target):
    if n == 1:  # Base case: Move the single disk
        print(f"Move disk 1 from {source} to {target}")
    else:
        tower_of_hanoi(n - 1, source, target, auxiliary)  # Move n-1 disks to auxiliary
        print(f"Move disk {n} from {source} to {target}")  # Move the nth disk
        tower_of_hanoi(n - 1, auxiliary, source, target)  # Move n-1 disks to target

# Example usage
tower_of_hanoi(3, 'A', 'B', 'C')  # Move 3 disks from A to C using B
```

**Explanation:**
- **Base Case**: If there's only one disk, it’s directly moved from the source to the target.
- **Recursive Case**: The problem is broken into smaller subproblems where `n-1` disks are moved to an auxiliary peg, then the nth disk is moved, and finally the `n-1` disks are moved to the target peg.

---



### **6. Sorting Algorithms – Bubble Sort, Selection Sort, Insertion Sort, Merge Sort, Quick Sort**

---

#### **1. Bubble Sort**

**Bubble Sort** is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The process is repeated until the list is sorted.

**Time Complexity**: O(n^2)

```python
# Bubble Sort Algorithm
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:  # Swap if the element is greater than the next
                arr[j], arr[j+1] = arr[j+1], arr[j]  # Swap elements
    return arr

# Example usage
arr = [64, 34, 25, 12, 22, 11, 90]
print("Sorted array:", bubble_sort(arr))
```

**Explanation**:
- The outer loop tracks the number of passes.
- The inner loop compares adjacent elements and swaps them if they are out of order.
- After each pass, the largest element is "bubbled" to its correct position.

---

#### **2. Selection Sort**

**Selection Sort** repeatedly selects the smallest (or largest) element from the unsorted part of the list and swaps it with the first unsorted element. It has O(n^2) time complexity, like Bubble Sort.

**Time Complexity**: O(n^2)

```python
# Selection Sort Algorithm
def selection_sort(arr):
    for i in range(len(arr)):
        min_idx = i  # Assume the first unsorted element is the smallest
        for j in range(i+1, len(arr)):
            if arr[j] < arr[min_idx]:
                min_idx = j  # Find the smallest element
        arr[i], arr[min_idx] = arr[min_idx], arr[i]  # Swap the smallest with the first unsorted element
    return arr

# Example usage
arr = [64, 25, 12, 22, 11]
print("Sorted array:", selection_sort(arr))
```

**Explanation**:
- The outer loop iterates through each element.
- The inner loop finds the smallest element from the unsorted part of the array.
- The smallest element is swapped with the first unsorted element.

---

#### **3. Insertion Sort**

**Insertion Sort** builds the final sorted array one item at a time by inserting each element into its correct position in the sorted part of the list.

**Time Complexity**: O(n^2) in the worst case, but O(n) in the best case (when the array is already sorted).

```python
# Insertion Sort Algorithm
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]  # Element to be inserted into the sorted part
        j = i-1
        while j >= 0 and arr[j] > key:  # Shift elements of the sorted part that are greater than the key
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key  # Insert the key at its correct position
    return arr

# Example usage
arr = [64, 25, 12, 22, 11]
print("Sorted array:", insertion_sort(arr))
```

**Explanation**:
- The key element is compared with the elements in the sorted part.
- The sorted part is shifted to make space for the key.
- The key is placed in its correct position.

---

#### **4. Merge Sort**

**Merge Sort** is a **divide and conquer** algorithm. It divides the array into halves, sorts each half recursively, and then merges the sorted halves into a single sorted array.

**Time Complexity**: O(n log n)

```python
# Merge Sort Algorithm
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2  # Find the middle of the array
        left_half = arr[:mid]  # Divide the array into two halves
        right_half = arr[mid:]

        merge_sort(left_half)  # Sort the left half
        merge_sort(right_half)  # Sort the right half

        i = j = k = 0
        # Merge the sorted halves into a single sorted array
        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        # Copy any remaining elements from the left half
        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        # Copy any remaining elements from the right half
        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1

    return arr

# Example usage
arr = [38, 27, 43, 3, 9, 82, 10]
print("Sorted array:", merge_sort(arr))
```

**Explanation**:
- The array is repeatedly divided into halves until the subarrays contain only one element.
- These subarrays are then merged back together in sorted order.

---

#### **5. Quick Sort**

**Quick Sort** is another **divide and conquer** algorithm. It picks a pivot element from the array and partitions the array around the pivot, such that elements smaller than the pivot go to the left, and elements greater than the pivot go to the right. The subarrays are then sorted recursively.

**Time Complexity**: O(n log n) on average, but O(n^2) in the worst case.

```python
# Quick Sort Algorithm
def quick_sort(arr):
    if len(arr) <= 1:  # Base case: array is already sorted
        return arr
    pivot = arr[len(arr) // 2]  # Choose the middle element as the pivot
    left = [x for x in arr if x < pivot]  # Elements less than pivot
    middle = [x for x in arr if x == pivot]  # Elements equal to pivot
    right = [x for x in arr if x > pivot]  # Elements greater than pivot
    return quick_sort(left) + middle + quick_sort(right)  # Recursively sort the subarrays

# Example usage
arr = [38, 27, 43, 3, 9, 82, 10]
print("Sorted array:", quick_sort(arr))
```

**Explanation**:
- The pivot element is chosen, and the array is divided into three subarrays: one with elements less than the pivot, one with elements equal to the pivot, and one with elements greater than the pivot.
- Each subarray is sorted recursively.

---
# 7. Searching Algorithms – Linear and Binary Search.
---

### **1. Linear Search (Basic)**

```python
# Basic Linear Search Algorithm
def linear_search(arr, target):
    for index, value in enumerate(arr):
        if value == target:
            return index
    return -1  # Element not found

# Example usage
arr = [10, 20, 30, 40, 50]
target = 30
result = linear_search(arr, target)
print(f"Element {target} found at index {result}" if result != -1 else f"Element {target} not found.")
```

---

### **2. Linear Search (With Index Check)**

```python
# Linear Search with index check
def linear_search_with_check(arr, target):
    if not arr:
        return "The list is empty."
    for index, value in enumerate(arr):
        if value == target:
            return index
    return "Element not found."

# Example usage
arr = [12, 23, 34, 45]
target = 23
result = linear_search_with_check(arr, target)
print(result)
```

---

### **3. Linear Search (Recursive)**

```python
# Linear Search using Recursion
def linear_search_recursive(arr, target, index=0):
    if index == len(arr):
        return -1  # Element not found
    if arr[index] == target:
        return index
    return linear_search_recursive(arr, target, index + 1)

# Example usage
arr = [1, 3, 5, 7, 9]
target = 5
result = linear_search_recursive(arr, target)
print(f"Element {target} found at index {result}" if result != -1 else f"Element {target} not found.")
```

---

### **4. Binary Search (Recursive)**

```python
# Binary Search using Recursion
def binary_search_recursive(arr, target, left=0, right=None):
    if right is None:
        right = len(arr) - 1
    if left > right:
        return -1  # Element not found
    mid = (left + right) // 2
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search_recursive(arr, target, mid + 1, right)
    else:
        return binary_search_recursive(arr, target, left, mid - 1)

# Example usage
arr = [2, 4, 6, 8, 10, 12]
target = 8
result = binary_search_recursive(arr, target)
print(f"Element {target} found at index {result}" if result != -1 else f"Element {target} not found.")
```

---

### **5. Binary Search (Iterative)**

```python
# Iterative Binary Search
def binary_search_iterative(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1  # Element not found

# Example usage
arr = [1, 4, 7, 9, 13, 15]
target = 9
result = binary_search_iterative(arr, target)
print(f"Element {target} found at index {result}" if result != -1 else f"Element {target} not found.")
```

---

### **6. Binary Search (Finding Lower Bound)**

```python
# Binary Search to find the lower bound (first occurrence)
def lower_bound(arr, target):
    left, right = 0, len(arr) - 1
    result = -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] >= target:
            result = mid
            right = mid - 1
        else:
            left = mid + 1
    return result

# Example usage
arr = [1, 2, 4, 4, 5, 6]
target = 4
result = lower_bound(arr, target)
print(f"Lower bound of {target} is at index {result}" if result != -1 else f"Element {target} not found.")
```

---

### **7. Binary Search (Finding Upper Bound)**

```python
# Binary Search to find the upper bound (first element greater than target)
def upper_bound(arr, target):
    left, right = 0, len(arr) - 1
    result = -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] > target:
            result = mid
            right = mid - 1
        else:
            left = mid + 1
    return result

# Example usage
arr = [1, 2, 4, 4, 5, 6]
target = 4
result = upper_bound(arr, target)
print(f"Upper bound of {target} is at index {result}" if result != -1 else f"Element {target} not found.")
```

---

### **8. Exponential Search**

**Exponential Search** is used to find an element in a sorted array by checking progressively larger indices exponentially, and then applying binary search on the found range.

```python
# Exponential Search Algorithm
def exponential_search(arr, target):
    if arr[0] == target:
        return 0
    index = 1
    while index < len(arr) and arr[index] <= target:
        index *= 2
    return binary_search_iterative(arr, target, index // 2, min(index, len(arr) - 1))

# Example usage
arr = [1, 2, 4, 10, 12, 19, 21, 25, 29]
target = 10
result = exponential_search(arr, target)
print(f"Element {target} found at index {result}" if result != -1 else f"Element {target} not found.")
```

**Explanation of Exponential Search**:
1. First, check if the target is at the first position.
2. Then, exponentially increase the search range (1, 2, 4, 8, 16...).
3. Once the target is likely within a range, apply **Binary Search** to that range.

---

### **Summary of All Search Programs**:

1. **Linear Search (Basic)**: A straightforward search through the list.
2. **Linear Search (With Index Check)**: Checks for an empty list before searching.
3. **Linear Search (Recursive)**: A recursive version of the basic linear search.
4. **Binary Search (Recursive)**: Recursively divides the list to find the target.
5. **Binary Search (Iterative)**: Non-recursive version of binary search.
6. **Binary Search (Lower Bound)**: Finds the first occurrence of the target or the lower bound.
7. **Binary Search (Upper Bound)**: Finds the first element greater than the target.
8. **Exponential Search**: Searches exponentially and then applies binary search.

---

# 8. Hashing – Hash tables and collision handling.

---

### **1. What is Hashing?**
Hashing is the process of converting an input (often a string or an object) into a fixed-size string of characters, which typically looks like a random number. The value generated is called a **hash code**.

### **2. What is a Hash Table?**
A **hash table** is a data structure that stores data in an associative array-like format, where a **key** maps to a **value**. The hash function is used to convert the key into an index for storing the value in an array.

### **3. Hash Function**
A **hash function** takes a key and converts it into an index in an array. Ideally, the function distributes the keys evenly across the array to minimize **collisions**.

---

### **4. Types of Collision Handling**

1. **Chaining**: When two keys hash to the same index, they are stored in a linked list at that index.
2. **Open Addressing**: When a collision occurs, the algorithm searches for the next available slot within the table using a certain probing technique (linear probing, quadratic probing, etc.).

---

### **Now, let’s go over multiple examples.**

---

### **1. Basic Hash Table Implementation (Without Collision Handling)**

```python
# Basic Hash Table Implementation
class HashTable:
    def __init__(self, size):
        self.size = size
        self.table = [None] * self.size

    def hash_function(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        index = self.hash_function(key)
        self.table[index] = value

    def get(self, key):
        index = self.hash_function(key)
        return self.table[index]

# Example usage
ht = HashTable(10)
ht.insert("apple", 100)
ht.insert("banana", 200)

print("Apple:", ht.get("apple"))    # Output: 100
print("Banana:", ht.get("banana"))  # Output: 200
```

**Explanation**: This is a simple hash table where the `insert` method puts the value at the index computed by the hash function. The `get` method retrieves the value.

---

### **2. Handling Collisions using Chaining**

```python
# Hash Table with Collision Handling using Chaining (Linked List)
class HashTableChaining:
    def __init__(self, size):
        self.size = size
        self.table = [[] for _ in range(size)]  # List of lists for chaining

    def hash_function(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        index = self.hash_function(key)
        # Append to the linked list at the index
        for item in self.table[index]:
            if item[0] == key:
                item[1] = value  # Update value if key already exists
                return
        self.table[index].append([key, value])

    def get(self, key):
        index = self.hash_function(key)
        for item in self.table[index]:
            if item[0] == key:
                return item[1]
        return None  # Return None if key is not found

# Example usage
ht = HashTableChaining(10)
ht.insert("apple", 100)
ht.insert("banana", 200)
ht.insert("orange", 300)

print("Apple:", ht.get("apple"))    # Output: 100
print("Banana:", ht.get("banana"))  # Output: 200
print("Orange:", ht.get("orange"))  # Output: 300
```

**Explanation**: This implementation uses chaining, where each index in the table holds a list (or linked list) of key-value pairs. If a collision occurs, the new key-value pair is appended to the list at that index.

---

### **3. Handling Collisions using Linear Probing (Open Addressing)**

```python
# Hash Table with Collision Handling using Linear Probing
class HashTableLinearProbing:
    def __init__(self, size):
        self.size = size
        self.table = [None] * self.size

    def hash_function(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        index = self.hash_function(key)
        original_index = index

        while self.table[index] is not None:
            if self.table[index][0] == key:  # Key already exists, update the value
                self.table[index] = (key, value)
                return
            index = (index + 1) % self.size
            if index == original_index:
                raise Exception("Hash Table is full")

        self.table[index] = (key, value)

    def get(self, key):
        index = self.hash_function(key)
        original_index = index

        while self.table[index] is not None:
            if self.table[index][0] == key:
                return self.table[index][1]
            index = (index + 1) % self.size
            if index == original_index:
                break  # We've looped back to the original index

        return None  # Key not found

# Example usage
ht = HashTableLinearProbing(10)
ht.insert("apple", 100)
ht.insert("banana", 200)
ht.insert("cherry", 300)

print("Apple:", ht.get("apple"))    # Output: 100
print("Banana:", ht.get("banana"))  # Output: 200
print("Cherry:", ht.get("cherry"))  # Output: 300
```

**Explanation**: **Linear Probing** is an open addressing collision resolution method. When a collision occurs, the algorithm checks the next index until an empty slot is found. The **wrap-around** ensures the index stays within bounds.

---

### **4. Handling Collisions using Quadratic Probing (Open Addressing)**

```python
# Hash Table with Collision Handling using Quadratic Probing
class HashTableQuadraticProbing:
    def __init__(self, size):
        self.size = size
        self.table = [None] * self.size

    def hash_function(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        index = self.hash_function(key)
        i = 0
        while self.table[index] is not None:
            if self.table[index][0] == key:  # Key already exists, update value
                self.table[index] = (key, value)
                return
            i += 1
            index = (index + i * i) % self.size
            if i == self.size:
                raise Exception("Hash Table is full")

        self.table[index] = (key, value)

    def get(self, key):
        index = self.hash_function(key)
        i = 0
        while self.table[index] is not None:
            if self.table[index][0] == key:
                return self.table[index][1]
            i += 1
            index = (index + i * i) % self.size
            if i == self.size:
                break
        return None  # Key not found

# Example usage
ht = HashTableQuadraticProbing(10)
ht.insert("apple", 100)
ht.insert("banana", 200)
ht.insert("grape", 300)

print("Apple:", ht.get("apple"))    # Output: 100
print("Banana:", ht.get("banana"))  # Output: 200
print("Grape:", ht.get("grape"))    # Output: 300
```

**Explanation**: **Quadratic Probing** works similarly to linear probing, but instead of checking sequential positions, it checks with quadratic increments (1, 4, 9, 16…). This helps reduce clustering.

---

### **5. Resizing Hash Table**

When the load factor (the number of elements divided by the size of the table) becomes too high, the hash table should be resized. Here’s an example of resizing.

```python
# Resizing Hash Table with Chaining
class HashTableResizing:
    def __init__(self, size):
        self.size = size
        self.table = [[] for _ in range(size)]

    def hash_function(self, key):
        return hash(key) % self.size

    def insert(self, key, value):
        if self.load_factor() > 0.7:  # Resize if the load factor exceeds 0.7
            self.resize()
        
        index = self.hash_function(key)
        for item in self.table[index]:
            if item[0] == key:
                item[1] = value
                return
        self.table[index].append([key, value])

    def get(self, key):
        index = self.hash_function(key)
        for item in self.table[index]:
            if item[0] == key:
                return item[1]
        return None

    def load_factor(self):
        return sum(len(bucket) for bucket in self.table) / self.size

    def resize(self):
        new_size = self.size * 2
        new_table = [[] for _ in range(new_size)]
        
        for bucket in self.table:
            for key, value in bucket:
                index = hash(key) % new_size
                new_table[index].append([key, value])
        
        self.size = new_size
        self.table =

 new_table

# Example usage
ht = HashTableResizing(4)
ht.insert("apple", 100)
ht.insert("banana", 200)
ht.insert("grape", 300)
ht.insert("orange", 400)

print("Apple:", ht.get("apple"))    # Output: 100
print("Banana:", ht.get("banana"))  # Output: 200
print("Grape:", ht.get("grape"))    # Output: 300
```

**Explanation**: This implementation resizes the hash table by doubling its size when the load factor exceeds 0.7. The table is then rehashed to distribute the existing keys into the new table.

---

# 9. Trees – Binary Trees and Binary Search Trees (BST).

---
### **1. What is a Tree?**
A **tree** is a hierarchical data structure consisting of nodes connected by edges. The top node is called the **root**, and the nodes without children are called **leaves**.

### **2. Binary Tree**
A **binary tree** is a type of tree where each node has at most two children: a **left child** and a **right child**. The tree can be empty, with just a root node, or it can grow to a large size.

### **3. Binary Search Tree (BST)**
A **Binary Search Tree (BST)** is a special kind of binary tree where the left child of a node contains values less than the node, and the right child contains values greater than the node. This property makes searching and sorting efficient.

---

### **Now, let's implement and explain different aspects of Binary Trees and BSTs.**

---

### **1. Basic Binary Tree Structure**

```python
# Binary Tree Node
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.value = key

# Basic Binary Tree Implementation
class BinaryTree:
    def __init__(self):
        self.root = None

    def insert(self, key):
        if not self.root:
            self.root = Node(key)
        else:
            self._insert(self.root, key)

    def _insert(self, node, key):
        if key < node.value:
            if node.left is None:
                node.left = Node(key)
            else:
                self._insert(node.left, key)
        else:
            if node.right is None:
                node.right = Node(key)
            else:
                self._insert(node.right, key)

    def inorder(self, node):
        if node:
            self.inorder(node.left)
            print(node.value, end=" ")
            self.inorder(node.right)

# Example usage
bt = BinaryTree()
bt.insert(10)
bt.insert(20)
bt.insert(5)
bt.insert(15)
bt.insert(30)

print("In-order traversal of Binary Tree:")
bt.inorder(bt.root)  # Output: 5 10 15 20 30
```

**Explanation**: This is a basic binary tree where nodes are inserted in such a way that each node has at most two children. The `inorder` traversal prints the nodes in sorted order.

---

### **2. Binary Search Tree (BST) Implementation**

```python
# Binary Search Tree Node
class BSTNode:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.value = key

# Binary Search Tree Implementation
class BinarySearchTree:
    def __init__(self):
        self.root = None

    def insert(self, key):
        if not self.root:
            self.root = BSTNode(key)
        else:
            self._insert(self.root, key)

    def _insert(self, node, key):
        if key < node.value:
            if node.left is None:
                node.left = BSTNode(key)
            else:
                self._insert(node.left, key)
        else:
            if node.right is None:
                node.right = BSTNode(key)
            else:
                self._insert(node.right, key)

    def inorder(self, node):
        if node:
            self.inorder(node.left)
            print(node.value, end=" ")
            self.inorder(node.right)

    def search(self, key):
        return self._search(self.root, key)

    def _search(self, node, key):
        if node is None or node.value == key:
            return node
        if key < node.value:
            return self._search(node.left, key)
        return self._search(node.right, key)

# Example usage
bst = BinarySearchTree()
bst.insert(10)
bst.insert(20)
bst.insert(5)
bst.insert(15)
bst.insert(30)

print("In-order traversal of BST:")
bst.inorder(bst.root)  # Output: 5 10 15 20 30

# Searching for a key in the BST
search_result = bst.search(15)
print("\nSearching for 15:", "Found" if search_result else "Not Found")
```

**Explanation**: The **Binary Search Tree (BST)** follows the rule where left nodes are less than the parent node and right nodes are greater. We also added a `search` method to find a key in the BST.

---

### **3. Deleting a Node in Binary Search Tree (BST)**

```python
# Delete node in BST
class BSTDeleteNode:
    def __init__(self):
        self.root = None

    def insert(self, key):
        if not self.root:
            self.root = BSTNode(key)
        else:
            self._insert(self.root, key)

    def _insert(self, node, key):
        if key < node.value:
            if node.left is None:
                node.left = BSTNode(key)
            else:
                self._insert(node.left, key)
        else:
            if node.right is None:
                node.right = BSTNode(key)
            else:
                self._insert(node.right, key)

    def inorder(self, node):
        if node:
            self.inorder(node.left)
            print(node.value, end=" ")
            self.inorder(node.right)

    def delete(self, root, key):
        if root is None:
            return root

        if key < root.value:
            root.left = self.delete(root.left, key)
        elif key > root.value:
            root.right = self.delete(root.right, key)
        else:
            # Node with only one child or no child
            if root.left is None:
                return root.right
            elif root.right is None:
                return root.left

            # Node with two children: Get the inorder successor (smallest in the right subtree)
            root.value = self.min_value_node(root.right).value
            root.right = self.delete(root.right, root.value)

        return root

    def min_value_node(self, node):
        current = node
        while current.left:
            current = current.left
        return current

# Example usage
bst = BSTDeleteNode()
bst.insert(10)
bst.insert(20)
bst.insert(5)
bst.insert(15)
bst.insert(30)

print("In-order traversal before deletion:")
bst.inorder(bst.root)  # Output: 5 10 15 20 30
bst.root = bst.delete(bst.root, 20)  # Deleting node 20
print("\nIn-order traversal after deletion of 20:")
bst.inorder(bst.root)  # Output: 5 10 15 30
```

**Explanation**: Deleting a node in a BST involves three cases:
1. **No children**: Simply remove the node.
2. **One child**: Replace the node with its child.
3. **Two children**: Find the **inorder successor** (the smallest node in the right subtree) and replace the node with it.

---

### **4. Finding Maximum and Minimum Values in BST**

```python
# Finding Min and Max values in BST
class BSTMinMax:
    def __init__(self):
        self.root = None

    def insert(self, key):
        if not self.root:
            self.root = BSTNode(key)
        else:
            self._insert(self.root, key)

    def _insert(self, node, key):
        if key < node.value:
            if node.left is None:
                node.left = BSTNode(key)
            else:
                self._insert(node.left, key)
        else:
            if node.right is None:
                node.right = BSTNode(key)
            else:
                self._insert(node.right, key)

    def min_value(self):
        return self._min_value(self.root)

    def _min_value(self, node):
        current = node
        while current.left:
            current = current.left
        return current.value

    def max_value(self):
        return self._max_value(self.root)

    def _max_value(self, node):
        current = node
        while current.right:
            current = current.right
        return current.value

# Example usage
bst = BSTMinMax()
bst.insert(10)
bst.insert(20)
bst.insert(5)
bst.insert(15)
bst.insert(30)

print("Minimum value in BST:", bst.min_value())  # Output: 5
print("Maximum value in BST:", bst.max_value())  # Output: 30
```

**Explanation**: In a BST, the **minimum value** is found by traversing the leftmost child, and the **maximum value** is found by traversing the rightmost child.

---

### **5. Depth of a Binary Tree**

```python
# Finding the Depth of a Binary Tree
class TreeDepth:
    def __init__(self):
        self.root = None

    def insert(self, key):
        if not self.root:
            self.root = Node(key)
        else:
            self._insert(self.root, key)

    def _insert(self, node, key):
        if key < node.value:
            if node.left is None:
                node.left = Node(key)
            else:
                self._insert(node.left, key)
        else:
            if node.right is None:
                node.right = Node(key)
            else:
                self._insert(node.right, key)

    def depth(self, node):
        if node is None:
            return 0
        left_depth = self.depth(node.left)
        right_depth = self

.depth(node.right)
        return max(left_depth, right_depth) + 1

# Example usage
bt = TreeDepth()
bt.insert(10)
bt.insert(20)
bt.insert(5)
bt.insert(15)
bt.insert(30)

print("Depth of the Binary Tree:", bt.depth(bt.root))  # Output: 3
```

**Explanation**: The **depth** of a tree is the longest path from the root node to a leaf. The depth is calculated recursively by comparing the left and right subtree depths.

---
# 10. Graphs – Basics, DFS, BFS.
---

### **1. What is a Graph?**
A **graph** is a collection of **nodes (vertices)** and **edges (connections)** between those nodes. A graph can represent various real-world systems, such as social networks, computer networks, or transportation systems.

- **Vertices**: The entities in the graph (e.g., people, cities, etc.).
- **Edges**: The connections between vertices (e.g., relationships between people, roads between cities).

Graphs can be:
- **Directed**: Edges have a direction (e.g., one-way streets).
- **Undirected**: Edges have no direction (e.g., two-way streets).
- **Weighted**: Each edge has a weight (e.g., distance, cost).
- **Unweighted**: All edges have the same weight.

---

### **2. Graph Representation**

Graphs can be represented in two common ways:

- **Adjacency Matrix**: A 2D matrix where `matrix[i][j] = 1` if there's an edge between node `i` and node `j`, and `0` otherwise.
- **Adjacency List**: A list where each node has a list of adjacent nodes (i.e., the nodes it's directly connected to).

We'll implement both methods.

---

### **3. Graph Representation using Adjacency List**

```python
# Graph Representation using Adjacency List (Undirected Graph)
class Graph:
    def __init__(self):
        self.graph = {}

    def add_edge(self, u, v):
        # Add edge from u to v and v to u (undirected graph)
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []
        self.graph[u].append(v)
        self.graph[v].append(u)

    def display(self):
        for vertex in self.graph:
            print(f"{vertex}: {self.graph[vertex]}")

# Example usage
g = Graph()
g.add_edge(1, 2)
g.add_edge(1, 3)
g.add_edge(2, 4)
g.add_edge(3, 4)

print("Graph representation using adjacency list:")
g.display()
```

**Explanation**: This implementation of an undirected graph uses an adjacency list. The `add_edge()` method adds edges between two vertices.

---

### **4. Depth-First Search (DFS)**
**DFS** explores as far as possible along each branch before backtracking. It's implemented using recursion or a stack.

#### **DFS using Recursion**
```python
# Depth-First Search (DFS) Implementation
class GraphDFS:
    def __init__(self):
        self.graph = {}

    def add_edge(self, u, v):
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []
        self.graph[u].append(v)
        self.graph[v].append(u)

    def dfs(self, start):
        visited = set()  # To keep track of visited nodes
        self._dfs_recursive(start, visited)

    def _dfs_recursive(self, node, visited):
        if node not in visited:
            print(node, end=" ")
            visited.add(node)
            for neighbor in self.graph[node]:
                self._dfs_recursive(neighbor, visited)

# Example usage
g_dfs = GraphDFS()
g_dfs.add_edge(1, 2)
g_dfs.add_edge(1, 3)
g_dfs.add_edge(2, 4)
g_dfs.add_edge(3, 4)

print("DFS traversal starting from node 1:")
g_dfs.dfs(1)  # Output: 1 2 4 3
```

**Explanation**: In DFS, we start from a node and explore each branch before backtracking. The recursive function `dfs_recursive` helps traverse the graph.

#### **DFS using Stack**
```python
# DFS using Stack
class GraphDFSStack:
    def __init__(self):
        self.graph = {}

    def add_edge(self, u, v):
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []
        self.graph[u].append(v)
        self.graph[v].append(u)

    def dfs(self, start):
        visited = set()
        stack = [start]
        while stack:
            node = stack.pop()
            if node not in visited:
                print(node, end=" ")
                visited.add(node)
                for neighbor in self.graph[node]:
                    if neighbor not in visited:
                        stack.append(neighbor)

# Example usage
g_dfs_stack = GraphDFSStack()
g_dfs_stack.add_edge(1, 2)
g_dfs_stack.add_edge(1, 3)
g_dfs_stack.add_edge(2, 4)
g_dfs_stack.add_edge(3, 4)

print("\nDFS traversal using stack starting from node 1:")
g_dfs_stack.dfs(1)  # Output: 1 3 4 2
```

**Explanation**: This non-recursive version of DFS uses a stack. The stack helps backtrack and explore deeper nodes.

---

### **5. Breadth-First Search (BFS)**
**BFS** explores all neighbors of a node before moving to the next level. It's implemented using a queue.

```python
# Breadth-First Search (BFS) Implementation
from collections import deque

class GraphBFS:
    def __init__(self):
        self.graph = {}

    def add_edge(self, u, v):
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []
        self.graph[u].append(v)
        self.graph[v].append(u)

    def bfs(self, start):
        visited = set()
        queue = deque([start])
        visited.add(start)
        
        while queue:
            node = queue.popleft()
            print(node, end=" ")
            for neighbor in self.graph[node]:
                if neighbor not in visited:
                    visited.add(neighbor)
                    queue.append(neighbor)

# Example usage
g_bfs = GraphBFS()
g_bfs.add_edge(1, 2)
g_bfs.add_edge(1, 3)
g_bfs.add_edge(2, 4)
g_bfs.add_edge(3, 4)

print("BFS traversal starting from node 1:")
g_bfs.bfs(1)  # Output: 1 2 3 4
```

**Explanation**: BFS starts at a given node, explores all neighbors, and proceeds to explore neighbors' neighbors level by level. It uses a **queue** to manage the nodes yet to be visited.

---

### **6. Directed Graphs**

In directed graphs, edges have a direction. We can use the same BFS and DFS algorithms for directed graphs, but the edges are one-way only.

```python
# Directed Graph using Adjacency List
class DirectedGraph:
    def __init__(self):
        self.graph = {}

    def add_edge(self, u, v):
        if u not in self.graph:
            self.graph[u] = []
        self.graph[u].append(v)  # One-way edge from u to v

    def display(self):
        for vertex in self.graph:
            print(f"{vertex} -> {self.graph[vertex]}")

# Example usage
g_directed = DirectedGraph()
g_directed.add_edge(1, 2)
g_directed.add_edge(1, 3)
g_directed.add_edge(2, 4)

print("Directed Graph representation:")
g_directed.display()
```

**Explanation**: In a **directed graph**, edges point in one direction. The adjacency list represents these edges as one-way connections.

---
