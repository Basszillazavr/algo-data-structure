### **Practical Lesson 1: Solutions** 🛠️

#### Task 1: The Static Array

```python
import array

# Emulating a static array with Python's `array` module for fixed type
# `i` stands for signed integer, and the size is 5
static_array = array.array('i', [0] * 5)

print("Original array:", static_array)

# Insert 5 numbers
static_array[0] = 10
static_array[1] = 20
static_array[2] = 30
static_array[3] = 40
static_array[4] = 50

print("Array after insertion:", static_array)

# Print an element by its index
index_to_print = 2
print(f"Element at index {index_to_print}: {static_array[index_to_print]}")

# Attempt to insert beyond array bounds
try:
    static_array[5] = 60
except IndexError as e:
    print(f"Error: {e}. Cannot insert element beyond array bounds.")
```

#### Task 2: The Dynamic Array

```python
# A Python list is a dynamic array
dynamic_array = []
print("Original list:", dynamic_array)

# Add 10 numbers to the list
for i in range(10):
    dynamic_array.append(i + 1)

print("List after adding 10 numbers:", dynamic_array)

# Insert a number at the beginning
dynamic_array.insert(0, 99)
print("List after inserting at the beginning:", dynamic_array)

# Remove a number from the middle (e.g., number 5)
try:
    dynamic_array.remove(5)
    print("List after removing 5:", dynamic_array)
except ValueError:
    print("Element 5 not found in the list.")

# Print the final list
print("Final list:", dynamic_array)
```

#### Task 3: The Linked List

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next_node = None

class LinkedList:
    def __init__(self):
        self.head = None

    def add_to_end(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        
        current_node = self.head
        while current_node.next_node:
            current_node = current_node.next_node
        current_node.next_node = new_node

    def print_list(self):
        current_node = self.head
        while current_node:
            print(current_node.data, end=" -> ")
            current_node = current_node.next_node
        print("None")

    def remove_node(self, data_to_remove):
        current_node = self.head
        if current_node and current_node.data == data_to_remove:
            self.head = current_node.next_node
            return

        prev_node = None
        while current_node and current_node.data != data_to_remove:
            prev_node = current_node
            current_node = current_node.next_node
        
        if current_node is None:
            return
        
        prev_node.next_node = current_node.next_node

# Example usage
my_linked_list = LinkedList()
my_linked_list.add_to_end(10)
my_linked_list.add_to_end(20)
my_linked_list.add_to_end(30)
my_linked_list.add_to_end(40)

print("Initial list:")
my_linked_list.print_list()

my_linked_list.remove_node(20)
print("List after removing 20:")
my_linked_list.print_list()

my_linked_list.add_to_end(50)
print("List after adding 50:")
my_linked_list.print_list()
```

-----

### **Practical Lesson 2: Solutions** 📚

#### Task 1: Implementing a Stack

```python
class Stack:
    def __init__(self):
        self.items = []

    def is_empty(self):
        return not self.items

    def push(self, item):
        self.items.append(item)
        print(f"Pushed item: {item}")

    def pop(self):
        if self.is_empty():
            return "Error: Stack is empty!"
        return self.items.pop()

    def peek(self):
        if self.is_empty():
            return "Stack is empty!"
        return self.items[-1]

    def size(self):
        return len(self.items)

# Example usage
my_stack = Stack()
my_stack.push(1)
my_stack.push(2)
my_stack.push(3)

print("Stack size:", my_stack.size())
print("Top element:", my_stack.peek())
print("Popped element:", my_stack.pop())
print("Stack size:", my_stack.size())
print("Popped element:", my_stack.pop())
print("Popped element:", my_stack.pop())
print("Attempting to pop from an empty stack:", my_stack.pop())
```

#### Task 2: Implementing a Queue

```python
class Queue:
    def __init__(self):
        self.items = []

    def is_empty(self):
        return not self.items

    def enqueue(self, item):
        self.items.append(item)
        print(f"Enqueued item: {item}")

    def dequeue(self):
        if self.is_empty():
            return "Error: Queue is empty!"
        return self.items.pop(0)

    def size(self):
        return len(self.items)

# Example usage
my_queue = Queue()
my_queue.enqueue("A")
my_queue.enqueue("B")
my_queue.enqueue("C")

print("Queue size:", my_queue.size())
print("Element to be dequeued first:", my_queue.items[0])
print("Dequeued element:", my_queue.dequeue())
print("Dequeued element:", my_queue.dequeue())
print("Dequeued element:", my_queue.dequeue())
print("Attempting to dequeue from an empty queue:", my_queue.dequeue())
```

-----

### **Practical Lesson 3: Binary Search Solution** 🔍

Binary search is an efficient algorithm for finding an item from a **sorted** list of items.

#### Task 1: Implementing Binary Search

```python
def binary_search(sorted_list, target):
    low = 0
    high = len(sorted_list) - 1

    while low <= high:
        # Find the middle index
        mid = (low + high) // 2
        guess = sorted_list[mid]

        if guess == target:
            # We found the target
            return mid
        elif guess < target:
            # The target is in the right half, so discard the left half
            low = mid + 1
        else:
            # The target is in the left half, so discard the right half
            high = mid - 1
            
    # The target was not found in the list
    return -1

# Code Exercise: Example Usage
sorted_numbers = [2, 5, 8, 12, 16, 23, 38, 56, 72, 91]

# Case 1: The target is in the list (e.g., 23)
target_found = 23
index = binary_search(sorted_numbers, target_found)

if index != -1:
    print(f"Number {target_found} found at index {index}")
else:
    print(f"Number {target_found} not found")

# Case 2: The target is not in the list (e.g., 50)
target_not_found = 50
index = binary_search(sorted_numbers, target_not_found)

if index != -1:
    print(f"Number {target_not_found} found at index {index}")
else:
    print(f"Number {target_not_found} not found")
```
