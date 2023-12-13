# Convexity



## Convex Functions

$f: \Omega \to \mathbb R$ is **convex** if $\forall x, y \in \Omega$ and $\forall \alpha \in [0, 1]$, we have

$$
f(\alpha x + (1-\alpha) y ) \le \alpha f(x) + (1-\alpha)f(y)
$$

### Equivalent Conditions for Convexity

1. If $f: \mathbb R^n \to \mathbb R$ is continuously differentiable then $f$ is **convex** <u>if and only if</u>:

   $\forall x$ and $\forall y\in \mathbb R^n$, we have
   
$$
f(y) \ge f(x) + \nabla f(x)^T (y-x)
$$

2. If $f$ is twice continuously differentiable, then $f$ is **convex** <u>if and only if</u>:

   $\forall x$, we have:

   $\nabla^2 f(x)$ is **positive semidefinite**

3. A differentiable function $f: \mathbb R^n \to \mathbb R$ is **convex** <u>if and only if</u>

   $\nabla f$ is **monotone**

#### Positive Semidefinite (PSD) and Positive Definite (PD)

A matrix $A \in \mathbb R ^{n\times n}$ is **positive semidefinite** (PSD) <u>if and only if</u>:

$$
x^T Ax\ge 0 \ \ \ \ \forall x\in \mathbb R^n
$$

##### Equivalent Condition

A matrix $A \in \mathbb R ^{n\times n}$ is **convex** <u>if and only if</u>:

$$
\lambda(A) \ge 0
$$

(All eigenvalues of A is greater or equal to 0)



##### Obtain Eigenvalue

1. For diagonal matrix, eigenvalues are the diagonal elements
2. Solve for $\det(A-\lambda I) = 0$



#### Monotone Function

A mapping $g: \mathbb R^n \to \mathbb R^n$ is called **monotone** if $\forall x, y \in \text{domain} (g)$

$$
(g(x) - g(y))^T(x-y) \ge 0
$$


## Convex Sets

A set $C$ is convex if $\forall x_1, x_2 \in C$ and $\forall \alpha\in [0, 1]$, we have

$$
\alpha x_1 + (1-\alpha)x_2 \in C
$$

### Properties

1. If $C_1$ and $C_2$ are convex sets, then $C_1 \cap C_2$ is a convex set
2. If $C_1$ and $C_2$ are convex sets,  $C_1 \cup C_2$ is not necessarily a convex set



## Strictly Convex Functions



## Strongly Convex Functions



1. 