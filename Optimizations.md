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

Let $f: \mathbb R^n \to \mathbb R$ be convex and continuously differentiable, then $x^\*$ is a <u>global minimum</u>, <u>if and only if</u>

$$
\nabla f(x^*) = 0
$$

### L-Lipschitz

A function $f: \Omega \to \mathbb R$ is **L-Lipschitz** if $\forall x, y \in \Omega$:

$$
|f(x) - f(y)| \le L||x-y||
$$

#### Lemma

1. If $f$ is **L-Lipschitz**, convex, and differentiable, then

$$
||\nabla f(x) || \le L \ \ \ \forall x \in \Omega
$$

2. If $||\nabla f(x) || \le L \ \ \ \forall x \in \Omega$ then

$$
|f(x) - f(y) | \le L||x-y||
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



### Convergence Rate of Normal GD

Let $f$ be convex, differentiable, L-Lip. And let:

- $||x^{(0)} - x^*|| \le R$
- $||\nabla f(x)|| \le L$

Choose $\mu = \frac{R}{L\sqrt t}$

Then

$$
f(\frac{1}{t}\sum^{t-1}_{s=0}x^{(s)}) - f(x^*) \le \frac{RL}{\sqrt t}
$$

(converge with $\frac{1}{\sqrt t}$)



### Interpretation & Different Versions of GD

- By Taylor’s Theorem, GD can be viewed as assuming $\nabla ^2 f(\xi) \approx \frac{1}{\mu}I$

- GD can be viewed as: $f(x^{t+1}) = f(x^t) - \mu \vec p$. We want to choose correct $\vec p$ for $\frac{\nabla f(x^{(t)})^T\vec p}{||p||_2}$
  - using different **vector norms** for the denominator 

#### For 1-norm GD

Let $j^*$ be the entry of $\nabla f(x^{(t)})$ with largest magnitude

$\vec p$ is the gradient with only that entry and zero in every other entry

- Only move at the steepest direction

#### For inf-norm GD

$\vec p = -||\nabla f(x^{(t)})||_1  \ \text{sign}(\nabla f(x^{(t)}))$

- Move at every direction equally but with sign



### Backtracking Line Search GD

##### Armijo Condition

$$
f(x^{(t+1)}) \le f(x^{(t)}) - \mu ^{(t)} \gamma ||\nabla f(x^{(t)})||^2
$$

##### Algorithm

1. Fix $\gamma < 1, \beta < 1$
2. Start with $\mu = a$ (a constant)
3. Decrease $\mu$ by $\mu^{(t+1)} = \beta \mu^{(t)}$, until the **Armijo Condition** is met

#### Convergence of Backtracking Line Search

For an L-smooth convex function with $\mu^{(t)}$ set by backtracking line search, GD gives

$$
f(x^{(t)}) - f(x^*) \le \frac{1}{2t \min_{s=1, ..., t}(\mu^{(s)})}
$$

And $\min_{s=1, ..., t}(\mu^{(s)}) \ge \min (1, \frac{\beta}{L})$, which guarantees $f(x^{(t)}) - f(x^*) \le \frac{L}{2t\beta}$



### Constraint Gradient Descent

#### Constraint Optimization Problem

$$
\min f(x) \text{ subject to } x\in \Omega
$$

#### Projection

The projection of a point $x$ onto a set $\Omega$ is defined as the closest point in $\Omega$ to x, that is

$$
\Pi_\Omega (x) = \arg \min_{y\in \Omega} ||x-y||
$$

#### Projected Gradient Descent

$$
x^{(t+1)} = \Pi_\Omega (x^{(t)} - \mu^{(t)}\nabla f(x^{(t)}))
$$

##### Important Facts

Conditions: $\Omega \subset \mathbb R^n$ is convex, closed, not empty, and if $x\in\Omega, y\in \mathbb R^n$

1. $\Pi_\Omega (y)$ is unique
2. $\Pi_\Omega(\Pi_\Omega(y)) = \Pi_\Omega(y)$
3. $(\Pi_\Omega (y) - x)^T(\Pi_\Omega(y) - y) \le 0$ 
4. $||\Pi_\Omega (y) -x||^2 + ||y-\Pi_\Omega(y)||^2 \le ||y-x||^2$
5. $||\Pi_\Omega(y) -x || \le ||y-x||$



### Convergence of L-Smooth GD

If $f: \mathbb R^n \to \mathbb R$ is L-smooth, convex, and $0 \le \mu \le \frac{1}{L}$, then GD gives

$$
f(x^{(t)}) - f(x^*) \le \frac{1}{2t\mu} ||x^{(0)} - x^*||
$$

(converge with $\frac{1}{t}$)

##### L-Smooth

A function is L-Smooth if its gradient is L-Lips



### Convergence of Strongly Convex GD

(Check definitions in convexity)

If $||\nabla^2F|| \le L$, $\alpha = \frac{1}{L}$

$$
F(x^{(t)}) - F(x*) \le (1 - \frac{c}{L})^t[F(x^{(0)})- F(x^*)] 
$$

