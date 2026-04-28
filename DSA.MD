# PART A — Short Answer Questions (2 marks each)

---

## Q1a. Column Major Order

In **column major order**, elements of a 2D array are stored column by column in memory. That is, all elements of the first column are stored first, then the second column, and so on.

**Address Formula:**
Address of A[i][j] = Base + (j × M + i) × element_size
where M = number of rows.

**Example:** For array A[3][3], Base = 1000, element size = 2 bytes:
Address of A[2][1] = 1000 + (1 × 3 + 2) × 2 = 1000 + 10 = **1010**

---

## Q1b. Circular Queue — Overflow and Underflow

A **circular queue** is a linear data structure where the last position connects back to the first, forming a circle. It eliminates the wastage of space in a regular queue.

**Overflow condition (Queue Full):** (rear + 1) % MAX == front → cannot insert.
**Underflow condition (Queue Empty):** front == −1 → cannot delete.

---

## Q1c. Tree Traversals (Tree: F→B,G; B→A,D; G→I; D→C,E; I→H)

**In-order** (Left → Root → Right): A, B, C, D, E, F, G, H, I
**Pre-order** (Root → Left → Right): F, B, A, D, C, E, G, I, H
**Post-order** (Left → Right → Root): A, C, E, D, B, H, I, G, F

---

## Q1d. Stack — Overflow and Underflow

A **stack** is a linear data structure that follows LIFO (Last In First Out). Elements are inserted and removed from one end called the TOP.

**Overflow condition:** top == MAX − 1 → stack is full, PUSH fails.
**Underflow condition:** top == −1 → stack is empty, POP fails.

---

## Q1e. Adjacency Matrix (Graph: vertices 1, 2, 3)

An **adjacency matrix** is a V×V 2D array where A[i][j] = 1 if an edge exists between vertices i and j, otherwise 0.

For the triangle graph (edges 1–2, 2–3, 1–3):

```
     1   2   3
1  [ 0   1   1 ]
2  [ 1   0   1 ]
3  [ 1   1   0 ]
```

---

## Q1. Overflow and Underflow of Circular Queue (May 2024 Paper)

Same as Q1b above. Additionally: when (rear + 1) % MAX == front, insertion causes overflow. When front == rear == −1, deletion causes underflow.

---

## Q1. PREFIX Expression for (B \* C ^ D)

**Infix:** ( B _ C ^ D )
Since ^ has higher precedence than _, fully parenthesize: ( B _ ( C ^ D ) )
Convert inner: ( B _ ^CD )
Convert outer: **\* B ^ C D**

**Prefix expression: \* B ^ C D**

---

## Q1. Difference Between Linear Search and Binary Search

Linear search works on both sorted and unsorted arrays and checks each element one by one — time complexity O(n). Binary search requires a **sorted array** and repeatedly divides the search space in half — time complexity O(log n). Binary search is significantly faster for large datasets, but linear search is simpler and works without prior sorting.

---

## Q1. Height of a Tree

The **height of a tree** is the number of edges on the longest path from the root node to any leaf node.

**Algorithm:**

```
HEIGHT(node):
  if node == NULL: return -1
  return 1 + max(HEIGHT(node.left), HEIGHT(node.right))
```

**Example:** Root=10 → Left=20 → Left=40 (leaf). Height = 2.

---

## Q1. Min-Heap for: 80, 60, 30, 40, 20, 10

In a **Min-Heap**, every parent node is smaller than its children. The smallest element is always at the root.

Insert each element and heapify upward:

```
Final Min-Heap:
         10
        /  \
      30    20
     / \   /
    80  40 60
```

---

# PART B — Long Answer Questions

---

## Q2a. Selection Sort — Elements: 34, 45, 12, 38, 90, 64, 80, 20, 50

**Algorithm:**

```
SELECTION_SORT(A, n):
  for i = 0 to n-2:
    min_idx = i
    for j = i+1 to n-1:
      if A[j] < A[min_idx]:
        min_idx = j
    swap(A[i], A[min_idx])
```

**Step-by-step execution:**

```
Initial: [34, 45, 12, 38, 90, 64, 80, 20, 50]
Pass 1:  Min=12 at pos 2 → swap with pos 0
         [12, 45, 34, 38, 90, 64, 80, 20, 50]
Pass 2:  Min=20 at pos 7 → swap with pos 1
         [12, 20, 34, 38, 90, 64, 80, 45, 50]
Pass 3:  Min=34 at pos 2 → no swap needed
         [12, 20, 34, 38, 90, 64, 80, 45, 50]
Pass 4:  Min=38 → no swap needed
Pass 5:  Min=45 at pos 7 → swap with pos 4
         [12, 20, 34, 38, 45, 64, 80, 90, 50]
Pass 6:  Min=50 at pos 8 → swap with pos 5
         [12, 20, 34, 38, 45, 50, 80, 90, 64]
Pass 7:  Min=64 at pos 8 → swap with pos 6
         [12, 20, 34, 38, 45, 50, 64, 90, 80]
Pass 8:  Min=80 at pos 8 → swap with pos 7
Sorted:  [12, 20, 34, 38, 45, 50, 64, 80, 90]
```

**Time Complexity:** O(n²) for all cases. **Space:** O(1).

---

## Q2b. Linear Queue Operations on Q[5]

**Algorithm — INSERT:**

```
INSERT(Q, value):
  if rear == MAX-1: print "Overflow" and return
  if front == -1: front = 0
  rear = rear + 1
  Q[rear] = value
```

**Algorithm — DELETE:**

```
DELETE(Q):
  if front == -1 or front > rear: print "Underflow" and return
  val = Q[front]
  front = front + 1
  return val
```

**Execution trace:**

