---
slides: "[[4.turing_machines.pdf]]"
---
# Multi-Tape TM
Take input from multiple tape-heads and decide next-steps based on that.
## Convert
Compile this to a single TM separate each machine by \# and each tape-head by an underline.
To make a step, scan over entire tape of single-tape TM.
## Binary Addition
- Use two extra tapes, copy reverse of a and b to new tapes.
- 1 bit of memory for carryout
- Add two bits under tape-heads, put module 2 on main tape and update carry.
	- Repeat until both tape-heads blank
- Reverse main tape to get correct answer
# Random Access TM
Memory modeled as infinite array $R$, allowing us to read/write to arbitrary locations in memory without scanning the tape.
- Store contents of array R on a tape as tuples: (location, value)
- Simulate read: scan R until find location, write value to value tape.
- Simulate write: scan R until find location, update value or append if location not found.
# TM Proof for PLs
- All programming languages are compiled to assembly code
- Assembly code instructions can be implemented on a Random Access TM.
# TM Pseudocode
Example: TM $M$ deciding $L = \{0^n1^n : n \geq 0\}$
```
M(w) {
	Check w in 0*1*, else reject;
	Count # of 0s and # of 1s
	Accept if counts are equal, else reject.
}
```
## Strings
We can encode anything as a string using angle brackets:
`<O>` denotes encoding of O as a string
## Problems
We can consider much more complex problems using complex languages
`<p>` where p is a prime number
`<G>` where G is a connected graph
`<M>` where M is a TM that halts on empty input.
# Universal TM
A Turing Machine $M_{UNIV}$ that can run any other Turing Machine as input.
$M_{UNIV}(<M>,w)$ Takes input of a Turing M, runs on w.
- If $M$ accepts $w$, $M_{UNIV}$ accepts
- If $M$ rejects $w$, $M_{UNIV}$ rejects
- If $M$ loops on $w$, $M_{UNIV}$ loops
# Non-Deterministic TM
Multiple actions the TM can take at any point.
Defined using transition function
- TM accepts if exists way to run the computation that ends in accept state.
- TM rejects if all computations reject.
To flatten this, use breadth first search on option tree.
	Only 1 step per "option" and then move on until all reject or one accept.

# Locality of  TM Configurations
Let $C$ and $C'$ be two configurations of a TM $M$.
Can check if $C$ yields $C'$ by only performing local checks within 2x3 window.
Importance: does $C$ follow from $C'$ in one step of the TM.