---
title: "Set Hash"
summary: "Explore the concept of set hashing to efficiently compare sets and handle multiple equality queries in constant time"
date: 2025-01-08T02:15:00+06:00
# tldr: "Wubba lubba dub dub"
tags: [Algorithms]
---

## Problem Description

### Input:
- An integer **K** representing the number of sets.
- An integer **M** representing the number of items in each set.
- A list of **K sets**, where each set contains **M integers**.
- An integer **Q** representing the number of queries.
- A list of **Q queries**, where each query is of the form `(i, j)` asking whether the **i-th** set is equal to the **j-th** set.

### Output:
- For each query, return `True` if the two sets are equal, otherwise return `False`.

### Constraints:
- \( 1 \leq K \leq 10^4 \)
- \( 1 \leq M \leq 10^3 \)
- \( 1 \leq Q \leq 10^4 \)
- Elements of each set are integers within the range \( 1 \leq \text{element} \leq 10^6 \).

---

## Brute-Force Solution

The brute-force solution involves directly comparing two sets for each query. This can be done using Python's set equality operator.

```python
# Input
K = 5  # Number of sets
M = 4  # Number of items per set
sets = [
    {1, 2, 3, 4},
    {4, 3, 2, 1},
    {5, 6, 7, 8},
    {1, 2, 3, 4},
    {9, 10, 11, 12}
]  # List of sets
Q = 3  # Number of queries
queries = [
    (0, 1),  # Compare set 0 with set 1
    (0, 3),  # Compare set 0 with set 3
    (2, 4)   # Compare set 2 with set 4
]

# Brute-force solution
results = []
for i, j in queries:
    # Compare sets[i] and sets[j] directly
    results.append(sets[i] == sets[j])

# Output results for each query
for query, result in zip(queries, results):
    print(f"Query {query}: {result}")
```

### Explanation:
1. **Input Parsing:**
   - The input includes \( K \) sets and \( Q \) queries.
2. **Direct Comparison:**
   - For each query `(i, j)`, use the equality operator (`==`) to check if `sets[i]` is equal to `sets[j]`.
3. **Output Results:**
   - Store the result (`True` or `False`) for each query and print them.

### Complexity Analysis:
- **Set Comparison:** Comparing two sets of size \( M \) takes \( O(M) \).
- **Overall Complexity:** For \( Q \) queries, the time complexity is: \( O(Q \times M) \)
- This can become inefficient for large \( Q \) and \( M \), motivating the need for an optimized solution using hashing.
