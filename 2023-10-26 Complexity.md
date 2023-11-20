---
slides: "[[Kolmogorov_complexity.pdf]]"
---
# Kolmogorov Complexity
Consider two strings
	"010101010101" - Less complex
	"100110111010" - More complex

The first string is less complex because there is TM that can describe it using less information than the string represents. There is no obvious TM for the second string.

We consider complexity the ability to compress a string $x$.
## Theorem 1
For every string of length $n$, there is a string $w$ that is not compressible.
## Theorem 2
There exists an $I$ that recognizes the language of strings that are incompressible.

Define TM $M(<n>)$: where $<n>$ is in binary
	Output first $x$ of length $n$ that is incompressible (by Theorem 1)

Now, let us take the output $x$ of $M(<n>)$
	We can compress this $x$ by simply some $c + log_n$
At a large scale, we will be compressing the incompressible $x$.
Therefore, contradiction.