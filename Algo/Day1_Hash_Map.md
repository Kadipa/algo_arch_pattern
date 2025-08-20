
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


## 2. Valid Anagram

### Problem

Given two strings s and t, return true if the two strings are anagrams of each other, otherwise false.

Definition:
An anagram is a string that contains the exact same characters as another string, but the order may differ.

### Example

Input: s = "racecar", t = "carrace"
Output: true

Input: s = "jar", t = "jam"
Output: false

### Constraints

Strings consist of lowercase English letters.

### Recommended Complexity

Time: O(n + m)

Space: O(1) (since only 26 lowercase letters)

### Approach

- Use a hash map (object in JS) to store character frequencies.
- Count all characters in s.
- Decrease counts while scanning t.
- If any character is missing or mismatched, return false.
- If all counts are balanced, return true.

### Solution

function isAnagram(s, t) {
  if (s.length !== t.length) return false;

  const map = {};

  // Count characters in s
  for (let char of s) {
    map[char] = (map[char] || 0) + 1;
  }

  // Decrease counts using t
  for (let char of t) {
    if (!map[char]) return false; // not found or already 0
    map[char]--;
  }

  return true;
}