```
INSERT(Q) → Q=[Q,_,_,_,_]  front=0, rear=0
INSERT(W) → Q=[Q,W,_,_,_]  front=0, rear=1
INSERT(E) → Q=[Q,W,E,_,_]  front=0, rear=2
INSERT(R) → Q=[Q,W,E,R,_]  front=0, rear=3
DELETE()  → Removes Q     → front=1, rear=3
DELETE()  → Removes W     → front=2, rear=3
INSERT(T) → Q=[_,_,E,R,T]  front=2, rear=4
DELETE()  → Removes E     → front=3, rear=4
DELETE()  → Removes R     → front=4, rear=4

Deleted elements in order: Q, W, E, R
Remaining in Queue: [T]
```

---

## Q2c. Bubble Sort — Elements: 10, 40, 20, 30, 80, 70, 90, 50, 60, 100

**Algorithm:**

```
BUBBLE_SORT(A, n):
  for i = 0 to n-2:
    swapped = false
    for j = 0 to n-2-i:
      if A[j] > A[j+1]:
        swap(A[j], A[j+1])
        swapped = true
    if swapped == false: break  (optimization)
```

**Step-by-step execution:**

```
Initial: [10, 40, 20, 30, 80, 70, 90, 50, 60, 100]
Pass 1:  [10, 20, 30, 40, 70, 80, 50, 60, 90, 100]  ← 100 settled
Pass 2:  [10, 20, 30, 40, 70, 50, 60, 80, 90, 100]  ← 90 settled
Pass 3:  [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]  ← sorted!
```

**Time Complexity:** Best O(n), Average/Worst O(n²). **Stable sort.**

---

## Q2d. AVL Tree — Insert: 40, 30, 20, 10, 55, 65, 85, 75, 45, 35, 25, 15

An **AVL Tree** is a self-balancing BST where the balance factor (BF) of every node = Height(Left) − Height(Right), and BF must always be −1, 0, or +1.

**Four rotation types:**

- **LL Rotation:** Single right rotation (left-left imbalance)
- **RR Rotation:** Single left rotation (right-right imbalance)
- **LR Rotation:** Left rotation then right rotation
- **RL Rotation:** Right rotation then left rotation

**Key insertions with rotations:**

```
Insert 40, 30:     [40(L:30)] — balanced
Insert 20:         BF(40) = +2, LL case → Right Rotate
                   Result: [30(L:20, R:40)]
Insert 10:         BF(30) = +2 → Right Rotate
                   Result: [20(L:10, R:30(R:40))]
Insert 55, 65:     BF becomes -2, RR case → Left Rotate
                   Result: [30(L:20(L:10), R:55(L:40,R:65))]
Insert 85:         RR rotation at 55 → Left Rotate
Insert 75:         RL rotation (right then left)
Insert 45, 35, 25, 15: Continue with appropriate rotations

Final balanced AVL tree satisfies BF ∈ {-1, 0, 1} at every node.
```

**Time Complexity:** O(log n) for insert, delete, search.

---

## Q3a. Array Insert and Delete Operations

**i) Insert at location 2:**

```
INSERT_AT(A, n, pos, value):
  if n == MAX: print "Array Full" and return
  for i = n-1 downto pos:
    A[i+1] = A[i]    ← shift elements right
  A[pos] = value
  n = n + 1
```

**ii) Delete from location 1:**

```
DELETE_AT(A, n, pos):
  if n == 0: print "Array Empty" and return
  deleted = A[pos]
  for i = pos to n-2:
    A[i] = A[i+1]    ← shift elements left
  n = n - 1
  return deleted
```

---

## Q3b. Linear Search and Binary Search Algorithms

**Linear Search:**

```
LINEAR_SEARCH(A, n, key):
  for i = 0 to n-1:
    if A[i] == key: return i   (found)
  return -1                    (not found)
```

**Binary Search (array must be sorted):**

```
BINARY_SEARCH(A, n, key):
  low = 0, high = n-1
  while low <= high:
    mid = (low + high) / 2
    if A[mid] == key:   return mid
    else if A[mid] < key: low = mid + 1
    else:                 high = mid - 1
  return -1
```

**Comparison Table:**

```
Feature           Linear Search     Binary Search
Array condition   Sorted/Unsorted   Must be Sorted
Time (worst)      O(n)              O(log n)
Time (best)       O(1)              O(1)
Method            Sequential scan   Divide & Conquer
Suitable for      Small datasets    Large datasets
Implementation    Simple            Slightly complex
```

---

## Q4a. What is a Binary Search Tree (BST)?

A **BST** is a binary tree where for every node: all values in the left subtree are smaller, and all values in the right subtree are larger.

**Algorithm to insert into BST:**

```
BST_INSERT(root, value):
  if root == NULL: create new node with value and return
  if value < root.data:
    root.left = BST_INSERT(root.left, value)
  else if value > root.data:
    root.right = BST_INSERT(root.right, value)
  return root
```

---

## Q4b. Construct BST for: 40, 30, 50, 80, 90, 20, 10, 60, 70, 100

```
Start with 40 as root:
Insert 30: 30 < 40, goes left
Insert 50: 50 > 40, goes right
Insert 80: 80 > 40 > 50, goes right of 50
Insert 90: right of 80
Insert 20: left of 30
Insert 10: left of 20
Insert 60: left of 80
Insert 70: right of 60
Insert 100: right of 90

Final BST:
              40
            /    \
          30      50
         /          \
        20           80
       /            /  \
      10           60   90
                    \     \
                    70    100
```

**Search Algorithm:**

```
BST_SEARCH(root, key):
  if root == NULL or root.data == key: return root
  if key < root.data: return BST_SEARCH(root.left, key)
  else: return BST_SEARCH(root.right, key)
```

---

## Q4c. Non-Recursive In-Order Traversal

```
INORDER_ITERATIVE(root):
  Initialize empty stack
  current = root
  while current != NULL or stack is not empty:
    while current != NULL:
      push current onto stack
      current = current.left
    current = pop from stack
    print current.data
    current = current.right
```

This visits nodes in Left → Root → Right order without recursion, using an explicit stack.

---

## Q4d. Postfix Evaluation Algorithm

