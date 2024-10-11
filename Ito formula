{%hackmd @Hipp0/Hippotumuxthem %}

# Diffusion Model

> we will learning Ito's formula
- 1D Ito formula 
- Muti-dimensional Ito formula 

In the last chaper, we learn how to use Euler-maruyama formula to solve Ito's process. and we just solve $\int_0^t dW_s$. If we want solve $\int_0^t s dW_s$ ? Then we need Ito's formula.

> We usually use fundamental theorem of calculus, and now we are in stochastic calculus, Ito's formula play the same role here.


## 1D Ito formula 

Let $X_t$ be an Ito process given by 
$dX_t = fdt + GdW_t$ Let $\phi (x, t) \in \mathbb{C} (\mathbb{R} \times [0, \infty])$ Then 

$Y_t  = \phi (X_t, t)$ is again an Ito process. And 

$$dY_t \space (or \space d\phi) = \frac{\partial \phi}{\partial t}(X_t, t) dt + \frac{\partial \phi}{\partial X}(X_t, t) + \frac{1}{2} \frac{\partial ^2 \phi}{\partial X^2}(X_t , t) (dX_t)^2$$

where $(dX_t)^2 = dX_t dX_t$ is computed by the rules
$$dtdt = dtdW_t = dW_t dt = 0$$
$$dW_t dW_t = dt$$
> (Ito integral version of the chain rule)

So $dX_t dX_t = (fdt + GdW_t)(fdt + GdW_t) = G^2 dt$


### Example 

What is $\int_0^t s dW_s$ ? 

Let $\phi(x, t) = tx$ ,recall $d\phi = \frac{\partial \phi}{\partial t} dt + \frac{\partial \phi}{\partial x} dx + \frac{1}{2} \frac{\partial^2 \phi}{\partial x^2} (dx)^2$

Let $Y_t = \phi (W_t, t) = tW_t$ then $dY_t = W_t dt + t dW_t$

$\therefore \int_0^t dY_s = \int_0^t W_s ds + \int_0^t s dW_s$
$\Rightarrow t W_t = \int_0^t W_s d_s + \int_0^t s dW_s$
$\Rightarrow \int_0^t s dW_s = tW_t - \int_0^t W_s ds$
> like integration by parts.

Thm: Suppose $f$ is cont. and if bounded variation in $[0, t]$ Then 

