---
DSA Python Topics
---
1. Introduction to Data Structures & Algorithms.
2. Basics of Algorithms, Distinct areas in the algorithms, Algorithms& Data Structures,
3. Qualitative and Quantitative Aspects of Algorithms, Algorithms features and Pseudo code.
4. Array operations, Array representation, Array insertion and deletion.
5. Introduction to Linked list Operations of Linked List, Types of Linked List, Insertion, Updation and Deletion in Single Linked List. Traversing and Searching in Single Linked List.
6. Introduction to Double Linked list, Operations Double Linked List, Updation and Deletion in Double Linked List. Traversing and Searching, Forward and Backward Display.
7. Introduction to Circular Linked list, Operations Double Linked List, Updation and Deletion in Circular Linked List. Traversing and Searching, Forward and Backward Display.
8. Introduction to Stack, Basic Operation of Stack, Implementation of Stack through Array, Implementation of Stack through Linked List.
9. Application of Stack, Infix, Prefix and Post Fix.
10. Introduction to Queue. Applications and examples of Queue.
11. Tree, Types of Trees, BST Traversing of BST, Sorting Searching, Insertion and Deletion in BST.
12. Heap Tree, Min, Max, Insertion and Deletion. Insertion and Deletion in Mix Max Heap.
13. AVL Tree. Balance factor and Insertion in AVL Tree.
14. Graph, Dijkstra Algorithm
15. Sorting and Searching Algorithm, Algorithm Analysis
16. Hashing and Time Complexity
---
---


# **Topic 5 (Linked List)**

### **Scenario: "Treasure Hunt" or "Train"**

Imagine there is a **Train**.

In every train **bogie (compartment)** there are **two things**:

1. **Passenger (Data):** The person sitting in that compartment.
2. **Hook (Pointer/Link):** The connector that links this compartment to the next one.

---

### **Difference Between Array and Linked List**

* **Array:**
  Think of it as a long bench where everyone is sitting side by side.
  If you want to seat someone in the middle, everyone has to shift.

* **Linked List:**
  It’s like train compartments. If you want to add a new compartment in the middle, you just open the hook of one compartment and attach it to the new one. No one needs to shift.

---

### **1. Technical Concept (Nodes)**

In a linked list, every item is called a **Node**.
Each Node has two parts:

1. **Data:** The actual value (e.g., 10, 20, "Ali").
2. **Next:** The address of the next node (Link).

---

### **2. Python Implementation (Step-by-Step)**

I’ll write the code in small pieces so you can explain it step by step.

#### **Step A: Creating a Compartment (Creating a Node)**

First, we need to create a class that represents a "compartment" (Node).

```python
class Node:
    def __init__(self, data):
        self.data = data      # This is the Passenger (Value)
        self.next = None      # This is the Hook (initially not connected to anyone)
```

#### **Step B: Creating the Train (Linked List Class)**

Now we will create a class that manages the whole Linked List (Train).
The main point is the **"Head"** (Engine), where the train starts.

```python
class LinkedList:
    def __init__(self):
        self.head = None  # At the beginning the train is empty (No Engine/Head)
```

---

### **3. Operations (How it works)**

Now we’ll add functions inside this `LinkedList` class.

#### **Operation 1: Insertion (Adding New Data)**

**Scenario:** Adding a new compartment at the end of the train.

```python
    # 1. Insertion at End
    def append(self, data):
        new_node = Node(data)  # Created a new compartment
        
        # If the train is empty, this will be the first compartment (Head)
        if self.head is None:
            self.head = new_node
            return
        
        # If the train is not empty, go to the last compartment
        last_node = self.head
        while last_node.next:  # As long as there is a next compartment, keep moving ahead
            last_node = last_node.next
        
        # Connect the hook of the last compartment to the new one
        last_node.next = new_node
```

#### **Operation 2: Traversing (Displaying the List)**

**Scenario:** The ticket checker starts from the Engine (Head) and goes till the last compartment.

```python
    # 2. Traversing (Display)
    def display(self):
        current = self.head
        while current:
            print(f"{current.data} ->", end=" ")  # Show the data
            current = current.next  # Move to the next compartment
        print("None")  # End of train
```

#### **Operation 3: Searching (Finding Data)**

