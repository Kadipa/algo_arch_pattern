## Two Sum — Hashmap Approach
### Problem

Given an array of integers nums and an integer target, return the indices i and j such that:

nums[i] + nums[j] == target


with the condition i != j.
Return the answer with the smaller index first.

### Key Idea

Rearrange the equation:

nums[j] = target - nums[i]


So, if we are at nums[i], we only need to check if target - nums[i] exists in the array before index i.

### Why Hashmap?

Hashmap stores numbers we’ve seen so far along with their indices.

It lets us check in O(1) time if the complement exists.

This avoids the O(n²) brute-force search.

Algorithm (Step-by-Step)

Create an empty hashmap: number → index.

Iterate through nums with index i.

Compute the complement:

need = target - nums[i]


If need exists in hashmap → return [map[need], i].

Otherwise, store nums[i] with its index in the hashmap.

Continue until the pair is found.

Complexity

Time: O(n) (single pass through the array).

Space: O(n) (for the hashmap).

### Example Walkthrough

Input: nums = [3,4,5,6], target = 7

i=0 → nums[0]=3 → need=4 → not in map → store {3:0}

i=1 → nums[1]=4 → need=3 → found in map at index 0 → return [0,1]

Answer: [0,1]

```javascript 
function twoSum(nums, target) {
  const map = new Map(); // number -> index

  for (let i = 0; i < nums.length; i++) {
    const need = target - nums[i];

    if (map.has(need)) {
      return [map.get(need), i];
    }

    map.set(nums[i], i);
  }
```

