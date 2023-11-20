---
slides: "[[5.undecidability.pdf]]"
---
# Unrecognizable Languages
$A_{TM} = <M, w> : M$ is a $TM$ and $M$ accepts $w$
	The universal $TM$ *recognizes* $A_{TM}$, therefore it is recognizable.

There are some languages that are not recognizable because they are uncountable.
	Complement $\overline{A_{TM}}$ is not recognizable because if it were, then $A_{TM}$ and $\overline{A_{TM}}$ would be decidable.
# Other Undecidable Languages
1. Post correspondence problem (PCP): arranging dominos
2. Number Theory: statements about natural numbers
3. Hilbert's 10th Problem: Does a polynomial have integer roots?
# Post Correspondence Problem
Input $P$ is a collection of pairs of strings as "dominos".
A **match** is a finite sequence of dominos in $P$ (**repeats allowed**)
	where the concatenation of the top row $t$ = concatenation of the bottom row $b$
Undecidable by brute force because there is no upper bound on repeats.
## Undecidability Proof
Show $A_{TM}$ is reducible to $PCP$. Assume match must start with first domino $t_1, b_1$.
$S(<M,w>)$:
	Construct PCP instance $P_{M,w}$ where a match corresponds to a computation history for $M$ on $w$.
$P_{M,w}:$
	$t_1 =$ "#", $b_1 = q_o, w_1, w_2, ..., w_n$ 
	Read the computation from the bottom row $b_1$ and put it on $t_2$
	Run $t_2$ on $M$ and output to $b_2$.
	Repeat until q accepts, then make top match bottom.
# Number Theory
Show $A_{TM}$ reduces to $NT$, where $NT$ is a statement in number theory.
Decider D for number theory where accepts if $M$ accepts $w$.
	Design way to encode TM computations as natural numbers $x$.
	Design a formula $x$ that represents an accepting computation of $M$ on $w$.
## Corollary
No "proof system" for **NT**.
	Soundness: No false statement has valid proof
	Completeness: Every true statement has valid proof
	Decidability: Can decide if proof is valid

If there were a proof system for **NT**, then it could decide **NT**.
## Godel's Proof
**QMS** - Quantified Mixed Statements (statement about natural numbers and strings)
A *computation history* of $M$ on $w$ is each state of the machine $M$.
	Represented by a string with states separated by $\#$
	$C_1$ is start configuration, $C_n$ is the accept configuration.
For any configuration $C_k$ where $i = \#$ and $j = \#$
	Ensure $C_{k+1}$ is a valid window when compared to $C_k$
Reduces to decidable, which proves undecidable.
## Unprovable Statement
Define $TM$, $M$ that does the following:
	1. Obtain it's own code $<M>$
	2. Construct statement $a$ = $R(<M, \epsilon>)$
	3. Let another statement $b = \overline{a}$
	4. Try all strings, if any is a valid proof of $b$, then accept.