**Scenario:** Is there a passenger named "Ali" in the train?

```python
    # 3. Searching
    def search(self, target):
        current = self.head
        while current:
            if current.data == target:
                return True  # Found!
            current = current.next
        return False  # Checked the whole train, not found
```

#### **Operation 4: Updation (Changing Data)**

**Scenario:** Changing a passenger’s seat value or updating their information.

```python
    # 4. Updation
    def update(self, old_val, new_val):
        current = self.head
        while current:
            if current.data == old_val:
                current.data = new_val  # Changed the value
                print(f"Updated {old_val} to {new_val}")
                return
            current = current.next
        print("Value not found to update.")
```

#### **Operation 5: Deletion (Deleting Data)**

**Scenario:** Removing a compartment from the middle.
We connect the hook of the previous compartment directly to the next one (skipping the middle one).

```python
    # 5. Deletion
    def delete(self, key):
        current = self.head

        # Case 1: If the Head (Engine) itself has to be deleted
        if current and current.data == key:
            self.head = current.next  # Shift the Head to the next node
            current = None  # Old head removed
            return

        # Case 2: Delete from middle or end
        prev = None
        while current and current.data != key:
            prev = current
            current = current.next

        if current is None:  # Value not found
            return

        # Bypass the node (connect previous to next)
        prev.next = current.next
        current = None
```

---

### **4. Final Full Code for Execution**

You can run this code and show it to students.

```python
# --- Complete Simple Code ---

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    # Add at end
    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        last.next = new_node

    # Print list
    def display(self):
        current = self.head
        while current:
            print(current.data, end=" -> ")
            current = current.next
        print("None")

    # Update value
    def update(self, old_val, new_val):
        current = self.head
        while current:
            if current.data == old_val:
                current.data = new_val
                return
            current = current.next

    # Delete value
    def delete(self, key):
        current = self.head
        # If head is to be deleted
        if current and current.data == key:
            self.head = current.next
            return
        # Find the node to delete
        prev = None
        while current and current.data != key:
            prev = current
            current = current.next
        # If not found
        if not current:
            return
        # Unlink the node
        prev.next = current.next

# --- Testing ---
ll = LinkedList()

print("1. Inserting 10, 20, 30:")
ll.append(10)
ll.append(20)
ll.append(30)
ll.display()  # Output: 10 -> 20 -> 30 -> None

print("\n2. Updating 20 to 25:")
ll.update(20, 25)
ll.display()  # Output: 10 -> 25 -> 30 -> None

print("\n3. Deleting 10 (Head):")
ll.delete(10)
ll.display()  # Output: 25 -> 30 -> None
```

---

### **Summary for Students:**

1. A **Linked List** is a chain of nodes.
2. **Insertion:** Adding a new link (node) into the chain.
3. **Deletion:** Removing a link from the chain and joining the previous and next links together.
4. **Traversal:** Going from the first link (head) to the last one.
5. **Linked List vs Array:**

   * A Linked List can be scattered in memory (not stored together).
   * An Array is stored in one continuous block in memory.


---
## **Topic 6: Doubly Linked List (DLL)**
---

In a **Singly Linked List**, the problem was that we could only move **forward**.
If we accidentally went too far ahead, we couldn’t go back.

A **Doubly Linked List** solves this problem.

---

### **Scenario: "Holding Hands Both Ways"**

Imagine students standing in a line:

* **Singly Linked List:**
  Each student has their hand on the **shoulder of only the next student**.
  They can only see and move **forward**.

* **Doubly Linked List:**
  Each student is holding **two hands**:

  1. One hand of the **previous** student.
  2. One hand of the **next** student.

The benefit? You can move in the line **forward** as well as **backward** using the pointers.

---

### **1. Technical Concept (Node Structure)**

A Doubly Linked List "Node" (box) is a bit heavier because it has 3 things:

1. **Prev:** Address of the previous node.
2. **Data:** The value.
3. **Next:** Address of the next node.

---

### **2. Python Implementation (Step-by-Step)**

#### **Step A: Creating a Node (3-Part Box)**

This time we will also add a `prev` (previous) pointer.

```python
class Node:
    def __init__(self, data):
        self.prev = None  # Link to previous node
        self.data = data  # Actual data
        self.next = None  # Link to next node
```

