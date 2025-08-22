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


## Extra Notes

### Overview

- Set: Stores unique values. No key–value mapping.
- Object {}: Simple key–value dictionary with string (or symbol) keys.
- Map: Key–value dictionary with keys of any type and predictable iteration.

### 1) Set

- Track uniqueness and test membership in O(1) average time.

```javascript 
const set = new Set();

// add
set.add(1);
set.add(1);        // ignored (already present)

// check
set.has(1);        // true
set.has(2);        // false

// size
set.size;          // 1

// delete
set.delete(1);     // true

// iterate
for (const v of set) {
  // use v
}

// convert
const unique = [...new Set([1, 2, 2, 3])]; // [1,2,3]
```

#### Common Use Cases

- Remove duplicates from an array.
- Check if an element has been seen before.
- Set operations (union/intersection/difference) with small helpers.

### 2) Plain Object {}

- Lightweight hash table for string keys (common in coding challenges, e.g., frequency counters).

```javascript 
const obj = {};

// set/update
obj["a"] = (obj["a"] || 0) + 1;

// get
const countA = obj["a"];       // 1

// existence
("a" in obj);                  // true
("b" in obj);                  // false

// delete
delete obj["a"];

// iterate keys/values
for (const k in obj) {
  const v = obj[k];
}

Object.keys(obj);              // array of keys
Object.values(obj);            // array of values
Object.entries(obj);           // [ [k, v], ... ]
```

- Keys are strings (numbers are coerced to strings).
- Avoid prototype collisions if using untrusted keys (or use Object.create(null) to create a “bare” dictionary with no prototype).

```javascript 
const dict = Object.create(null);
dict["a"] = 1;
("toString" in dict); // false
```

#### Common Use Cases

- Character frequency counting.
- Simple maps from small strings to numbers.
- Fast and concise in algorithm problems.

### 3) Map

- Hash table with keys of any type and reliable insertion order iteration.

```javascript 
const map = new Map();

// set/update
map.set("a", 1);
map.set(2, "two");
map.set({ x: 1 }, "obj");

// get
map.get("a");     // 1
map.get(2);       // "two"

// existence
map.has("a");     // true
map.has("z");     // false

// size
map.size;         // 3

// delete
map.delete("a");  // true

// iterate
for (const [k, v] of map) {
  // use k, v
}

// convert
const fromPairs = new Map([["a", 1], ["b", 2]]);
```

#### Common Use Cases

- Keys not limited to strings (e.g., numbers, objects, tuples).
- Safer than {} for arbitrary keys (no prototype issues).
- When you need predictable iteration order of insertions.

### Choosing Between Them

- Uniqueness/membership only	Set
- Simple string-key frequency counts	Object {}
- Arbitrary key types or safer mapping

