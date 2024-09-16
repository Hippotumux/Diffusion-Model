{%hackmd @Hipp0/Hippotumuxthem %}

# Diffusion Model

> we will learning forward process
- Preliminary
- Ito process
- Euler-Maruyama method

## Discrete random variable (離散隨機變數)

$x = 0, 1, ..., n$ or $x = 0, 1, ...$

### probability distribution: 

$$0 <= P(x) <= 1 \space \space \forall x$$ 
$$\sum_xP(x) = 1$$

### cumulative distribution: 

$$F(a) = P(x \leq a) = \sum_{x \leq a} P(x)$$
$$F(a \leq x \leq b) = F(b) - F(a)$$

### expectation:

$$E(x) = \mu = \sum_x xP(x)$$

### variance:

$$Var(x) = \sigma^2 = E((x - \mu)^2) = E(x^2) - E(x)^2$$

## Continuous random variable

$a \leq x \leq b$ or $a \leq x$ or $x \leq b$ or $-\infty < x < \infty$

### probability distribution: 

$$0 \leq f(x) \leq 1 \space \space \forall x$$

$$\int_{\mathbb{R}} f(x) dx = 1, \space P(x = x) = 0$$

### cumulative distribution function 

$$F(a) = P(x \leq a) = P(x < a) = \int_{-\infty}^a f(x) dx$$

$$F(a \leq x \leq b) = \int_a^b f(x) dx$$

### expectation 

$$E(x) = \mu = \int_{-\infty}^{\infty} xf(x) dx$$

### variance:

