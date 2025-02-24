# Memory Map Analysis and Total Bytes Calculation

## Understanding the Code and Variables

The code declares the following variables:

1. **Characters:**
   - `char a` → 1 byte
   - `char *b` (pointer) → 8 bytes (on a 64-bit system)
   - `char c[3]` → 3 bytes

2. **Integers:**
   - `int i` → 4 bytes
   - `int *j` (pointer) → 8 bytes
   - `int k[3]` → 3 × 4 bytes = 12 bytes

---

## Assignments and Values at End of Execution

1. **`a = 'N'`**
   - `a` holds the ASCII value of `'N'` (78).

2. **`b = &(c[2]);`**
   - `b` now points to `c[2]` (the last element of `c` array).

3. **`j = &(k[0]);`**
   - `j` points to the first element of `k`.

4. **Loop Execution (`for (i=0; i<3; i++)`)**
   ```c
   for (i=0; i<3; i++) {
       *b = a - (char)i;
       b--;
       *j = i + 5;
       j++;
   }
   ```
   **Iteration breakdown:**
   - `i = 0`:
     - `*b = 'N' - 0 = 'N'`
     - `b` moves to `c[1]`
     - `*j = 5`
     - `j` moves to `k[1]`
   - `i = 1`:
     - `*b = 'N' - 1 = 'M'`
     - `b` moves to `c[0]`
     - `*j = 6`
     - `j` moves to `k[2]`
   - `i = 2`:
     - `*b = 'N' - 2 = 'L'`
     - `b` moves to an invalid location (before `c[0]`)
     - `*j = 7`
     - `j` moves beyond `k[2]`

---

## Final Memory Layout
| Variable | Address | Value |
|----------|---------|-------|
| `a` |  | `'N'` (ASCII 78) |
| `b` |  | Invalid (out of `c` bounds) |
| `c[0]` |  | `'L'` |
| `c[1]` |  | `'M'` |
| `c[2]` |  | `'N'` |
| `i` |  | 3 (after loop ends) |
| `j` |  | Points beyond `k[2]` |
| `k[0]` |  | 5 |
| `k[1]` |  | 6 |
| `k[2]` |  | 7 |

---

## Total Memory Usage
| Data Type | Variables | Size |
|-----------|-----------|------|
| `char` | `a` | 1 byte |
| `char *` | `b` | 8 bytes |
| `char[3]` | `c` | 3 bytes |
| `int` | `i` | 4 bytes |
| `int *` | `j` | 8 bytes |
| `int[3]` | `k` | 12 bytes |
| **Total** | | **36 bytes** |

## Final Answer:
- The code declares a total of **36 bytes** of memory.
- The final values in memory are as listed in the table above.


