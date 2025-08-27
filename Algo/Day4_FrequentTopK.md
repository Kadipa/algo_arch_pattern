# Top K Frequent Elements

## Problem
Given an integer array `nums` and an integer `k`, return the `k` most frequent elements in any order.

### Example 1
Input: `nums = [1,2,2,3,3,3], k = 2`  
Output: `[2,3]`

### Example 2
Input: `nums = [7,7], k = 1`  
Output: `[7]`

### Constraints
- 1 <= nums.length <= 10^4
- -1000 <= nums[i] <= 1000
- 1 <= k <= number of distinct elements in nums

---

## Naive Solution
1. Count frequencies of each element.
2. Sort elements by frequency.
3. Take top `k`.

- Time Complexity: **O(n log n)** (due to sorting)

---

## Optimized Solution (Bucket Sort)

### Idea
- Instead of sorting, use **bucket sort** to group elements by their frequency.
- Maximum frequency ≤ n (`nums.length`).
- Build `n+1` buckets where `buckets[f]` holds all elements with frequency `f`.

### Steps
1. **Count frequencies** with a hash map.
2. **Bucket elements** by their frequency.
3. **Collect results** from highest frequency bucket down until we have `k` elements.

- Time Complexity: **O(n)**
- Space Complexity: **O(n)**

---

## Example Walkthrough
`nums = [1,2,2,3,3,3], k = 2`

1. Frequency map:
   - 1 → 1  
   - 2 → 2  
   - 3 → 3  

2. Buckets (index = frequency):
   - buckets[1] = [1]  
   - buckets[2] = [2]  
   - buckets[3] = [3]  

3. Collect from top:
   - buckets[3] → [3]  
   - buckets[2] → [2]  
   Result = `[3,2]`

---

## JavaScript Implementation
```js
function topKFrequent(nums, k) {
  // Step 1: count frequencies
  const freq = new Map();
  for (const x of nums) {
    freq.set(x, (freq.get(x) || 0) + 1);
  }

  // Step 2: create buckets
  const buckets = Array(nums.length + 1).fill(0).map(() => []);
  for (const [num, f] of freq.entries()) {
    buckets[f].push(num);
  }

  // Step 3: collect results
  const res = [];
  for (let f = buckets.length - 1; f >= 1 && res.length < k; f--) {
    for (const num of buckets[f]) {
      res.push(num);
      if (res.length === k) break;
    }
  }

  return res;
}
```