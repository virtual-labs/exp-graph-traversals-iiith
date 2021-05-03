

    Suppose that G is a directed graph with a vertex u with both a nonzero indegree and a nonzero outdegree. Can u end up in a DFS tree containing only itself? Justify your answer.
    Take an example directed graph of about 12 vertices and 20 edges. Perform DFS on the graph and record the discovery and finish time of each vertex.
    Repeat the above question with respect to BFS.
    Suppose that G is a directed graph and (u,v) is an edge in the graph. Is it true that the finish time of u is always larger than the finish time of v?
    Consider a directed graph G with an edge (u,v). Suppose that there is no path from v to u in G. Is it true that the finish time of u is always larger than the finish time of v?
    Consider the setting of the above question. Suppose now that C and C' are two subsets of vertices so that there is a path between every vertex in C (C') to every other vertex in C (C'), and there is an edge (u,v) with u in C and v in C'. Suppose also that there is no path from any vertex in C' to any vertex in C. Is it true that any vertex in C has a finish time larger than any vertex in C'? Justify your answer.
    Let G be an undirected graph and we apply BFS on G. Classify the edges of G as tree edges, back edges, forward edges, and cross edges. Are any of these classes empty? If so, why?
    Let G be an undirected graph. Use DFS on G to partition the vertices of G into subsets V1, V2, ..., so that two vertices u and v are in the same partition if and only if there is a path between u to v. Such subsets are called as the connected components of G.
    Let G have k connected components. How would k change if one edge is added to G? How would k change if one edge is removed from G.
    Consider the problem of arranging the vertices of a directed acyclic graph so that if (u,v) is an edge in the graph then $u$ appears before $v$ in the arragenment. Such an arrangement is called as a topological sorting of the graph. Design an algorithm using DFS to obtain a topological sort of a given directed acyclic graph. What is the runtime of your algorithm.
    Repeat the above question with using BFS instead of DFS. Is there any difference in the runtime? Which approach do you prefer and why?


