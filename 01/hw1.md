# 时间序列 HW1

`18300290007 加兴华`

## Pb 1.2

### a

```R
s = c(rep(0,100), 10*exp(-(1:100)/20)*cos(2*pi*1:100/4))
x = s + rnorm(200)
plot.ts(x)
```

<img src="E:\华为云盘\2022春\时间序列\作业\01\hw1.assets\image-20220312131717958.png" alt="image-20220312131717958" style="zoom: 33%;" />

### b

```R
s = c(rep(0,100), 10*exp(-(1:100)/200)*cos(2*pi*1:100/4))
x = s + rnorm(200)
plot.ts(x)
```

<img src="E:\华为云盘\2022春\时间序列\作业\01\hw1.assets\image-20220312131811061.png" alt="image-20220312131811061" style="zoom: 33%;" />

### c

t=0:100 时，(a)(b)均与地震序列的前半段接近；t=101:200 时,(a)与爆炸的后半段相近呈现快速衰减 而(b)与地震的后半段相近呈现不衰减或极缓慢地衰减



```R
s =  exp(-(1:100)/20)
plot.ts(s,col=1)
s =  exp(-(1:100)/200)
lines(s,col=6,lty=2)
legend('topright', inset=.02, title="legend", c("exp{t/20}","exp{t/200}"),lty=c(1, 2), col=c(1,6))
```

<img src="E:\华为云盘\2022春\时间序列\作业\01\hw1.assets\image-20220312135545862.png" alt="image-20220312135545862" style="zoom: 33%;" />

可以观察出，(a)比(b)下降快很多，另外(a)的下降速率由快变慢而(b)的下降速率则相对平稳



## Pb 1.5

### a


$$
\mu_{t}=E x_{t}=E s_{t}+E w_{t}=s_{t}  \qquad (w_{t}\sim WN\Rightarrow E w_{t}=0)
$$
<img src="E:\华为云盘\2022春\时间序列\作业\01\hw1.assets\image-20220312140139159.png" alt="image-20220312140139159" style="zoom: 33%;" />

### b

$$
\gamma(s, t)=\mathrm{E}\left[\left(x_{s}-\mu_{s}\right)\left(x_{t}-\mu_{t}\right)\right]=\mathrm{E}[w_{s} w_t]=\{\begin{matrix} 
  1,\quad s=t \\  
  0,\quad o.w
\end{matrix}
$$

## Pb 1.8

### a

$$
\begin{array}{l} 
  \left\{\begin{matrix} 
  x_{t}-x_{t-1} & = & \delta+w_{t}, \\  
  \vdots \\
  x_{1}-x_{0} & = & \delta+w_{1},
\end{matrix}\right.  
\\
\\
\Rightarrow x_{t}-x_{0} = \delta\cdot t+\sum _{1}^{t}w_i=x_t
\end{array}
$$

### b

$$
\mu(t)=E(x_t)=E(\delta\cdot t+\sum _{1}^{t}w_i)=\delta\cdot t+\sum _{1}^{t}E(w_i)=\delta\cdot t\\
\gamma(s, t)=E[(x_s-\mu_s)(x_t-\mu_t)]=E[(\sum _{1}^{s}w_k)(\sum _{1}^{t}w_i)]=E[\sum _{1}^{t\wedge s}w_i^2+\sum _{k,j}w_kw_j]=t\wedge s
$$

### c

平稳性要求$x_t-x_s\sim x_{t-s}$ ,从方差来看 $V(x_t-x_s)=t^2+s^2-2Cov(x_t,x_s)=t^2+s^2-2(t\wedge s),V(x_{t-s})=(t-s)^2 $ 并不相等,所以不平稳

### d

$$
\begin{align}
\rho_{x}(t-1, t) & = \frac{\gamma(t-1, t)}{\sqrt{\gamma(t-1, t-1) \gamma(t, t)}}\\
&= \frac{t-1}{\sqrt{(t-1)t} } \\
&= \sqrt{\frac{t-1}{t} }\longrightarrow 1
\end{align}
$$

说明随着t的增大，序列中相邻变量的相关程度越来越大

### e

$$
y_t\doteq x_t-x_{t-1}=\delta +w_t\\
u_y(t)=E(y_t)=\delta \equiv Const \\
\gamma(y_s,y_t)=E[(y_s-\mu_y(s))(y_t-\mu_y(t))]=E[w_sw_t]=I(|t-s|=0)\\
\therefore |t-s|\longmapsto \gamma(y_s,y_t)
$$

均值函数为常数且$\gamma(y_s,y_t)$只由|t-s|决定，因此是平稳的。

## Pb 1.25

### a

假设$x_t$是某一平稳分布序列，则：
$$
\begin{eqnarray}
&& Var(\sum_1^n a_ix_{i})\geq 0,\\
\Longrightarrow && \sum_i\sum_ja_iCov(x_{i},x_{j})a_j\geq 0,\\
\because \  && \{x_t\}\mathbf{为平稳分布序列} \\
\therefore \  && \gamma (i-j)=\gamma (x_{i},x_{j})=Cov(x_{i},x_{j}),\\
\therefore \ && \sum_i\sum_ja_i\gamma (i-j)a_j\geq 0, \quad \forall a\\
i.e. && \gamma (h) \mathbf{半正定.} 
\end{eqnarray}
$$

### b

不妨先取均值化，令$y_t=x_t-\overline{x} $，然后：
$$
\begin{eqnarray} 
 \mathbf{记 } \  &&A=\left(\begin{array}{cccccccc}
0 & \cdots & 0 & y_{1} & y_{2} & \cdots & y_{N-1} & y_{N} \\
0 & \cdots & y_{1} & y_{2} & y_{3} & \cdots & y_{N} & 0 \\
\vdots & \cdots & \vdots & \vdots & \vdots & \cdots & \vdots & \vdots \\
y_{1} & \cdots & y_{N-1} & y_{N} & 0 & \cdots & 0 & 0
\end{array}\right)\\
\\
\because \ && \hat{\gamma }(|i-j|)=\frac{1}{N} \sum_{k=1}^{n-|i-j|}y_{k+|i-j|}\cdot y_k\\
\therefore \ && \hat{\gamma }(|i-j|)=\frac{1}{N}(AA^T)_{i,j}\\
\therefore \ && \sum_i^N\sum_j^Na_i\hat{\gamma }(|i-j|)a_j=a^T\cdot\frac{1}{N}(AA^T)\cdot a=\frac{1}{N} \norm{A^Ta}_2^2\geq 0 \quad \forall a\\
i.e. &&\hat{\gamma }(h) \mathbf{半正定.}
\end{eqnarray}
$$