# Interview - Technical / Coding

## Implementations - C++
### Strings
1. String can be made using `string a = "str"`
2. String length is found using `str.length()` or `str.size()`. Better remember `str.size()`
3. To test if string is empty, try `if (str.empty())`
4. String concatenation can happen with `operator+`
5. String find: to find use `str.find()` (string, char\* or char), will give position or if not found `string::npos`
6. String reverse find `str.rfind()`
 

## Graph
Two types:
- Undirected
- Directed

Generally triplet is used `(u,v,w)` for source, dest, and weight along with whether it is undirected or directory.

A tree is an `undirected, no cycle` graph

**Rooted trees**: Trees with designated root node.
When edges point away from the root the graph is called `arborescence (out tree)`, if edges point towards the root it is called `anti-arborescence (in-tree)`.

**DAG (Directed Acyclic Graph)**: DIrected graph without cycles.
All out trees are DAGs.

**Bipartite graphs**: A graph which is two colorable. 

**Complete graph**: where there is one explicit edge between every pair of nodes. Denoted by `K(c)` eg. `K1`, `K2` etc.

Two ways to represent graphs:
1. Adjecency matrix
2. Adjecency list

One other way is edge list in form of `(u,v,w)`. Lacks structure and not used frequently

### Common graph theory problems
Before going in the problem check for:
1. dir / undir graph
2. edge weight yes / no
3. sparse / dense
4. adj mat / adj list

**Problems**
1. Shortest path problem
```
- BFS (unweighted graph)
- Djikstra
- Bellman Ford
- Floyd Warshall
- A*
etc
```

2. Connectivity
```
- Union find data structure
- search algo (eg DFS)
```

3. Negative cycles
```
- Bellman Ford
- Floyd warshall
```

4. Strongly connected components ( connectivity for directed graphs )
```
- Tarjan's algo
- Kosaraju's algo
```

5. TSP problem
```
- Held Karp
- Branch and bound
more appx algos
```

6. Finding the bridges ( edges if removed increase the number of connected components )

7. Articulation points (bridges but now vertices)

8. Minimum spanning tree (MST)
```
- Kruskal
- Prims
- Boruvka
```

9. Max flow
```
- Ford fulkerson
- Edmonds- Karp
- Dinic algo
```

### Depth first search
- Easy to code
- Time complexity `O(V+E)`

You can do connectivity problem solution by DFS on `[0, n)` labelling all the unvisited nodes with colors and DFS for that.

What else can DFS do
- Graph MST
- Find cycles in graph
- Check if graph is bipartite
- Find strongly connected components
- Topologically sort the nodes of a graph
- Find bridges and articulation points
- Find augmenting paths in flow network
- Generate mazes

### Breadth first search
- Easy to code (similar to DFS)
- Time complexity `O(V+E)`

