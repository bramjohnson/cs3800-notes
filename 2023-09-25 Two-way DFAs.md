This is a *bonus* lecture, and is not part of the course material.
# Two-way DFAs
Imagine a tape that can move left and right between some indices $0-n$.
Each index contains a state, and each transition moves one index left/right.
This tape is called a **2DFA**.
## Theorem
For any 2DFA, we can build a DFA that recognizes the same language.
## Construction
Build DFA for language $L(M)$.
	$Q$ = all possible tables (table represents state -> state transition)
	$F$ = all accepting tables
	$\sigma$ = $\sigma(T_x, a) = T_{xa}$
	