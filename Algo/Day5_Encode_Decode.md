# Encode and Decode Strings

### Problem
Design an algorithm to:
- Encode a list of strings into one string.
- Decode that single string back into the original list.

---

### Examples
Input: `["neet","code","love","you"]`  
Output: `["neet","code","love","you"]`

Input: `["we","say",":","yes"]`  
Output: `["we","say",":","yes"]`

---

### Constraints
- `0 <= strs.length < 100`
- `0 <= strs[i].length < 200`
- `strs[i]` contains only UTF-8 characters
- Target complexity:  
  - **Time:** O(m) per encode/decode  
  - **Space:** O(m+n)  

Where:  
- `m` = total characters in all strings  
- `n` = number of strings

---

### Why Not a Simple Delimiter?
- Using a character like `"|"` or `","` to join strings fails if a string itself contains that character.  
- Need a method that works for any possible input.

---

### Key Idea
Use **length-prefix encoding**:
- For each string, store:  
  `length + "#" + string`
- Concatenate all of them.

Example:  
`["neet","code","love","you"]`  
→ `"4#neet4#code4#love3#you"`

---

### Encoding Logic
1. For each string:
   - Find its length.
   - Append `length + "#" + string` to result.
2. Return the concatenated string.

---

### Decoding Logic
1. Start from index `i = 0`.
2. Move forward until `#` is found → this part is the string’s length.
3. Convert length to integer `L`.
4. Read the next `L` characters as one decoded string.
5. Add it to the result list.
6. Move `i` forward and repeat until the end.

---

### Edge Cases
- Empty list → `""`
- Empty string → `"0#"`
- Strings containing `#` → still safe (length tells how many chars to read)
- Multi-digit lengths (e.g., `"12#helloworld!!"`)

---

### Complexity
- **Encoding:** O(m)  
- **Decoding:** O(m)  
- **Space:** O(m + n)