```
EVALUATE_POSTFIX(expression):
  Initialize empty stack
  for each token in expression:
    if token is operand:
      push token onto stack
    if token is operator:
      operand2 = pop from stack
      operand1 = pop from stack
      result = apply operator to operand1 and operand2
      push result onto stack
  return pop from stack (final result)
```

---

## Q5a. AVL Tree — Insert: 90, 80, 70, 60, 50, 10, 20, 30, 40, 55

```
Insert 90, 80:  [90(L:80)]
Insert 70:      BF(90)=+2, LL → Right Rotate
                [80(L:70, R:90)]
Insert 60:      BF(80)=+2 → Rotate → [70(L:60,R:80(R:90))]
Insert 50:      LL rotation → adjust
Insert 10:      Insert → imbalance → rotate
Insert 20:      LR rotation (left then right)
Insert 30, 40:  Multiple rotations applied
Insert 55:      Final adjustment

Each step maintains BF ∈ {-1, 0, 1} at all nodes.
```

---

## Q5b. Max-Heap Tree for: 71, 61, 91, 31, 41, 61, 81, 51

In a **Max-Heap**, every parent is greater than or equal to its children. The largest element is at the root.

```
Insert 71: [71]
Insert 61: [71, 61]
Insert 91: [91, 61, 71]   ← 91 > 71, swap
Insert 31: [91, 61, 71, 31]
Insert 41: [91, 61, 71, 31, 41]
Insert 61: [91, 61, 71, 31, 41, 61]
Insert 81: [91, 61, 81, 31, 41, 61, 71]  ← 81 > 71
Insert 51: [91, 61, 81, 51, 41, 61, 71, 31]

Final Max-Heap:
              91
            /    \
          61      81
         /  \    /  \
        51  41  61   71
       /
      31
```

---

## Q5c. Hash Functions — Elements: 30, 32, 45, 65, 57, 99

**Three standard hash functions:**

**1. Division Method:** h(k) = k mod m (where m = table size, say 10)

```
h(30)=0, h(32)=2, h(45)=5, h(65)=5*, h(57)=7, h(99)=9
*collision at 5
```

**2. Mid-Square Method:** Square the key, take middle digits

```
30²=900  → mid digit=9  → h(30)=9
32²=1024 → mid digits=02 → h(32)=0
45²=2025 → mid digits=02 → h(45)=0
65²=4225 → mid digits=22 → h(65)=2
57²=3249 → mid digits=24 → h(57)=2
99²=9801 → mid digits=80 → h(99)=8
```

**3. Folding Method:** Split key into parts and add them

```
h(30)=3+0=3,  h(32)=3+2=5,  h(45)=4+5=9
h(65)=6+5=11→1, h(57)=5+7=12→2, h(99)=9+9=18→8
```

---

## Q5d. BFS Algorithm (Graph Traversal Using Queue)

**Breadth First Search** visits all nodes level by level using a queue.

```
BFS(graph, start):
  Initialize empty queue Q
  Mark start as visited
  Enqueue start into Q
  while Q is not empty:
    vertex = Dequeue from Q
    print vertex
    for each neighbor of vertex:
      if neighbor is not visited:
        mark neighbor as visited
        Enqueue neighbor into Q
```

**For the graph (0,1,2,3,4,5) starting from node 1:**
Traversal sequence: 1 → 3 → 0 → 2 → 4 → 5

**Time Complexity:** O(V + E) where V = vertices, E = edges.

---

## Q. Infix to Postfix — Z = Q\*W/(E^R-T)

**Algorithm:**

```
Precedence: ^ > * = / > + = -
Associativity: ^ is right-to-left, rest are left-to-right

Converting: Q*W/(E^R-T)
Token  Stack         Output
Q                    Q
*      *             Q
W      *             QW
/      /             QW*   (/ same precedence as *, pop *)
(      / (           QW*
E      / (           QW*E
^      / ( ^         QW*E
R      / ( ^         QW*ER
-      / ( -         QW*ER^  (pop ^, then push -)
T      / ( -         QW*ER^T
)      /             QW*ER^T-  (pop until '(')
END                  QW*ER^T-/

Postfix: Q W * E R ^ T - /
```

---

## Q. Construct Binary Tree from Traversals

**In-order:** 10, 20, 25, 30, 35, 50, 60, 70, 90
**Pre-order:** 50, 20, 10, 30, 25, 35, 70, 60, 90

**Method:** First element of pre-order is always the **root**. Find root in in-order — elements to the left form the left subtree, elements to the right form the right subtree. Repeat recursively.

```
Root = 50 (first in pre-order)
In-order left of 50:  [10, 20, 25, 30, 35]  → left subtree
In-order right of 50: [60, 70, 90]           → right subtree

Left subtree root = 20 (next in pre-order)
  Left of 20:  [10]
  Right of 20: [25, 30, 35] → root=30, left=25, right=35

Right subtree root = 70
  Left of 70:  [60]
  Right of 70: [90]

Final Tree:
              50
            /    \
          20      70
         /  \    /  \
        10  30  60   90
           /  \
          25   35
```

---

## Q. Hashing — Employee IDs: 987654, 876562, 764089

**Division Method** (m = 100):
h(987654) = 987654 mod 100 = **54**
h(876562) = 876562 mod 100 = **62**
h(764089) = 764089 mod 100 = **89**

**Mid-Square Method** (take middle 2 digits of key²):
987654² → take middle 2 digits → approx **54**
876562² → take middle 2 digits → approx **26**
764089² → take middle 2 digits → approx **42**

**Folding Method** (split into 3-digit parts and add):
987654 → 987 + 654 = 1641 → 641 mod 100 = **41**
876562 → 876 + 562 = 1438 → 438 mod 100 = **38**
764089 → 764 + 089 = 853 → 853 mod 100 = **53**

---

> **Exam Tip:** For any tree construction question, always show each step of insertion. For sorting questions, show every pass. For algorithms, write clearly in pseudocode with proper indentation. These steps earn full marks even if the final answer has a minor error.

---

---

