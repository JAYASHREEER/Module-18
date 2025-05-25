Ex. No: 18A - Prim's Minimum Spanning Tree (MST) Algorithm

AIM:
To write a Python program for **Prim's Minimum Spanning Tree (MST)** algorithm.

ALGORITHM:

Initialize a min-priority queue (min-heap).

Start from vertex 0:

Mark it as visited.

Add all its edges to the min-heap.

While the MST has fewer than V-1 edges:

Pop the smallest edge from the heap.

If it connects to an unvisited vertex:

Add the edge to the MST.

Mark the vertex as visited.

Add its unvisited neighbors to the heap.


PYTHON PROGRAM

```
# A Python program for Prim's Minimum Spanning Tree (MST) algorithm.
# The program is for adjacency matrix representation of the graph

import sys # Library for INT_MAX

class Graph():

	def __init__(self, vertices):
		self.V = vertices
		self.graph = [[0 for column in range(vertices)]
					for row in range(vertices)]

	# A utility function to print the constructed MST stored in parent[]
	def printMST(self, parent):
		print ("Edge   Weight")
		for i in range(1, self.V):
			print (parent[i], "-", i, "  ",self.graph[i][parent[i]])

	# A utility function to find the vertex with
	# minimum distance value, from the set of vertices
	# not yet included in shortest path tree
	def minKey(self, key, mstSet):

		# Initialize min value
		min = sys.maxsize

		for v in range(self.V):
			if key[v] < min and mstSet[v] == False:
				min = key[v]
				min_index = v

		return min_index

	# Function to construct and print MST for a graph
	# represented using adjacency matrix representation
	def primMST(self):

		# Key values used to pick minimum weight edge in cut
		key = [sys.maxsize] * self.V
		parent = [None] * self.V # Array to store constructed MST
		# Make key 0 so that this vertex is picked as first vertex
		key[0] = 0
		mstSet = [False] * self.V

		parent[0] = -1 # First node is always the root of

		for cout in range(self.V):

			u=self.minKey(key,mstSet)
			
			mstSet[u]=True
			for v in range(self.V):
			    if self.graph[u][v]>0 and mstSet[v]==False and key[v]>self.graph[u][v]:
			        key[v]=self.graph[u][v]
			        parent[v]=u
		self.printMST(parent)

g = Graph(5)
g.graph = [ [0, 2, 0, 6, 0],
			[2, 0, 3, 8, 5],
			[0, 3, 0, 0, 7],
			[6, 8, 0, 0, 9],
			[0, 5, 7, 9, 0]]

g.primMST();



```

OUTPUT
![image](https://github.com/user-attachments/assets/991552d5-5f63-4c45-8725-705628af2709)


RESULT
Thus, a Python program for **Prim's Minimum Spanning Tree (MST)** algorithm was successfully implemented and verified.