$\int_0^t f(s) dW_s = f(t) W_t - \int_0^t W_s df_s$
($= f(t)W_t - \int_0^t W_s f'(s) ds$ if $f$ is diff.)

### Example2 

We say it is like integration by parts.
Is $\int_0^t W_s dW_s = \frac{1}{2} W_t^2$ ? (No!)

By Ito's formula, we have 

Let $X_t = W_t$ and $\phi (x) = \frac{x^2}{2} \Rightarrow Y_t = \phi (W_t) = \frac{1}{2} W_t^2$

By Ito's formula, we have 

$d\phi = \frac{\partial \phi}{\partial t} dt + \frac{\partial \phi}{\partial x} dx + \frac{1}{2} \frac{\partial ^2 \phi}{\partial x^2}(dx)^2$
$\space \space = 0 + x dx + \frac{1}{2} (dx)^2$

$dY_t = W_t dW_t + \frac{1}{2} (dW_t)^2 = W_t dW_t + \frac{1}{2} dt$


$\therefore \frac{1}{2} W_t^2 - \frac{1}{2} 0^2 = \int_0^t W_s dW_s + \int_0^t \frac{1}{2} ds = \int_0^t W_s dW_s + \frac{1}{2} t$
$\therefore \int_0^t W_s dW_s = \frac{1}{2} W_t^2 - \frac{t}{2}$

## Muti-dimensional Ito formula 

Assume X(t) is an d-dimensional

Ito process: $dX = fdt + GdW$. Namely, 

\begin{align*}
&X_1 = f_1 dt + G_{11} dW_1 + G_{12}dW_2 + \cdots + G_{1d}dW_d\\
&X_2 = f_2 dt + G_{21} dW_1 + G_{22}dW_2 + \cdots + G_{2d}dW_d\\
&\vdots\\
&X_d = f_d dt + G_{d1} dW_1 + G_{d2}dW_2 + \cdots + G_{dd}dW_d
\end{align*}

Let $\phi (x, t) = \begin{pmatrix} \phi_1 (x, t) \\ \phi_2(x,t) \\ \vdots \\\phi_n(x, t)  \end{pmatrix}$ be a $C^2$ map from $\mathbb{R}^d \times [0, \infty) \rightarrow \mathbb{R}^n$

Them the process $Y =\phi (X(t), t)$ is again an Ito process whose component $Y_k$ is given by 

$$dY_k = \frac{\partial \phi_k}{\partial t}(x, t) dt + \sum_{i=1}^d \frac{\partial \phi_k}{\partial x_i} (x, t) dX_i + \frac{1}{2} \sum_{i, j}^d \frac{\partial^2 \phi_k}{\partial x_i \partial x_j}(x, t) dX_i dX_j$$

where $dt dt = 0, \hspace{0.3cm} dW_i dt = dW_i dt = 0, \hspace{0.3cm} dW_i dW_j = \delta_{i,j}dt$ ($dWdW^T = Idt$)


### Example (vector case)

Consider $\begin{cases} dX_t = dW_t \\ X(0) = 0 \end{cases} \Rightarrow X_t = W_t \sim N(0, tI)$

Hense, its pdf is $p(x, t) =  \frac{1}{(2\pi t)^{\frac{d}{2}}}  e^{-\frac{\Vert x^2 \Vert}{2t}}$

And $\begin{cases} \frac{\partial p}{\partial t} = \frac{1}{2} \Delta p \\ \lim\limits_{t\rightarrow 0} p(x, t) = \delta(x) \end{cases}$

Laplace operator$\Delta$ 
$\Delta P(x_1, x_2, x_3, t) = P_{x_1x_1} + P_{x_2x_2} + P_{x_3x_3}$


### Example

$\begin{cases} dX_t = \Sigma ^{\frac{1}{2}} dW_t \\ X(0) = X_0 \end{cases}$ with $\Sigma ⪰ 0$ : const matrix (半正定)

> ![image](https://hackmd.io/_uploads/H1LiNEDTA.png)

$\Rightarrow X_t = X_0 + \Sigma^{\frac{1}{2}} \int_0^t dW_s = X_0 + \Sigma^{\frac{1}{2}}W_t$

If $X_0$ is const. vector, then $E[X_t] = X_0, \space Cov[X_t] = \Sigma Cov(W_t) = t \Sigma$.

If $X_0 \sim N(\mu_0, \Sigma_0)$ then $E[X_t] = \mu_0, \space Cov[X_t] = \Sigma_0 + t \Sigma$


### Example 

$\begin{cases} dX_t = fdt + \Sigma ^{\frac{1}{2}} dW_t \\ X(0) = X_0 \end{cases}$ with $\Sigma ⪰ 0$ : const matrix, $f \in \mathbb{R}^d$ is const. vector 

$\Rightarrow X_t = X_0 + \int_0^t f ds +\Sigma^{\frac{1}{2}} \int_0^t dW_s = X_0 + ft +\Sigma^{\frac{1}{2}}W_t$

If $X_0 \sim N(\mu_0, \Sigma_0)$ then 
$E[X_t] = E[X_0] + ft = \mu_0 + ft$ 
$Cov[X_t] = Cov[x_0] + \Sigma Cov[W_t] = \Sigma_0 + t \Sigma$

### Example

$\begin{cases} dX_t = F X_t dt + G dW_t \\ X(0) \sim N(\mu_0, \Sigma_0) \end{cases}$ with $F \in \mathbb{R}^{d \times d}$, $G \in \mathbb{R}^{d \times d}$ is const. vector 

We can only obtain $X_t = X_0 + \int_0^t F X_s ds + \int_0^t G dW_s$.

Let $\phi (x, t) = e^{-Ft} x$, by Ito's formula, 

![image](https://hackmd.io/_uploads/HkMgs4waC.png)
![image](https://hackmd.io/_uploads/HyAliEPaC.png)
![image](https://hackmd.io/_uploads/S1CZoEPpC.png)
![image](https://hackmd.io/_uploads/BJpzoNv6C.png)
![image](https://hackmd.io/_uploads/Sko0hVDTC.png)