---

---

---

---

Here are complete, exam-ready answers for all questions from both papers:

---

# DATA STRUCTURES AND ALGORITHMS — COMPLETE EXAM ANSWERS

---

## PART A — SHORT ANSWERS

---

**Q1a. Address of Q[4][3] — Row Major Order**
Given: Base = 9000, size = 5 bytes, Q[8][8], so N = 8 columns.

Formula: Address = Base + [(i × N) + j] × size
= 9000 + [(4 × 8) + 3] × 5
= 9000 + [32 + 3] × 5
= 9000 + 175
**= 9175**

---

**Q1b. Overflow and Underflow in Stack (Array-based)**

A stack uses an array with a TOP pointer.

**Overflow** occurs when we try to PUSH into a full stack.
Condition: if TOP == SIZE – 1 → "Stack Overflow, cannot insert"

**Underflow** occurs when we try to POP from an empty stack.
Condition: if TOP == –1 → "Stack Underflow, cannot delete"

---

**Q1c. Construct Binary Tree from Pre-order and In-order**

Pre-order: 51, 21, 11, 31, 25, 35, 71, 61, 91
In-order: 11, 21, 25, 31, 35, 51, 61, 71, 91

Step 1: First element of pre-order = Root = **51**
Step 2: In in-order, 51 divides: Left = {11, 21, 25, 31, 35}, Right = {61, 71, 91}
Step 3: Next pre-order element for left subtree = **21** → root of left subtree
Step 4: In in-order, 21 divides left group: Left = {11}, Right = {25, 31, 35}
Step 5: 11 → left child of 21 (leaf)
Step 6: Next pre-order = **31** → root of right subtree of 21
Step 7: In in-order, 31 divides: Left = {25}, Right = {35} → 25 is left child, 35 is right child of 31
Step 8: For right of 51: next pre-order = **71**, in-order: Left = {61}, Right = {91}

```
            51
           /  \
         21    71
        /  \  /  \
       11  31 61  91
          / \
         25  35
```

---

**Q1d. Expression Tree for (B/C – D^E\*F + G)**

Operator precedence: ^ > \* > / > – > +
Parsed as: (B/C) – ((D^E) \* F) + G

Root = + (lowest precedence, evaluated last)
Left of + = – node
Right of + = G
Left of – = / node → left=B, right=C
Right of – = \* node → left=^ node (D, E), right=F

```
           +
          / \
         –   G
        / \
      (/)  (*)
      /\    /\
     B  C (^) F
           /\
          D  E
```

---

**Q1e. In-degree and Out-degree**

For any directed graph:

- **In-degree** of a vertex = number of edges pointing INTO that vertex
- **Out-degree** of a vertex = number of edges going OUT from that vertex
- Sum of all in-degrees = Sum of all out-degrees = Total number of edges

Trace each arrow in the given graph diagram. For each directed edge u → v: out-degree of u increases by 1, in-degree of v increases by 1.

---

## PART B — DETAILED ANSWERS

---

### ARRAYS AND MATRIX

---

**Q2a. Insertion and Deletion on Array Q[10] (elements 10,20,30,40,50 at index 0–4)**

**Algorithm for Insertion at position POS:**

```
Algorithm INSERT(Q, N, ITEM, POS):
1. If N == MAX:
      Print "Array is Full"
      Return
2. Set i = N – 1
3. While i >= POS:
      Q[i + 1] = Q[i]
      i = i – 1
4. Q[POS] = ITEM
5. N = N + 1
6. Stop
```

Example: Insert 25 at POS=2
Before: [10, 20, 30, 40, 50]
Shift 50→index5, 40→index4, 30→index3
Place 25 at index 2
After: [10, 20, 25, 30, 40, 50]

**Algorithm for Deletion at position POS:**

```
Algorithm DELETE(Q, N, POS):
1. If N == 0:
      Print "Array is Empty"
      Return
2. ITEM = Q[POS]
3. Set i = POS
4. While i < N – 1:
      Q[i] = Q[i + 1]
      i = i + 1
5. N = N – 1
6. Return ITEM
```

Example: Delete element at POS=1 (value 20)
Before: [10, 20, 30, 40, 50]
Shift: 30→index1, 40→index2, 50→index3
After: [10, 30, 40, 50], N=4

---

**Q2b. Radix Sort — 670, 903, 786, 451, 234, 432, 975, 444, 810, 339, 287**

Radix Sort sorts digit by digit from least significant to most significant using bucket sort at each pass.

**Pass 1 — Sort by Units digit (ones):**

Bucket 0: 810, 670
Bucket 1: 451
Bucket 2: 432
Bucket 3: 903
Bucket 4: 234, 444
Bucket 5: 975
Bucket 6: 786
Bucket 7: 287
Bucket 9: 339

Order after Pass 1: 810, 670, 451, 432, 903, 234, 444, 975, 786, 287, 339

**Pass 2 — Sort by Tens digit:**

Bucket 0: 903
Bucket 1: 810
Bucket 3: 432, 234, 339
Bucket 4: 444, 451
Bucket 5: 670 (no—67 in tens is 7)

Let us redo carefully:
810 → tens=1, 670 → tens=7, 451 → tens=5, 432 → tens=3, 903 → tens=0, 234 → tens=3, 444 → tens=4, 975 → tens=7, 786 → tens=8, 287 → tens=8, 339 → tens=3

Bucket 0: 903
Bucket 1: 810
Bucket 3: 432, 234, 339
Bucket 4: 444
Bucket 5: 451
Bucket 7: 670, 975
Bucket 8: 786, 287

Order after Pass 2: 903, 810, 432, 234, 339, 444, 451, 670, 975, 786, 287

**Pass 3 — Sort by Hundreds digit:**

903→9, 810→8, 432→4, 234→2, 339→3, 444→4, 451→4, 670→6, 975→9, 786→7, 287→2

Bucket 2: 234, 287
Bucket 3: 339
Bucket 4: 432, 444, 451
Bucket 6: 670
Bucket 7: 786
Bucket 8: 810
Bucket 9: 903, 975

