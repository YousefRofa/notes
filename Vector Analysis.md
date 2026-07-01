Dot products and cross products are both distributive, however dot products are commutative while cross products are not.

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
