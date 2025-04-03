# Graph-Data-Structure
In C++, graphs are non-linear data structures that are used to represent the relationships between various objects. A graph is defined as a collection of vertices and edges. In this article, we will learn how to implement the graph data structure in C++.

## Implementation of Graph Data Structure in C++
There are two primary ways to implement or represent graph data structures in C++:

1. Using Adjacency Matrix
2. Using Adjacency List


# Adjacency Matrix Representation of Graph in C++
An adjacency matrix is a square matrix (2D vector in C++) used to represent a finite graph. It provides a straightforward way to describe the relationships between nodes (vertices) in a graph.

## Rules to Create Adjacency Matrix of a Graph
- Create an n x n 2d vector named matrix, where n is the number of vertices, with all entries initialized to 0.
- For an undirected graph, set both matrix[i][j] and matrix[j][i] to 1 if there is an edge between vertices i and j.
- For a directed graph, set matrix[i][j] to 1 if there is an edge from vertex i to vertex j.
- For a weighted graph, set matrix[i][j] to the weight of the edge between vertices i and j.
- If there is a self-loop on vertex i, set matrix[i][i] to 1 (or the weight if weighted).

#From the above rules, we can create the adjacency matrix:

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240613161501/graph-in-cpp.webp">

# Program:
```
// C++ Program to Implement a Graph Using Adjacency Matrix
#include <iostream>
#include <vector>
using namespace std;

class Graph {
    // Adjacency matrix to store graph edges
    vector<vector<int> > adj_matrix;

public:
    // Constructor to initialize the graph with 'n' vertices
    Graph(int n)
    {
        adj_matrix
            = vector<vector<int> >(n, vector<int>(n, 0));
    }

    // Function to add an edge between vertices 'u' and 'v'
    // of the graph
    void add_edge(int u, int v)
    {
        // Set edge from u to v
        adj_matrix[u][v] = 1;
        // Set edge from v to u (for undirected graph)
        adj_matrix[v][u] = 1;
    }

    // Function to print the adjacency matrix representation
    // of the graph
    void print()
    {
        // Get the number of vertices
        cout << "Adjacency Matrix for the Graph: " << endl;
        int n = adj_matrix.size();
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                cout << adj_matrix[i][j] << " ";
            }
            cout << endl;
        }
    }
};

int main()
{
    // Number of vertices
    int n = 4;
    // Create a graph with 4 vertices
    Graph g(n);

    // Adding the specified edges in the graph
    g.add_edge(0, 1);
    g.add_edge(0, 2);
    g.add_edge(1, 3);
    g.add_edge(2, 3);

    // Print the adjacency matrix representation of the
    // graph
    g.print();
    return 0;
}
```
# Output
```
Adjacency Matrix for the Graph: 
0 1 1 0 
1 0 0 1 
1 0 0 1 
0 1 1 0
```
Time Complexity: O(V^2), where V is the number of vertices in the graph.
<br>
Auxiliary Space: O(V^2)


