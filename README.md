# LeetCode 1534 - Count Good Triplets

## Problem Statement

Given an array of integers `arr`, and three integers `a`, `b`, and `c`, find the number of **good triplets**.

A triplet `(arr[i], arr[j], arr[k])` is **good** if the following conditions are all satisfied:

- \( 0 \leq i < j < k < arr.length \)
- \( |arr[i] - arr[j]| \leq a \)
- \( |arr[j] - arr[k]| \leq b \)
- \( |arr[i] - arr[k]| \leq c \)

Return the **number of good triplets**.

---

## Example

**Input:**  
`arr = [3,0,1,1,9,7], a = 7, b = 2, c = 3`  
**Output:**  
`4`  
**Explanation:**  
The good triplets are:  
- `(3,0,1)`  
- `(3,0,1)`  
- `(3,1,1)`  
- `(0,1,1)`

**Input:**  
`arr = [1,1,2,2,3], a = 0, b = 0, c = 1`  
**Output:**  
`0`  
**Explanation:**  
No valid triplet satisfies all three conditions.

---

## Intuition

Since the constraints are small (array length ≤ 100), we can use a brute-force approach by checking all possible triplets `(i, j, k)` where `i < j < k`.

---

## Approach

1. Use three nested loops to iterate over all triplets `i < j < k`.
2. For each triplet, check if:
   - `|arr[i] - arr[j]| <= a`
   - `|arr[j] - arr[k]| <= b`
   - `|arr[i] - arr[k]| <= c`
3. Count the triplet if it satisfies all three conditions.

---

## Complexity

- **Time Complexity:**  
  \(O(n^3)\) — due to triple nested loops

- **Space Complexity:**  
  \(O(1)\) — only a counter is used

---

## Python Code

```python
class Solution(object):
    def countGoodTriplets(self, arr, a, b, c):
        """
        :type arr: List[int]
        :type a: int
        :type b: int
        :type c: int
        :rtype: int
        """
        count = 0
        n = len(arr)
        # Iterate over all triplets (i, j, k) such that i < j < k
        for i in range(n):
            for j in range(i + 1, n):
                if abs(arr[i] - arr[j]) <= a:
                    for k in range(j + 1, n):
                        if abs(arr[j] - arr[k]) <= b and abs(arr[i] - arr[k]) <= c:
                            count += 1
        return count
```
