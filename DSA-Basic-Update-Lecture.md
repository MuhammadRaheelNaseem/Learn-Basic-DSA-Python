### **1. Introduction to DSA – Basic Concepts, Importance, and Python’s Role**

#### **Real-World Example: "Online Shopping Cart"**
- **Explanation**: Data Structures and Algorithms (DSA) are the building blocks of efficient software. Imagine an online shopping cart where you need to manage products, perform operations like adding/removing products, and sorting items. These operations need efficient algorithms and data structures to run effectively.

#### **Python Code Examples**:
1. **Basic Product List (Array)**
   - *Storing product names in a list and accessing them*.
   
```python
# List of products in the cart
products = ["Laptop", "Phone", "Headphones", "Smartwatch"]

# Accessing the first product
print("First product:", products[0])
```

2. **Adding Products to Cart**
   - *Adding products dynamically*.
   
```python
# Adding new products
products.append("Keyboard")
print("Updated product list:", products)
```

3. **Removing Products from Cart**
   - *Removing a product by its name*.
   
```python
# Removing a product by name
products.remove("Phone")
print("Updated product list:", products)
```

4. **Sorting Products in Cart**
   - *Sorting products alphabetically*.
   
```python
# Sorting products alphabetically
products.sort()
print("Sorted product list:", products)
```

5. **Searching for a Product in Cart**
   - *Searching for a specific product*.
   
```python
# Searching for a product
def search_product(cart, product):
    if product in cart:
        return f"{product} found in the cart!"
    else:
        return f"{product} not found in the cart."

print(search_product(products, "Smartwatch"))
```

---

### **2. Arrays & Lists – Basic Operations, Searching, and Sorting**

#### **Real-World Example: "Playlist Management"**
- **Explanation**: Arrays and Lists are useful for organizing collections of similar items. For instance, managing a playlist involves adding/removing songs, and sorting them.

#### **Python Code Examples**:
1. **Creating and Accessing a List (Playlist)**
   - *Creating a playlist and accessing songs*.
   
```python
# Initial playlist
playlist = ["Song1", "Song2", "Song3"]

# Accessing the first song
print("First song in playlist:", playlist[0])
```

2. **Adding Songs to Playlist**
   - *Adding songs dynamically*.
   
```python
# Adding songs to the playlist
playlist.append("Song4")
playlist.insert(1, "Song5")  # Inserting at a specific position
print("Updated playlist:", playlist)
```

3. **Removing Songs from Playlist**
   - *Removing a song*.
   
```python
# Removing a song from the playlist
playlist.remove("Song2")
print("Updated playlist:", playlist)
```

4. **Sorting Playlist**
   - *Sorting songs alphabetically*.
   
```python
# Sorting the playlist alphabetically
playlist.sort()
print("Sorted playlist:", playlist)
```

5. **Searching for a Song**
   - *Searching for a song in the playlist*.
   
```python
# Searching for a song in the playlist
def search_song(playlist, song):
    if song in playlist:
        return f"{song} is in the playlist."
    return f"{song} is not in the playlist."

print(search_song(playlist, "Song1"))
```

---

### **3. Stacks & Queues – Implementation and Applications**

#### **Real-World Example: "Undo/Redo in Text Editor" (Stack)**
- **Explanation**: A Stack is a data structure that follows Last-In-First-Out (LIFO) order. It's great for undo/redo operations where the most recent action is undone first.

#### **Python Code Examples**:
1. **Creating a Stack and Pushing Items**
   - *A stack that holds text actions*.
   
```python
# Stack for text actions
stack = []

# Pushing actions to stack (like typing text)
stack.append("Typed 'Hello'")
stack.append("Typed 'World'")
print("Stack:", stack)
```

2. **Popping from the Stack (Undo)**
   - *Undoing the last action*.
   
```python
# Undo last action (pop the stack)
last_action = stack.pop()
print("Undone action:", last_action)
print("Stack after undo:", stack)
```

3. **Peeking at the Top Item in the Stack**
   - *View the top of the stack without removing it*.
   
```python
# Peeking at the top item without popping it
if stack:
    print("Top item in stack:", stack[-1])
```

4. **Checking if the Stack is Empty**
   - *Check if there are any actions to undo*.
   
```python
# Check if stack is empty
if not stack:
    print("No actions to undo.")
```

5. **Simulating Undo Operations**
   - *Simulate multiple undos in a text editor*.
   
```python
# Simulating undo for multiple actions
actions = ["Typed 'Hello'", "Typed 'World'", "Deleted 'World'"]
stack = actions.copy()
while stack:
    print("Undo:", stack.pop())
```

---

#### **Real-World Example: "Queue in a Call Center" (Queue)**
- **Explanation**: A Queue is used in scenarios like a call center, where customers are served in the order they arrive (FIFO).

#### **Python Code Examples**:
1. **Creating a Queue and Enqueuing Items**
   - *A simple queue for handling customers*.
   
```python
# Queue to manage incoming calls
queue = []

# Adding calls to the queue
queue.append("Call 1")
queue.append("Call 2")
print("Queue:", queue)
```

