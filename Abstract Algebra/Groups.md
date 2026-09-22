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

Ofcourse! an example that I like is rock–paper–scissors, we can define $\{R, P, S\}$, and let the operation $a \ast b$ be the winner of $a$ vs $b$, (with $a \ast a = a$, which is both winning or losing lol)

Here it's clearly commutative, the winner doesn't depend on order (if we were to create a multiplication table, it would be symmetric). But it's not associative: $(R \ast P) \ast S = P \ast S = S$, but $R \ast (P \ast S) = R \ast S = R$.

> So commutativity does not imply associativity. Abelian groups are associative only because associativity is a group axiom.

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

Where the identity map is basically the map that does nothing.

**Proposition. An identity element, if it exists, is unique.**

_Proof._ Suppose $1$ and $1'$ are both identities. Then
$$1 \cdot 1' = 1' \quad (\text{because } 1 \text{ is an identity}), \qquad 1 \cdot 1' = 1 \quad (\text{because } 1' \text{ is an identity}).$$
So $1 = 1'$. $\blacksquare$

This is why we can say **_the_** identity and give it a fixed symbol!

---

## 3. Invertible elements

**Definition.** Let $\cdot$ be a law on $X$ with identity $1$. An element $a \in X$ is **invertible** if there is an element $a^{-1} \in X$ with
$$a \cdot a^{-1} = 1 \quad\text{and}\quad a^{-1} \cdot a = 1.$$
Then $a^{-1}$ is called the _inverse_ of $a$. In additive notation it is written $-a$.

Again the condition is two-sided: $a^{-1}$ must undo $a$ from both sides.

| Set and law                           | Which elements are invertible?                 |
| ------------------------------------- | ---------------------------------------------- |
| $(\mathbb{Z}, +)$                     | all of them: the inverse of $a$ is $-a$        |
| $(\mathbb{Z}, \cdot)$                 | only $1$ and $-1$ ($2$ has no integer inverse) |
| $(\mathbb{R}, \cdot)$                 | everything except $0$                          |
| $(\mathrm{Mat}_n(\mathbb{R}), \cdot)$ | the matrices with $\det A \neq 0$              |
| (maps $T \to T$, $\circ$)             | the bijections (proved in §6.1)                |

**Proposition. If the law is associative, an inverse, if it exists, is unique.**

_Proof._ Suppose $b$ and $c$ are both inverses of $a$. Then
$$b = b \cdot 1 = b(ac) = (ba)c = 1 \cdot c = c. \qquad \blacksquare$$

Associativity was used in the middle step. This is why the notation $a^{-1}$ is safe.

**Proposition. If $a$ and $b$ are invertible, so is $ab$, with**
$$(ab)^{-1} = b^{-1}a^{-1}.$$

_Proof._ $(ab)(b^{-1}a^{-1}) = a(bb^{-1})a^{-1} = a \cdot 1 \cdot a^{-1} = aa^{-1} = 1$, and similarly $(b^{-1}a^{-1})(ab) = 1$. $\blacksquare$

The order reverses — think of putting on socks then shoes; to undo it you remove the shoes first. When the law is not commutative, $a^{-1}b^{-1}$ is generally the **wrong** answer.

**Cancellation.** Invertibility is exactly what lets you cancel. If $a$ is invertible and $ab = ac$, multiply on the left by $a^{-1}$ to get $b = c$. Without invertibility this fails: in $(\mathbb{Z}, \cdot)$, $0 \cdot 2 = 0 \cdot 3$ but $2 \neq 3$.

---

## 4. Groups

**Definition.** A **group** is a set $G$ with a law of composition such that

1. the law is **associative**;
2. there is an **identity element** $1$;
3. every element is **invertible**.

