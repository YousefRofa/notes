# Groups

A group is a set together with a way of combining its elements. We need to talk about what "a way of combining them" really means, percisely, we need to talk about the **Laws of Composition**, which I didn't find the need to create a seperate file to explain :)

### 1. Laws of composition

**Definition:** A _law of composition_ on a set $X$ is a map
$$X \times X \to X, \qquad (a, b) \mapsto a \ast b.$$

It takes two elements of $X$ and returns one element of $X$.

The codomain here is important, The definition requires $a \ast b$ to land back in $X$. This is called **closure**, and it is built into the phrase "law of composition" rather than being a separate axiom.

Examples:

- Addition is a law of composition on $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$.
- Subtraction is a law on $\mathbb{Z}$ but **not** on $\mathbb{N}$: $1 - 2 = -1 \notin \mathbb{N}$.
- Division is not a law on $\mathbb{R}$, but it is one on $\mathbb{R} \setminus \{0\}$.
