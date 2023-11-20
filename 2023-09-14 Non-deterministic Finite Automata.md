---
slides: "[[2.automata.pdf]]"
cssclasses:
  - no-scrollbar
---
# Non-deterministic Finite Automata
Need option for multiple inferred "next states" to solve some problems.
Defined as *Non-deterministic Finite Automata (NFA)*.
[[2023-09-11 Regular Languages & Closures#Finite Automata|Standard automata]] defined as: *Deterministic Finite Automata (DFA)*.
**Theorem:** We can always convert NFA to DFA.
## Syntax
Transitions can now *also* be labeled with $\epsilon$.
	Computation can take these transitions with no input.
	Effectively branching computation.
States can have arbitrary outgoing transitions with each symbol.
## Visualization
![[2.automata.pdf#page=37#toolbar=0&navpanes=0&scrollbar=0]]
## Definition
$M = (Q, \sum, \delta, q_{start}, F)$ where:
	$Q$ is a finite set called the *states*.
	$\sum$ is a finite set called the *alphabet*.
	$\delta: Q\times (\sum \cup \{\epsilon\})\rightarrow Powerset(Q)$ is a *transition function*.
		Input: state, alphabet symbol or $\epsilon$
		Output: set of states.
	$q_{start} \in Q$ is the *start state*.
	$F$ is the set of *accept states*.

The **$\epsilon$-closure** of a state *q* is the set of epsilon-transitions.
The **extended transition function** is the set of states reachable.
NFA *accepts* a string if it is possible to reach an accept state.
The *language* is defined the same as *DFA*.
# NFA to DFA
For any NFA **N** there exists a DFA **D** such that $L(D) = L(N)$.
This allows us to prove all the regular language [[2023-09-11 Regular Languages & Closures#Closure|closure properties.]]

Idea: DFA with states that correspond to subsets of NFA states.
	NFA states = Powerset(Q) DFA states.
DFA states correspond to how many states you could reach in the NFA.
## Example
![[2.automata.pdf#page=63]]

## Proof
**Lemma:** For all w in alphabet, there is a DFA that correlates to the NFA.
	Proof by induction (over $w_0...w_n$)
	Base case: empty string should be epsilon closure of NFA, which is what we define the start state of DFA to be.
	Induction: Assume holds for $n-1$.
		Definition of NFA shows that we go from any n-1 to any n.
		Inductive replacement to replace NFA from n-1 to DFA from n-1.
		Definition of DFA transition function allows substitution into that function.
**Theorem:** For all $w \in \sum ^*$: N accepts w $\Leftrightarrow$  D accepts w.
**Corollary**: $L(N) = L(D)$.