(Closure is part of "law of composition", so it isn't listed separately.) If the law is also commutative, $G$ is an **abelian** group.

**Examples.** $(\mathbb{Z}, +)$, $(\mathbb{Q}, +)$, $(\mathbb{R}, +)$, $(\mathbb{C}, +)$ are abelian groups. $(\mathbb{R} \setminus \{0\}, \cdot)$ is an abelian group, written $\mathbb{R}^\times$; likewise $\mathbb{Q}^\times$, $\mathbb{C}^\times$.

**Non-examples.** $(\mathbb{N}, +)$: $1$ has no inverse. $(\mathbb{Z}, \cdot)$: $2$ has no inverse. $(\mathrm{Mat}_n(\mathbb{R}), \cdot)$: singular matrices have no inverse.

**How to build groups.** The non-examples suggest a fix. If a set has an associative law with an identity, then **its invertible elements form a group** — closure holds by the $(ab)^{-1}$ formula, $1$ is invertible, and $a^{-1}$ is invertible with inverse $a$. Both of the big families below are made this way: start with all matrices, or all maps, and throw away what can't be inverted.

---

## 5. The order of a group

**Definition.** The **order** of a group $G$, written $|G|$, is the number of elements of $G$. A group is **finite** if $|G| < \infty$ and **infinite** otherwise.

| Group                                                      | Order    |
| ---------------------------------------------------------- | -------- |
| $\{1\}$, the trivial group                                 | $1$      |
| $\{1, -1\}$ under multiplication                           | $2$      |
| $S_n$, the symmetric group (§6)                            | $n!$     |
| $S_3$                                                      | $6$      |
| $(\mathbb{Z}, +)$, $\mathbb{R}^\times$, $GL_n(\mathbb{R})$ | infinite |

**Do not confuse with the order of an element.** For $g \in G$, the order of $g$, written $|g|$, is the smallest $n \geq 1$ with $g^n = 1$ (or $\infty$ if there is none). $|G|$ counts elements of the group; $|g|$ counts how many times you must apply $g$ to get back to $1$. They are related — for finite $G$, $|g|$ always divides $|G|$ (Lagrange's theorem, later) — but they are different numbers. In $S_3$, which has order 6, the elements have orders 1, 2 and 3 (see §7).

---

## 6. Matrix groups

### 6.1 The general linear group $GL_n$

**Definition (Artin 2.2.4).**
$$GL_n = \{\, n \times n \text{ invertible matrices } A \,\}$$
under matrix multiplication. We write $GL_n(\mathbb{R})$ or $GL_n(\mathbb{C})$ to specify real or complex entries. Over a field,
$$A \in GL_n \iff \det A \neq 0.$$

**$GL_n$ is a group.**

| Axiom         | Reason                                                                                                                    |
| ------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Closure       | If $A, B$ are invertible, $AB$ is invertible with inverse $B^{-1}A^{-1}$. Equivalently $\det(AB) = \det A \det B \neq 0$. |
| Associativity | Matrix multiplication is associative.                                                                                     |
| Identity      | $I_n$, since $I_nA = AI_n = A$, and $\det I_n = 1 \neq 0$.                                                                |
| Inverses      | $A^{-1}$ exists by assumption and is itself invertible, with inverse $A$.                                                 |

**Small cases.**

- $GL_1(\mathbb{R})$ is just $\mathbb{R}^\times$: a $1 \times 1$ matrix $(a)$ is invertible iff $a \neq 0$.
- For $n = 2$ there is an explicit inverse:
  $$\begin{pmatrix} a & b \\ c & d \end{pmatrix}^{-1} = \frac{1}{ad - bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}, \qquad ad - bc \neq 0.$$

**$GL_n$ is not abelian for $n \geq 2$.**

$$
\begin{pmatrix}1&1\\0&1\end{pmatrix}\begin{pmatrix}1&0\\1&1\end{pmatrix} = \begin{pmatrix}2&1\\1&1\end{pmatrix}, \qquad
\begin{pmatrix}1&0\\1&1\end{pmatrix}\begin{pmatrix}1&1\\0&1\end{pmatrix} = \begin{pmatrix}1&1\\1&2\end{pmatrix}.
$$

**Order.** $GL_n(\mathbb{R})$ is infinite: it contains $aI_n$ for every nonzero real $a$.

### 6.2 The special linear group $SL_n$

**Definition (Artin 2.2.11).**
$$SL_n(\mathbb{R}) = \{\, A \in GL_n(\mathbb{R}) \;:\; \det A = 1 \,\}.$$

**$SL_n$ is a subgroup of $GL_n$** — a subset that is a group under the same law. We check the three subgroup conditions (associativity is inherited automatically):

- **Closure.** If $\det A = \det B = 1$, then $\det(AB) = \det A \cdot \det B = 1$.
- **Identity.** $\det I_n = 1$.
- **Inverses.** $\det(A^{-1}) = (\det A)^{-1} = 1$.

Everything rests on the multiplicativity of the determinant, $\det(AB) = \det A \det B$.

**Examples in $SL_2(\mathbb{R})$.**
$$\begin{pmatrix}1&t\\0&1\end{pmatrix} \ (\text{shears}), \qquad \begin{pmatrix}\lambda&0\\0&\lambda^{-1}\end{pmatrix} \ (\text{stretch one axis, squeeze the other}), \qquad \begin{pmatrix}\cos\theta&-\sin\theta\\ \sin\theta&\cos\theta\end{pmatrix} \ (\text{rotations}).$$

**Geometric meaning.** $|\det A|$ is the factor by which $A$ scales areas (volumes for $n \geq 3$), and the sign records whether orientation is flipped. So $GL_n$ is all invertible linear transformations, and $SL_n$ is those that **preserve volume and orientation**.

---

## 7. Symmetric groups

### 7.1 Permutations

Let $T$ be a set, and consider all maps $f : T \to T$ under composition. This law is associative with identity $\mathrm{id}_T$, but not every map has an inverse. Which ones do?

**Proposition.** A map $f : T \to T$ has an inverse if and only if $f$ is bijective.

_Proof._ ($\Leftarrow$) If $f$ is bijective, each $t \in T$ equals $f(s)$ for exactly one $s$ — at least one by surjectivity, at most one by injectivity. Define $g(t) := s$. Then $g(f(s)) = s$ and $f(g(t)) = t$.

($\Rightarrow$) Suppose $g \circ f = \mathrm{id} = f \circ g$. If $f(s) = f(s')$, applying $g$ gives $s = s'$, so $f$ is injective. For any $t$, $t = f(g(t))$, so $f$ is surjective. $\blacksquare$

A bijection $T \to T$ is called a **permutation** of $T$. By §4, the permutations of $T$ form a group under composition.

**Definition (Artin 2.2.5).** The **symmetric group** $S_n$ is the group of permutations of $\{1, 2, \dots, n\}$.

**The elements are the maps, not the arrangements.** A permutation is an _operation_ — a rule saying where each of $1, \dots, n$ goes. The group law is doing one operation after another. Arrangements of $1, \dots, n$ are a convenient way to _record_ a permutation (see one-line notation below), but you compose permutations, not arrangements.

**Order.** $|S_n| = n!$. To build a permutation, choose where $1$ goes ($n$ choices), then where $2$ goes ($n-1$ remaining), and so on down to $1$ choice for the last:
$$|S_n| = n(n-1)\cdots 2 \cdot 1 = n!.$$

So $|S_2| = 2$, $|S_3| = 6$, $|S_4| = 24$, $|S_5| = 120$.

### 7.2 How to multiply: the composition convention

Artin writes composition multiplicatively:
$$qp := q \circ p, \qquad\text{meaning: apply } p \text{ first, then } q.$$

So **products are read right to left**, like $f(g(t))$. To compute $qp$, take each number, send it through $p$, then send the result through $q$.

> **Warning.** Some books use the opposite convention (left to right). This reverses every product. Pick Artin's and never switch mid-computation.

### 7.3 Four ways to write a permutation

Take the permutation $p$ of $\{1, 2, 3\}$ with $p(1) = 2$, $p(2) = 3$, $p(3) = 1$.

**(a) As a list of values.** Just write out $p(1) = 2$, $p(2) = 3$, $p(3) = 1$. Clear, but bulky.

**(b) Two-line notation.** Put the inputs on top and their images underneath:
$$p = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 3 & 1 \end{pmatrix}.$$
Read each column as "top goes to bottom". This is the most transparent notation for beginners.

**(c) One-line notation.** Drop the top row, since it is always $1, 2, \dots, n$ in order:
$$p = 231.$$
Read it as: "$1$ goes to the first entry, $2$ goes to the second entry, …". This is where the link to arrangements comes from: one-line notation turns every permutation into an arrangement and back, which is why counting arrangements gives $n!$.

**(d) Cycle notation.** Follow a single element around until it returns:
$$1 \mapsto 2 \mapsto 3 \mapsto 1, \qquad\text{written}\qquad p = (1\,2\,3).$$
A cycle $(a_1\, a_2\, \dots\, a_k)$ means $a_1 \mapsto a_2 \mapsto \cdots \mapsto a_k \mapsto a_1$, and every number not listed is fixed. Rules:

- The starting point doesn't matter: $(1\,2\,3) = (2\,3\,1) = (3\,1\,2)$.
- The direction does: $(1\,3\,2)$ is a _different_ permutation from $(1\,2\,3)$.
- A 2-cycle $(a\,b)$ swaps $a$ and $b$; it is called a **transposition**. Note $(a\,b) = (b\,a)$.
- The identity is written $e$, $1$, or $()$; sometimes $(1)(2)(3)$.

Cycle notation is the standard in algebra and is what Artin uses.

> **Notation trap.** "12" without brackets (one-line) is the **identity** of $S_2$. "$(1\,2)$" with brackets (cycle) is the **swap**. They look alike and mean opposite things. Brackets mean cycles.

**(e) Bonus: as a matrix.** Each permutation $p$ of $\{1, \dots, n\}$ gives an $n \times n$ **permutation matrix** $P_p$, whose $j$-th column is the standard basis vector $e_{p(j)}$. For our $p$:
$$P_p = \begin{pmatrix} 0&0&1\\1&0&0\\0&1&0 \end{pmatrix}, \qquad P_p e_1 = e_2,\; P_p e_2 = e_3,\; P_p e_3 = e_1.$$
With this convention $P_qP_p = P_{qp}$, so multiplying the matrices _is_ composing the permutations. Permutation matrices are invertible, so this places a copy of $S_n$ inside $GL_n$ — one reason Artin calls $GL_n$ and $S_n$ the groups that other groups live inside. Every permutation matrix has determinant $\pm 1$; those with determinant $+1$ lie in $SL_n$.

### 7.4 Warm-up: $S_2$

$S_2$ is the permutations of $\{1, 2\}$. There are $2! = 2$:

| Map      | Two-line                               | One-line | Cycle    |
| -------- | -------------------------------------- | -------- | -------- |
| identity | $\begin{pmatrix}1&2\\1&2\end{pmatrix}$ | $12$     | $e$      |
| swap     | $\begin{pmatrix}1&2\\2&1\end{pmatrix}$ | $21$     | $(1\,2)$ |

Swapping twice returns everything to its place, so $(1\,2)(1\,2) = e$. The table is:

| $\cdot$  | $e$      | $(1\,2)$ |
| -------- | -------- | -------- |
| $e$      | $e$      | $(1\,2)$ |
| $(1\,2)$ | $(1\,2)$ | $e$      |

The permutations of any two-element set $\{a, b\}$ have exactly this table; renaming $a \to 1$, $b \to 2$ turns them into $S_2$. In fact **every** group of order 2 has this table: call its elements $1, g$; three products are forced by the identity, and $gg = g$ would cancel to $g = 1$, so $gg = 1$. There is essentially only one group of order 2.

---

## 8. Deriving $S_3$

### 8.1 The six elements

$|S_3| = 3! = 6$. Listing every bijection of $\{1, 2, 3\}$:

| Description            | Two-line                                   | One-line | Cycle       |
| ---------------------- | ------------------------------------------ | -------- | ----------- |
| fix everything         | $\begin{pmatrix}1&2&3\\1&2&3\end{pmatrix}$ | $123$    | $e$         |
| rotate $1\to2\to3\to1$ | $\begin{pmatrix}1&2&3\\2&3&1\end{pmatrix}$ | $231$    | $(1\,2\,3)$ |
| rotate $1\to3\to2\to1$ | $\begin{pmatrix}1&2&3\\3&1&2\end{pmatrix}$ | $312$    | $(1\,3\,2)$ |
| swap 1 and 2           | $\begin{pmatrix}1&2&3\\2&1&3\end{pmatrix}$ | $213$    | $(1\,2)$    |
| swap 1 and 3           | $\begin{pmatrix}1&2&3\\3&2&1\end{pmatrix}$ | $321$    | $(1\,3)$    |
| swap 2 and 3           | $\begin{pmatrix}1&2&3\\1&3&2\end{pmatrix}$ | $132$    | $(2\,3)$    |

Three kinds: the identity, two **3-cycles**, three **transpositions**.

### 8.2 Two generators

Following Artin, name two of them:
$$x = (1\,2\,3), \qquad y = (1\,2).$$
We will show every element of $S_3$ is a product of $x$'s and $y$'s, and find the rules they obey.

**Rule 1: $x^3 = 1$.** Applying $x$ sends $1 \to 2 \to 3 \to 1$; three applications bring every number back. Along the way,
$$x^2: \quad 1 \xrightarrow{x} 2 \xrightarrow{x} 3, \quad 2 \xrightarrow{x} 3 \xrightarrow{x} 1, \quad 3 \xrightarrow{x} 1 \xrightarrow{x} 2,$$
so $x^2 = (1\,3\,2)$. Note $x^2 = x^{-1}$, since $x^2 \cdot x = x^3 = 1$.

**Rule 2: $y^2 = 1$.** Swapping twice undoes the swap. So $y = y^{-1}$.

**Rule 3: $yx = x^2y$.** Compute both sides, applying the right factor first.

$$yx:\quad 1 \xrightarrow{x} 2 \xrightarrow{y} 1, \qquad 2 \xrightarrow{x} 3 \xrightarrow{y} 3, \qquad 3 \xrightarrow{x} 1 \xrightarrow{y} 2 \qquad\Longrightarrow\qquad yx = (2\,3).$$

$$x^2y:\quad 1 \xrightarrow{y} 2 \xrightarrow{x^2} 1, \qquad 2 \xrightarrow{y} 1 \xrightarrow{x^2} 3, \qquad 3 \xrightarrow{y} 3 \xrightarrow{x^2} 2 \qquad\Longrightarrow\qquad x^2y = (2\,3).$$

They agree, so $yx = x^2y$. ✓

**The other product.**
$$xy:\quad 1 \xrightarrow{y} 2 \xrightarrow{x} 3, \qquad 2 \xrightarrow{y} 1 \xrightarrow{x} 2, \qquad 3 \xrightarrow{y} 3 \xrightarrow{x} 1 \qquad\Longrightarrow\qquad xy = (1\,3).$$

Since $xy = (1\,3) \neq (2\,3) = yx$, **$S_3$ is not abelian.** It is the smallest non-abelian group: every group of order $\le 5$ is abelian.

### 8.3 Every element in terms of $x$ and $y$

We now have all six:

| Name   | Cycle       | Order of the element |
| ------ | ----------- | -------------------- |
| $1$    | $e$         | 1                    |
| $x$    | $(1\,2\,3)$ | 3                    |
| $x^2$  | $(1\,3\,2)$ | 3                    |
| $y$    | $(1\,2)$    | 2                    |
| $xy$   | $(1\,3)$    | 2                    |
| $x^2y$ | $(2\,3)$    | 2                    |

$$S_3 = \{\,1,\; x,\; x^2,\; y,\; xy,\; x^2y\,\} = \{\, x^iy^j : 0 \le i \le 2,\; 0 \le j \le 1 \,\}.$$

**These six are distinct** — visible from the cycle column, but here is an argument using only the rules. Suppose $x^iy^j = x^ky^l$. Then $x^{i-k} = y^{l-j}$. The left side is a power of $x$, so it is $1$, $x$ or $x^2$; the right side is $1$ or $y$. But $y$ is not a power of $x$ ($y$ has order 2, while $x$ and $x^2$ have order 3). So both sides equal $1$, forcing $i = k$ and $j = l$.

### 8.4 The multiplication rule

The three rules
$$x^3 = 1, \qquad y^2 = 1, \qquad yx = x^2y$$
are the **defining relations** of $S_3$ (Artin 2.2.6). They let you reduce any product to the form $x^iy^j$: push every $y$ to the right using rule 3, then shrink exponents using rules 1 and 2.

It helps to have rule 3 in a general form. Since $x^2 = x^{-1}$, rule 3 says $yx = x^{-1}y$. Applying it $k$ times:
$$\boxed{\,yx^k = x^{-k}y\,}$$
so moving $y$ past $x^k$ **flips the sign of the exponent**. In particular $yx^2 = xy$.

Then the general product is
$$(x^iy^j)(x^ky^l) = \begin{cases} x^{i+k}\,y^{l} & \text{if } j = 0,\\[2pt] x^{i-k}\,y^{1+l} & \text{if } j = 1, \end{cases}$$
with exponents of $x$ read mod 3 and of $y$ read mod 2.

**Worked example (Artin 2.2.8).** Reduce $x^{-1}y^3x^2y$:
$$x^{-1}y^3x^2y = x^2\,(yx^2)\,y = x^2\,(xy)\,y = x^3y^2 = 1.$$

### 8.5 The multiplication table

Entry = (row) $\cdot$ (column), with the **column applied first**.

| $\cdot$    | $1$    | $x$    | $x^2$  | $y$    | $xy$   | $x^2y$ |
| ---------- | ------ | ------ | ------ | ------ | ------ | ------ |
| **$1$**    | $1$    | $x$    | $x^2$  | $y$    | $xy$   | $x^2y$ |
| **$x$**    | $x$    | $x^2$  | $1$    | $xy$   | $x^2y$ | $y$    |
| **$x^2$**  | $x^2$  | $1$    | $x$    | $x^2y$ | $y$    | $xy$   |
| **$y$**    | $y$    | $x^2y$ | $xy$   | $1$    | $x^2$  | $x$    |
| **$xy$**   | $xy$   | $y$    | $x^2y$ | $x$    | $1$    | $x^2$  |
| **$x^2y$** | $x^2y$ | $xy$   | $y$    | $x^2$  | $x$    | $1$    |

**How the rows were computed.**

- Rows $1, x, x^2$: multiplying on the left by $x^i$ just adds to the exponent of $x$: $x^i \cdot x^ky^l = x^{i+k}y^l$.
- Row $y$: use $yx^k = x^{-k}y$. For example $y \cdot xy = (yx)y = x^2y^2 = x^2$.
- Rows $xy, x^2y$: same idea. For example $xy \cdot x = x(yx) = x \cdot x^2y = x^3y = y$, and $x^2y \cdot xy = x^2(yx)y = x^2x^2y^2 = x^4 = x$.

**Check one entry directly with permutations.** Row $y$, column $x$ claims $y \cdot x = x^2y = (2\,3)$. This is exactly the $yx$ computed by tracing in §8.2. ✓

**Reading the table.**

- **Every element appears exactly once in each row and each column.** This is forced by cancellation ($ab = ac \Rightarrow b = c$) and is a quick sanity check on any group table.
- **The table is not symmetric about the diagonal.** Row $x$, column $y$ gives $xy$; row $y$, column $x$ gives $x^2y$. A group is abelian exactly when its table is symmetric.
- **The top-left $3 \times 3$ block** is closed: products of $1, x, x^2$ stay among $1, x, x^2$. That block is the subgroup of rotations, $A_3 = \{1, x, x^2\}$.
- **The diagonal** tells you the orders: $x \cdot x = x^2 \neq 1$ while each of $y, xy, x^2y$ squares to $1$.

### 8.6 The picture: symmetries of a triangle

Label the corners of an equilateral triangle $1, 2, 3$. Each symmetry of the triangle permutes the corners, and each permutation of the corners is realised by a symmetry, so $S_3$ **is** the symmetry group of the triangle.

- $x = (1\,2\,3)$ and $x^2 = (1\,3\,2)$ are the **rotations** by $120°$ and $240°$.
- The transpositions are the three **reflections**, each in the axis through one corner: $(1\,2)$ fixes corner 3, $(1\,3)$ fixes corner 2, $(2\,3)$ fixes corner 1.

In this language the relation $yxy = x^{-1}$ (which is rule 3 multiplied on the right by $y$) says: **a rotation seen in a mirror turns the other way.** And non-commutativity is visible — rotate-then-flip leaves the triangle in a different position from flip-then-rotate.

### 8.7 Subgroups of $S_3$

Reading off the table:

| Subgroup            | Elements        | Order |
| ------------------- | --------------- | ----- |
| trivial             | $\{1\}$         | 1     |
| generated by $y$    | $\{1, y\}$      | 2     |
| generated by $xy$   | $\{1, xy\}$     | 2     |
| generated by $x^2y$ | $\{1, x^2y\}$   | 2     |
| rotations $A_3$     | $\{1, x, x^2\}$ | 3     |
| whole group         | $S_3$           | 6     |

**$S_3$ is not cyclic**: no element has order 6, so no single element generates it. A cyclic group of order 6 would have exactly one subgroup of each order $1, 2, 3, 6$; $S_3$ has three of order 2. So two groups of the same order can have genuinely different structures, and $S_3$ is the first example.

---

## Summary

- A **law of composition** on $X$ is a map $X \times X \to X$; closure is built in. Group laws are always associative, rarely commutative.
- The **identity** is unique. **Inverses** are unique when the law is associative, and $(ab)^{-1} = b^{-1}a^{-1}$.
- A **group** is associative, has an identity, and has inverses. Its **order** $|G|$ is its number of elements.
- The invertible elements of any associative law with identity form a group. Applied to matrices this gives $GL_n$; applied to self-maps of $\{1, \dots, n\}$ it gives $S_n$, of order $n!$.
- $SL_n$ (determinant 1) is a subgroup of $GL_n$ because $\det$ is multiplicative.
- Permutations can be written in two-line, one-line, cycle, or matrix form; Artin multiplies **right to left**.
- $S_3 = \{1, x, x^2, y, xy, x^2y\}$ with $x^3 = y^2 = 1$ and $yx = x^2y$. It has order 6, is the smallest non-abelian group, and is the symmetry group of a triangle.
