# 977. Squares of a Sorted Array

- **Problem Link:** [LeetCode - 977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)
- **Difficulty:** 🟢 Easy
- **Topics:** Array, Two Pointers, Sorting

---

## 📝 Problem Statement

Given an integer array `nums` sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

---

## 💻 Solution

```python
def sortedSquares(self, nums: List[int]) -> List[int]:
    left = 0
    right = len(nums) - 1
    result = []

    while left <= right:
        if abs(nums[left]) > abs(nums[right]):
            result.append(nums[left]**2)
            left = left + 1
        else:
            result.append(nums[right]**2)
            right = right - 1
    result.reverse()
    return result
```
## ⏱️ Complexity Analysis

* **Time Complexity:** $O(n)$  
  We process each element in the array of length $n$ at most once using our two pointers.

* **Space Complexity:** $O(n)$  
  An additional array/list of size $n$ is required to store the sorted squared values.

---

## 💡 Key Takeaways & Intuition

* **Exploiting the Sorted Input:**  
  Since the input array is already sorted, the largest squared values are guaranteed to be at the extreme ends (the most negative numbers on the left or the largest positive numbers on the right).

* **Two Pointers Technique:**  
  By placing `left` at index `0` and `right` at `len(nums) - 1`, we can compare the absolute values (or squared values) at both ends and work our way inward.

* **Avoiding $O(n \log n)$ Sorting:**  
  Filling the result array from largest to smallest based on pointer comparison lets us achieve a sorted output in a single $O(n)$ pass, bypassing the need for a separate sort step.

    