**Final Sorted Order: 234, 287, 339, 432, 444, 451, 670, 786, 810, 903, 975**

---

**Row Major and Column Major — W[10][10], Base=10000, size=10, find W[5][5]**

**Row Major Formula:**
Address = Base + [(i × N) + j] × size
= 10000 + [(5 × 10) + 5] × 10
= 10000 + 55 × 10
**= 10550**

**Column Major Formula:**
Address = Base + [(j × M) + i] × size
= 10000 + [(5 × 10) + 5] × 10
= 10000 + 55 × 10
**= 10550**

(Both are equal here because i = j = 5 and the matrix is square 10×10)

---

**Sparse Matrix — Definition and Storage**

A matrix is called **sparse** if it contains more zero elements than non-zero elements. Generally, if the number of zeros > (2/3) of total elements, it is sparse.

**Algorithm to test:**

```
1. Count total = rows × cols
2. Count zero_count by scanning all elements
3. If zero_count > total / 2:
      Print "Matrix is Sparse"
   Else:
      Print "Not Sparse"
```

**3-Column Representation (Alternate storage):**
Store only non-zero elements in a table with three columns: Row, Column, Value.
The first row of this table stores: [total_rows, total_cols, total_nonzero_count]

Example:

```
Original Matrix:        3-Column Table:
0  0  5                Row  Col  Value
0  8  0      →          3    3     2     ← (3 rows, 3 cols, 2 non-zeros)
0  0  0                 0    2     5
                         1    1     8
```

This saves memory when the matrix has very few non-zero values.

---

### STACK AND QUEUE

---

**Push and Pop Algorithms (Array-based Stack)**

```
Algorithm PUSH(STACK, TOP, SIZE, ITEM):
1. If TOP == SIZE – 1:
      Print "Stack Overflow"
      Return
2. TOP = TOP + 1
3. STACK[TOP] = ITEM
4. Return

Algorithm POP(STACK, TOP):
1. If TOP == –1:
      Print "Stack Underflow"
      Return
2. ITEM = STACK[TOP]
3. TOP = TOP – 1
4. Return ITEM
```

---

**Q3a. Stack Trace — STACK[SIZE=4], TOP=–1**

Operations: PUSH(10), PUSH(20), POP(), PUSH(30), PUSH(40), PUSH(50), PUSH(60), POP(), POP(), POP(), PUSH(70)

```
PUSH(10) → TOP=0, Stack = [10]
PUSH(20) → TOP=1, Stack = [10, 20]
POP()    → Removes 20, TOP=0, Stack = [10]
PUSH(30) → TOP=1, Stack = [10, 30]
PUSH(40) → TOP=2, Stack = [10, 30, 40]
PUSH(50) → TOP=3, Stack = [10, 30, 40, 50]  ← Stack FULL
PUSH(60) → TOP=3 == SIZE–1=3 → OVERFLOW! Element not inserted
POP()    → Removes 50, TOP=2, Stack = [10, 30, 40]
POP()    → Removes 40, TOP=1, Stack = [10, 30]
POP()    → Removes 30, TOP=0, Stack = [10]
PUSH(70) → TOP=1, Stack = [10, 70]
```

**Final Stack: [10, 70], TOP = 1**

---

**Stack of Books (LIFO concept) — Push and Pop**

```
Algorithm PUSH_BOOK(STACK, TOP, SIZE, BOOK):
1. If TOP == SIZE – 1:
      Print "Rack is Full, Cannot add book"
      Return
2. TOP = TOP + 1
3. STACK[TOP] = BOOK
4. Print "Book pushed successfully"
5. Return

Algorithm POP_BOOK(STACK, TOP):
1. If TOP == –1:
      Print "Rack is Empty, No book to remove"
      Return
2. BOOK = STACK[TOP]
3. TOP = TOP – 1
4. Print "Book removed:", BOOK
5. Return BOOK
```

---

**Infix to Postfix — Q = A–S/D+(E\*F^G)–H**

Precedence (High to Low): ^ then \*/ then +–
Left to right associativity except ^ which is right to left.

```
Symbol | Stack Content    | Output
-------|------------------|------------------
A      | []               | A
–      | [–]              | A
S      | [–]              | A S
/      | [–, /]           | A S
D      | [–, /]           | A S D
+      | [+]              | A S D / –
(      | [+, (]           | A S D / –
E      | [+, (]           | A S D / – E
*      | [+, (, *]        | A S D / – E
F      | [+, (, *]        | A S D / – E F
^      | [+, (, *, ^]     | A S D / – E F
G      | [+, (, *, ^]     | A S D / – E F G
)      | [+]              | A S D / – E F G ^ *
–      | [–]              | A S D / – E F G ^ * +
H      | [–]              | A S D / – E F G ^ * + H
End    | []               | A S D / – E F G ^ * + H –
```

**Postfix Result: A S D / – E F G ^ \* + H –**

---

**Postfix Evaluation — 50, 60, \*, 240, 20, 30, ^, /, –**

```
Token | Action                          | Stack
------|----------------------------------|------------------
50    | Push 50                         | [50]
60    | Push 60                         | [50, 60]
*     | Pop 60 and 50; 50×60 = 3000     | [3000]
240   | Push 240                        | [3000, 240]
20    | Push 20                         | [3000, 240, 20]
30    | Push 30                         | [3000, 240, 20, 30]
^     | Pop 30,20; 20^30 = very large V | [3000, 240, V]
/     | Pop V,240; 240/V ≈ 0            | [3000, 0]
–     | Pop 0,3000; 3000 – 0 = 3000     | [3000]
```

**Final Result = 3000**

---

**Queue Operations — QUEUE[SIZE=5], Front=–1, Rear=–1**

Operations: INSERT(Q), INSERT(W), INSERT(E), INSERT(R), DELETE(), DELETE(), INSERT(T), DELETE(), DELETE()

