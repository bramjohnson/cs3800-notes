---
slides: "[[5.undecidability.pdf]]"
---
# Overview
'We want to show other languages are undecidable, given the fact that [[2023-10-05 Undecidability#Undecidability|the self-unacceptance TM]] is undecidable.
# Reductions
Reduce a problem $A$ to problem $B$:
	Show how to solve $A$ using a way to solve $B$.

If $A$ and $B$ are languages, we reduce $A$ to $B$ by constructing decider $D_A$ for $A$ using a hypothetical decider $D_B$ for $B$ as a "subroutine".

By reducing $A$ to $B$ we show:
	$B$ decidable $\Rightarrow$ $A$ decidable
	A undecidable $\Rightarrow$ B undecidable (contrapositive)
# Extension
## TM Acceptance
$A_{TM} = \{<M, w> : M$ is a $TM$ and $M$ accepts $w\}$
Want to show this is undecidable using self-accepting Turing machine.

Consider a decider $D_a$ for $A_{TM}$. Construct a decider $D_s$ for $SA_{TM}$.
$D_s(<M>) \{$Output $D_a(<M, M>)\}$.
Using the above reduction, we can show that $D_a$ is undecidable in this case.
## Halting Problem
$H = \{<M,w> : M$ is a $TM$ and $M$ halts on $w\}$
Want to show halting problem is undecidable using [[2023-10-12 Undecidability Extended#TM Acceptance|Acceptance TM]].

Reduce $A_{TM}$ to $H$ where
	$A_{TM} = \{<M, w> : M$ is a $TM$ and $M$ accepts $w\}$
	Construct decider $D_{ATM}$ using decider $D_H$ as subroutine.
$D_{ATM}(<M,w>)$:
	Run $D_H(<M, w>)$ and if rejects, reject.
	Else run $M(w)$ return output.
If you could decide $A_{TM}$ using $D_H$, 
	then if $D_{ATM}$ is undecidable, then so is $D_H$.
## Empty String
$E_{TM}$ = $\{<M> : M$ is a $TM$ and $M$ accepts $\epsilon\}$

Reduce $A_{TM}$ to $E_{TM}$
$D_{ATM}(<M,w>)$:
	Create $M'_w$ that has $w$ hardcoded and runs $M$ on $w$
	On any input for $M'_w$, run $M(w)$.
	Output $D_{ETM}(<M'_w>)$
Therefore, on the empty string (or any other string), $M(w)$ is run and we can output the result of $E_{TM}$ 
## Regular Language
$R = \{<M> : M$ is a $TM$ and $L(M)$ is *regular*$\}$

$D_{ATM}(<M,w>):$
	Create $<M'_w>$
	$M'_w(x):$
		If x is of form $0^n1^n$ then accept.
		else output $M(w)$
	This TM's language is regular only if $M(w)$ accepts.
	If $M(w)$ does not accept, then $M'$ only accepts irregular language ($0^n1^n$).
	If $M(w)$ does accept, then we accept all strings with is a regular language.
	Output $D_R(M'_w)$
## Equal Languages
$EQ_{TM} = {<M_1, M_2>: L(M_1) = L(M_2)}$ 

$D_{ATM}(<M,w>):$
	Create $<M_1>, <M_2>$
	$M_1(x):$ Output $M(w)$
	$M_2(x):$ Output accept
	Output $D_{EQTM}(<M_1>, <M_2>)$
# Rice's Theorem
Any non-trivial property of the language of a TM is undecidable.
	Given `<M>`, any non-trivial property of `L(<M>)` is undecidable.
## Theorem
Let "property" $P$ be some set of TMs such that
	$P$ contains some but not all TMs
	Whenever $L(M)$ = $L(M')$, then $M \in P$ and $M' \in P$
		(Only depends on language for differences)
	Then language $L_P$ is undecidable
## Proof
Assume $M_{reject} \notin P$
Reduce $A_{TM}$ to $L_P$ by constructing a decider $D_{ATM}$ using $D_P$ as subroutine.
Reduction:
$M_w(x):$
	Output $M(w)$ AND $M'(x)$
If $M(w)$ accepts, the language is $M'(x)$
If $M(w)$ rejects, the language is empty string