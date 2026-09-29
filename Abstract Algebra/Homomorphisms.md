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

## 3. The image

**Definition:** The **image** of $\varphi : G \to G'$ is
$$\operatorname{im}\varphi = \{\, x \in G' : x = \varphi(a) \text{ for some } a \in G \,\}.$$

It's everything in $G'$ that actually gets "hit". You can think of it as the part of $G'$ that $\varphi$ is able to "talk about".

**Proposition.** $\operatorname{im}\varphi$ is a subgroup of $G'$.

_Proof._

- **Closure.** $\varphi(a)\varphi(b) = \varphi(ab)$, which is in the image.
- **Identity.** $1' = \varphi(1)$.
- **Inverses.** $\varphi(a)^{-1} = \varphi(a^{-1})$. $\blacksquare$

Examples: $\operatorname{im}(\det) = \mathbb{R}^\times$ (the matrix $\operatorname{diag}(c, 1, \dots, 1)$ has determinant $c$), $\operatorname{im}(\exp) = \mathbb{R}_{>0}$, $\operatorname{im}(\lvert\cdot\rvert) = \mathbb{R}_{>0}$, $\operatorname{im}(n \mapsto 2n) = 2\mathbb{Z}$.

### 3.1 The image of $n \mapsto a^n$ is the cyclic group $\langle a \rangle$

Fix an element $a \in G$ and define
$$\varphi : \mathbb{Z}^+ \to G, \qquad n \mapsto a^n.$$
(Here $\mathbb{Z}^+$ means $\mathbb{Z}$ under $+$.) It's a homomorphism because $\varphi(m + n) = a^{m+n} = a^m a^n = \varphi(m)\varphi(n)$.

**The intuition: $a$ is a step, $n$ is how many steps you take.**

Picture yourself standing at $1$ in the group. The element $a$ is a "move" you're allowed to make. The integer $n$ is an instruction: "take $n$ steps" (negative $n$ means walk backwards, i.e. use $a^{-1}$). The homomorphism property just says

> walking $m$ steps and then $n$ more steps is the same as walking $m + n$ steps.

which is obviously true, and that's why this map is a homomorphism!

Now the image is **every place you can possibly reach using only the move $a$** (forwards or backwards):
$$\operatorname{im}\varphi = \{\, \dots, a^{-2}, a^{-1}, 1, a, a^2, \dots \,\} = \langle a \rangle,$$
which is exactly the **cyclic subgroup generated by $a$**. So "the subgroup generated by $a$" and "the image of $\mathbb{Z}$ under $n \mapsto a^n$" are the same thing. The integers are the universal "counting steps" group and $\langle a \rangle$ is the shadow they cast inside $G$.

Two things can happen:

- **You walk in a loop.** If $a$ has finite order $k$, then after $k$ steps you're back at $1$ and it repeats: $a^k = 1$, $a^{k+1} = a$, … . The image is $\{1, a, \dots, a^{k-1}\}$, with exactly $k$ elements. Example: $a = x = (1\,2\,3)$ in $S_3$ gives image $\{1, x, x^2\} = A_3$. Or $a = i$ in $\mathbb{C}^\times$: $1 \to i \to -1 \to -i \to 1$, image $\{1, i, -1, -i\}$.
- **You walk forever.** If $a$ has infinite order, you never revisit a spot ($a^m = a^n$ would give $a^{m-n} = 1$). The image is an infinite copy of $\mathbb{Z}$. Example: $a = 2$ in $\mathbb{R}^\times$ gives $\{\dots, \tfrac14, \tfrac12, 1, 2, 4, \dots\}$.

Which case we're in is decided by the kernel, which is next.

---

## 4. The kernel

**Definition.** The **kernel** of $\varphi : G \to G'$ is
$$\ker\varphi = \{\, a \in G : \varphi(a) = 1' \,\}.$$

It's everything that $\varphi$ **squashes to the identity**, i.e. everything $\varphi$ "can't see". If $\varphi$ is a translator, the kernel is the set of words that get translated to silence.

**Proposition.** $\ker\varphi$ is a subgroup of $G$.

_Proof._ If $\varphi(a) = \varphi(b) = 1'$ then $\varphi(ab) = 1' \cdot 1' = 1'$ and $\varphi(a^{-1}) = (1')^{-1} = 1'$. And $\varphi(1) = 1'$. $\blacksquare$

| Homomorphism                                                  | Kernel                                                        |
| ------------------------------------------------------------- | ------------------------------------------------------------- |
| $\det : GL_n(\mathbb{R}) \to \mathbb{R}^\times$               | $SL_n(\mathbb{R})$                                            |
| $\operatorname{sign} : S_n \to \{\pm 1\}$                     | $A_n$, the even permutations (for $S_3$: $\{1, x, x^2\}$)     |
| $\exp : (\mathbb{R},+) \to \mathbb{R}^\times$                 | $\{0\}$                                                       |
| $\lvert\cdot\rvert : \mathbb{C}^\times \to \mathbb{R}^\times$ | the unit circle $\{z : \lvert z\rvert = 1\}$                  |
| $\mathbb{Z} \to G$, $n \mapsto a^n$                           | $k\mathbb{Z}$ if $a$ has order $k$; $\{0\}$ if infinite order |

Look at the first row! $SL_n$ was defined as "matrices with $\det = 1$", and now we see that it's just the kernel of $\det$. That's why its subgroup proof in the Groups notes rested entirely on $\det(AB) = \det A \det B$: that's the homomorphism property.

And the last row finishes §3.1: the kernel of "take $n$ steps" is the set of step counts that bring you home. If you're walking in a loop of length $k$, those are exactly the multiples of $k$.

### 4.1 The kernel measures how much information is lost

**Proposition.** $\varphi(a) = \varphi(b)$ if and only if $a^{-1}b \in \ker\varphi$.

_Proof._ $\varphi(a) = \varphi(b) \iff \varphi(a)^{-1}\varphi(b) = 1' \iff \varphi(a^{-1}b) = 1'$. $\blacksquare$

So two elements look the same to $\varphi$ exactly when they "differ by" something in the kernel. In particular:

**Corollary.** $\varphi$ is injective $\iff$ $\ker\varphi = \{1\}$.

That's a really nice shortcut: to check a homomorphism is one-to-one, you only need to check what goes to $1$, not compare every pair. E.g. $\exp$ is injective because only $0$ goes to $1$.

"$b$ differs from $a$ by something in the kernel" means $b = ak$ for some $k \in K$. The set of all such $b$ is our next object.

## 5. Left cosets

**Definition.** Let $H$ be a subgroup of $G$ and $a \in G$. The **left coset** of $H$ through $a$ is
$$aH = \{\, ah : h \in H \,\}.$$

In words: take the whole subgroup $H$ and multiply every element by $a$ on the left. It's "$H$, shifted by $a$".

Keep in mind that a coset is usually NOT a group, as it does not contain the element.

### 5.1 The picture: parallel lines

Take $G = (\mathbb{R}^2, +)$ and $H$ = the $y$-axis $= \{(0, t)\}$. (In additive notation the coset is written $a + H$.) Then for $a = (3, 5)$:
$$a + H = \{(3, 5 + t) : t \in \mathbb{R}\} = \text{the vertical line } x = 3.$$

So the cosets of the $y$-axis are **all the vertical lines**. Each one is a parallel copy of $H$, slid over. Only one of them, $H$ itself, passes through the origin (i.e. contains the identity); the others are not subgroups, just shifted copies.

Now here's the punchline. Consider the homomorphism $\pi : \mathbb{R}^2 \to \mathbb{R}$, $(x, y) \mapsto x$. Its kernel is the $y$-axis. And the cosets (vertical lines) are exactly the sets where $\pi$ is constant: $\pi$ can't tell apart points on the same vertical line, because they only differ by a kernel element (a vertical move). It's like looking at the plane from directly below: every vertical line collapses to a single point.

### 5.2 A discrete picture: clocks

Take $\varphi : \mathbb{Z}^+ \to \mathbb{C}^\times$, $n \mapsto i^n$ (walking around the square $1, i, -1, -i$). The kernel is $4\mathbb{Z}$. Its cosets are

$$
\begin{aligned}
0 + 4\mathbb{Z} &= \{\dots, -4, 0, 4, 8, \dots\} &&\longmapsto 1\\
1 + 4\mathbb{Z} &= \{\dots, -3, 1, 5, 9, \dots\} &&\longmapsto i\\
2 + 4\mathbb{Z} &= \{\dots, -2, 2, 6, 10, \dots\} &&\longmapsto -1\\
3 + 4\mathbb{Z} &= \{\dots, -1, 3, 7, 11, \dots\} &&\longmapsto -i
\end{aligned}
$$

These are the residue classes mod 4! Each coset is "all the step counts that land you on the same spot". So the cosets of the kernel are precisely the **fibers** of $\varphi$ (the sets of things sent to the same place).

### 5.3 The general statement

**Proposition.** Let $K = \ker\varphi$. Then
$$\varphi(a) = \varphi(b) \iff b \in aK.$$
So the fiber of $\varphi$ over $\varphi(a)$ is exactly the coset $aK$.

_Proof._ By §4.1, $\varphi(a) = \varphi(b) \iff a^{-1}b \in K \iff b = ak$ for some $k \in K \iff b \in aK$. $\blacksquare$

So a homomorphism chops its domain into slices, all of them copies of the kernel, and collapses each slice to a single point of the image.

### 5.4 Cosets partition the group

This works for **any** subgroup $H$, not only kernels:

1. **Every element is in some coset:** $a = a \cdot 1 \in aH$.
2. **Two cosets are either equal or disjoint.** If $c \in aH \cap bH$, then $aH = cH = bH$. (Indeed if $c = ah$, then $cH = ahH = aH$, since $hH = H$ as $H$ is a subgroup.)
3. **All cosets have the same size:** $H \to aH$, $h \mapsto ah$ is a bijection (its inverse is multiplication by $a^{-1}$).

So the cosets tile $G$ like floor tiles, all the same size, no overlaps, no gaps. If $G$ is finite this immediately gives
$$|G| = (\text{number of cosets}) \times |H|,$$
so **$|H|$ divides $|G|$**. That's Lagrange's theorem, coming soon.

Useful fact: $aH = bH \iff a^{-1}b \in H$. (Same logic as §4.1.) In particular $aH = H \iff a \in H$.

### 5.5 Example in $S_3$

Recall $S_3 = \{1, x, x^2, y, xy, x^2y\}$ with $x = (1\,2\,3)$, $y = (1\,2)$, $yx = x^2y$.

**Cosets of $H = \{1, y\}$:**
$$1H = \{1, y\}, \qquad xH = \{x, xy\}, \qquad x^2H = \{x^2, x^2y\}.$$
Three cosets of size 2, total $6$. ✓

**Cosets of $A_3 = \{1, x, x^2\}$:**
$$1A_3 = \{1, x, x^2\} = \text{rotations}, \qquad yA_3 = \{y, yx, yx^2\} = \{y, x^2y, xy\} = \text{reflections}.$$
Two cosets of size 3. This is exactly the fiber picture for $\operatorname{sign}$: even stuff goes to $+1$, odd stuff goes to $-1$.

---

## 6. Conjugation

**Definition.** For $g, x \in G$, the element
$$gxg^{-1}$$
is called the **conjugate** of $x$ by $g$.

Read it right to left (like composition): **undo $g$, do $x$, redo $g$**. This is a "change of perspective". You travel to a different point of view, perform $x$ there, then come back.

**Linear algebra version.** You've seen this before: $PAP^{-1}$ is a matrix **similar** to $A$. It's the same linear transformation, just described in a different basis. Change coordinates, apply $A$, change back. Similar matrices have the same determinant, trace, eigenvalues… because they're really "the same map from a different angle".

**$S_3$ version.** Take the rotation $x$ and conjugate by the reflection $y$:
$$yxy^{-1} = yxy = (x^2y)y = x^2 = x^{-1}.$$
Flip, rotate, flip back = rotating the **other way**. That's the "a rotation seen in a mirror turns the other way" from the Groups notes, and it's really a statement about conjugation! Notice that conjugating a rotation still gives a rotation, just possibly in the other direction.

Now conjugate the reflection $y$ by the rotation $x$:
$$xyx^{-1} = xyx^2 = x(yx^2) = x(xy) = x^2y.$$
Rotate, reflect, rotate back = a reflection, but in a **different axis**. (Makes sense: if you rotate the triangle, reflect across the corner-3 axis, and then rotate back, you've effectively reflected across whichever axis got rotated into that position.)

**Some facts** (quick to check):

- Conjugation by $g$, i.e. $x \mapsto gxg^{-1}$, is a homomorphism $G \to G$: $(gxg^{-1})(gyg^{-1}) = gxyg^{-1}$. The $g^{-1}g$ in the middle cancels. It's even a bijection (inverse: conjugate by $g^{-1}$).
- Conjugates have the same order: $(gxg^{-1})^n = gx^ng^{-1}$, which is $1$ iff $x^n = 1$.
- If $G$ is abelian, conjugation does nothing: $gxg^{-1} = gg^{-1}x = x$. So conjugation measures how non-commutative things are. In fact $gxg^{-1} = x \iff gx = xg$.

---

## 7. Normal subgroups

**Definition.** A subgroup $N$ of $G$ is **normal** if
$$gNg^{-1} = N \quad \text{for all } g \in G,$$
i.e. for every $n \in N$ and every $g \in G$, the conjugate $gng^{-1}$ is still in $N$.

(Strictly, the definition asks for $gng^{-1} \in N$, i.e. $gNg^{-1} \subseteq N$, for all $g$. Applying it with $g^{-1}$ as well gives the reverse inclusion, so the two versions are equivalent.)

**Intuition:** a normal subgroup is one that **looks the same from every point of view**. No matter how you change perspective, $N$ gets carried to itself. Ordinary subgroups can get "rotated" into a different subgroup under conjugation, normal ones can't.

### 7.1 Examples and a non-example

- **In an abelian group, every subgroup is normal**, since conjugation does nothing.
- **$A_3 = \{1, x, x^2\}$ is normal in $S_3$.** Conjugating a rotation gives a rotation (we saw $yxy^{-1} = x^2$). The subgroup of rotations looks the same in the mirror.
- **$H = \{1, y\}$ is NOT normal in $S_3$.** We computed $xyx^{-1} = x^2y \notin H$. Changing perspective turns the reflection in one axis into a reflection in another axis, so this subgroup "depends on where you're standing". ❌
- **$SL_n$ is normal in $GL_n$**: $\det(PAP^{-1}) = \det P \det A (\det P)^{-1} = \det A = 1$. (Spoiler, this is a special case of the theorem below.)

### 7.2 Normal $\iff$ left cosets = right cosets

The **right coset** is $Hg = \{hg : h \in H\}$. Since $gNg^{-1} = N$ is the same as $gN = Ng$ (multiply on the right by $g$), we get:

> $N$ is normal $\iff$ $gN = Ng$ for every $g \in G$.

Check with $S_3$:

| Subgroup   | Left cosets                            | Right cosets                           | Normal?         |
| ---------- | -------------------------------------- | -------------------------------------- | --------------- |
| $\{1, y\}$ | $\{1, y\},\ \{x, xy\},\ \{x^2, x^2y\}$ | $\{1, y\},\ \{x, x^2y\},\ \{x^2, xy\}$ | no, they differ |
| $A_3$      | $A_3,\ \{y, xy, x^2y\}$                | $A_3,\ \{y, xy, x^2y\}$                | yes             |

(For the right cosets of $\{1, y\}$: $Hx = \{x, yx\} = \{x, x^2y\}$ and $Hx^2 = \{x^2, yx^2\} = \{x^2, xy\}$.)

So for a normal subgroup, "shift on the left" and "shift on the right" give the same tiling of the group. That's what later lets us turn the set of cosets itself into a group (the quotient group $G/N$).

---

## 8. The kernel is always normal

**Theorem.** If $\varphi : G \to G'$ is a homomorphism, then $\ker\varphi$ is a normal subgroup of $G$.

_Proof._ Let $k \in \ker\varphi$ and $g \in G$. Then
$$\varphi(gkg^{-1}) = \varphi(g)\,\varphi(k)\,\varphi(g)^{-1} = \varphi(g) \cdot 1' \cdot \varphi(g)^{-1} = 1'.$$
So $gkg^{-1} \in \ker\varphi$. $\blacksquare$

That's the whole proof, 1 line lol. But here's why it makes sense:

- **Invisibility is perspective-independent.** The kernel is what $\varphi$ can't see. If $k$ is invisible to $\varphi$, then "change perspective, do $k$, change back" is also invisible: $\varphi$ sees "change perspective", then nothing, then "change back", and those two cancel in $G'$.
- **The coset picture.** We saw that the cosets of $K = \ker\varphi$ are the fibers of $\varphi$. But the fiber containing $g$ can also be described as $Kg$ (because $\varphi(b) = \varphi(g) \iff bg^{-1} \in K$). So the fiber through $g$ equals both $gK$ and $Kg$, meaning $gK = Kg$. Left cosets = right cosets, so $K$ is normal by §7.2.

**Examples all at once:**

- $SL_n = \ker(\det)$ is normal in $GL_n$.
- $A_n = \ker(\operatorname{sign})$ is normal in $S_n$. In $S_3$ that's $A_3 = \{1, x, x^2\}$, matching what we found by hand.
- The unit circle $= \ker\lvert\cdot\rvert$ is normal in $\mathbb{C}^\times$ (this one is automatic, $\mathbb{C}^\times$ is abelian).

And this gives a slick proof that $\{1, y\}$ is **not** the kernel of any homomorphism out of $S_3$: it's not normal!

> Coming up: the converse is also true. Every normal subgroup is the kernel of some homomorphism, namely the map $G \to G/N$, $g \mapsto gN$. So "normal subgroup" and "kernel of a homomorphism" are really the same idea. :)

---

## Summary

| Concept                  | Definition                                 | Intuition                                                       |
| ------------------------ | ------------------------------------------ | --------------------------------------------------------------- |
| Homomorphism             | $\varphi(ab) = \varphi(a)\varphi(b)$       | a translator that respects grammar                              |
| Image                    | $\{\varphi(a)\}$, subgroup of $G'$         | what $\varphi$ can reach                                        |
| Kernel                   | $\{a : \varphi(a) = 1'\}$, subgroup of $G$ | what $\varphi$ can't see                                        |
| Image of $n \mapsto a^n$ | $\langle a \rangle$                        | every place reachable by stepping with $a$                      |
| Left coset               | $aH = \{ah\}$                              | $H$ shifted by $a$; for $H = \ker\varphi$, a fiber of $\varphi$ |
| Conjugate                | $gxg^{-1}$                                 | $x$ viewed from $g$'s perspective                               |
| Normal subgroup          | $gNg^{-1} = N$ for all $g$                 | looks the same from every perspective                           |
| $\ker\varphi$ is normal  | $\varphi(gkg^{-1}) = 1'$                   | invisible from any angle stays invisible                        |
