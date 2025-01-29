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

# **3. Stacks & Queues** – Implementation and applications.
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
