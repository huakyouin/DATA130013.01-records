# 时间序列 HW03

`18300290007 加兴华`

## 3.2

### a

$$
\forall t\in N,
x_{t}=\phi x_{t-1}+w_{t}=\phi \{\phi x_{t-2}+w_{t-1}\}+w_t=\dots =\phi^{t-1}x_0+\sum^{t-1}_{i=0}\phi^i w_{t-i}=\sum^{t}_{i=0}\phi^i w_{t-i}
$$

### b

$$
E\left(x_{t}\right)=\sum^{t}_{i=0}\phi^i E(w_{t-i})=0
$$

### c

$$
\begin{array}{c}
& \forall t\in N,\\
&var\left(x_{t}\right) = \sum^{t}_{i = 0}\phi^{2i} var(w_{t-i}) = \sum^{t}_{i = 0}\phi^{2i}\sigma _w^2\\
\because &|\phi|<1\\
\therefore & \sum^{t}_{i = 0}\phi^{2i}=\frac{1-\phi ^{2(t+1)}}{1-\phi ^2}  \\
\therefore & var\left(x_{t}\right)=\frac{1-\phi ^{2(t+1)}}{1-\phi ^2}*\sigma _w^2
\end{array}
$$

### d

$$
\begin{eqnarray}
cov(x_{t+h},x_t)&= \phi ^h var(x_t)+\sum_{i=0}^{h-1}cov(\phi^iw_{t-i},x_t)=\phi ^h var(x_t)
\end{eqnarray}
$$

### e

$x_t$ 不平稳, 因为$var(x_t)$ 不是t的常值函数, 从而自相关函数也与t相关, 并非只与h相关, 因此不平稳.

### f

当$t\to \infty$ , $var(x_t)\to \frac{1}{1-\phi ^2}*\sigma_w^2$ 是t的常值函数, 从而自相关函数只与相关; 另一方面$E(x_t)$ 也为t的常值函数, 因此$x_t$ 渐进平稳.

### g

将生成的标准正态序列乘以$\sigma _w^2 $ 即可得到白噪声序列$w_t$.

然后可根据公式$x_t=\sum^{t}_{i=0}\phi^i w_{t-i}$ 获得一串非平稳AR(1)模型序列, 

再截取t>N(N为相当大的正数)的序列作为平稳AR(1)模型序列.

### h

$$
\begin{align}
x_{t}&=\phi x_{t-1}+w_{t}=\phi \{\phi x_{t-2}+w_{t-1}\}+w_t=\dots =\phi^{t-1}x_0+\sum^{t-1}_{i=0}\phi^i w_{t-i}\\
&=\frac{w_0\phi ^{t-1}}{\sqrt{1-\phi ^2}} +\sum^{t-1}_{i=0}\phi^i w_{t-i}\\
E(x_t)&=0,\\
var(x_t)&=\frac{var(w_0)\phi ^{2t-2}}{1-\phi ^2} +\sum^{t-1}_{i=0}\phi^{2i}var(w_{t-i})\\
&=\sigma_w^2\cdot(\frac{\phi ^{2t-2}}{1-\phi ^2}+\sum^{t-1}_{i=0}\phi^{2i})\\
&=\sigma_w^2\cdot\frac{1}{1-\phi ^2} \quad\text{是t的常值函数,}\\
cov(x_{t+h},x_t)&= \phi ^h var(x_t)+\sum_{i=0}^{h-1}cov(\phi^iw_{t-i},x_t)=\phi ^h var(x_t) \quad \text{是只和h相关的函数}
\end{align}
$$

由以上推导知: 新定义的$x_0$ 能让过程平稳. 

## 3.3

### a

$$
\begin{align}
x_{t}&=\phi x_{t-1}+w_{t}\\
\Rightarrow\quad x_t &= \phi^{-1} x_{t+1}-w_{t+1}\\
&=\dots\\
&=\phi^{-\infty}x_{+\infty}-\sum_{i=1}^{+\infty }\phi ^{-i}w_{t+i}\\
&=-\sum_{i=1}^{+\infty }\phi ^{-i}w_{t+i},\\
\Rightarrow\quad E(x_t) &=-\sum_{i=1}^{+\infty }\phi ^{-i}E(w_{t+i})=0,\\
var(x_t) &= \sum_{i=1}^{+\infty }\phi ^{-2i}var(w_{t+i})\\
&= \sigma _w^2 \cdot \frac{\phi ^{-2}}{1-\phi ^{-2}} ,\\
\Rightarrow cov(x_{t+h},x_t)&=\phi ^{-h}var(x_{t+h})+\sum_{i=1}^{h-1}cov(\phi ^{-i}w_{t+i},x_{t+h})\\
&= \phi ^{-h}var(x_{t+h})\\
&= \sigma_{w}^{2} \phi^{-2} \phi^{-h} /\left(1-\phi^{-2}\right)
\end{align}
$$