#### **Step B: Class Setup**

The overall structure is similar to the singly linked list.

```python
class DoublyLinkedList:
    def __init__(self):
        self.head = None
```

---

### **3. Operations (How it works)**

#### **Operation 1: Insertion (Inserting New Data)**

**Scenario:** Add a new person at the end of the line.
They must hold the hand of the previous person.

```python
    # 1. Insertion at End
    def append(self, data):
        new_node = Node(data)
        
        # If the list is empty
        if not self.head:
            self.head = new_node
            return
        
        # Go to the last node
        last = self.head
        while last.next:
            last = last.next
            
        # Linking (Most important step)
        last.next = new_node      # Previous node points to new node
        new_node.prev = last      # New node points back to previous node
```

#### **Operation 2: Traversing (Forward & Backward)**

**Scenario:** First go forward, then from there come back backward.

```python
    # 2. Forward & Backward Display
    def display_forward_backward(self):
        # --- Going Forward ---
        print("Forward: ", end="")
        current = self.head
        last = None  # We will save this to use when coming back
        
        while current:
            print(current.data, end=" <-> ")
            last = current          # Track the last node
            current = current.next
        print("None")
        
        # --- Coming Backward ---
        # Now we are standing at the 'last' node
        print("Backward: ", end="")
        while last:
            print(last.data, end=" <-> ")
            last = last.prev        # Move backward using prev pointer
        print("None")
```

#### **Operation 3: Deletion (Deleting Data)**

**Scenario:** Remove someone from the middle of the line.
We have to change **two connections**.

If we want to delete **B** from: `A <-> B <-> C`

* **A**’s `next` will become **C**.
* **C**’s `prev` will become **A**.

```python
    # 3. Deletion
    def delete(self, key):
        current = self.head
        
        # Case: Empty list
        if not current:
            return

        # Case: Head needs to be deleted
        if current.data == key:
            self.head = current.next
            if self.head:  # If list still has more nodes
                self.head.prev = None
            return

        # Case: Delete from middle or end
        while current and current.data != key:
            current = current.next
            
        if not current:  # Value not found
            return
            
        # Logic:
        # current.prev (Previous) -> current.next (Next)
        if current.next:
            current.next.prev = current.prev
            
        if current.prev:
            current.prev.next = current.next
```

---

### **4. Final Full Code for Execution**

This is the complete code you can run and show to students.
It will first print forward, then backward, then delete and show again.

```python
# --- Complete Doubly Linked List Code ---

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None  # Extra pointer for previous node

class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Insert at end
    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        last = self.head
        while last.next:
            last = last.next
        
        # Connecting both ways
        last.next = new_node
        new_node.prev = last

    # Display Forward and Backward
    def display_full(self):
        print("\nTraversing Forward:")
        current = self.head
        last_node = None
        while current:
            print(f"[{current.data}]", end=" <-> ")
            last_node = current
            current = current.next
        print("None")
        
        print("Traversing Backward (Reverse):")
        while last_node:
            print(f"[{last_node.data}]", end=" <-> ")
            last_node = last_node.prev
        print("None")

    # Update Value
    def update(self, old_val, new_val):
        current = self.head
        while current:
            if current.data == old_val:
                current.data = new_val
                return
            current = current.next

    # Delete Node
    def delete(self, key):
        current = self.head
        
        # Find the node to delete
        while current and current.data != key:
            current = current.next
            
        if not current:
            return  # Not found
        
        # Adjust previous node's next
        if current.prev:
            current.prev.next = current.next
        else:
            # We are deleting the head
            self.head = current.next
            
        # Adjust next node's prev
        if current.next:
            current.next.prev = current.prev
            
        current = None  # Free the node (helps GC)

# --- Testing ---
dll = DoublyLinkedList()

print("1. Inserting 100, 200, 300:")
dll.append(100)
dll.append(200)
dll.append(300)
dll.display_full()

print("\n2. Updating 200 to 250:")
dll.update(200, 250)
dll.display_full()

print("\n3. Deleting 250 (Middle node):")
dll.delete(250)
dll.display_full()
```

---

### **Summary for Students:**

