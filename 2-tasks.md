Sure, here are four fun and engaging tasks for your "Data Structures and Space Complexity" lesson that will improve knowledge and encourage critical thinking.

-----

### **Task 1: The Memory Diet Challenge** 🍎

**Objective:** To understand how different data structures impact space complexity by creating a program that solves a problem in two different ways: one with high space complexity and one with low space complexity.

**Problem:** You have a list of strings. Your goal is to find all the duplicate strings.

* **Version A (High Space Complexity):** Use a **hash map (dictionary)** to store the counts of each string. Then, iterate through the hash map to find any string with a count greater than 1. This approach uses space proportional to the number of unique strings.
* **Version B (Low Space Complexity):** First, **sort** the list of strings. Then, iterate through the sorted list, checking if the current string is the same as the previous one. If it is, you've found a duplicate. This approach can be done with very little extra space.

**Discussion:** After coding both versions, discuss which one was easier to write and which one is more "memory-friendly." When would you choose one over the other?

-----

### **Task 2: The "Space Invaders" Game (on paper)** 👾

**Objective:** To visualize and track space complexity in a fun, non-coding way.

**Setup:**

1.  Draw a grid on a piece of paper. This grid represents your "memory."
2.  Assign each square a variable or data structure name (e.g., `i`, `total`, `new_list`).
3.  Each square represents one unit of memory.

**Game:** "Run" a piece of code line-by-line, and for each new variable or data structure that gets created, mark a new square on the grid.

**Code to "Run":**

```
def find_unique_words(text_file):
    words = text_file.split()
    seen_words = set()
    unique_list = []
    for word in words:
        if word not in seen_words:
            seen_words.add(word)
            unique_list.append(word)
    return unique_list
```

**Discussion:** As you "run" the code, discuss how the `seen_words` set and `unique_list` grow in size. What is the space complexity of this function? When does it reach its peak memory usage?

-----

### **Task 3: The Recursive "N-Queens" Challenge** 👑

**Objective:** To understand the space complexity of **recursion** and the function call stack.

**Problem:** The N-Queens puzzle is a classic problem: place N chess queens on an NxN chessboard so that no two queens threaten each other. A common solution uses a recursive backtracking algorithm.

**Task:** Don't write the full solution. Instead, write a function that simply calls itself recursively with a smaller input.

```python
def recursive_call(n):
    if n == 0:
        return
    print(f"Calling with n = {n}")
    recursive_call(n - 1)
```

**Discussion:**

1.  Run this code and observe the output. What's happening on the **call stack**?
2.  Discuss how each function call adds to the stack. What is the space complexity of a function that calls itself this way? Is it $O(n)$? Why or why not?
3.  How would the space complexity change if this were a recursive binary search instead?

-----

### **Task 4: The Data Structure Matchmaker** 💖

**Objective:** To apply knowledge of space and time complexity to real-world problems.

**Setup:** Provide students with two problem scenarios. For each scenario, they must choose the best data structure and justify their choice based on **time** and **space** complexity.

**Scenario A:**
You need to store a large number of user comments on a social media post. The most frequent operation is to add new comments. Deleting an old comment is rare. Memory usage is a key concern.

* **Options:** Linked List vs. Array

**Scenario B:**
You are building a real-time spell checker. You have a dictionary of 100,000 words. For every word a user types, you need to check if it exists in the dictionary **as fast as possible**.

* **Options:** Sorted List vs. Hash Set (set in Python)

**Discussion:** Have students present their justifications. This exercise forces them to think about the trade-offs between different data structures and how both time and space complexity influence real-world design choices.
