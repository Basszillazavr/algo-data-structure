
-----

## **Logic Questions for Managers (Non-Coding)** 🧠

### **Question 1: The Stable Sandwich Line** 🥪

**Context:** Your company's cafeteria uses an automated sorting system to organize customer orders. Customers place two orders in succession: a **drink** (primary item) and a **sandwich** (secondary item).

**Problem:** On Monday, two customers, Alice and Bob, both ordered the same drink (Coffee). Alice ordered her coffee first, then Bob ordered his. Later, when the sorting system is organizing the orders by drink type, it puts Bob's Coffee order first, followed by Alice's Coffee order, before moving on to the sandwich sorting.

**Question:** Which trait of the sorting algorithm did the cafeteria system fail to use: **Stability** or **In-Place Sorting**? Why does this failure mean that the relative order of Alice's and Bob's *sandwiches* is now incorrect in the final sorted list?

-----

### **Question 2: The Best-Case Bonus** 🚀

**Context:** Your team has two junior developers:

* **Dev A** used **Selection Sort** for a project.
* **Dev B** used **Insertion Sort** for a project.

Both were assigned to sort a massive list of user data. Unbeknownst to them, the system crashed the week before, and all the data was perfectly **pre-sorted** by the recovery routine.

**Question:** Who is most likely to get a bonus for delivering the fastest performance, and what is the Big O time complexity that explains their superior result?

-----

## **Coding Task: Insertion Sort Shift Counter** 💻

Implement the **Insertion Sort** function, but modify it to count the number of data **shifts** (copies) performed, as this is the dominant operation affecting performance in this specific algorithm.

**Requirements:**

1.  Write the function `insertion_sort_with_shifts(arr)`.
2.  The function must return the **total number of shifts** (when an element is moved to the right) performed to sort the array.
3.  Test the function on the array: `[5, 4, 3, 2, 1]`.

<!-- end list -->

```python
def insertion_sort_with_shifts(arr):
    # Your code here to implement Insertion Sort and count shifts
    pass

# Test the function: 
data = [5, 4, 3, 2, 1]
# total_shifts = insertion_sort_with_shifts(data) 
# print(f"Total number of shifts: {total_shifts}") 
```

-----

### **Question 1: The Stable Sandwich Line** 🥪

The trait the system failed to use is **Stability**.

**Explanation:**

* A **stable** sorting algorithm preserves the relative order of elements that have equal values (keys). Since Alice and Bob both ordered 'Coffee' (the primary sorting key), a stable sort would have ensured that Alice's order remained before Bob's order, as it was originally placed.
* Because the sort was **unstable**, the system arbitrarily swapped their relative positions. When the system later processes the orders based on this new, incorrect sequence, the assumption about the secondary item (the sandwich) is now wrong, leading to an error in the final arrangement.

### **Question 2: The Best-Case Bonus** 🚀

**Dev B** (who used **Insertion Sort**) is most likely to get the bonus for delivering the fastest performance.

**Explanation:**

* **Dev A (Selection Sort):** Time complexity is always **$O(n^2)$** (best, average, and worst). It must scan the entire unsorted portion of the list in every pass, even if the list is already sorted.
* **Dev B (Insertion Sort):** Time complexity in the **best case** (when the array is already sorted) is **$O(n)$**. Insertion Sort only needs to make a single pass through the list to confirm that no swaps or insertions are needed.

The Big O time complexity that explains the superior result is **$O(n)$**.

-----

## **Coding Task: Insertion Sort Shift Counter** 💻

The goal is to implement **Insertion Sort** and count the number of data **shifts** (copies) performed.

```python
def insertion_sort_with_shifts(arr):
    shift_count = 0
    n = len(arr)

    # Start from the second element (index 1)
    for i in range(1, n):
        # 'key' is the element to be inserted into the sorted part
        key = arr[i]
        j = i - 1

        # While j >= 0 AND the element on the left is greater than 'key', shift it right
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j] # This is the 'shift' (copy)
            shift_count += 1    # Increment the shift counter
            j -= 1
        
        # Insert 'key' into the now-empty slot
        arr[j + 1] = key

    return shift_count

# Test the function: 
data = [5, 4, 3, 2, 1]

# Expected shifts for [5, 4, 3, 2, 1] (Worst Case):
# Element 4 shifts 5 (1 shift)
# Element 3 shifts 5, 4 (2 shifts)
# Element 2 shifts 5, 4, 3 (3 shifts)
# Element 1 shifts 5, 4, 3, 2 (4 shifts)
# Total: 1 + 2 + 3 + 4 = 10 shifts

total_shifts = insertion_sort_with_shifts(data) 

print(f"Total number of shifts: {total_shifts}")
# Output: Total number of shifts: 10
```