1. **Structure:** Each node has **3 fields** – `prev`, `data`, `next`.
2. **Memory:** It uses a bit more memory than a singly linked list (because of the extra pointer).
3. **Flexibility:** You can move both **forward and backward** through the list.
4. **Complexity:** Code must be written carefully so that both `prev` and `next` are correctly connected.


---
## **Topic 7: Circular Linked List**.
### **Scenario: "Musical Chairs" or "Prayer Beads (Tasbeeh)"**

Imagine a **round table** conference, or kids playing **Musical Chairs**.

* **Linear List (Normal Linked List):**
  It’s like a straight line. There is a **Start** and an **End**.
  After the end, there is nothing (a cliff / `None`).

* **Circular List (Round):**
  This is a **circle**.

  * The **last person** is holding the hand of the **first person**.
  * There is never a point where you reach `"The End" (None)`.
    If you keep going, you eventually come back to the start.

**Real-life examples:**

* **Music Playlist (Repeat Mode):**
  When the last song finishes, the **first song** starts again automatically.
* **Tasbeeh (prayer beads):**
  After the last bead, you are back at the **first bead**.

---

### **1. Technical Concept (The Loop)**

In a normal **Singly Linked List**, the `next` of the last node is **`None`**.

In a **Circular Linked List**, the `next` of the last node points back to the **head (first node)**.

So the nodes form a loop.

---

### **2. Python Implementation (Step-by-Step)**

We’ll build a **Singly Circular Linked List**, because that’s the easiest to understand.

#### **Step A: Node (Same as Singly Linked List)**

The node (box) is the same as before:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

#### **Step B: Operations (The Tricky Part)**

The tricky part is in the **looping**, because if we’re not careful, we can end up in an **infinite loop** (never-ending traversal).

---

### **Operation 1: Insertion (Creating / Growing the Circle)**

**Scenario:**
We want to add a new person into the circle.
We have to go to the **last person** and say:

> “Your hand should now hold this new person, and the new person will hold the hand of the head (first person).”

```python
    # 1. Append (Add at the end)
    def append(self, data):
        new_node = Node(data)
        
        # If the list is empty
        if not self.head:
            self.head = new_node
            self.head.next = self.head  # Points to itself (self-loop)
            return
        
        # Find the last node
        current = self.head
        while current.next != self.head:  # Stop when we come back to head
            current = current.next
            
        # Linking
        current.next = new_node      # Last node now points to new node
        new_node.next = self.head    # New node points back to head (circle complete)
```

---

### **Operation 2: Traversing (Walking Around the Circle)**

**Scenario:**
We want to print all the elements, but we must remember to **stop when we come back to head**, otherwise the code will run forever.

```python
    # 2. Display (Traversing)
    def display(self):
        if not self.head:
            print("List is empty")
            return
            
        current = self.head
        while True:
            print(f"{current.data} ->", end=" ")
            current = current.next
            # Break condition: stop when we come back to head
            if current == self.head:
                break
        print("(Back to Head)")
```

---

### **Operation 3: Deletion (Removing from the Circle)**

**Scenario:**
We want to remove a person from the circle and still keep the circle connected.

If we want to delete the **head**, we must also update the **last node’s link**, so that it points to the **new head**. That part is a bit tricky.

```python
    # 3. Deletion
    def delete(self, key):
        if not self.head:
            return

        current = self.head
        prev = None

        # Loop to find the node to delete
        while True:
            if current.data == key:
                # Found the node to delete

                # Case 1: Only one node in the list
                if current.next == self.head and current == self.head:
                    self.head = None
                    return
                
                # Case 2: Delete the head node
                if current == self.head:
                    # Find the last node to update its link
                    last = self.head
                    while last.next != self.head:
                        last = last.next
                    
                    self.head = current.next    # Move head forward
                    last.next = self.head       # Last node points to new head
                
                # Case 3: Delete from middle or end
                else:
                    prev.next = current.next    # Skip the current node
                
                return  # Deletion done, exit the function
            
            # Move forward
            prev = current
            current = current.next
            
            # If we came back to head and didn't find the key
            if current == self.head:
                break
```

---

### **3. Final Full Code for Execution**

This code is great for showing students how an **"infinite loop"** can happen if we don’t use a proper stopping condition.

