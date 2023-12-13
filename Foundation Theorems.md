# Foundations

Some topics not elaborated here:

- Gradient & Hessian

## Basic Vector Derivatives

- $f(x) = Ax$
  - $\nabla f = A$
- $f(x) = x^TAy$
  - $x^T A y = y^TA^Tx$
  - $\nabla f =y^TA^T$
- $f(x) = x^T A x$
  - $\nabla f = x^T(A + A^T)$
  - $\nabla ^2 f = (A + A^T)$
  - Notice if A is symmetric, those will be $2A$

## Taylor's Theorem

First order Taylor series approximation of $f$ around the point $x$

- If $f: \mathbb R^n \to \mathbb R$ is twice continuously differentiable

$$
f(y) = f(x) + \nabla f(x)^T(y-x)+\frac{1}{2}(y-x)^T\nabla^2f|_\xi(y-x)
$$

- $\xi = ty + (1-t)x$ where $t\in (0, 1)$



## Norms

### Vector Norms

**n-norm** to be
$$
||x||_n = (\sum_i |x_i|^n)^\frac{1}{n}
$$

### Matrix Norm

$$
||M|| = \max _{x\ne 0} \frac{||Mx||}{||x||}
$$

Consequence
$$
\forall z: ||Mz|| \le ||M|| \ ||z||
$$
