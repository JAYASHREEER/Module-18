Ex. No: 18D - Travelling Salesman Problem (TSP)

AIM:
To write a Python program to find the shortest possible route that visits every city exactly once and returns to the starting point using the **Travelling Salesman Problem (TSP)** approach.

ALGORITHM:
Use a bitmask to represent the set of visited cities.

Define a recursive function tsp(mask, pos):

mask: bitmask of visited cities.

pos: current city.

Base case: if all cities are visited, return distance to the starting city.

For all unvisited cities, call tsp recursively and find the minimum cost.

Use memoization to store already computed results.



PYTHON PROGRAM

```
import sys

def tsp(dist):
    n = len(dist)
    memo = {}

    def visit(mask, pos):
        if (mask, pos) in memo:
            return memo[(mask, pos)]

        if mask == (1 << n) - 1:
            return dist[pos][0]  # return to start

        min_cost = sys.maxsize
        for city in range(n):
            if mask & (1 << city) == 0:
                new_cost = dist[pos][city] + visit(mask | (1 << city), city)
                min_cost = min(min_cost, new_cost)

        memo[(mask, pos)] = min_cost
        return min_cost

    return visit(1, 0)  # start from city 0 with only it visited

# Example distance matrix (4 cities)
dist_matrix = [
    [0, 10, 15, 20],
    [10, 0, 35, 25],
    [15, 35, 0, 30],
    [20, 25, 30, 0]
]

min_cost = tsp(dist_matrix)
print("Minimum cost of TSP tour:", min_cost)


```
OUTPUT


RESULT
Thus,a Python program to find the shortest possible route that visits every city exactly once and returns to the starting point using the **Travelling Salesman Problem (TSP)** approach  was successfully implemented and verified.

