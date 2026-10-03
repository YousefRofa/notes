Griffith 71: You can only have discontinuity in the first derivative of the wave function when the potential goes to infinity. If the potential just changes like in the case of a finite well then you cant have a discontinuity. You can show such a thing by solving the TISE w a small epsilon and taking the limit.
Because otherwise $\psi$ wouldn't solve the Schrödinger equation at the boundary. It's not an extra rule; it's forced by the equation.

The TISE says:

$$\psi'' = \frac{2m}{\hbar^2}\,(V - E)\,\psi$$

At a boundary like $x = a$ in the finite well, $V$ jumps from $-V_0$ to $0$, but it stays finite. So the right side is finite, which means $\psi''$ is finite there.

If $\psi'$ jumped at $x = a$, the slope would change by a finite amount over zero distance. That requires an infinite $\psi''$ at that point, a delta-function spike. The right side has no spike to match it, so the equation would fail at $x = a$. A kinked $\psi$ at a finite step isn't a solution.
