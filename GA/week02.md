# Graded Assignment 2

**Question: Q1**

What is the time complexity of the following Python function `mystery_function(n)`?

```python
def mystery_function(n):
    total = 0
    for i in range(n):
        total += i

    j = 1
    while j < n:
        total *= 2
        j *= 2
    
    return total
```

**Options:**

A) $\mathcal{O}(n)$
B) $\mathcal{O}(n \log n)$
C) $\mathcal{O}(n^2)$
D) $\mathcal{O}(\log n)$

**Correct Answer:**

A) $\mathcal{O}(n)$

**Explanation:**

Let's analyze the time complexity of each part of the `mystery_function(n)`:

1.  **First loop (lines 3-4):**
    ```python
    for i in range(n):
        total += i
    ```
    This `for` loop iterates `n` times (from `i = 0` to `n-1`). Inside the loop, the operation `total += i` takes constant time, $\mathcal{O}(1)$. Therefore, this section contributes $\mathcal{O}(n)$ to the total time complexity.

2.  **Second loop (lines 6-9):**
    ```python
    j = 1
    while j < n:
        total *= 2
        j *= 2
    ```
    This `while` loop starts with `j = 1`. In each iteration, `j` is multiplied by 2. This means `j` takes values like $1, 2, 4, 8, \dots, 2^k$ until $2^k \ge n$. The number of iterations `k` required for this condition to be met is approximately $\log_2 n$. Inside the loop, `total *= 2` and `j *= 2` are constant time operations, $\mathcal{O}(1)$. Therefore, this section contributes $\mathcal{O}(\log n)$ to the total time complexity.

**Overall Time Complexity:**

To determine the overall time complexity of the function, we take the maximum (dominant) complexity among its individual parts. We have:
* First loop: $\mathcal{O}(n)$
* Second loop: $\mathcal{O}(\log n)$

Since $n$ grows much faster than $\log n$, the dominant term is $\mathcal{O}(n)$.

Therefore, the time complexity of the `mystery_function(n)` is $\mathcal{O}(n)$.

---

**Question: 2**

What is the time complexity of the given function `func(n)`?

```python
def func(n):
    s = 0
    if n <= 0:
        return 0
    for i in range(n):
        j = 0
        while j * j < n:
            s += j
            j += 1
    return s
```

**Options:**

A) $\mathcal{O}(n)$
B) $\mathcal{O}(n^2)$
C) $\mathcal{O}(n \log n)$
D) $\mathcal{O}(n \sqrt{n})$

**Correct Answer:**

D) $\mathcal{O}(n \sqrt{n})$

**Explanation:**

Let's analyze the time complexity of the given Python function `func(n)`:

1.  **Initial check (lines 2-4):**
    ```python
    s = 0
    if n <= 0:
        return 0
    ```
    The initialization `s = 0` and the `if` condition with the `return` statement take constant time, $\mathcal{O}(1)$.

2.  **Outer loop (lines 5-9):**
    ```python
    for i in range(n):
        j = 0
        while j * j < n:
            s += j
            j += 1
    ```
    The `for i in range(n):` loop iterates `n` times.

3.  **Inner loop (lines 7-9):**
    ```python
    j = 0
    while j * j < n:
        s += j
        j += 1
    ```
    Inside the outer loop, the `while` loop is executed. The condition for this loop is `j * j < n`. This means the loop will continue as long as the square of `j` is less than `n`. Approximately, this loop will run until $j \approx \sqrt{n}$. Since `j` is incremented by 1 in each iteration, the number of iterations of the inner `while` loop is roughly $\sqrt{n}$. Inside the `while` loop, the operations `s += j` and `j += 1` take constant time, $\mathcal{O}(1)$.

**Overall Time Complexity:**

The outer loop runs `n` times, and for each iteration of the outer loop, the inner `while` loop runs approximately $\sqrt{n}$ times. Therefore, the total number of operations is roughly $n \times \sqrt{n} = n^{1} \times n^{1/2} = n^{1 + 1/2} = n^{3/2}$.

In Big O notation, we ignore constant factors and lower-order terms. Thus, the time complexity of the function `func(n)` is $\mathcal{O}(n \sqrt{n})$.

---

**Question: 3**

Let $T_{\text{best}}(n)$, $T_{\text{avg}}(n)$, and $T_{\text{worst}}(n)$ be the best-case, average-case, and worst-case running times of an algorithm, respectively, executed on an input of size $n$.

Which of the following statement(s) is/are **always true** regarding these running times?

1. $T_{\text{best}}(n) = O(T_{\text{avg}}(n))$

2. $T_{\text{worst}}(n) = \Omega(T_{\text{avg}}(n))$

3. If $T_{\text{best}}(n) = \Theta(n^2)$ and $T_{\text{worst}}(n) = \Theta(n^2)$, then $T_{\text{avg}}(n) = \Theta(n^2)$

4. $T_{\text{avg}}(n) = O(T_{\text{best}}(n))$
</br></br>
**answer for Q3 is**
 - [x] 2. $T_{\text{worst}}(n) = \Omega(T_{\text{avg}}(n))$
