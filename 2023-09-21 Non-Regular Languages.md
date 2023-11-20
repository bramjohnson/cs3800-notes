---
slides: "[[3.regex.pdf]]"
---
# Non-Regular Languages
## Example
$L = \{0^n1^n : n \geq 0\}$

**Proof:** assume by contradiction that there is a DFA $M=(Q,\sum,\sigma,F)$ that recognizes $L$. Let $|Q| = p$.
	Let $r_k \in Q$ be the state $M$ reaches after reading $0^k$.
	After reading $i$ and $j$ 0s, where j greater than i, end up in the same state.
	This means $0^j1^i$ is in the language, which is a contradiction.

# Pumping Lemma
For some integer $p \geq 0$,
pick a string in the language of length $\geq p$.
For some contraints $x,y,z$ where $xy \leq p$ and $y > 0$,
pick an $i \geq 0$ if $xy^iz$ not in language.

## Example
Some $p \geq 0$
We pick string $0^p1^p$
Therefore, $y$ must be only 0s because it must be contained within the first half of the string.
We pick $i=0$, therefore we have removed some 0s from the string and the 0s and 1s are no longer the same.