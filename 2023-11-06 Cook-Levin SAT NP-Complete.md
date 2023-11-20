---
slides: "[[7.NPReductionsCompleteness.pdf]]"
---
# Cook-Levin
Every $L \in NP$ can be poly-time reduced to [[2023-10-26 Complete Problems#Boolean Satisfiability|SAT]].
	SAT is NP-Complete therefore we can reduce to it.
## Proof
**Lemma**: for every function $f: \{0,1\}^m \rightarrow \{0,1\}$ there is an equivalent CNF formula.
For each *value* that makes $f$ evaluate to 0, add a clause to ensure variables can't take that value.

We know the following about the description of the Turing Machine
	$w \in L$ such that $\exists y : V(w, y)$ accepts
	$\exists$ configurations $C_1, C_2, C_3, ... C_t$
	$C_1 = q_0w,y$ is start config
	$C_t$ is accepting config
	$\forall i < t: C_i$ yields $C_{i+1}$

Want to reduce language $L$ to $SET$
Converter $R$ that maps strings $w$ to sections of $C_i$ and $C_{i+1}$
![[7.NPReductionsCompleteness.pdf#page=23]]
We can define some formula that checks the window created by $R$ and checks if they represent a valid window.
	Because formula is constant check (3x2), it is a CNF by the Lemma.
# Decision vs Search
All previous problems have been *decision* problems:
	*decide* if a formula is satisfiable
Solving *search* problems in poly-time would also be useful:
	*find* a satisfying assignment
## Theorem
If $P=NP$ then every $NP$-search problem can be solved in poly-time

Here is an example of a search algorithm for the SAT problem.
$SEARCH-SAT(𝜑)$:
	For every variable x in 𝜑:
		Check if 𝜑 ^ x is satisfiable
		If it is, set x = true
		If not, set x = false
## Theorem (Generalized)
If $P=NP$ then every $NP$-search problem can be solved in poly-time

Fix an $NP$ language $L$ with a verifier $V$.
	Want to find $y$ such that $V(w,y)$ accepts, where $w \in L$
	Find $y$ one bit at a time.

Let $L_p = \{<w,y_p>: \exists y_s | V(w, y_p y_s)$ accepts\}
	Where $y_p$ is the certificate prefix and $y_s$ is the certificate suffix
(If there is a prefix of a certificate, we can find a suffix to complete that certificate)
$L_p$ is in $NP$ so if $P=NP$ we have a poly-time decider $D_p$ for it.

$SEARCH(w):$
	Set $y_p = \epsilon$
	For each bit $i = 1, ..., p(|w|)$
		If $D_p(<w, y_p + 0>$ accepts, set $y_p = y_p + 0$
		Otherwise $y_p = y_p + 1$
	Output $y_p$
# Beyond NP
## UNSAT
$UNSAT = \{<\phi>: \phi$ is an unsatisfiable formula\}
	$UNSAT$ is the complement of $SAT$. We don't know if it is in $NP$ but most believe it isn't because it doesn't have a certificate.
## CoNP
$coNP$ = set of all $\overline{L}$ for $L \in NP$
## Harder than NP
Problems beyond $NP \cup coNP$:
	$MAX$-$CLIQUE = \{<G,t>:$ the largest clique in $G$ has size $t\}$
	$MIN$-$FORMULA = \{<\phi>:$ no shorter formula is equivalent to $\phi\}$
### Polynomial Hierarchy
A language $L$ is in $PH$ if there is some number $k$ and a poly-time "PH Verifier" $V_k$ such that:
	$w \in L \Leftrightarrow \forall y_1 \exists y_2 \forall y_3 ... \exists y_k | V(w,y_1...y_k)$ accepts
	Translation: for each $y_1$ formula, there exists a $y_2$ set of truth assignments that satisfies $w$

This class of languages is a generalization of $NP$ and $coNP$
	$NP$ = single $\exists$ quantifier
	$coNP$ = single $\forall$ quantifier
#### Theorem
If $P=NP$ then $PH = P$

Suppose $L \in PH$ with "PH Verifier" $V_k$ (and $k$ is even).
For any $w, y_1, y_2, y_{k-1}$ deciding if $\exists y_k : V_k(w,y_1,...y_{k-1},y_k) = 1$ is in $NP$
If $P = NP$ then there exists some poly-time $V_{k-1}$
	$V_{k-1}(w,y_1, ..., y_{k-1})=1 \Leftrightarrow \exists y_k : V_k(w, y_1, ..., y_k) = 1$
In this process we are reducing $k$ to $k-1$ until $k=0$
	Then we just verify if $V_0(w) = 1$

### EXP
$EXP = TIME(2^{n^c})$
$P \subseteq NP\subseteq coNP \subseteq PH \subseteq EXP \subseteq  DECIDABLE$ 
#### Theorem
$P \neq EXP$

Consider $TM$ $D$ where
$D(<M>):$ Run $M(<M>)$ for $2^{|<M>|}$ time
	If it accepts, then reject.
	Else accept.
$D$ runs in exponential time, so $L(D) \in EXP$
$D$ also accepts itself
Suppose $L(D)$ in $P$. Let $F$ be the poly-time decider for $L(D)$.
	Then $F(<F>) = D(<F>) = \neg F(<F>)$
	Because D accepts itself, but D rejects F (because it runs too fast).
	Therefore $F(<F>)$ is always the opposite of $D(<F>)$
