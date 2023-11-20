---
slides: "[[5.undecidability.pdf]]"
---
# Outline
There exists languages which are **not** decidable.
- Proof by counting: $|languages| > |TMs|$
## Proof
The following language is not decidable:
	$A_{TM} = \{<M, w> : M$ is a $TM$ that accepts $w\}$
This machine could loop and not halt.

Can show other languages $L$ are undecidable via *reduction*. 
# Infinities
Many infinite sets: Natural numbers, Even numbers, Rational numbers, Real numbers.
## Comparing Infinities
Let $S$ and $T$ be infinite sets.
Define *one-to-one* mapping as a function from $S$ to $T$ such that the input and output are unique.
	If so, $S$ is a effectively a subset of $T$: $|T| \geq |S|$
	If $T$ is also a subset of $S$: $|T| = |S|$
### Smallest Infinity
 $\mathbb{N}$ is the smallest infinity.
	 You can always map all in $\mathbb{N}$ to unique values in another infinite set.
### Example: Even and Natural
$f: \mathbb{E} \rightarrow \mathbb{N}$ = $f(x) = x$ is one-to-one. $|\mathbb{N}| \geq |\mathbb{E}|$
$g: \mathbb{N} \rightarrow \mathbb{E}$ = $g(x) = 2x$ is one-to-one $|\mathbb{E}| \geq |\mathbb{N}|$
Therefore, $|\mathbb{N}| = |\mathbb{E}|$

### Example: $\{0,1\}^*$ and Natural
$g: \{0,1\}^* \rightarrow \mathbb{N}$ = $g(x) = 1w$ converted to binary.

### Example: Rational and Natural
Convert any rational number $m/n$ to a string with alphabet $\{0, 1, ..., 9, /\}$ 
$g: \mathbb{Q} \rightarrow \Sigma^*$ = $g(x) = m/n$ as string.

This example allows us to convert any object with a "finite description" to a finite alphabet $\Sigma$, which can be proved in this same way.

## Uncountable Infinity
Show set $\mathbb{S}$ of all infinite binary sequences is uncountable.
Different from $\{0,1\}^*$ because that set has finite elements, while this set has infinite elements
### Proof - Contradiction
Assume $\mathbb{S}$ is countable.
There is a one-to-one function $f : \mathbb{S} \rightarrow \mathbb{N}$ 
There exists a list $s_1,s_2,s_3,...$ such that all sequences are defined.
![[5.undecidability.pdf#page=13]]
Define a sequence $s^* : b_1, b_2, b_3, ...$ where $b$ is a flipped version of $a$, and is taken from the $i$th position of each sequence.
$s^*$ differs from every existing sequence in at least one position $i$.
## Proof - Reduction
If some set $|\mathbb{R}| \geq |\mathbb {S}|$ then $\mathbb{R}$ is uncountable as well.

Show set $\mathbb{L}$ of all languages over $\{0,1\}$ is uncountable
$f(s) = \{<i> : a_i = 1\}$
Map where ith element of $a$ is 1. There must be some position $i$ where two sequences differ, therefore we cover all languages.

# Undecidability
We have $\mathbb{L}$ of all languages (uncountable) and $\mathbb{M}$ of all TMs (countable).
If we have a $f: \mathbb{L} \rightarrow \mathbb{M}$, then $|\mathbb{L}| \leq |\mathbb{S}|$.
THATS ILLOGICAL!
therefore, win :3

# TM Self-Acceptance Problem
$S = \{<M> : M$ is a TM that accepts $<M>\}$ 
$\bar S$ = $\{<M> : M$ is a TM that does *not* accept $<M>\}$

## Proof - For Complement
$\bar S$ is an undecidable language. Accept $M$ if $M$ does not accept itself as input.

Assume we have a **decider** $D$ that always halts for $\bar S$.
	$D$ accepts $<M>$ IF $M$ does not accept $<M>$
What if we run $D(<D>)$
	$D$ accepts $<D>$ IF $D$ does not accept $<D>$

That makes no sense, contradiction!