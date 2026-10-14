Back to [[CSP]]

### Graphs and quivers

**Definition**: Graph. Category of graphs

**Definition**: Digraph. Gategory of digraphs

**Definition**: Multidigraph/Quiver


**Definition**: Two graphs (quivers) $G,H$ are _homomorphically equivalent_ if there are maps $G\rightarrow H$ and $H\rightarrow G$. We denote it by $G\leftrightarrows H$

**Lemma**: Assume $G\leftrightarrows G'$ and $H\leftrightarrows H'$ for quivers $G,G', H, H'$. Then $\hom(G,H)$ is empty if and only if $\hom(G',H')$ is empty.


We can regard a graph as a digraph by given two opposite directed edges for every non-directed edge.

**Corollary**: There is an fully faithful embedding of categories
$$
\textup{Graph}\hookrightarrow \textup{Quiver}
$$



### Relational Structures







#### Example (Example 2.4)
Consider the category $D=\{e\rightrightarrows v\}$
Consider the Yoneda embedding $$
\begin{matrix}
\lambda\colon & D^{\textup{op}} & \longrightarrow & \textup{Fun}(D,\textup{Fin})\\
& d & \mapsto & \hom(d,-)
\end{matrix}
 $$
 $\lambda(v)$ is the graph with one vertex
 $\lambda(e)$ is the graph with one directed edge (with vertices $s$ and $t$).
 The $\lambda(s)$ and $\lambda(t)$ are the maps sending the vertex $\lambda(v)$ to the vertices $s$ and $t$ respectively.

##### Corolary
$\textup{Fun}(D,\textup{Fin})$  is spanned by $\lambda(D^{\textup{op}})$ under finite colimits.
**Proof**