### b

$$
\begin{align}
y_t&=\phi^{-\infty}y_{-\infty}+\sum^{+\infty}_{i=0}\phi^{-i }w_{t-i}\\&=\sum^{+\infty}_{i=0}\phi^{-i }w_{t-i},\\
\Rightarrow\quad E(y_t)&=\sum^{+\infty}_{i=0}\phi^{-i }E(w_{t-i})=0,\\
var(y_t)&=\sum^{+\infty}_{i=0}\phi^{-2i }var(w_{t-i})\\
&=\sigma _w^2\phi^{-2} \cdot (\frac{1}{1-\phi^{-2}} ),\\
\Rightarrow\quad cov(y_{t+h},y_t)&=\phi ^{-h}var(y_t)+\sum_{i=0}^{h-1}cov(\phi ^iw_{t+i},y_{t})\\
&=\phi ^{-h}var(y_t)\\
&=\sigma_{w}^{2} \phi^{-2} \phi^{-h} /\left(1-\phi^{-2}\right)
\end{align}
$$

因此$y_t$ 的期望和自相关函数都与$x_t$ 的相同.

## 3.4

### a

$$
\begin{align}
&\left.\begin{matrix} 
  A(z)=1-0.8z+0.15z^2=(1-0.3z)(1+0.5z) \\  
  B(z)=1-0.3z
\end{matrix}\right\}\Rightarrow\quad (1+0.5 \mathscr B )(x_t)=w_t\\
\therefore &\text{该模型是AR(1)causal的、MA(0)invertible的}
\end{align}
$$

### b

$$
\begin{align}
&\left.\begin{matrix} 
  A(z)=1-z+0.5z^2 \Rightarrow z=1\pm i \text{在单位圆外} \\  
  B(z)=1-z \Rightarrow z=1 \text{在单位圆上}
\end{matrix}\right\}\Rightarrow\quad (1 -\mathscr B+0.5\mathscr{B}^2  )(x_t)=(1-\mathscr{B} )(w_t)\\
\therefore &\text{该模型是AR(2)causal的、MA(1)非invertible的}
\end{align}
$$

## 附加题

假设$y_t$ 为满足该等式的平稳解, 则: 
$$
\begin{align}
\qquad& y_t=\phi^ny_{t-n}+\sum^{n-1}_{i=0}\phi^iw_{t-i}, \quad\forall n\in N^*\\
\Rightarrow \quad& var(y_t-\phi^ny_{t-n})=var(\sum^{n-1}_{i=0}\phi^iw_{t-i}),\\
\Rightarrow \quad& var(y_t)+\phi^{2n}var(y_{t-n})-2\phi^ncov(y_t,y_{t-n})=\sum^{n-1}_{i=0}\phi^{2i}var(w_{t-i}),\\
\Rightarrow \quad& 2\phi^ncov(y_t,y_{t-n})+\sigma^2\sum^{n-1}_{i=0}\phi^{2i}=var(y_t)+\phi^{2n}var(y_{t-n}),\\
\because \quad& |\phi|=1 ,\ \therefore\phi^{2n}=\phi^{2i}=1, \ \forall i\in N\\
\\
\Rightarrow \quad& 2\gamma(0)-2\phi^n\gamma(n) =n\sigma^2，\quad (y_t平稳)\\
\\
\Rightarrow \quad& |2\gamma(0)|+|2\phi^n\gamma(n)| \geq|n\sigma^2|, \\
\\
又\because \quad&  |\gamma(n)|\leq |\gamma(0)|,\\
\\
\Rightarrow  \quad& 2|2\gamma(0)|\geq |2\gamma(0)|+|2\phi^n\gamma(n)| \geq|n\sigma^2|




\end{align}
$$
因为$y_t$ 平稳，不等式左边为常数；但右边随n增大趋于正无穷。因此不等式不恒成立，假设矛盾.

综上, 不存在平稳解.

