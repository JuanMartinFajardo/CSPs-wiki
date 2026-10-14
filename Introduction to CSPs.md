Back to [[CSP]]

A Constraint Satisfaction Problem is a **decision** problem on the existence of an object in certain domain that satisfies certain constraints.
#### Examples
1. Graph coloring:
   Given a graph $H$, we can say a graph $G$ is $H$-colorable if there is a graph morphism $G\rightarrow H$. We have to assign each vertex of $G$ to a vertex of $H$ subject to the constraint that the image of the edge between to vertices goes to the edge between to images. Note that for the classical situation of $k$-coloring, the problem consists on finding a homomorphism $G\rightarrow K_k$. Where $K_k$ is just the complete graph of $k$ vertices.
2. Schedule problem:
   Imagine we need to have 3 meetings and only have two slots. And we have two constraints: meeting 1 and meeting 2 need to be at different times, and meeting 3 need to be no sooner than meeting 2.
3. SAT:
4. Inequations/equations: 

### Definition 1. Homomorphism problem of relational structures

**Definition:** A _relational structure_ is a tuple $(A,R_1^A, R_2^A, \ldots, R_n^A$) , where $A$ is a finite set, and $R^A_k\subseteq A^{p_k}$, where $p_k$ is called the _arity_ of the relational symbol $R_k$.


Whenever we compare relational structures, we fix the symbols $R_1, \ldots R_n$. We just write $R$ to shorten notation. 


**Definition**: Given two relational structures $(A,R^A)$, and $(B,R^B)$ a morphism $(A,R^A)\rightarrow (B, R^B)$ is a set function $A\rightarrow B$ together with functions $R^A_k\rightarrow R^B_k$ that factor through the map $A\rightarrow B$ via the projections to $A$ a and B, for every k.
Namely, there is a map $f:A\rightarrow B$ and for every $1\leq k \leq n$ there is a map $f_k\colon R^A_k\rightarrow R^B_k$ such that the following diagram commutes
$$ \begin{CD} R^A @>f_k>> R^B \\ @V \pi_i V V @VV \pi_i V \\ A @>>f> B \end{CD} $$
for all $1\geq i\geq p_i$. 

**Definition**: Given two relational structures $(A,R^A)$, and $(B,R^B)$ the _Constraint Satisfaction Problem_ (or homomorphism problem) associated to them is the decision problem of deciding on the existence of a morphism $(A,R^A)\rightarrow (B, R^B)$. The relational structure $B$ is called the _template_ and $A$ is called an _instance_.
###### Example 1. Graph coloring:
We can regard a graph $G=(E,V)$ as a relational structure whose domain is $V$ and relations are just the pairs $E\subset V\times V$ that correspond to an edge.
###### Example 2. Schedule problem:
The meeting-schedule problem described above can be regarded as homomorphism $A\rightarrow B$ where $A=\{x_1,x_2,x_3\}$ is the set of variables, $B=\{1,2\}$ is the domain of the variables (the two time-slots). The two constraints can be given as follows: if there is an assignment $f\colon A\rightarrow B$, it must verify $f(x_1)\neq f(x_2)$ and $f(x_3)\geq f(x_2)$. To formalize this, we can define two relations $R_{\neq}$ and $R_{\geq}$, such that
$$
R^A_{\neq}=\{(x_1,x_2)\}\subset A^2, \quad\quad R^B_{\neq}=\{(1,2),(2,1)\}\subset B^2 
$$
$$
R^A_{\geq}=\{(x_3,x_2)\}\subset A^2, \quad\quad R^B_{\geq}=\{(2,2),(2,1)\}\subset B^2 
$$
##### Example 3. SAT


### Definition 2. Combinatorial CSP definition

**Definition**: A (Combinatorial) Constraint Satisfaction Problem consists on, given the following data
1. A finite set of _variables_: $v_1, \ldots,v_n$
2. with respective _domains_: $D_1, \ldots, D_n$ (finite sets)
3. And _constraints_ $C_1, \ldots, C_m$. Where every constraint is of the form $\{(v_{i_1}, \ldots v_{i_k}),  R\subseteq D_{i_1}\times \ldots\times D_{i_k}\}$. The tuple $(v_{i_1}, \ldots v_{i_k})$ is called the _scope_ of the restriction.
Decide whether there is a valuation of the variables so that all the constraints are satisfied.

