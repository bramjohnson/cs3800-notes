---
slides: "[[7.NPReductionsCompleteness.pdf]]"
---
# Reductions
Consider two languages $A,B$.
## Oracle Solution
$A$ reduces to $B$ in poly-time
	Construct a poly-time decider $D_A$ for $A$ 
	using a hypothetical poly-time decider $D_B$ for $B$ as a subroutine.

If $A$ reduces to $B$ in poly-time and $B \in P$, then $A \in P$.
If $A$ reduces to $B$ in poly-time and $A \notin P$, then $B \notin P$.
## Mapping Solution
$A$ reduces to $B$ in poly-time
	There is a poly-time *converter* $R_{A,B}$
	$R_{A,B}$ converts an input $w_A$ and converts it to $w_B$
	such that $w_B \in B \Leftrightarrow w_A \in A$.

$D_A(w_A) = D_B(R_{A,B}(w_A))$
	Can create decider for $A$ using decider for $B$ where you convert input to $A$ to input to $B$.

Mapping is *transitive*.
# NP-Completeness
A language $A$ is **NP-Complete** if
	$A \in NP$
	$\forall B \in NP: B$ is reducible to $A$.

By the *Cook-Levin* theorem, the [[2023-10-26 Complete Problems#Boolean Satisfiability|SAT]] problem is NP-complete.
## 3SAT
3NF formula has exactly 3 literals in each clause.
We want to reduce the SAT problem to the 3SAT problem by
	Convert CNF formula into a 3CNF formula such that
	if the original is satisfiable, so is the 3CNF formula
### Reduction
Two cases, less than 3 literals in a clause or more than 3 literals in a clause
1. if $C_i > 3$ literals, break it up into two smaller clauses
	$x \vee \neg y \vee z \vee y = (x \vee \neg y \vee w) \wedge (Z \vee u \vee \neg w)$ by introducing new literal w
	w does not matter because one of the original clauses can still be satisfied.
	This process happens recursively until $C_i == 3$ literals 
2. if $C_i < 3$ literals, pad it by repeating
	$x \vee \neg y = (x \vee \neg y \vee \neg y)$
## CLIQUE
Graph $G$ and target $t$, does graph $G$ have $t$-clique?
Want to reduce 3SAT to CLIQUE in polynomial time!
### Reduction
Given a list of 3 literal clauses, make every literal into a node and connect each node except:
	Nodes in the same clause
	Nodes that create contradictions ($z \wedge \neg z$)
If there is a configuration of literals that satisfies the formula, there will be a clique with target size = number of clauses.
## SUBSET-SUM
Set $S$ and target $t$, does subset of $S$ exist that sums to $t$?
Want to reduce 3SAT to SUBSET-SUM in polynomial time.
### Reduction
3 variables + 3 clauses = 6 digits for each number
	Two numbers for each variable $v$ in formula
	First number corresponds to $v$ being true, and second corresponds to $v$ being false.
For the formula: $(x \vee y \vee z) \wedge (\neg x \vee \neg y \vee z) \wedge (x \vee y \vee \neg z)$

| x   | y   | z   | $c_1$ | $c_2$ | $c_3$ |
| --- | --- | --- | ----- | ----- | ----- |
| 1   | 0   | 0   | 1     | 0     | 1     |
| 1   | 0   | 0   | 0     | 1     | 0     |
| 0   | 1   | 0   | 1     | 0     | 1     |
| 0   | 1   | 0   | 0     | 1     | 0     |
| 0   | 0   | 1   | 1     | 1     | 0     |
| 0   | 0   | 1   | 0     | 0     | 1      |

For each clause, also make table:

| x   | y   | z   | $c_1$ | $c_2$ | $c_3$ |
| --- | --- | --- | ----- | ----- | ----- |
| 0   | 0   | 0   | 1     | 0     | 0     |
| 0   | 0   | 0   | 1     | 0     | 0     |
| 0   | 0   | 0   | 0     | 1     | 0     |
| 0   | 0   | 0   | 0     | 1     | 0     |
| 0   | 0   | 0   | 0     | 0     | 1     |
| 0   | 0   | 0   | 0     | 0     | 1     |

Our target:
$t$ = 1 1 1 3 3 3
## 3COLOR
A 3-coloring of a graph colors each node using at most 3 colors
Want to reduce 3SAT to 3COLOR

Use some insanely cool "widgets" made out of nodes and connections to create boolean logic.
## Hamiltonian Path
Graph $G$ with path from $s$ to $t$ that goes through every node of $G$ exactly once.
	[Cool application for snake](https://www.youtube.com/watch?v=TOpBcfbAgPg)
Want to reduce 3SAT to HAMPATH 🍔

[Really good diagram of the process](https://opendsa-server.cs.vt.edu/ODSA/Books/Everything/html/threeSAT_to_hamiltonianCycle.html)
Create a new graph using variables from statement and clause nodes

![[Pasted image 20231106120516.png]]
Here each row is for the different variables.
## Traveling Salesman Problem
Same as Hamiltonian path but edges have lengths and must visit under $t$ budget.
## Knapsack Problem
Same as subset-sum but with weights
