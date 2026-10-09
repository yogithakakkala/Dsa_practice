# Day-wise Learning

---

## Day 1 — 5 Oct 2026

### 🧠 Concepts: Python Basics

**Python** is an *interpreted* language (code runs line by line, no separate compile step).

#### Operators
- Arithmetic · Logical · Relational · Assignment · Ternary · Bitwise
- **Membership operators:** `in`, `not in`

#### Bitwise Shifts
- **Left shift** `n << k` = `n × 2^k`
  ```
  110      (6)
  1100     (12)  → shifted by 1
  11000    (24)  → shifted by 2
  ```
- **Right shift** `n >> k` = `n // 2^k`

#### Conditional Statements
```python
if cond:
    ...
elif other:
    ...
else:
    ...
```

#### Control Statements
- `break` exits the loop
- `continue` skips to the next iteration

#### Loops
- `for` loop
- `while` loop
- ❌ `do-while`: **not supported** in Python

### ✅ Problems Solved

| Platform | Problem | Result |
|---|---|---|
| Codeforces | [A - Odd Divisor](https://codeforces.com/problemset/problem/1475/A) | ✅ Accepted (TLE on 1st try, fixed) |

---

## Day 2 — 6 Oct 2026

### 🧠 Concepts

#### `range()`
```python
for i in range(start, end, step):
    ...
```

#### Formatted Strings (f-strings)
```python
print(f"{i} - even number")   # {i} is the iterator variable
```

#### Leap Year
A year is a leap year if it is divisible by **4 and not by 100**, **or** divisible by **400**.
```python
is_leap = (year % 4 == 0 and year % 100 != 0) or (year % 400 == 0)
```

#### Missing Number
- Sum of first n numbers = `n(n+1)/2`
- Missing number = expected sum − sum of the given list

#### Dictionaries
- `keys()`, `values()`, `items()`
- **Frequency count:**
  ```python
  freq[x] = freq.get(x, 0) + 1
  ```

### ✅ Problems Solved

| Platform | Problem | Difficulty | Result |
|---|---|---|---|
| LeetCode | [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/) | Medium | ✅ Accepted |
| LeetCode | [268. Missing Number](https://leetcode.com/problems/missing-number/) | Easy | ✅ Accepted |
| LeetCode | [169. Majority Element](https://leetcode.com/problems/majority-element/) | Easy | ✅ Accepted |
| Codeforces | [A - New Year and Hurry](https://codeforces.com/problemset/problem/750/A) | Div. 2 A | ✅ Accepted |

---

## Day 3 — 7 Oct 2026

### 🧠 Concepts

#### Contains Duplicate
- Count occurrences with a dictionary; if any count > 1 → duplicate exists
- (Faster: `len(set(nums)) != len(nums)`)

#### Valid Anagram
- Same length, same characters, order can differ
- Approach: **sort both and compare** → `sorted(s) == sorted(t)`

#### Star Patterns

**Right triangle**
```
*
* *
* * *
* * * *
```
```python
for i in range(4):
    for j in range(i + 1):
        print("*", end=" ")
    print()
```

**Hollow square**
```
* * * *
*     *
*     *
* * * *
```
```python
n = 4
for i in range(n):
    for j in range(n):
        if i == 0 or i == n - 1 or j == 0 or j == n - 1:
            print("*", end=" ")
        else:
            print(" ", end=" ")
    print()
```

#### OOP — Introduction
Four pillars:
- **Encapsulation**: binding data and methods together
- **Abstraction**
- **Polymorphism**
- **Inheritance**

```python
class Student:
    def __init__(self, name):
        self.name = name

    def display(self):
        print("Name:", self.name)
```

### ✅ Problems Solved

| Platform | Problem | Difficulty | Result |
|---|---|---|---|
| LeetCode | [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/) | Easy | ✅ Accepted |

---

## Day 4 — 8 Oct 2026

### 🧠 Concepts

#### Polymorphism
"Existing in many forms"
- **Method overloading**: same method name, different parameters
- **Method overriding**: child class redefines a parent's method

#### Two Sum — Hashmap Approach
Store each number's index; for every number check if `target - num` was already seen.
```python
lookup = {}
for i, num in enumerate(nums):
    if target - num in lookup:
        return [lookup[target - num], i]
    lookup[num] = i
```
⏱ Time: O(n) · Space: O(n)

### ✅ Problems Solved

| Platform | Problem | Difficulty | Result |
|---|---|---|---|
| LeetCode | [1. Two Sum](https://leetcode.com/problems/two-sum/) | Easy | ✅ Accepted |
| LeetCode | [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/) | Easy | ✅ Accepted |
| LeetCode | [485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/) | Easy | ✅ Accepted |
| LeetCode | [1342. Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/) | Easy | ✅ Accepted |
| LeetCode | [1281. Subtract the Product and Sum of Digits of an Integer](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/) | Easy | ✅ Accepted |
| LeetCode | [1480. Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/) | Easy | ✅ Accepted |
| LeetCode | [75. Sort Colors](https://leetcode.com/problems/sort-colors/) | Medium | 🔁 Attempted (restrictions failed) |

---

## Day 5 — 9 Oct 2026

### 🧠 Concepts: Sliding Window (Fixed Size)

Keep a window of size `k`. As it slides right, **insert** the new element at `j` and **remove** the old element at `i`.

```
[ i  .  .  j ] → slide → [ i  .  .  j ]
  ↑ remove                         ↑ insert
```

Window size = `j - i + 1`

#### Template
```python
i = j = 0
window = 0
best = float("-inf")

while j < len(arr):
    window += arr[j]                 # add j-th element

    if j - i + 1 < k:                # window not full yet
        j += 1
    elif j - i + 1 == k:             # window size reached
        best = max(best, window)     # do the math / record answer
        window -= arr[i]             # remove i-th element
        i += 1
        j += 1
```
⏱ Time: O(n) instead of O(n·k)

### ✅ Problems Solved

| Platform | Problem | Difficulty | Result |
|---|---|---|---|
| LeetCode | [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/) | Easy | ✅ Accepted |
| LeetCode | [1343. Number of Sub-arrays of Size K and Average ≥ Threshold](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/) | Medium | ✅ Accepted |
| LeetCode | [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/) | Easy | ✅ Accepted |
| LeetCode | [1423. Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/) | Medium | 🔁 Attempted |
| LeetCode | [29. Divide Two Integers](https://leetcode.com/problems/divide-two-integers/) | Medium | 🔁 Attempted (TLE) |

