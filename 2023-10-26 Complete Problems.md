---
slides: "[[6.PandNP.pdf]]"
---
# Run Time
Using asymptotic notation $g(n) = O(f(n))$
## Polynomial Time
$g(n) = poly(n)$ if $g(n) = n^c$

Class $P$ is languages that can be decided in *polynomial* time.
	These are the languages that can be decided "efficiently".
# Languages not in P
Undecidable languages are not in $P$.
Some languages **are** decidable but are not in $P$
## Brute-Force Search & [[2023-10-26 Complete Problems#NP|NP]]
Below problems can be solved inefficiently via "brute-force search".
Verifying if a solution is good can be done efficiently.
### Boolean Satisfiability
A boolean formula consists of variables (true or false) and connectives (and, or, not). We want to know if there is a true combination of the formula. There is no efficient way, and a brute-force search must be used.
### CLIQUE
A graph G with undirected edges.
A k-clique is a set of k nodes that are all directly connected.
Decidable using brute-force
### Subset-Sum
For a list of numbers, see if any subset sums to $t$.
	Decidable using brute-force
# NP
Can efficiently verify if $w \in L$ given some additional polynomial-size "certificate" y as a *hint*.
There is a poly-time TM $V$ (verifier) such that:
- $w \in L \Rightarrow \exists y:     V(w,y)$ accepts
- $w \notin L \Rightarrow \forall y: V(w,y)$ rejects

With this definition, we can **brute-force** search.
	Try all values $y$ and check if $V(w,y)$ accepts any of them non-deterministically.
## Formal Definition
A poly-time verifier $V$ runs in polynomial time such that $t(n) = poly(n)$
	$\exists y: |y| \leq t(|w|) .. V(w,y)$ accepts
The string $y$ is a "certificate". It determines if $w$ can be efficiently verified.

$NP$ = $L$ for which there exists a *poly-time* verifier $V$ for $L$.
	You can check the solution in poly-time.
## P = NP Problem
No known $L \in NP$ where $L \notin P$.
But, also if $P = NP$ then verifying solutions is no harder than finding solutions.
Hmm.


