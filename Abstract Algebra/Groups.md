# Groups

A group is a set together with a way of combining its elements. We need to talk about what "a way of combining them" really means, percisely, we need to talk about the **Laws of Composition**, which I didn't find the need to create a seperate file to explain :)

## 1. Laws of composition

**Definition:** A _law of composition_ on a set $X$ is a map
$$X \times X \to X, \qquad (a, b) \mapsto a \ast b.$$

It takes two elements of $X$ and returns one element of $X$.

The codomain here is important, The definition requires $a \ast b$ to land back in $X$. This is called **closure**, and it is built into the phrase "law of composition" rather than being a separate axiom.

Examples:

- Addition is a law of composition on $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$.
- Subtraction is a law on $\mathbb{Z}$ but **not** on $\mathbb{N}$: $1 - 2 = -1 \notin \mathbb{N}$.
- Division is not a law on $\mathbb{R}$, but it is one on $\mathbb{R} \setminus \{0\}$.

### 1.1 Associativity and commutativity

A law $\ast$ on $X$ is

- **associative** if $(a \ast b) \ast c = a \ast (b \ast c)$ for all $a, b, c \in X$;
- **commutative** if $a \ast b = b \ast a$ for all $a, b \in X$.

These are independent properties. Matrix multiplication and composition of map, for example, are associative but **not** commutative.
Are there any sets that have an operation that are commutative but not associative?

Ofcourse! an example that I like is

**Why associativity matters.** It lets us write $abc$ without brackets. More strongly, if a law is associative then _every_ bracketing of a product $a_1 a_2 \cdots a_n$ gives the same answer (Artin, Prop. 2.1.4). Every group law is associative, so from now on we drop brackets freely.

**Commutativity is not assumed.** The most important groups — matrix groups and symmetric groups — are not commutative. The order of the factors in a product is information you cannot throw away.

---

**Definition:** An _identity element_ for a law on $X$ is an element $1 \in X$ such that
$$1 \cdot a = a \quad\text{and}\quad a \cdot 1 = a \qquad \text{for every } a \in X.$$

In additive notation the identity is written $0$, and the condition reads $0 + a = a + 0 = a$.

| Set and law                           | Identity                                |
| ------------------------------------- | --------------------------------------- |
| $(\mathbb{Z}, +)$                     | $0$                                     |
| $(\mathbb{R}, \cdot)$                 | $1$                                     |
| $(\mathrm{Mat}_n(\mathbb{R}), \cdot)$ | the identity matrix $I_n$               |
| (maps $T \to T$, $\circ$)             | the identity map $\mathrm{id}_T(t) = t$ |

The condition is **two-sided**. For the law $a \ast b := b$ (always return the right-hand element), every element $e$ satisfies $e \ast a = a$, so every element is a _left_ identity — but $a \ast e = e \neq a$ in general, so none is an identity.

**Proposition. An identity element, if it exists, is unique.**

_Proof._ Suppose $1$ and $1'$ are both identities. Then
$$1 \cdot 1' = 1' \quad (\text{because } 1 \text{ is an identity}), \qquad 1 \cdot 1' = 1 \quad (\text{because } 1' \text{ is an identity}).$$
So $1 = 1'$. $\blacksquare$

This is why we can say **_the_** identity and give it a fixed symbol!

---