2. **Dequeuing Items (Serving Customers)**
   - *Serving the first customer*.
   
```python
# Serving the first call in the queue
call_served = queue.pop(0)  # Removing from the front of the queue
print("Served call:", call_served)
print("Queue after serving:", queue)
```

3. **Checking the Front of the Queue**
   - *Peek at the front customer without removing*.
   
```python
# Peek at the front call without serving it
if queue:
    print("Front of the queue:", queue[0])
```

4. **Queue Size (Number of Pending Calls)**
   - *Check how many calls are left in the queue*.
   
```python
# Checking the number of calls in the queue
print("Calls remaining in queue:", len(queue))
```

5. **Simulating Queue System**
   - *Simulating a queue system in a call center*.
   
```python
# Simulating the queue for a set of customers
calls = ["Call 1", "Call 2", "Call 3"]
queue = calls.copy()
while queue:
    print("Serving:", queue.pop(0))
```

---

### **4. Linked Lists – Types and Operations**

#### **Real-World Example: "Music Playlist" (Linked List)**
- **Explanation**: A Linked List is a linear collection of elements, where each element points to the next one. It’s like a playlist where each song (node) is connected to the next.

#### **Python Code Examples**:
1. **Creating a Singly Linked List**
   - *A simple linked list of songs*.
   
```python
class Node:
    def __init__(self, song):
        self.song = song
        self.next = None

class Playlist:
    def __init__(self):
        self.head = None

    def add_song(self, song):
        new_node = Node(song)
        new_node.next = self.head
        self.head = new_node

    def view_playlist(self):
        current = self.head
        while current:
            print(current.song, end=" -> ")
            current = current.next

# Create and view playlist
playlist = Playlist()
playlist.add_song("Song1")
playlist.add_song("Song2")
playlist.add_song("Song3")
print("Playlist:")
playlist.view_playlist()
```

2. **Inserting a Song in the Playlist (At Beginning)**
   - *Add a song to the beginning of the playlist*.
   
```python
# Inserting a song at the beginning
playlist.add_song("Song4")
print("\nPlaylist after adding Song4 at the beginning:")
playlist.view_playlist()
```

3. **Removing a Song from the Playlist**
   - *Removing a song from the list*.
   
```python
# Removing a song (manual process for simplicity)
def remove_song(playlist, song):
    current = playlist.head
    prev = None
    while current:
        if current.song == song:
            if prev:
                prev.next = current.next
            else:
                playlist.head = current.next
            print(f"Removed {song}")
            return
        prev = current
        current = current.next

# Removing "Song2"
remove_song(playlist, "Song2")
playlist.view_playlist()
```

4. **Reversing the Playlist (Linked List)**
   - *Reversing the order of songs*.
   
```python
def reverse_playlist(playlist):
    prev = None
    current = playlist.head
    while current:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node
    playlist.head = prev

reverse_playlist(playlist)
print("\nReversed Playlist:")
playlist.view_playlist()
```

5. **Searching for a Song in Playlist**
   - *Searching for a song in the playlist*.
   
```python
# Searching for a song in the playlist
def search_song(playlist, song):
    current = playlist.head
    while current:
        if current.song == song:
            return f"{song} is in the playlist."
        current = current.next
    return f"{song} is not in the playlist."

print(search_song(playlist, "Song3"))
```

---

### **5. Recursion – Concept and Examples**

#### **Real-World Example: "Factorial Calculation"**
- **Explanation**: Recursion is a way to solve a problem by breaking it down into smaller instances of the same problem. A classic example is calculating the factorial of a number.

#### **Python Code Examples**:
1. **Calculating Factorial Using Recursion**
   - *Using recursion to compute the factorial of a number*.
   
```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)

print("Factorial of 5:", factorial(5))  # Output: 120
```

2. **Fibonacci Sequence Using Recursion**
   - *Finding Fibonacci numbers using recursion*.
   
```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

print("Fibonacci of 6:", fibonacci(6))  # Output: 8
```

3. **Sum of Natural Numbers Using Recursion**
   - *Calculating the sum of the first N natural numbers*.
   
```python
def sum_of_natural_numbers(n):
    if n == 1:
        return 1
    return n + sum_of_natural_numbers(n - 1)

print("Sum of first 5 natural numbers:", sum_of_natural_numbers(5))  # Output: 15
```

4. **Reversing a String Using Recursion**
   - *Reverse a string by calling the function on smaller substrings*.
   
```python
def reverse_string(s):
    if len(s) == 0:
        return s
    return reverse_string(s[1:]) + s[0]

print("Reversed string:", reverse_string("hello"))  # Output: "olleh"
```

5. **Binary Search Using Recursion**
   - *Implementing binary search using recursion*.
   
```python
def binary_search(arr, target, left, right):
    if left > right:
        return -1
    mid = (left + right) // 2
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search(arr, target, mid + 1, right)
    else:
        return binary_search(arr, target, left, mid - 1)

arr = [1, 2, 3, 4, 5, 6]
print("Element found at index:", binary_search(arr, 4, 0, len(arr) - 1))  # Output: 3
```

---