$$Var(x) = \sigma^2 = E(\int_{-\infty}^{\infty}  (x - \mu)^2 f(x) dx = E(x^2) - E(x)^2$$

## Property of Expectation

![image](https://hackmd.io/_uploads/Hkta64m6A.png)

## Property of Variance

![image](https://hackmd.io/_uploads/HJPWAEmaR.png)



## (Stochastic Differentail Equations) SDEs

### Ito SDE (forward process)

\begin{cases}
dX_t = f(X_t, t) dt + G(X_t, t) dW_t \\
X(0) = X_0 
\end{cases}

$$X_t \in \mathbb{R}^d, f \in \mathbb{R}^d, G\in \mathbb{R}^{d \times d}$$

If there is no $G$, then it's an "deterministic" DE
therefore, $G$ has the random factor $dW_t$.

The solution of the Ito SDE cna be formally written as 

$$X_t = X_0 + \int_0^t f(X_s, s) ds + \int_0^t G(X_s, s) dW_s$$ (Ito integral equation)

Def: A stochastic is a parametinize collection of random variables $\{ X_t \}_{t \in T}$ defined on a probability space ($\Omega, F, p$) and assuming values in $\mathbb{R}^d$


![image](https://hackmd.io/_uploads/rknwANXaR.png)

> Next we will explaim dWt (random factor)

## Weiner Process (Brownian motion)

$W_t \in \mathbb{R}^d$ is a constant stochastic process with the following properties

- Any incerment $\Delta W_t = W(t + \Delta t) - W(t)$ is a zero mean Gaussian random variable with covariance $\Delta t I$ 
    $$W(t_0 + t) - W(t_0) \sim N(0, tI)$$
- When the time spans of in crement do not overlap, the increments are independent, i.e, 
    $$W_{t_1}, W_{t_2-t_1}, W_{t_3-t_2}$$ are independent with $$t_1 < t_2 < t_3$$
- $W_0 = W(0) \equiv 0$ the process starts at the origin

Brownian motion: $t \mapsto W(t)$ is nowhere diff.
But we can use White noise which can be considered at the formal derivative $h(t) = \frac{dW}{dt}$

## White noise process

A white noise process $h(t) \in \mathbb{R}^d$ in a "random" function with the following properties: 

- The two values are $h(t)$ and $h(t')$ are independent if $t \neq t'$
- The mapping $t \mapsto h(t)$ is a Gaussian process with zero mean and Dirac Delta correlation:
    1. $E[h(t)] = 0$
    2. $E[h(t)h^T(s)] = \delta (t-s) I$ (cov. $\in \mathbb{R}^{d \times d}$)
    
The sample path $t \mapsto h(t)$ is discontinuous almost everywhere. so White noise is unbounded and it takes arbitrarily large positive and negative value at finite interval.

> How to intepret $\int_0^t G(X_s,s)dW_s  = \int_0^t G(X(s),s)dW(s) = \int_0^t G(X(s),s)W'(s)ds$ (white noise)

Ito integral:
$$\int_0^t G(X(s),s)dW_s = \lim_{n \rightarrow \infty} \sum_{k=0}^{n-1} G(X(t_k),t_k)[W(t_{k+1}) - W(t_k)]$$

### Gaussion distribution

- PDF
$$f(\mu, \sigma^2) = \frac{1}{\sqrt{2\pi}\sigma} e ^{\frac{-(x-\mu)^2}{\sigma^2}}$$
- Expectation
$$E(W_t) = \int_{-\infty}^{\infty} xf(0, t) dx = 0$$

備註: 
![image](https://hackmd.io/_uploads/rJ8nSB7pA.png)
![image](https://hackmd.io/_uploads/ryXgLSXT0.png)
![image](https://hackmd.io/_uploads/S1SHIrmTC.png)

## Euler-Maruyama method

> to solve SDE

Recall the SDE:

\begin{cases}
dX_t = f(X_t, t) dt + G(X_t, t) dW_t \\
X(0) = X_0 
\end{cases}

$$X_t = X_0 + \int_0^t f(X_s, s) ds + \int_0^t G(X_s, s) dW_s$$

### Euler-Maruyama method

$$\hat X (t_{n+1}) = \hat X (t_n) + \int_0^t f(\hat X (t_n), t_n) \Delta t + \int_0^t G(\hat X (t_n), t_n) \Delta W (t_n)$$

where $$t_n = n \Delta t, \Delta W(t_n) = W(t_{n+1}) - W (t_n) = W(t_n + \Delta t) - W(t_n) \sim N(0, \Delta t I) = \sqrt{\Delta t}N(0, I)$$

or $$\hat X (t_{n+1}) = \hat X (t_n) + \int_0^t f(\hat X (t_n), t_n) \Delta t + \int_0^t G(\hat X (t_n), t_n) \sqrt{\Delta t} Z(t_n)$$

Note: In particular, when $\sigma = 1, X_0 = 0$, we have $X(t) = W_t \sim N(0, t)$ with the PDF $p(x, t) = \frac{1}{\sqrt{2 \pi t}} e^{-\frac{x^2}{2t}}$. One can check that $p$ fulfills 

\begin{cases}
\frac{\partial p}{\partial t} = \frac{1}{2} \frac{\partial ^2 p}{\partial x^2}\\
\lim\limits_{t \rightarrow 0} \space p(x, t) = p_0(x) = \delta(x)
\end{cases}

which is called $\color{red}{Fokker-Planck \space equation}$ and also form of a simplest diffusion equation.


### Ornstein-Uhlenbeck Process

> To make image noise

\begin{cases}
dX_t = -\beta X_t dt + \sigma dW_t , \space \beta, \sigma > 0\\
X(0) = X_0 \space : constant \space or \space r.m. \space variable
\end{cases}

Integral, then

$$X(t) = X_0 + \int_0^t -\beta X_s ds + \int_0^t \sigma d W_s$$
$$= X_0 - \int_0^t \beta X_s ds + \sigma W_t$$

and $\int_0^t \beta X_s d_s$ now explicitly solved, now try the method of ODE:

$dX = -\beta X d_t + \sigma dW$
$\Rightarrow e^{\beta t} dX + e^{\beta t} \beta X dt = \sigma e^{\beta t} dW$

($\phi = e^{\beta t} \beta X d_t = \sigma e^{\beta t} dW$, $d\phi = \frac{\partial \phi}{\partial t} dt + \frac{\partial \phi}{\partial X} dX = \beta e^{\beta ^t}Xd_t + e^{\beta t} dX$)

$\Rightarrow d(e^{\beta t}) x = e^{\beta t} \sigma dW$
$\Rightarrow e^{\beta t} X - X(0) = \int_0^t e^{\beta s} \sigma dW_s$

$\therefore X(t) = e^{-\beta t} X(0) + \sigma \int_0^t e^{-\beta(t-s)} dW_s$
$\Rightarrow E[X(w)] = e^{\beta t} X(0)$
$Var[X(t)] = \frac{\sigma^2}{2\beta}(1-e^{-2\beta t})$

> Variance
![image](https://hackmd.io/_uploads/rk4sWlI6C.png)


If $X(0) = X_0$ is constant, then $X_t \sim N(e^{\beta t} X(0), \frac{\sigma^2}{2\beta}(1-e^{-2\beta t}))$

If $X(0) \sim N(\mu_0, \sigma_0^2)$, then $X_t \sim N(\mu_t, \sigma_t^2)$, where
$\mu_t = e^{\beta t} \mu_0, \sigma_t^2 = e^{-2\beta t} \sigma_0^2 + \frac{\sigma^2}{2\beta}(1-e^{-2\beta t})$


In particular, if $X(0) = X_0 = 0$, then $X_t \sim N(0, \frac{\sigma^2}{2\beta}(1-e^{-2\beta t}))$.
The PDF is $p(x, t) = \frac{1}{\sqrt{2 \pi} \sigma_t} e^{-\frac{x^2}{2\sigma_t^2}}$, where $\sigma_t^2 = \frac{\sigma^2}{2\beta}(1-e^{-2\beta t})$

Check: $p(x,t)$ satisfies

$\frac{\partial p}{\partial t} = -\frac{\partial}{\partial x}(-\beta X p) + \frac{\sigma^2}{2} \frac{\partial ^2 p}{\partial x^2} = \beta \frac{\partial p}{\partial x} + \beta p + \frac{\sigma^2}{2} \frac{\partial ^2 p}{\partial x^2}$
> How to solve? hard 

:::danger
This is also an Fokker–Planck equation, this is important in SDE. (We can deduce some function from F-P equation) It help us to solve reverse process.
:::


> drift term : $\beta \frac{\partial p}{\partial x} + \beta p$
diffusion term : $\frac{\sigma^2}{2} \frac{\partial ^2 p}{\partial x^2}$