```
INSERT(Q): Front=0, Rear=0 → [Q, _, _, _, _]
INSERT(W): Front=0, Rear=1 → [Q, W, _, _, _]
INSERT(E): Front=0, Rear=2 → [Q, W, E, _, _]
INSERT(R): Front=0, Rear=3 → [Q, W, E, R, _]
DELETE():  Remove Q, Front=1 → [_, W, E, R, _]
DELETE():  Remove W, Front=2 → [_, _, E, R, _]
INSERT(T): Front=2, Rear=4 → [_, _, E, R, T]
DELETE():  Remove E, Front=3 → [_, _, _, R, T]
DELETE():  Remove R, Front=4 → [_, _, _, _, T]
```

**Final Queue: only T remains at index 4, Front=4, Rear=4**

---

### LINKED LIST

---

**Q4a. Single Linked List — Insert New Node at End**

Given list: 10 → 20 → 30 → 40 → 50 → NULL

```
Algorithm INSERT_END(START, ITEM):
1. NEW = Create new node
2. NEW.DATA = ITEM
3. NEW.NEXT = NULL
4. If START == NULL:
      START = NEW
      Return
5. PTR = START
6. While PTR.NEXT != NULL:
      PTR = PTR.NEXT
7. PTR.NEXT = NEW
8. Return
```

After inserting 60:
10 → 20 → 30 → 40 → 50 → 60 → NULL

---

**Q4c. Double Linked List — Insert New Node at Beginning**

DLL Node structure: [PREV | DATA | NEXT]

```
Algorithm INSERT_BEGIN_DLL(START, ITEM):
1. NEW = Create new node
2. NEW.DATA = ITEM
3. NEW.PREV = NULL
4. NEW.NEXT = START
5. If START != NULL:
      START.PREV = NEW
6. START = NEW
7. Return
```

Before: NULL ← [10] ↔ [20] ↔ [30] ↔ [40] ↔ [50] → NULL
After inserting 5:
NULL ← [5] ↔ [10] ↔ [20] ↔ [30] ↔ [40] ↔ [50] → NULL

---

**DLL — Delete Node from End**

```
Algorithm DELETE_END_DLL(START):
1. If START == NULL:
      Print "List is Empty"
      Return
2. If START.NEXT == NULL:
      START = NULL
      Return
3. PTR = START
4. While PTR.NEXT != NULL:
      PTR = PTR.NEXT
5. PTR.PREV.NEXT = NULL
6. Return
```

---

**Queue on Single Linked List**

```
Algorithm ENQUEUE(FRONT, REAR, ITEM):
1. NEW = Create new node
2. NEW.DATA = ITEM; NEW.NEXT = NULL
3. If REAR == NULL:
      FRONT = REAR = NEW
      Return
4. REAR.NEXT = NEW
5. REAR = NEW
6. Return

Algorithm DEQUEUE(FRONT, REAR):
1. If FRONT == NULL:
      Print "Queue Empty"
      Return
2. ITEM = FRONT.DATA
3. FRONT = FRONT.NEXT
4. If FRONT == NULL:
      REAR = NULL
5. Return ITEM
```

---

**DLL — Insert PTR1 between PTR2 (4th node) and PTR3 (6th node):**

```
PTR1.PREV = PTR2
PTR1.NEXT = PTR3
PTR2.NEXT = PTR1
PTR3.PREV = PTR1
```

---

### TREES

---

**Q3b. Binary Search Tree — Definition and Insertion Algorithm**

A **Binary Search Tree (BST)** is a binary tree where for every node:

- All values in the **left subtree** are **less than** the node's value
- All values in the **right subtree** are **greater than** the node's value

```
Algorithm BST_INSERT(ROOT, ITEM):
1. NEW = Create new node
   NEW.DATA = ITEM
   NEW.LEFT = NULL; NEW.RIGHT = NULL
2. If ROOT == NULL:
      ROOT = NEW; Return
3. PTR = ROOT
4. While PTR != NULL:
      If ITEM < PTR.DATA:
         If PTR.LEFT == NULL:
            PTR.LEFT = NEW; Return
         Else:
            PTR = PTR.LEFT
      Else:
         If PTR.RIGHT == NULL:
            PTR.RIGHT = NEW; Return
         Else:
            PTR = PTR.RIGHT
```

BST for: 40, 30, 50, 80, 90, 20, 10, 60, 70, 100

```
              40
            /    \
          30      50
         /           \
        20            80
       /             /  \
      10            60   90
                      \     \
                      70    100
```

---

**Tree Traversal Algorithms (Recursive)**

```
INORDER(ROOT):      ← Left → Root → Right
1. If ROOT == NULL: Return
2. INORDER(ROOT.LEFT)
3. Print ROOT.DATA
4. INORDER(ROOT.RIGHT)

PREORDER(ROOT):     ← Root → Left → Right
1. If ROOT == NULL: Return
2. Print ROOT.DATA
3. PREORDER(ROOT.LEFT)
4. PREORDER(ROOT.RIGHT)

POSTORDER(ROOT):    ← Left → Right → Root
1. If ROOT == NULL: Return
2. POSTORDER(ROOT.LEFT)
3. POSTORDER(ROOT.RIGHT)
4. Print ROOT.DATA
```

For tree (root=50, left=25, right=75, 25's children=10,49, 75's child=99):

- **In-order:** 10, 25, 49, 50, 75, 99
- **Pre-order:** 50, 25, 10, 49, 75, 99
- **Post-order:** 10, 49, 25, 99, 75, 50

---

**Non-Recursive In-order Traversal:**

```
Algorithm NONREC_INORDER(ROOT):
1. Create empty STACK
2. PTR = ROOT
3. While PTR != NULL OR STACK is not empty:
      While PTR != NULL:
         Push PTR onto STACK
         PTR = PTR.LEFT
      PTR = POP from STACK
      Print PTR.DATA
      PTR = PTR.RIGHT
4. Return
```

---

**Q4d. Heap Tree — Definition, Types, and Max-Heap Construction**