###### Graph coloring:
Easy exercise
##### Schedule problem
Easy exercise



### Definition 3. Definition as a finite copresheaf
**Definition**: A _finite copresheaf_ is a functor $S\rightarrow \textup{Fin}$, where $S$ is a finite category and $\textup{Fin}$ is the category of finite sets.

**Definition**: A _Constraint Satisfaction Problem_ consists on, given a finite copresheaf $D\colon S\rightarrow \textup{Fin}$, decide whether $\lim F$ is empty or not.

###### Example 1. Graph coloring:
We can regard a graph $G$ as a functor $F_G\colon Q\rightarrow \textup{Fin}$.
Where $Q=\{e \rightrightarrows v\}$ is the category with two objects and two non trivial maps $s,t\colon e\rightarrow v$.
So, given two graphs $G,H$, $\hom(G,H)\simeq \textup{Nat}(F_G,F_H)$. But we just call the latter $\textup{Nat}(G,H)$.
Note that there is a functor (the Grothendieck construction) $\pi_G\colon \int G\rightarrow Q$. Then the composition
$$
F_{G,H}\colon\int G\xrightarrow{\pi_G}Q\xrightarrow{H}\textup{Fin}.
$$
is a finite copresheaf.

**Proposition:** There is a natural isomorphism $\textup{Nat}(G,H)\xrightarrow{\simeq} \lim F_{G,H}$.
**Proof**: Apply lLemma 3.11
###### Example 2. Schedule problem
Exercise


## Equivalences of definitions

### Definition 1 -> Definition 2
Given $(A,R_1^A, \ldots R_n^A)$ and $(B,R_1^B, \ldots R_n^B)$ two relational structures, we can define a CSP.
The set of variables is $A$.
The domain of each variable is $B$.
A constraint is a tuple $(R^A_k,R^B_k)$

Then one can check that the existence of a morphism of relational structures $(A,R_1^A, \ldots R_n^A)\rightarrow(B,R_1^B, \ldots R_n^B)$  is equivalent to the existence of a solution to the associated combinatorial CSP.
### Definition 2 -> Definition 1
Given a combinatorial CSP with variables $X$, domain $D$ (we can assume that all the variables have the same domain) and constraints $C$, we built two relational structures.

Fix the following notation for a constraint $C_i=(S_i,R_i\subseteq D^{k_i})$. Say $m=|C|$.
Call the define the template as  $$B=(D,(R_j^{B})_{j=1,\ldots, m})$$
for $R^B_j:=R_j.$
And define the instance as
$$
A=(X, (R^A_j)_{j=1,\ldots m})
$$
with $R_j^A=\{S_i: (S_i, R_j)\in C\}$.

With this definition, one can verify that the original combinatorial CSP has a solution if and only if there is a morphism of relational structures $A\rightarrow B$.
### Definition 1 -> Definition 3
We can get inspiration from Example 1 in Definition 3. We can regard any relational structure $A=(A,R^A_1, \ldots, R^A_n)$ as a functor $F_A\colon Q_A\rightarrow \textup{Fin}$, where $Q_A$ is the category whose objects are
$\{A, R_1^A,\ldots , R^A_n\}$, (whose image under $F_A$ goes to the set with the same name) the only non trivial morphisms are $\hom(R^A_k,A)=\{p_1,\ldots, p_k\}$ which are mapped to the projections $p_i\colon R_k^A\rightarrow A$ in $\textup{Fin}$.
There is a fully faithful embedding $\textup{RelS}\hookrightarrow \textup{FinCoPSh}$.

Given two relational structures $A,B\colon Q\rightarrow \textup{Fin}$, we consider the following composition
$$
F_{A,B}\colon \int A\xrightarrow{\pi_{A}} Q \xrightarrow{B}\textup{Fin}.
$$

**Proposition**:  There is a natural isomorphism $\textup{Nat}(A,B)\xrightarrow{\simeq} \lim F_{A,B}$.
**Proof**: Apply Lemma 3.11

### Definition 3 -> Definition 1




**Lemma 3.11:** Given two finite copresheaves $G,H\colon S\rightarrow \textup{Fin}$, there is a natural bijection
$$
Hom(G,H)\simeq \lim (H\circ \pi_G)
$$
where $\pi_G$ is the Grothendieck construction of $G$.

**Proof**: Write later

