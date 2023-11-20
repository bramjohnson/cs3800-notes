---
slides: "[[4.turing_machines.pdf]]"
---
# Summary
Can we define a notion of an algorithm?
Are there problems that cannot be solved by *any* algorithm?
# Turing Machines
A **Turing Machine** (TM) is a DFA with infinite *memory tape*
- Tape head is at left-most position.
- For each step, a machine can change the symbol at the index, then move left/right
- At any point, the machine can halt and accept/reject.

| 0   | 1   | 0   | 1   | 1   | 0   | 0   | 1   | 0   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ^ |     |     |     |     |     |     |     |     |
## TM DFAs
Transitions *read/write* under tape-head.
Transitions also *move* the tape-head R (right) or L (left).
States may be *accept* or *reject*, in which case computation would immediately halt.
### Example Transition
$0 \rightarrow 1, R$ (if 0, write 1, and move right)
$1 \rightarrow 1, R$ (if 1, move right)
## Syntax
$M = (Q, \Sigma, \Gamma, \delta, q_{start}, q_{accept}, q_{reject})$
	$Q$ is the finite *states*
	$\Sigma$ is an *input alphabet*
	$\Gamma$ is the *tape alphabet*, such that $\Sigma \subset \Gamma$, where $\Gamma$ includes the *blank symbol* "-" which is not in $\Sigma$
	$\delta$ = symbol $\rightarrow$ symbol, direction
	$q_{start}$ is the start state
	$q_{accept}$ is the accept state
	$q_{reject}$ is the reject state
## Computation
A *configuration* of $M$ is a tuple $C=(u,q,v)$
	$u$ is the left of the tape head
	$q$ is the current state
	$v$ is the current symbol and right of the tape head
## Language
A TM $M$ on input $w$ can either **accept**, **reject** (halt) or **loop**.
$M$ *recognizes* the language $L(M)$ if $w$ is accepted.
	Loops allowed.
$M$ *decides* the language $L(M)$ if $w$ is accepted or rejected. 
	Loops disallowed.
$L$ is *recognizable* if there is a TM that recognizes $L$
### Tape-head Level Description
Instead of using a state diagram (tedious), describe what the tape-head should do to determine the language.
## Examples
### Example 1: Power of 2 0s
Walk tape-head left->right crossing off every other 0.
- If tape contained a single 0, accept.
- If number of 0s was odd, reject.
- Else return to left-hand end and repeat.
### Example 2: Two words between pound sign
$L = \{w\#w : w \in \{0,1\}^*\}$
- Ensure there is only one # 
- Find first not crossed off $b \in \{0,1\}$ on the left of the # and the first not crossed off $b' \in \{0,1\}$ to the right of the # 
	- If b or b' does not exist, reject
	- if b != b', reject
- Return to left and repeat.
## Beyond Boolean
We can consider a model of TM that outputs it's contents when it enters an accept/reject state.