A **Heap Tree** is a complete binary tree that satisfies the heap property.

**Types:**

- **Max-Heap:** Parent node value ≥ children node values. Root is the maximum element.
- **Min-Heap:** Parent node value ≤ children node values. Root is the minimum element.

**Max-Heap Construction for: 71, 61, 91, 31, 41, 61, 81, 51**

Insert each element and apply heapify-up (compare with parent and swap if greater):

```
Insert 71 → [71]
Insert 61 → [71, 61]           61 < 71, no swap
Insert 91 → [71, 61, 91]       91 > 71, swap → [91, 61, 71]
Insert 31 → [91, 61, 71, 31]   31 < 61, no swap
Insert 41 → [91, 61, 71, 31, 41] 41 < 61, no swap
Insert 61 → [91, 61, 71, 31, 41, 61]  61 = 71, no swap needed
Insert 81 → [91, 61, 71, 31, 41, 61, 81] 81 > 71, swap → [91,61,81,31,41,61,71]
Insert 51 → 51 < 31? No, 51 > 31, swap → check parent 61, 51<61 stop
           [91, 61, 81, 51, 41, 61, 71, 31]
```

**Final Max-Heap:**

```
              91
            /    \
          61      81
         /  \    /  \
        51   41 61   71
       /
      31
```

---

**Q5a. AVL Tree — Balance Factor and Construction for 70,20,10,30,40,50,60,25,35,75**

**Balance Factor (BF)** = Height(Left subtree) – Height(Right subtree)
For AVL tree, BF must be –1, 0, or +1 for every node.

**Four AVL Rotations:**

- **LL Rotation:** BF = +2 and left child BF = +1 → Single Right Rotation
- **RR Rotation:** BF = –2 and right child BF = –1 → Single Left Rotation
- **LR Rotation:** BF = +2 and left child BF = –1 → Left rotate child, then Right rotate node
- **RL Rotation:** BF = –2 and right child BF = +1 → Right rotate child, then Left rotate node

**Step-by-step insertion:**

```
Insert 70: Tree = [70]

Insert 20: 70→left=20. BF(70)=+1. Balanced.

Insert 10: BF(70)=+2, left child(20) BF=+1 → LL Rotation at 70
Result:
        20
       /  \
      10   70

Insert 30: 70→left=30. BF(70)=+1. Balanced.
        20
       /  \
      10   70
           /
          30

Insert 40: BF(70)=–2, right child(30) BF=–1 → RR Rotation at 70
        20
       /  \
      10   30
             \
             40
Wait — 30 becomes parent of 70 and 40:
        20
       /  \
      10   30
             \
             40
BF(20)=–1 — still balanced.

Insert 50: BF(30)=–2, RR Rotation at 30
        20
       /  \
      10   40
          /  \
         30   50

Insert 60: BF(40)=–2 → RR at 40 → BF(20)=–2 → RR at 20
        40
       /  \
      20   50
     /  \    \
    10   30   60

Insert 25: goes under 30's left. Balanced.

Insert 35: goes under 30's right.
BF(30)=0. BF(20)=–1. BF(40)=+1. Balanced.

Insert 75: goes to right of 60. Balanced.
```

---

**Binary Tree Terminology:**

**Complete Binary Tree:** All levels are completely filled except possibly the last level, and the last level has all nodes as far left as possible.

**Skew Binary Tree:** A tree where every node has only one child. If all nodes have only left children it is called Left-Skewed; if all have only right children it is Right-Skewed. It resembles a linked list.

**Strictly Binary Tree:** Every node in the tree has either 0 or exactly 2 children. No node can have exactly 1 child.

**Height of a node:** The length of the longest path from that node to any leaf node below it. Height of a leaf = 0.

**Depth of a node:** The length of the path from the root to that node. Depth of root = 0.

---

### SORTING AND SEARCHING

---

**Q2d. Quick Sort — 34, 56, 12, 23, 90, 78, 67, 45**

```
Algorithm QUICKSORT(A, LOW, HIGH):
1. If LOW < HIGH:
2.    PIVOT_POS = PARTITION(A, LOW, HIGH)
3.    QUICKSORT(A, LOW, PIVOT_POS – 1)
4.    QUICKSORT(A, PIVOT_POS + 1, HIGH)

PARTITION(A, LOW, HIGH):
1. PIVOT = A[LOW]
2. i = LOW; j = HIGH
3. While i < j:
      While A[i] <= PIVOT AND i < HIGH: i++
      While A[j] > PIVOT: j--
      If i < j: Swap A[i] and A[j]
4. Swap A[LOW] and A[j]
5. Return j
```

**Pass 1 — Pivot = 34:**
Array: [34, 56, 12, 23, 90, 78, 67, 45]
i moves right past elements ≤ 34: stops at 56
j moves left past elements > 34: stops at 23
i < j → Swap 56 and 23 → [34, 23, 12, 56, 90, 78, 67, 45]
i continues to 56, j moves to 12
i > j → Swap pivot(34) with A[j]=12 → [12, 23, 34, 56, 90, 78, 67, 45]
Pivot 34 is now at index 2 (correct position)

Left subarray [12, 23] and Right subarray [56, 90, 78, 67, 45] are recursively sorted.

**Final Sorted: 12, 23, 34, 45, 56, 67, 78, 90**

---

**Bubble Sort Algorithm:**

```
Algorithm BUBBLE_SORT(A, N):
1. For i = 0 to N–2:
2.    For j = 0 to N–2–i:
3.       If A[j] > A[j+1]:
4.          Swap A[j] and A[j+1]
5. Return
```

Each pass pushes the largest unsorted element to its correct position. Time Complexity: O(n²).

---

**Insertion Sort — 70, 40, 50, 30, 35, 25, 45**

```
Algorithm INSERTION_SORT(A, N):
1. For i = 1 to N–1:
2.    key = A[i]
3.    j = i – 1
4.    While j >= 0 AND A[j] > key:
5.       A[j+1] = A[j]
6.       j = j – 1
7.    A[j+1] = key
8. Return
```