- [x] 1. $T_{\text{best}}(n) = O(T_{\text{avg}}(n))$
 - [x] 3. If $T_{\text{best}}(n) = \Theta(n^2)$ and $T_{\text{worst}}(n) = \Theta(n^2)$, then $T_{\text{avg}}(n) = \Theta(n^2)$

---
**Question: 4**

Consider the below function for the selection sort algorithm:

```python
def selectionsort(L):
    n = len(L)
    if n < 1:
        return(L)
    for i in range(n-1):
        minpos = i
        for j in range(i+1,n):
            if L[j] < L[minpos]:
                minpos = j
        (L[i],L[minpos]) = (L[minpos],L[i]) #Swap Operation
    return(L)
```

Consider the list `L = [5, 2, 8, 2, 4]`. If this list is sorted using the provided `selectionsort` algorithm, how many *effective swaps* will be performed? (An effective swap is counted only when `minpos != i` at the moment of the swap).

**Options:**

A) 2
B) 3
C) 4
D) 5

**Correct Answer:**

B) 3

**Explanation:**

By tracing the selection sort on the list `[5, 2, 8, 2, 4]`, we find that effective swaps happen in the following iterations:

1.  Swap 5 and the first 2.
2.  Swap the second 5 and the second 2.
3.  Swap 8 and 4.

This results in a total of 3 effective swaps.

---

**Question: 5**
**Question:**

Consider the given insertion sort algorithm. Which of the following statements are correct? [MSQ]

```python
def insertionsort(L):
    n = len(L)
    if n < 1:
        return(L)
    for i in range(n):
        j = i
        while(j > 0 and L[j] < L[j - 1]):
            (L[j], L[j - 1]) = (L[j - 1], L[j])
            j = j - 1
    return(L)
```

**Options:**

A) The sort is stable and it does not sort in-place <br>
B) The sort is unstable and it sorts in-place <br>
C) The sort is stable and it sorts in-place <br>
D) After $m$ iterations of the for-loop, the first $m$ elements in the list are in sorted order <br>
E) After $m$ iterations of the for-loop, the first $m$ elements in the list are the $m$ smallest elements of the list <br>

**Correct Answer(s):**

C) The sort is stable and it sorts in-place <br>
D) After $m$ iterations of the for-loop, the first $m$ elements in the list are in sorted order

**Explanation:**

* **In-place:** The algorithm swaps elements within the original list.
* **Stable:** Equal elements maintain their relative order.
* **After $m$ iterations:** The first $m$ elements are sorted.
* **Not necessarily smallest $m$:** The first $m$ sorted elements are not guaranteed to be the smallest $m$ overall.

---

**Question 6:**

You are implementing binary search on a sorted array that may contain duplicate values of the target element $X$. You need to find the index of the **last occurrence** of $X$. If an instance of $X$ is found at $L[mid]$, how should the search proceed to find the last possible occurrence?

**Options:**

A) Store `mid` as a potential answer and continue searching in the left subarray by setting `high = mid - 1`. <br>
B) Immediately return `mid`, as binary search on a sorted array with duplicates will always find the last occurrence if multiple exist. <br>
C) Store `mid` as a potential answer and continue searching in the right subarray by setting `low = mid + 1`. <br>
D) Discard `mid` and search both the left (`high = mid - 1`) and right (`low = mid + 1`) subarrays recursively. <br>

**Correct Answer:**

C) Store `mid` as a potential answer and continue searching in the right subarray by setting `low = mid + 1`.

**Explanation:**

To find the last occurrence, even if we find $X$ at `mid`, there might be more occurrences of $X$ to its right. So, we store `mid` as a possible answer and continue searching in the right subarray to find a potentially later occurrence.

---

**Question 7:**

A school wants to maintain a database of its students. Each student has a unique id and it is stored along with other details. Adding a new student with a unique id, searching for a student using their id, and removal of students are the frequent operations performed on the database. From the options given below, choose the most efficient technique to store the data.

**Options:**

A) Maintain a sorted list with id. Whenever a new student is added, append the student details at the end, and sort the entire list using selection sort. <br>
B) Maintain a sorted list with id. Whenever a new student is added, append the student details at the end, and sort the entire list using insertion sort. <br>
C) Maintain a sorted list with id. Whenever a new student is added, append the student details at the end, and sort the entire list using merge sort. <br>
D) Maintain a sorted list with id. Whenever a new student is added, insert the student details into the respective position in the sorted list by id. <br>

**Correct Answer:**

D) Maintain a sorted list with id. Whenever a new student is added, insert the student details into the respective position in the sorted list by id.

**Explanation:**

For frequent searches based on a unique ID, a sorted structure allows efficient searching (e.g., binary search in $\mathcal{O}(\log n)$ time). Inserting in the correct position maintains the sorted order without resorting the entire list, which would be less efficient for frequent additions. Options A, B, and C involve sorting the entire list after each addition, which is less efficient than directly inserting into the sorted position.