```python
# --- Complete Circular Linked List Code ---

class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class CircularLinkedList:
    def __init__(self):
        self.head = None

    # Insert at end
    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            self.head.next = self.head  # Point to itself
            return
        
        current = self.head
        while current.next != self.head:
            current = current.next
        
        current.next = new_node
        new_node.next = self.head  # Close the loop

    # Display all elements
    def display(self):
        if not self.head:
            return
        current = self.head
        print("Circle: ", end="")
        while True:
            print(f"[{current.data}]", end=" -> ")
            current = current.next
            if current == self.head:
                break
        print("(Repeats Head)")

    # Delete a node
    def delete(self, key):
        if not self.head:
            return
        
        current = self.head
        prev = None
        
        while True:
            if current.data == key:
                # Case 1: Only one node in the list
                if current.next == self.head and current == self.head:
                    self.head = None
                    return
                
                # Case 2: Deleting the head node
                if current == self.head:
                    last = self.head
                    while last.next != self.head:
                        last = last.next
                    self.head = current.next
                    last.next = self.head
                
                # Case 3: Deleting a middle or last node
                else:
                    prev.next = current.next
                return
            
            prev = current
            current = current.next
            if current == self.head:
                break

# --- Testing ---
cll = CircularLinkedList()

print("1. Creating Circle 10, 20, 30:")
cll.append(10)
cll.append(20)
cll.append(30)
cll.display()
# Output: [10] -> [20] -> [30] -> (Repeats Head)

print("\n2. Deleting 10 (Head):")
# Note: 30's link should now point to 20 (the new head)
cll.delete(10)
cll.display()
# Output: [20] -> [30] -> (Repeats Head)
```

---

### **Summary for Students:**

1. **Identity:** A circular linked list has **no real end** (`None`). It loops back to the **head**.
2. **Usage:** Useful in situations where things need to **repeat** (e.g., round-robin scheduling, music players in repeat mode).
3. **Caution:** While looping, you **must** have a stopping condition like `if current == head: break`,
   otherwise the program will never stop (infinite loop / hang).


---
## **Topic 8: Stack** 
**Topic 8: Stack** is one of the easiest and most important topics in DSA. Its concept is very clear and straight-forward.

### **Scenario: "Wedding Plates" or "Pile of Books"**

Imagine at a wedding buffet there is a **pile of plates** stacked on top of each other.

1. When the waiter brings a newly washed plate, he puts it on **top** of the pile.
2. When a guest comes to eat, they always pick the plate from the **top**.

This concept is called **LIFO** – *Last In, First Out*.

* **Last In:** The plate that came last (the top plate).
* **First Out:** That same plate is taken out first.

---

### **1. Basic Operations of a Stack**

In a stack, we never remove things from the middle.
All operations happen on the **Top** only.

1. **Push:** Put a new item on top (Insert).
2. **Pop:** Remove the top item (Delete).
3. **Peek (or Top):** Just look at what is on the top (without deleting it).
4. **IsEmpty:** Check if the stack is empty or not.

---

### **2. Implementation: Stack using Array (Python List)**

In Python, a `list` (`[]`) behaves like an array, and it is perfect for implementing a stack because it already has `append()` and `pop()` functions.

**Code Logic:**

* The **last element of the list** will be the **Top** of the stack.

```python
# --- 1. Stack using Array (Python List) ---

class StackArray:
    def __init__(self):
        self.stack = []  # Empty list (Array)

    # 1. Push (Place on top)
    def push(self, data):
        self.stack.append(data)
        print(f"Pushed: {data}")

    # 2. Pop (Remove from top)
    def pop(self):
        if not self.stack:  # If stack is empty
            print("Stack is Empty! (Underflow)")
            return None
        return self.stack.pop()  # Python's built-in pop

    # 3. Peek (Just see the top element)
    def peek(self):
        if not self.stack:
            return "Empty"
        return self.stack[-1]  # Last item in the list

    # Display all elements
    def display(self):
        print("Stack (Bottom -> Top):", self.stack)

# --- Testing ---
s = StackArray()
s.push(10)
s.push(20)
s.push(30)
s.display()  # [10, 20, 30]

print("Popped:", s.pop())          # 30 will be removed
print("Top element is:", s.peek()) # Now 20 is on the top
```

