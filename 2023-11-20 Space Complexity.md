# Space Complexity
How much space does it take to decide various problems?

We will use a Turing Machine with 
	input tape (read only)
	work tape (read/write)

Space of computation = maximum space used on work-tape during computation.
Space of $M$ = worst-case space usage 
	max $w \in \Sigma^n :$ space of $M(w)$
## Classes
$PSPACE$ = solved in $SPACE(n^c)$
$NPSPACE =$ solved in non-deterministic space

$TIME(n) \subseteq SPACE(n) \subseteq NSPACE(n) \subseteq TIME(2^n)$
	Cannot write more than $SPACE(n)$ in $TIME(n)$
	IF done in $SPACE(n)$ then easy to do in $NSPACE(n)$
	Can be done in  $TIME(2^n)$ using a traversal tree
		Each step has constant next steps, therefore asymptotically $2^n$
Can construct graph in $2^n$ time
### Corollary
$P \subseteq PSPACE \subseteq NPSPACE \subseteq EXP$
	Where do we put $NP$?
Is $PSPACE = NPSPACE$ same as $P = NP$?

No. $PSPACE = NSPACE$ is true!
	Therefore, $NP \subseteq PSPACE$
Prove this using traversal tree described above
#### Proof
$Reach(u,v,i):$
	If i =0; accept if edge $u, v$
	For all vertices $w$:
		if $Reach(u,w,i-1)$ and $Reach(w,v,i-1)$ accept
		(There exists some midpoint between $u$ and $v$)
	Reject

This algorithm is deterministic in $2^{s^2(n)}$ time but only $s^2(n)$ space
Therefore we can take non-deterministic space and turn it into deterministic space without much space gain

## PSPACE Complete
### Quantified Boolean Formula (QBF)
$Q_1 x_1 Q_2 x_2... \phi (x_1, x_2, ...)$
Where $Q$ is either $\forall$ or $\exists$

Example: $\forall x_1 \exists x_2 | x_1 \wedge x_2$
	Either true or false

$TQBF =$ language of QBF that are true
#### Reductions from SAT to TQBF
$R(\phi) = \exists x_1 \exists x_2... \phi(x_1 ... x_2 ...)$ for satisfiable
$R(\phi) = \forall x_1 \forall x_2... \phi(x_1 ... x_2 ...)$ for unsatisfiable
	Can reduce in PSPACE

#### Reductions from any PSPACE to TQBF
$R(w) = \psi$ in polyspace
Use tree traversal in reduction
$\psi(C, C', i)$ where $C =$ configurations of variables
	Outputs true if path from $C$ to $C'$ is length $\leq 2^i$
$\exists C^* \forall D_1 \forall D_2$
	($D_1 = C \wedge D_2 = C^*$ ) $\vee$ $(D_1 = C^* \wedge D_2 = C')$
Then $\psi (D_1, D_2, i-1)$
Only one recursive call, therefore PSPACE
