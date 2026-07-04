 Dot products and cross products are both distributive, however dot products are commutative while cross products are not. (Are they associative though?)

We can prove the distributivity of cross and dot products for 3 vectors when they are coplanar, then extend that to the general case.


Let $\vec{a}, \vec{b}, \vec{c}$ lie on the plane $\Pi$ with a fixed unit normal $\hat{n}$, then:

$$
\vec{a} \cdot \vec{v} = \vert\vec{a} \vert \vert \vec{v}\vert \sin{\theta_v}
\qquad 
\vec{a} \times \vec{v} = \vert\vec{a} \vert \vert \vec{v}\vert \cos{\theta_v}
$$

The key lemma is that dot and cross products are **extractors**, that is:

$$
v_{\vert \vert} = v\cos{\theta_v} \qquad v_{\perp} = v\sin{\theta_v}
$$

Where these correspond to the perpendicular and parallel components of the vector v with respect to the vector a.

Hence:
$$

\vec{a} \cdot \vec{v} = \vert\vec{a} \vert v_{\vert\vert}
\qquad 
\vec{a} \times \vec{v} = \vert\vec{a} \vert v_{\perp} \hat{n}
$$

This makes the matter easier as all we need to show now is that:

$$
(\vec{b}+\vec{c})_{\vert \vert} = b_{\vert \vert}+ c_{\vert \vert}\quad and \quad (\vec{b}+\vec{c})_{\perp } = b_{\perp}+ c_{\perp}
$$

Which can be easily seen through a graph 
![[dot_product_projection_additivity.png]]

---

We usually don't interpret why the dot product works the way it does, and proceed by merely memorizing the fact that its multiplying each component from a vector to the one it corresponds to in the other vector and add them all together, the reason it behaves that way is due to how the unit vectors are mutually perpendicular:

$$
\hat{x} \cdot \hat{x} = \hat{y} \cdot \hat{y} =\hat{z} \cdot \hat{z}=1 \qquad \hat{x}\cdot \hat{y} = \hat{y} \cdot \hat{z} = \hat{z} \cdot \hat{x} = 0
$$

So distributing each terms leaves only the ones that corresponds to the same unit basis vector direction staying.
The same applies for cross products which is why $\vec{A} \times \vec{B}$ doesn't have any terms corresponding to $A_xB_x$, $A_yB_y$ ,or $A_zB_z$ in any of the basis directions.

---

## Triple products
### Scalar Triple Product

*Multiply* three things, get a scalar.

Since a cross product results in a vector that with a length corresponding to the area of the two vectors crossed, taking the dot product of a cross product results in the volume of a parallelepiped. Since that volume is the same regardless how we measure it, evidently:

$$
A \cdot (B \times C) = B \cdot (C \times A) = C \cdot (A \times B) 
$$

While conserving the **alphabetical order** to keep the sign right, the corresponding formulas with non alphabetical order results in the negative of those value(s?).

> Hence we deduce that the dot and cross product are interchangeable as long as the parentheses are placed correctly
> $$ A\cdot (B \times C) = (A \times B) \cdot C$$


### Vector Triple Product

*Multiply* three things, get a vector.