---

### **3. Implementation: Stack using Linked List**

This is important to explain to students.
With an array, there can be a size issue (if it’s a fixed-size array), but with a linked list the memory is dynamic.

**Logic Change:**

In a Linked List based stack, we treat the **Head** as the **Top**.

* **Push:** Insert a new node **before** the current head (make it the new head).
* **Pop:** Remove the head and move the head to the next node.

**Why?**
Because in a Linked List, inserting/removing at the **start** is easy (`O(1)`), but inserting/removing at the **end** requires a full traversal.

```python
# --- 2. Stack using Linked List ---

# Same old Node
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class StackLinkedList:
    def __init__(self):
        self.top = None  # Here we call the head 'top'

    # 1. Push (Insert at head/top)
    def push(self, data):
        new_node = Node(data)
        new_node.next = self.top  # New node points to previous top
        self.top = new_node       # New node becomes the new top
        print(f"Pushed: {data}")

    # 2. Pop (Remove from head/top)
    def pop(self):
        if self.top is None:
            print("Stack Underflow! (Empty)")
            return None
        
        popped_data = self.top.data
        self.top = self.top.next  # Shift top to next node
        return popped_data

    # 3. Peek (See top)
    def peek(self):
        if self.top is None:
            return "Empty"
        return self.top.data

    # Display (Top to Bottom)
    def display(self):
        current = self.top
        print("Stack (Top -> Bottom): ", end="")
        while current:
            print(f"[{current.data}]", end=" -> ")
            current = current.next
        print("None")

# --- Testing ---
sl = StackLinkedList()
print("\n--- Linked List Stack ---")
sl.push("Plate 1")
sl.push("Plate 2")
sl.push("Plate 3")  # This will be at the top
sl.display()

print("Popped:", sl.pop())  # Plate 3 will be removed
sl.display()
```

---

### **Key Difference for Students (Exam-Friendly Table):**

| Feature            | Stack using Array (List)                       | Stack using Linked List                           |
| ------------------ | ---------------------------------------------- | ------------------------------------------------- |
| **Easy to write?** | Very easy (especially in Python).              | Requires more code (nodes, pointers).             |
| **Speed**          | Fast, but may need resizing in some languages. | Fast `O(1)` operations, no resize step needed.    |
| **Size**           | Fixed in C++/Java arrays; dynamic in Python.   | Limited only by available memory (fully dynamic). |

**Summary for students:**

> A **Stack** means **LIFO** – *Last In, First Out.*
> The item that comes in last is the first to go out.
> We can implement a stack using both **Array/List** and **Linked List**.



---


## Topic 15: Sorting and Searching Algorithms

### Part A: **Sorting (Giving Order)**

#### Scenario: **"School Assembly Line"**

Imagine in the morning assembly, the teacher wants students to stand in a line **according to their height** (short to tall).

What will the teacher do?

1. She looks at the **first two students**.
2. If the **first** student is taller than the **second**, she swaps their positions.
3. Then she moves one step forward and keeps doing this for the whole line.
4. She keeps repeating this process until **no more swaps** are needed.

This idea is called **Bubble Sort** – the **heaviest / largest** element slowly “bubbles up” to the **end** of the list.

---

### Python Implementation: Bubble Sort

```python
def bubble_sort(arr):
    n = len(arr)
    # On each pass, the largest element will settle at the end
    for i in range(n):
        swapped = False
        # Last i elements are already sorted, so ignore them
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                # Swap positions
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        
        # If no swap happened in this pass, the list is already sorted
        if not swapped:
            break

# --- Testing ---
numbers = [64, 34, 25, 12, 22, 11, 90]
print("Original:", numbers)
bubble_sort(numbers)
print("Sorted:  ", numbers)
```

---

### Part B: **Searching (Finding Data)**

Here we compare **brute force** vs **smart searching**.

---

### 1. **Linear Search (Brute Force / One by One)**

**Scenario:**
You have a random pile of books. You need the **English** book.
You pick up **each book one by one** and check its title.

* If there are 100 books, in the worst case you might check all 100.
* **Time Complexity:**
  [
  O(n)
  ]
  (“n” steps in the worst case)

