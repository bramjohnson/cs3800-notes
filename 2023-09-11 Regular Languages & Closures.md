---
slides: "[[2.automata.pdf]]"
cssclasses:
  - no-scrollbar
---
# Languages
A *language* **L** over an alphabet $\sum$ is a subset of $\sum^*$
	May be finite or infinite.

# Finite Automata
Computer with a *limited* number of states.
Consists of *states* and *transitions*.
	Transitions are labeled with symbols of alphabet $\sum$.
	For each state, there is **exactly one** outgoing transition labeled with each alphabet symbol.
Automata have a unique *start state* and *accept states*.
## Example 1
Language: $L(M) =$ {w | w ends with 1}
![[Pasted image 20230911121800.png|500]]
## Example 2
Language: $L(M) =$ {w | length of w is even}
![[Pasted image 20230911121952.png]]
## Defining Automata
Automata is visually described using a *state diagram*.
Can also use sets and functions to define automata.

*Definition*: a **Deterministic Finite Automaton** (DFA) consists of a tuple $M = (Q, \sum, \delta, q_{start}, F)$
	$Q$ is a finite set called the *states*
	$\sum$ is a finite set called the *alphabet*.
	$\delta$ is the transition function
		Input: State/Symbol
		Output: Next State
	$q_{start}$ is the *start state*.
	F is the set of *accept states*.
## Conversion Example
![[Pasted image 20230911125210.png]]
## Inductive Example
![[Pasted image 20230911125702.png]]

# Regular Languages
A *language* **L** is **regular** if there exists *some* finite automaton **M** that recognizes **L**.
## Irregular Language
Language where there are $n$ 0s followed by $n$ 1s.
	Impossible to define using finite automaton.
## Composing Regular Languages
Suppose $A$ and $B$ are *regular* languages.
The following operations produce other regular languages:
- $A \cup B$: Symbols in $A$ or $B$ (Union)
- $A \bullet B$: Combinations of $A$ and $B$ (Concatenation)
- $A^*$: All combinations of $A$; $n$ concatenations (Star)
- $\bar A$: Symbols not in A (Complement)
- $A \cap B$: Symbols in $A$ and $B$ (Intersection)
### Closure
Regular languages are *closed under* the above operations.
	Applying these operations produce regular languages.
### Complement
We can flip all accept/reject states to get $\bar A$ the complement of $A$
### Concatenation
Need to "infer" some things about input to create automata.
Must use [[2023-09-14 Non-deterministic Finite Automata|Non-deterministic Finite Automata (NFA)]].

Add epsilon between accepts of A and starts of B.
If first part is accepted in A, check if rest is accepted in B.
### Union
Using [[2023-09-14 Non-deterministic Finite Automata#NFA to DFA|NFA.]]
Add a start node with epsilon to A and B.
### Star
All accept states epsilon to start state.
Faux start/accept state to handle empty string.
### Intersection
Write in terms of complement and union (already proved) using De Morgan's law.