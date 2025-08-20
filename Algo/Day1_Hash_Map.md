
## 1. Contains Duplicate

### Problem
Given an integer array `nums`, return `true` if any value appears more than once in the array, otherwise return `false`.

### Example

Input: nums = [1, 2, 3, 3]
Output: true

Input: nums = [1, 2, 3, 4]
Output: false


### Recommended Complexity

- Time: O(n)
- Space: O(n)

### Approach

- Use a Set to store seen numbers.
- For each number:
- If it already exists in the set → return true.
- Otherwise, add it to the set.
- If the loop ends without duplicates → return false.

### One Line Solution

const containsDuplicate = nums => new Set(nums).size !== nums.length;