---

### 2. **Binary Search (Smart Search)**

**Scenario:**
You have a **dictionary** that is already **sorted A–Z**.
You want to search for the word **“Monkey”**.

Steps:

1. You open the book in the **middle**.
2. Suppose the word you see is **“Lion”**.
3. Since **“M”** comes **after** “L”, you know the word "Monkey" must be in the **second half**.

   * So you **ignore the first half** completely.
4. You repeat the same process (take middle, compare, cut half) until you find the word.

**Key Condition:**
Binary Search **only works if the data is already sorted**.

* **Time Complexity:**
  [
  O(\log n)
  ]
  (For 1000 items, you need only about 10 steps!)

---

### 🔍 Python Implementation: Binary Search

```python
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2  # Find the middle index
        guess = arr[mid]

        if guess == target:
            return mid  # Found it! Return the index
        if guess > target:
            high = mid - 1  # Target is smaller, search the left half
        else:
            low = mid + 1   # Target is larger, search the right half
            
    return -1  # Not found

# --- Testing (List must be sorted) ---
my_list = [10, 20, 30, 40, 50, 60, 70, 80, 90]
target = 70

result = binary_search(my_list, target)
if result != -1:
    print(f"Target found at index: {result}")
else:
    print("Target not found")
```

---

## Topic 16: Hashing and Time Complexity

This topic is **super powerful**. The goal is to access data in about **O(1)** time – i.e., *almost instant*.

---

### Part A: **Hashing**

#### Scenario: **"Token System" or "Locker Room"**

Imagine you go to a **bag counter**.

1. You hand over your bag.
2. The counter staff gives you **Token #55** and puts your bag in **Locker #55**.
3. When you come back, you show **Token #55**.
4. They do **not search** all lockers. They go **directly** to **Locker #55** and give you your bag.

This is the idea of **Hashing**.

* **Key:** Your bag (or your data).
* **Hash Function:** The formula that decides **which locker number** to use.
* **Hash Table:** The big array of lockers where all bags (data) are stored.

#### 🔁 Collision (Clash)

What if **two people** get the **same locker number**?
This is called a **Collision**.

One simple way to handle this:
Inside that locker, we keep a **small list (chain)** of all items that mapped to that locker.
This is called **chaining**.

---

### Python Implementation using Dictionary

In Python, a `dict` (dictionary) is basically a **hash table** internally.

```python
# --- Hashing using Dictionary ---

# Scenario: Get student name from roll number
student_db = {
    101: "Ali",
    102: "Sara",
    105: "Ahmed",
    999: "Zoya"
}

# Searching (Hash lookup)
# This does not loop; it directly jumps to the memory location
roll_no = 105
print(f"Roll No {roll_no} is: {student_db.get(roll_no)}")

# Average speed is O(1), even if there are 10 million students
```

---

### Part B: **Time Complexity (Quick Summary)**

You can give students this table as a **revision cheat-sheet** for exams and interviews.

**Time Complexity** = How many steps an algorithm roughly takes **relative to input size** `n`.

| Data Structure / Algorithm  | Operation | Time (Big O)  | Intuition / Meaning                                |
| --------------------------- | --------- | ------------- | -------------------------------------------------- |
| **Array / Linked List**     | Search    | (O(n))        | **Slow.** Might check the whole list.              |
| **Binary Search**           | Search    | (O(\log n))   | **Fast.** Throw away half the data each step.      |
| **Hash Table (Dictionary)** | Search    | (O(1))        | **Super Fast.** Jump directly to the data.         |
| **Bubble Sort**             | Sort      | (O(n^2))      | **Very Slow.** Compare everything with everything. |
| **Merge / Quick Sort**      | Sort      | (O(n \log n)) | **Efficient.** Use divide-and-conquer.             |

---

### Easy Rule of Thumb for Students

1. **(O(1))** – *Magic time* 
   Instant or constant time (like going straight to locker #55).

2. **(O(\log n))** – *Smart work* 
   Like searching in a dictionary by repeatedly cutting in half.

3. **(O(n))** – *Hard work* 
   Checking every page/item one by one.

4. **(O(n^2))** – *Very inefficient* 
   Nested loops (loop inside a loop) – like comparing every student with every other student.

