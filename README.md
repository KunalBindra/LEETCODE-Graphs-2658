# LEETCODE-Graphs-2658
- **Approach:** 
  - Use DFS to traverse connected components of the grid (cells with non-zero values).
  - Collect fish from all connected cells, marking them as visited by setting their value to `0` to avoid revisiting.
  - Track the maximum fish count for any connected component.

---

### Dry Run Example

**Input Grid:**
```
[
    [4, 0, 0, 5],
    [0, 6, 0, 0],
    [7, 0, 8, 0]
]
```

**Variables Initialization:**
- `m = 3` (number of rows)
- `n = 4` (number of columns)
- `directions = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}}` (up, down, left, right)
- `maxfish = 0`

---

#### Iteration Steps:
1. **Outer Loop (`i = 0`):**
   - **Inner Loop (`j = 0`):**
     - Cell `(0, 0)` has `4`. Start DFS:
       - `fishcount = 4`. Mark `(0, 0)` as visited (`grid[0][0] = 0`).
       - Check neighbors:
         - `(1, 0)` is water (`grid[1][0] = 0`).
         - `(-1, 0)` is out of bounds.
         - `(0, -1)` is out of bounds.
         - `(0, 1)` is water (`grid[0][1] = 0`).
       - Total fish from `(0, 0)` = `4`.
     - Update `maxfish = max(0, 4) = 4`.

   - **Inner Loop (`j = 1, j = 2`):**
     - Cells `(0, 1)` and `(0, 2)` are water (`grid[i][j] = 0`).

   - **Inner Loop (`j = 3`):**
     - Cell `(0, 3)` has `5`. Start DFS:
       - `fishcount = 5`. Mark `(0, 3)` as visited (`grid[0][3] = 0`).
       - Check neighbors:
         - `(1, 3)` is water (`grid[1][3] = 0`).
         - `(-1, 3)` is out of bounds.
         - `(0, 2)` is water (`grid[0][2] = 0`).
         - `(0, 4)` is out of bounds.
       - Total fish from `(0, 3)` = `5`.
     - Update `maxfish = max(4, 5) = 5`.

2. **Outer Loop (`i = 1`):**
   - **Inner Loop (`j = 0`):**
     - Cell `(1, 0)` is water (`grid[1][0] = 0`).

   - **Inner Loop (`j = 1`):**
     - Cell `(1, 1)` has `6`. Start DFS:
       - `fishcount = 6`. Mark `(1, 1)` as visited (`grid[1][1] = 0`).
       - Check neighbors:
         - `(2, 1)` is water (`grid[2][1] = 0`).
         - `(0, 1)` is water (`grid[0][1] = 0`).
         - `(1, 0)` is water (`grid[1][0] = 0`).
         - `(1, 2)` is water (`grid[1][2] = 0`).
       - Total fish from `(1, 1)` = `6`.
     - Update `maxfish = max(5, 6) = 6`.

   - **Inner Loop (`j = 2, j = 3`):**
     - Cells `(1, 2)` and `(1, 3)` are water (`grid[i][j] = 0`).

3. **Outer Loop (`i = 2`):**
   - **Inner Loop (`j = 0`):**
     - Cell `(2, 0)` has `7`. Start DFS:
       - `fishcount = 7`. Mark `(2, 0)` as visited (`grid[2][0] = 0`).
       - Check neighbors:
         - `(3, 0)` is out of bounds.
         - `(1, 0)` is water (`grid[1][0] = 0`).
         - `(2, -1)` is out of bounds.
         - `(2, 1)` is water (`grid[2][1] = 0`).
       - Total fish from `(2, 0)` = `7`.
     - Update `maxfish = max(6, 7) = 7`.

   - **Inner Loop (`j = 1`):**
     - Cell `(2, 1)` is water (`grid[2][1] = 0`).

   - **Inner Loop (`j = 2`):**
     - Cell `(2, 2)` has `8`. Start DFS:
       - `fishcount = 8`. Mark `(2, 2)` as visited (`grid[2][2] = 0`).
       - Check neighbors:
         - `(3, 2)` is out of bounds.
         - `(1, 2)` is water (`grid[1][2] = 0`).
         - `(2, 1)` is water (`grid[2][1] = 0`).
         - `(2, 3)` is water (`grid[2][3] = 0`).
       - Total fish from `(2, 2)` = `8`.
     - Update `maxfish = max(7, 8) = 8`.

   - **Inner Loop (`j = 3`):**
     - Cell `(2, 3)` is water (`grid[2][3] = 0`).

---

**Final Output:**
`maxfish = 8`. The maximum number of fish collectable from any connected component is `8`.
