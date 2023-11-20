---
parent: "[[CS3800 - Hub]]"
slides: "[[1.intro.pdf]]"
---
# Proofs
## Definition
### Formal
Write down axioms (base)
Steps that follow each other (using logical inference)
### For this class
Proofs "by humans, for humans".
	Use full English sentences. Be clear, precise, and concise.
## Types
- **Construction**: build a solution; does it exist.
- **Contradiction**: Assume the statement is false; derive contradiction.
- **Induction**: Show for base, show for increments. 
# Boolean Logic
# Sets
# Strings
Let $\sum$ be a finite set, called the *alphabet*. The elements of $\sum$ are called *symbols*.
The *strings over* $\sum$ are tuples
*Empty string* is denoted by $\epsilon$

$\sum^* = \sum^1 \cup \sum^2 \cup ...$ 
$\sum^0$ = {$\epsilon$}
# Functions
$f : D \rightarrow R$ is a *function* with *domain* **D**, *range* **R**.

Focus of this class will be on computing functions with:
	Domain over *alphabet*
	Range over *boolean*
## Languages
A *language* **L** over an alphabet $\sum$ is a subset of $\sum^*$.
	A language may be finite or infinite.
	Simply a subset of strings
*Language* can be defined as function: $L = \{w : f(w) = true\}$
	If a string is accepted, it's a part of the language.
	Computing $f(w)$ is deciding if $\in$ some language $L$. 