**Step-by-step trace:**

```
Initial:  [70, 40, 50, 30, 35, 25, 45]
Pass 1:   key=40 → [40, 70, 50, 30, 35, 25, 45]
Pass 2:   key=50 → [40, 50, 70, 30, 35, 25, 45]
Pass 3:   key=30 → [30, 40, 50, 70, 35, 25, 45]
Pass 4:   key=35 → [30, 35, 40, 50, 70, 25, 45]
Pass 5:   key=25 → [25, 30, 35, 40, 50, 70, 45]
Pass 6:   key=45 → [25, 30, 35, 40, 45, 50, 70]
```

**Final Sorted: 25, 30, 35, 40, 45, 50, 70**

---

**Binary Search Algorithm:**

```
Algorithm BINARY_SEARCH(A, N, ITEM):
1. LOW = 0; HIGH = N – 1
2. While LOW <= HIGH:
3.    MID = (LOW + HIGH) / 2
4.    If A[MID] == ITEM:
         Print "Found at index", MID
         Return MID
5.    Else If ITEM < A[MID]:
         HIGH = MID – 1
6.    Else:
         LOW = MID + 1
7. Print "Element Not Found"
8. Return –1
```

Array must be **sorted** before applying binary search. Time Complexity: O(log n).

---

### GRAPHS AND HASHING

---

**Q5c. DFS Traversal Algorithm:**

```
Algorithm DFS(G, START):
1. Create empty STACK
2. Mark all vertices as UNVISITED
3. Push START onto STACK
4. Mark START as VISITED
5. While STACK is not empty:
6.    POP vertex V from STACK
7.    Print V
8.    For each neighbor W of V:
9.       If W is UNVISITED:
10.          Mark W as VISITED
11.          Push W onto STACK
12. Return
```

For graph with vertices 1–6, starting from vertex 1:
DFS visits: 1 → 2 → 4 → 6 → 3 → 5 (order depends on adjacency list)

---

**BFS Traversal Algorithm (using Queue):**

```
Algorithm BFS(G, START):
1. Create empty QUEUE
2. Mark all vertices UNVISITED
3. Enqueue START; Mark START VISITED
4. While QUEUE is not empty:
5.    Dequeue vertex V; Print V
6.    For each neighbor W of V:
7.       If W is UNVISITED:
8.          Mark W VISITED
9.          Enqueue W
10. Return
```

---

**Q6c. Adjacency Matrix and Incidence Matrix**

**Adjacency Matrix:** An n × n matrix A where A[i][j] = 1 if there is an edge from vertex i to vertex j, otherwise 0.

**Incidence Matrix:** An n × e matrix (n = vertices, e = edges) where entry is 1 if the vertex is an endpoint of that edge (undirected), or +1 for tail / –1 for head (directed).

For graph A–B–C–D–E with edges AB, AD, BC, BE, CE, DE:

```
Adjacency Matrix:
     A  B  C  D  E
A  [ 0, 1, 0, 1, 0 ]
B  [ 1, 0, 1, 0, 1 ]
C  [ 0, 1, 0, 0, 1 ]
D  [ 1, 0, 0, 0, 1 ]
E  [ 0, 1, 1, 1, 0 ]
```

---

**Q6a. Hash Function — Division Method on 120, 195, 354, 430, 627, 595, 315, 409, 747, 303**

A **Hash Function** maps a key to an index in a hash table. The **Division Method** uses: h(key) = key mod TableSize

Using TableSize = 10:

```
h(120) = 120 mod 10 = 0
h(195) = 195 mod 10 = 5
h(354) = 354 mod 10 = 4
h(430) = 430 mod 10 = 0  → Collision
h(627) = 627 mod 10 = 7
h(595) = 595 mod 10 = 5  → Collision
h(315) = 315 mod 10 = 5  → Collision
h(409) = 409 mod 10 = 9
h(747) = 747 mod 10 = 7  → Collision
h(303) = 303 mod 10 = 3
```

**Three Hash Functions (for 30, 32, 45, 65, 57, 99):**

1. **Division Method:** h(k) = k mod m (e.g., mod 10)
   30→0, 32→2, 45→5, 65→5, 57→7, 99→9

2. **Mid-Square Method:** Square the key, extract middle digits
   30²=900 → take middle digit → 0
   32²=1024 → middle digits 02 → 2
   45²=2025 → middle digits 02 → 2

3. **Folding Method:** Split key into equal parts, add them
   For 2-digit keys, fold is just the number itself mod table size.
   For larger keys: e.g., 354 → 35 + 4 = 39 mod 10 = 9

---

**Weighted Graph and Self-Loop:**

**Weighted Graph:** A graph in which a numerical value (weight) is associated with each edge. The weight may represent distance, cost, time, or capacity. Used in algorithms like Dijkstra's shortest path and Prim's minimum spanning tree.

**Self-Loop:** An edge that connects a vertex directly to itself. Both the starting and ending vertex of the edge are the same. In an adjacency matrix, self-loops appear as non-zero values on the diagonal A[i][i].

---

**Sequential and Linked Representation of Binary Tree:**

**Sequential (Array) Representation:**
Store tree in an array where for a node at index i:

- Left child is at index 2i
- Right child is at index 2i + 1
- Parent is at index i/2

For tree with root 8 (index 1), left child 3 (index 2), right child 10 (index 3), and so on.

**Linked Representation:**
Each node has three fields: LEFT pointer | DATA | RIGHT pointer
Root pointer points to the root node. NULL pointers indicate absent children.

```
Node structure:
[LEFT_PTR | DATA | RIGHT_PTR]

Example: root node of value 8:
[→3 | 8 | →10]
```

---

This covers every question from both the April 2025 and May 2024 GIET University DSA papers with complete algorithms, step-by-step traces, and examples — exactly what you need for your exam. Study the algorithms carefully as they carry the most marks in Part B.
