---
slides: "[[3.regex.pdf]]"
---
# Regular Operations
The **regular operations** are: *union, concatenation, star*.
Useful for building regular languages from simple ones.
# Regular Expressions
Notation for specifying regular languages using regular operations.

**Atomic** expressions: $\emptyset$, $\epsilon$, symbols from $\sum$.
**Operations** \*, $\circ$, $\cup$.
	Order of operations in same order as above.
**Other Notation**: $R^+$ (1+ copies of $R$); $R^n$ ($n$ concatenations of $R$)

## Examples
01 $\cup$ 10
	$L = \{01, 10\}$
$0^*$
	$L =$ language with all 0s
$\Sigma ^*$
	$L =$ all strings
$\Sigma ^ * 1 \Sigma ^ *$
	$L =$ string must contain a $1$
$0^*10^*$
	$L =$ exactly one $1$
$\Sigma ^ * 010 \Sigma ^ *$
	$L =$ contains $010$
$\emptyset ^ *$
	$L =$ $\{\epsilon\}$ (Because you can take no strings at all)
$\Sigma \Sigma$
	$L =$ strings of length 2
$(\Sigma \Sigma) ^ *$
	$L =$ strings of even length
## Anti-Examples
$L =$ contain 00 and 11 as substrings
	$\Sigma ^ * 00 \Sigma ^ * 11 \Sigma ^ *$ $\cup$ $\Sigma ^ * 11 \Sigma ^ * 00 \Sigma ^ *$
$L =$ starts and ends with same symbol
	$1 \Sigma ^ * 1$ $\cup$ $0 \Sigma ^ * 0$ $\cup$ $\epsilon$ $\cup$ $\Sigma$
# Regular Languages
**Theorem:** A language **A** is regular if and only if there is a regular expression $R$ such that $A = L(R)$.
## Generalized NFA
Transitions labeled with regular expressions.
	Follow transition by reading a matching block of input symbols.

## Simple Form
Can convert any GNFA into a *simple form*.
- Accept state is unique & no transitions out
- No transitions entering the start state
- At most 1 transition between each pair of states.
# DFA to Regular Expression
1. Start with DFA **D** that recognizes regular language **A**
2. Convert it into a GNFA **G** that has "simple form". 
3. Remove intermediate states of **G** one at a time without changing which language it recognizes.
	For each pair of states, $q_i$ and $q_j$ connected through $q_{kill}$, add a transition that includes all conditions of $q_{kill}$ in the regular expression.
4. At the end, you have one transition that corresponds to the regular expression.
