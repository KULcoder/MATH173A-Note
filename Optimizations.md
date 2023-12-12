# Optimizations

## Important Theorems for Optimality

#### Guarantee on Global Solution

For convex functions defined on convex sets, local minima are global minima

#### Necessary Condition for Optimality

1. If $f$ is continuously differentiable & $x^*$ is a local min, then

   $\nabla f(x^*) = 0$

2. If $\nabla^2 f$ is continuous and $x^*$ is a local minimum, then

   $\nabla^2 f(x^*) \succeq 0$ (PSD)

#### Sufficient Condition for Optimality

If $f$ is twice continuously differentiable, and $x^*$ satisfies:

- $\nabla f(x^*) = 0$
- $\nabla ^ 2 f(x^*) \succ 0$

then $x^*$ is a local minimum

#### Formal Statement on Global Solution

Let $f: \mathbb R^n \to \mathbb R$ be convex and continuously differentiable, then $x^*$ is a <u>global minimum</u>, <u>if and only if</u>
$$
\nabla f(x^*) = 0
$$


## Gradient Descent

#### **Descent Direction**

$\vec v \in \mathbb R^n$ is a descent direction for $f: \mathbb R^n \to \mathbb R$ at $x$ if $<\vec v, \nabla f|_x>  \ < \ 0$

### Algorithm

- Choose $x^{(0)} \in \mathbb R^n$
- for $t= 1, 2 ,3, ...$ (till stopping criterion)
  - Set $x^{(t+1)} = x^{(t)} - \mu^{(t)}\nabla f(x^{(t)})$



#### Stopping Conditions

- Max iterations
- Small $||x_t - x_{t-1}||$



### Constraint Gradient Descent



### Accelerate Gradient Descent



## Newton’s Method



## Conjugate Gradient Methods



