### Breadth First Search (BFS)  

BFS is similar to level order traversal in a tree, where we visit vertices in a level by level order. We specify a starting vertex S and start visiting vertices of the graph G from the vertex S. As a general graph can have cycles, we may visit the same vertex more than once. To solve this, we also maintain the state of each vertex. A vertex can be in one of three states, VISITED, NOT_VISITED, IN_PROCESS. The basic idea of breadth first search is to find the least number of edges between S and any other vertex in G. Starting from S, we visit vertices of distance k before visiting any vertex of distance k+1. For that purpose, define ds(v) to be the least number of edges between S and v in G. So, for vertices v that are not reachable from S we can have ds(v) = ∞. We can use a queue to store vertices in progress.  

We also a maintain from[u] for each of the vertex u, which denotes the vertex that discovered u. This information can be used to define the predecessor subgraph of G, which has all edges (from[u],u). These edges are called as tree edges. For a tree edge (u, v), ds(v) = ds(u) + 1. All other edges are called non-tree edges and are further classified as back edges and cross edges. A non-tree edge (u, v) is called as a back edge if ds(v) < ds(u), meaning u can be reached from S via v, but there is yet another shortest path through path u can be reached from S. An edge (u, v) is called a cross edge if d(v) ≤ d(u) + 1.  

Procedure BFS(G)  
for each v in V(G) do  
from[v] = NIL; state[v] = NOT_VISITED; d(v) = ∞  
end-for  

ds[S] = 0; state[S] = IN_PROCESS; from[s] = NIL;  
Q = EMPTY; Q.Enqueue(S);  

While Q is not empty do  
v = Q.Dequeue();  
for each neighbour w of v do  
if state[w] == NOT_VISITED then  
state[w] = IN_PROCESS; from[w] = v; ds[w] = ds[v] + 1; Q.Enqueue(w);  
end-if  
state[v] = VISITED  
end-for  
end-while  
End-BFS  
 
Runtime: Each vertex enters the queue at most once and each edge is considered only once. Therefore, runtime of BFS is O(m+n), where n is the number of vertices and m is the number of edges in G.  

### Depth First Search (DFS)  

The idea of DFS is to start from a specified start vertex S and explore from S as deep as possible. We go from S, to one of its neighbors x, to a neighbor of x, and so on. We stop when there are no new neighbors to explore from a given vertex. If all vertices are not visited, pick another start vertex from such vertices. We have to keep track of the state of a vertex and similar to BFS, a vertex can be in three states: VISITED, NOT_VISITED, IN_PROCESS. We also a maintain from[u], d[u], f[u] for each of the vertex u, which denotes the vertex that discovered u, the discovery time of u and the finish time u.  

Procedure Explore(v)  
d[v] = cur_time;  
cur_time = cur_time + 1;  
for each neighbor w of v  
if state(w) == NOT_VISITED then  
state(w) = IN_PROCESS;  
Explore(w);  
end-if  
end-for  
state(v) = VISITED;  
f[v] = cur_time;  
cur_time = cur_time + 1;  
End-Explore  

Procedure DFS(G)  
cur_time = 0  
for v = 1 to n do  
if state(v) == NOT_VISITED then  
state(v) = IN_PROCESS;  
Explore(v);  
end-if  
end-for  
End-DFS  
Runtime: Explore() is called for each vertex exactly once and each edge is considered only once. Therefore, runtime of DFS is O(m+n), where n is the number of vertices and m is the number of edges in G.  

**Classification of edges, based on Depth First traversal is as follows**

 - Tree Edges : All edges (from[u],u) are called as tree edges and define a dfs tree, a subgraph of G.  
    - An edge (u,v) is a tree edge if from[v] = u  

 - Back Edges : A non-tree edge (u, v) is called as a back edge if v is an ancestor of u in the dfs tree. u can be reached from v using tree edges, but there an edge from u to v also.  
    - An edge (u,v) is a back edge if [d(u), f(u)] is a subinterval of [d(v), f(v)]

 - Forward Edges : A non-tree edge (u, v) is called as a forward edge if v is a descendant of u in the dfs tree. v can be reached from u using tree edges, but there an edge from u to v also.
    - An edge (u,v) is a forward edge if [d(v), f(v)] is a subinterval of [d(u), f(u)].

 - Cross Edges : Non-tree edges (u, v) where u and v do not share any ancestor/descendant relationship are called cross edges.
    - An edge (u,v) is a cross edge if the two intervals [d(u), f(u)] and [d(v), f(v)] do not overlap.  

