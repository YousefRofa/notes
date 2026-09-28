# Homomorphisms

So far we've looked at groups one at a time: $\mathbb{Z}$, $GL_n$, $S_3$ ,... each living in its own little world. But some interesting stuff happens when we compare groups. Is $S_3$ secretly "the same" as the triangle's symmetries? Does the determinant tell us something about $GL_n$? To talk about this we need maps between groups, but not just any map, we need maps that _respect the group structure_. These are homomorphisms.

## 1. The definition

**Definition:** Let $G$ and $G'$ be groups. A homomorphism $\varphi : G \to G'$ is a map such that
$$\varphi(ab) = \varphi(a)\,\varphi(b) \qquad \text{for all } a, b \in G.$$

Notice that the two products live in different groups. On the left, $ab$ is computed in $G$ with $G$'s law. On the right, $\varphi(a)\varphi(b)$ is computed in $G'$ **with $G'$'s law**. The condition says you get the same answer either way:

$$
\begin{array}{ccc}
(a, b) & \xrightarrow{\ \text{multiply in } G\ } & ab \\
\big\downarrow \varphi & & \big\downarrow \varphi \\
(\varphi(a), \varphi(b)) & \xrightarrow{\ \text{multiply in } G'\ } & \varphi(a)\varphi(b) = \varphi(ab)
\end{array}
$$

> Intuitively, a homomorphism is a map that is compatible with the laws of composition in the two groups, and it provides a way to relate different groups.

I like to think of it as a **translator** between two languages. If you say "$a$ then $b$" in the language of $G$, and translate the whole sentence, you get the same thing as translating each word and then combining them in the language of $G'$. A bad translator (a random map) would garble the grammar.

If the laws are written additively, the condition just changes its outfit. For example if $G$ is additive and $G'$ is multiplicative, it reads $\varphi(a + b) = \varphi(a)\varphi(b)$ (hi, exponential function!)

### 1.1 Two free gifts

When a homomorphism only promises to respect multiplication. It turns out it then respects the identity and inverses also for free.

**Proposition:** If $\varphi : G \to G'$ is a homomorphism, then

1. $\varphi(1) = 1'$ (identity goes to identity);
2. $\varphi(a^{-1}) = \varphi(a)^{-1}$ (inverses go to inverses).

_Proof._ (1) $\varphi(1) = \varphi(1 \cdot 1) = \varphi(1)\varphi(1)$. Now cancel one $\varphi(1)$ (we are in a group, so we can multiply by $\varphi(1)^{-1}$) to get $1' = \varphi(1)$.

(2) $\varphi(a)\varphi(a^{-1}) = \varphi(aa^{-1}) = \varphi(1) = 1'$, and similarly in the other order. So $\varphi(a^{-1})$ is _an_ inverse of $\varphi(a)$, and inverses are unique. $\blacksquare$

Also by induction, $\varphi(a^n) = \varphi(a)^n$ for every integer $n$.

### Some Examples

| Homomorphism                                                                                | Why it works                                       |
| ------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| $\det : GL_n(\mathbb{R}) \to \mathbb{R}^\times$                                             | $\det(AB) = \det A \cdot \det B$                   |
| $\operatorname{sign} : S_n \to \{\pm 1\}$                                                   | sign of a composition = product of signs           |
| $\exp : (\mathbb{R}, +) \to \mathbb{R}^\times$, $\ x \mapsto e^x$                           | $e^{x+y} = e^x e^y$                                |
| $\lvert\cdot\rvert : \mathbb{C}^\times \to \mathbb{R}^\times$, $\ z \mapsto \lvert z\rvert$ | $\lvert zw\rvert = \lvert z\rvert\,\lvert w\rvert$ |
| $\mathbb{Z} \to G$, $\ n \mapsto a^n$ (fixed $a \in G$)                                     | $a^{m+n} = a^m a^n$                                |
| $\mathbb{Z} \to \mathbb{Z}$, $\ n \mapsto 2n$                                               | $2(m+n) = 2m + 2n$                                 |
| inclusion $H \hookrightarrow G$ of a subgroup                                               | the law on $H$ _is_ the law on $G$                 |
| trivial map $G \to G'$, $\ a \mapsto 1'$                                                    | $1' = 1' \cdot 1'$ lol                             |

**The determinant** is the most important example I believe. $GL_n$ is a big complicated non-abelian group, and $\det$ squashes each matrix into a single nonzero number, but it does so in a way that respects multiplication. So it's like a "shadow" of the matrix that still remembers how to multiply. Geometrically: $\det$ remembers only the area-scaling factor (and orientation), and "scale by $\det A$ then by $\det B$" is the same as "scale by $\det(AB)$".