- $\frac{L}{C}=\kappa$, condition number

### Accelerate Gradient Descent

#### GD with Momentum

$$
x^{(t+1)} = x^{(t)} - \mu \nabla f(x^{(t)}) + \beta (x^{(t)} - x^{(t-1)})
$$

##### Analysis for general quadratics on GD

$$
||x^{(t+1)} - x^*|| \le \max \{1-\mu \lambda_\min, \mu\lambda_\max - 1\}^t ||x^{(0)}||
$$

- The optimal choice: $\mu^* = \frac{2}{\lambda_\max + \lambda_\min}$
- This will lead to rate of convergence $= \frac{\lambda_\max - \lambda_\min}{\lambda_\max + \lambda_\min}$
- Defining that $\kappa = \frac{\lambda_\max}{\lambda_\min}$
- We will have rate of convergence $=\frac{\kappa - 1}{\kappa +1}$
  - Large $\kappa$ will slow the convergence

##### The case for GD with momentum

- rate of convergence $=\frac{\sqrt \kappa -1}{\sqrt \kappa + 1}$
  - Accelerated compare to GD



#### GD with Nesterov’s Acceleration

$$
x^{(t+1)} = x^{(t)} + \beta (x^{(t)} - x^{(t-1)}) - \mu \nabla f(x^{(t)} + \beta(x^{(t)}- x^{(t-1)}))
$$

- Converges at an accelerated rate for any convex problem

## Newton’s Method

Derived by Second Order Expansion of Taylor Theorem, taking derivative and set to zero

$$
x^{(t+1)} = x^{(t)} - [\nabla ^2 f(x^{(t)})]^{-1} \nabla f(x^{(t)})
$$

### Convergence of Newton’s Method

Conditions:

- Let $f$ be twice continuously differentiable
- suppose $x^\*$ has $\nabla f(x^\*) = 0$
- $||\nabla^2f(x^\*)^{-1}|| \le \frac{1}{h}$ for some h > 0
- $||\nabla^2 f(x) - \nabla ^2 f(x^\*)|| \le L||x-x^\*|| \ \ \ \forall x$
- if $||x^{(0)} - x^*|| \le \frac{2h}{3L}$
- and $x^{(t+1)} = x^{(t)} - [\nabla ^2 f(x^{(t)})]^{-1} \nabla f(x^{(t)})$

We have

$$
||x^{(t)} - x^*|| \le \frac{2h}{3L}  \ \ \ \ \forall t
$$

$$
||x^{(t+1)} - x^\*|| \le \frac{3L}{2h}||x^{(t)} - x^\*||^2 \ \ \ \forall t
$$

- Converges exponentially to the optimal

### Remarks

- Newton’s method require hessian invertible (also is expensive)
- Newton’s method may not always converge



## Conjugate Gradient Methods

### Conjugate vectors

A set of vectors $\{p_1, ..., p_n\}$ is conjugate w.r.t. A (symmetric, positive definite) if 

$$
p_i^TAp_j = 0 \ \ \ \ \ \forall i\ne j
$$

### C.G. Method

$$
x^{(t+1)} = x^{(t)} + \alpha _t p_t
$$

- where $\alpha = \arg \min_{a \in \mathbb R} \phi (x_t + ap_t)$

#### For Quadratic

$$
\alpha = \frac{(b-Ax^{(t)})^T p_t}{p_t^TAp_t} (= \frac{-\nabla \phi (x^{(t)})^Tp_t}{p_t^TAp_t})
$$

### Convergence Rate

For any $x^{(0)}$ with conjugate vectors, CG method guaranteed to converge to $x^*$ in at most $n$ steps ($n$ is the number of conjugate vectors)



### Algorithm Version 0

- Initialize $x^{(0)}$, set $p_0 = - \nabla \Phi (x^{(0)})$
- for $t=1, 2, ...$
  - $\beta_t = \frac{p_{t-1}^T A \nabla \Phi(x^{(t)})}{p_{t-1}^TAp_{t-1}}$
  - $p_t = -\nabla \Phi(x^{(t)}) + \beta_t p_{t-1}$
  - $\alpha_t = - \frac{\nabla \Phi (x^{(t)})^Tp_t}{p_t^TAp_t}$
  - $x^{(t+1)} = x^{(t)} + \alpha_t p_t$



### Algorithm Version 1

- Initialize $x^{(0)}$, set $r_0 = Ax^{(0)} - b = \nabla \Phi(x^{(0)})$, $p_0 = - r_0$
- for $t=1, 2, ...$
  - $\alpha_t = \frac{r_t^T r_t}{p_t^TAp_t}$
  - $x^{(t+1)} = x^{(t)} + \alpha_t p_t$
  - $r_{t+1} = r_t + \alpha_t Ap_t$
  - $\beta \_{t+1} = \frac{r_{t+1}^T r_{t+1}}{r_t^Tr_t}$
  - $p_{t+1} = -r_{t+1} + \beta_{t+1}p_t$

