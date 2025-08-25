### Group Anagrams – Notes
Problem Recap

Given an array of strings, group all anagrams together.

An anagram means two words have the same letters in the same frequencies, but possibly in a different order.

### Example:

Input: ["act","pots","tops","cat","stop","hat"]

Output: [["hat"], ["act","cat"], ["stop","pots","tops"]]

### Approaches
1. Sorting Approach (O(m·n log n))

Sort each word alphabetically.

Use the sorted word as the key.

Group words by the same sorted result.

Example:

"act" → "act"

"cat" → "act"

"stop" → "opst"

Groups:

"act" → ["act","cat"]

"opst" → ["stop","pots","tops"]

2. Frequency Array Approach (O(m·n))

Use a 26-length array to count how many times each character appears in the word.

Convert this array to a string or tuple to use as the key in a map.

Group words with the same key.

Example:

"act" → [1,0,1,0,...,1,...] (1 at a, 1 at c, 1 at t)

"cat" → same frequency → same key.

Groups:

"[1,0,1,...,1]" → ["act","cat"]

Another key → ["stop","pots","tops"]

### Common Mistakes

Skipping the last character

Using for (i < word.length - 1) only loops until the second-to-last character.

Correct: loop until i < word.length.

### Resetting groups

Writing if (groups.has(key)) groups.set(key, []) overwrites existing groups.

Correct: only set a new list if the key does not exist.

### Pushing into undefined

If the group wasn’t initialized, groups.get(key) will be undefined.

Always ensure the group is created before pushing.

Complexity Analysis

Sorting approach: O(m · n log n)

Frequency array approach: O(m · n)

Extra space: O(m) for storing groups

### Solution

```javascript 
class Solution {
    /**
     * @param {string[]} strs
     * @return {string[][]}
     */
    groupAnagrams(strs) {

        const groups = new Map();

        strs.forEach((word)=>{
            const counts = new Array(26).fill(0);
            for(let i= 0; i < word.length; i++){
                counts[word.charCodeAt(i)-97]++;
            }
            const key = counts.join("#");
            if(!groups.has(key)) groups.set(key,[])
             groups.get(key).push(word)
        })
        return Array.from(groups.values())
    }
}
```