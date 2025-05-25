Ex. No: 18E - Count the Number of Triangles in an Undirected Graph

AIM:
To write a Python program to **count the number of triangles** present in an **undirected graph** using matrix operations.

ALGORITHM:
Input the adjacency matrix A of the graph (must be symmetric for undirected graphs).

Compute matrix multiplication:
A2 = A × A
A3 = A2 × A

Compute the trace of A3 (sum of diagonal elements).

Divide the trace by 6 to get the number of triangles.



PYTHON PROGRAM
```
import numpy as np

def count_triangles(adj_matrix):
    # Step 1: Convert to numpy array for matrix operations
    A = np.array(adj_matrix)

    # Step 2: Compute A^3
    A2 = np.matmul(A, A)
    A3 = np.matmul(A2, A)

    # Step 3: Trace of A^3
    trace = np.trace(A3)

    # Step 4: Each triangle is counted 6 times
    return trace // 6

# Example: Undirected graph with 4 vertices and 2 triangles
adj_matrix = [
    [0, 1, 1, 0],
    [1, 0, 1, 1],
    [1, 1, 0, 1],
    [0, 1, 1, 0]
]

print("Number of triangles:", count_triangles(adj_matrix))

```

OUTPUT
![image](https://github.com/user-attachments/assets/406415a2-7128-4fc0-a6ce-8b9af6c7141f)


RESULT
Thus,a Python program to **count the number of triangles** present in an **undirected graph** using matrix operations was successfully implemented and verified.
