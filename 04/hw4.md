# 时间序列 hw4

`18300290007 加兴华`

## Pb 3.5

假定AR(2)方程形如$X_t=\phi_1X_{t-1}+\phi_2X_{t-2}+W_t$, 需证:
$$
\phi(z)=1-\phi_1z-\phi_2z^2的两根|z_1|>1,|z_2|>1\Leftrightarrow \phi_{1}+\phi_{2}<1, \quad \phi_{2}-\phi_{1}<1, \; \text { 且 }\left|\phi_{2}\right|<1
$$

1. $\Rightarrow$:

$$
\begin{align}
\quad \quad &\phi (z)=1-\phi_1z-\phi_2z^2=(1-z_1^{-1}z)(1-z_2^{-1}z) \\
\Rightarrow \quad &\left\{\begin{matrix} 
  \phi _1=z_1^{-1}+z_2^{-1},\\  
  \phi _2=-(z_1z_2)^{-1}
\end{matrix}\right. \\
\therefore   \quad & |\phi _2|=\frac{1}{|z_1z_2|} <1;\\  \\
\quad  \quad & \phi(1)=  (1-z_1^{-1})(1-z_2^{-1})=\frac{(z_1-1)(z_2-1)}{z_1z_2} \\
\quad  \quad & \phi(-1)=  (1+z_1^{-1})(1-z_2^{-1})=\frac{(z_1+1)(z_2+1)}{z_1z_2} \\ \\
&case1:z_1,z_2为实根,\; i.e.\  z_i>1 \ or \ z_i<-1\\
\Rightarrow  \quad &\frac{z_i-1}{z_i}>0,\frac{z_i+1}{z_i}>0;\\
\Rightarrow  \quad & \phi(-1)=1+\phi _1-\phi _2>0,\phi(1)=1-\phi _1-\phi _2>0\\ \\
&case1:z_1,z_2为共轭复根,\; i.e.\  z_1=\overline{z_2}\\
\Rightarrow  \quad &z_1 \pm 1 ,z_2\pm 1也为共轭复根\\
\Rightarrow  \quad & \phi(-1),\phi(1)分子分母均>0,\\
\Rightarrow  \quad & \phi(-1)=1+\phi _1-\phi _2>0,\phi(1)=1-\phi _1-\phi _2>0\\

\end{align}
$$

2. $\Leftarrow$: 

$$
case 1:z_1,z_2为共轭复根\\
由韦达定理得: z_1z_2=\frac{1}{-\phi_2}
\Rightarrow |z_1z_2|=\frac{1}{|\phi_2|}>1\\
\therefore |z_i|=\sqrt{|z_1z_2|}>1\\ \\
case 2:z_1,z_2为实根(\phi(0)=1因而\ne 0)\\
\phi(1)=1-\phi_1-\phi_2=\frac{(z_1-1)(z_2-1)}{z_1z_2}>0 \\
\phi(-1)=1+\phi_1-\phi_2=\frac{(z_1+1)(z_2-1)}{z_1z_2}>0 \\
\therefore \frac{(z_1-1)(z_2-1)}{z_1z_2}/\frac{(z_1+1)(z_2+1)}{z_1z_2}>0\\
\Rightarrow \frac{(z_1-1)(z_2-1)}{(z_1+1)(z_2+1)}>0 \\
假设\frac{z_i-1}{z_i+1}<0,则z_i\in(-1,1)\\
|z_1z_2|=\frac{1}{|\phi_2|}\in(-1,1) 与|\phi_2|<1矛盾,\\
\therefore \frac{z_i-1}{z_i+1}>0,则|z_i|>1.
$$

<div STYLE="page-break-after: always;"></div>

## Pb 3.7

### a

$$
\begin{array}{l}
&\phi (z) & = 1+1.6z+0.64z^2=(1+0.8z)^2
\\ \therefore \quad  &\phi (z)&有两个相同实根z=-1.25,
\\ \Rightarrow \quad &\rho (h)&=(-1.25)^{-h}(c_1+c_2h) 
\\ &\rho (h) & = \left\{\begin{matrix} 
  1, \quad &h  = 0 \\  
  \frac{\phi _1}{1-\phi _2}  = \frac{-1.6}{1+0.64} , \quad &h  = \pm 1 
\end{matrix}\right. 
\\ \Rightarrow \quad &参数&\left\{\begin{array}{l} 
  c_1&= 1\\  
  c_2&=\frac{1.6*1.25}{1.64}-1\approx 0.2195
\end{array}\right. 
\\ \Rightarrow \quad &\rho (h)&=(-1.25)^{-h}(1+0.2195h) 
\end{array}
$$

```R
x=c(0:10)
y<-(-1.25)**(-x)*(1+(1.25*1.6/1.64-1)*x)
plot.ts(y,ylab='ACF',xlab='lags',lwd=2)
lines(ARMAacf(c(-1.6,-0.64),lag.max = 10 ),col='red',lty=2,lwd=2)
legend('topright', inset=.01,bty='n', legend=c("my answer","ARMAacf"),lty=c(1, 2),cex=0.7,col=c('black','red'),lwd=c(1.5,1.5))
abline(h=0)
```

<img src="E:\华为云盘\2022春\时间序列\作业\04\hw4.assets\image-20220402012238493.png" alt="image-20220402012238493" style="zoom:50%;" />

从图像上看检查计算ACF结果正确。

<div STYLE="page-break-after: always;"></div>

### b

$$
\begin{array}{l}
&\phi (z) & = 1-0.4z-0.45z^2=(1-0.9z)(1+0.5z)
\\ \therefore \quad  &\phi (z)&有两个不同实根z_1=1/0.9,z_2=-2,
\\ \Rightarrow \quad &\rho (h)&=c_1 0.9^h+c_2 (-0.5)^h 
\\ &\rho (h) & = \left\{\begin{matrix} 
  1, \quad &h  = 0 \\  
  \frac{\phi _1}{1-\phi _2}  = \frac{0.4}{1-0.45} , \quad &h  = \pm 1 
\end{matrix}\right. 
\\ \Rightarrow \quad &参数&\left\{\begin{array}{l} 
  c_1+c_2&= 1\\  
  0.9c_1-0.5c_2&= \frac{8}{11}
\end{array}\right. 
\Rightarrow
\left\{\begin{array}{l} 
  c_1&= 0.8766\\  
  c_2&= 0.1234
\end{array}\right. 
\\ \Rightarrow \quad &\rho (h)&=0.8766 \cdot0.9^h+0.1234\cdot(-0.5)^h
\end{array}
$$

```R
x=c(0:10)
y<-0.8766*0.9**x+0.1234*(-0.5)**x
plot.ts(y,ylab='ACF',xlab='lags',lwd=2)
lines(ARMAacf(c(0.4,0.45),lag.max = 10 ),col='red',lty=2,lwd=2)
legend('topright', inset=.01,bty='n', legend=c("my answer","ARMAacf"),lty=c(1, 2),cex=0.7,col=c('black','red'),lwd=c(1.5,1.5))
```

<img src="E:\华为云盘\2022春\时间序列\作业\04\hw4.assets\image-20220401122340772.png" alt="image-20220401122340772" style="zoom: 50%;" />

从图像上看检查计算ACF结果正确。

<div STYLE="page-break-after: always;"></div>

### c

$$
\begin{array}{l}
&\phi (z) & = 1-1.2z+0.85z^2=(\frac{0.6}{\sqrt{0.85}}-\sqrt{0.85}z)^2+\frac{0.49}{0.85}
\\ \therefore \quad  &\phi (z)&有虚根z=\frac{0.6}{0.85}\pm \frac{0.7}{0.85}i,令z_1=\frac{0.6}{0.85}+ \frac{0.7}{0.85}i
\\ \Rightarrow \quad &\rho (h)&=c_1 z_1^{-h}+\overline{c_1} (\overline{z_1})^{-h} 
\\ &\rho (h) & = \left\{\begin{matrix} 
  1, \quad &h  = 0 \\  
  \frac{\phi _1}{1-\phi _2}  = \frac{1.2}{1+0.85} , \quad &h  = \pm 1 
\end{matrix}\right. 
\\ \Rightarrow \quad &参数&\left\{\begin{array}{l} 
  2Re(c_1)&= 1\\  
  2Re(c_1z_1)&= \frac{1.2}{1.85}
\end{array}\right. 
\Rightarrow
\left\{\begin{array}{l} 
  Re(c_1)&= 0.5\\  
  Im(c_1)&= 0.045/1.295
\end{array}\right. 
\\ \Rightarrow \quad &\rho (h)&=(0.5+\frac{0.045}{1.295}i) z_1^{-h}+(0.5-\frac{0.045}{1.295}i) (\overline{z_1})^{-h} 
\end{array}
$$

```R
x=c(0:10)
y<-(0.5+0.045/1.295i)*(6/8.5+7/8.5i)**(-x)+(0.5-0.045/1.295i)*(6/8.5-7/8.5i)**(-x)
plot.ts(y,ylab='ACF',xlab='lags',lwd=2)
lines(ARMAacf(c(1.2,-0.85),lag.max = 10 ),col='red',lty=2,lwd=2)
legend('topright', inset=.01,bty='n', legend=c("my answer","ARMAacf"),lty=c(1, 2),cex=0.7,col=c('black','red'),lwd=c(1.5,1.5))
abline(h=0)
```

<img src="E:\华为云盘\2022春\时间序列\作业\04\hw4.assets\image-20220402012420848.png" alt="image-20220402012420848" style="zoom:50%;" />

从图像上看检查计算ACF结果正确。

<div STYLE="page-break-after: always;"></div>

## Pb 3.8

### i

$$
\begin{array}{l}
x_{t} = \phi x_{t-1}+\theta w_{t-1}+w_{t}, \text { where }|\phi|<1
\\
\because   |\phi |<1 
\\
\therefore   序列causal.\;
x_t = \sum_{k = 0}^{\infty} \psi_{k}\mathcal{w}_{t-k}
\\
\therefore (1-\phi z)(\psi_0+\psi_1z+\cdots)=1+\theta z
\\
\therefore \psi_0=1;\psi_1=\phi +\theta;\psi_2=\phi (\phi +\theta );
\\
另外E(x_{t+k}w_t)=\left\{\begin{matrix} 
  \psi_k \sigma_w^2 \quad &k\geq0 \\  
   0 \quad &k<0
\end{matrix}\right. 
\\ \\
E(x_t)=0
\\
\gamma (1)=E(x_tx_{t-1})=\phi \gamma (0)+\theta E(w_{t-1}x_{t-1})+E(w_{t}x_{t-1})
\\
\gamma (1)=\phi \gamma (0)+\psi_0\theta \sigma _w^2
\\ \\
\gamma (0)=E(x_tx_{t})=E(x_t(\phi x_{t-1}+\theta w_{t-1}+w_{t}))=\phi \gamma (-1)+\theta E(w_{t-1}x_{t})+E(w_{t}x_{t})
\\
\gamma (0)=\phi \gamma (1)+\theta\sigma _w^2\psi_1+\psi _0\sigma _w^2
\\ \\
解得\gamma(0)=\sigma_{w}^{2} \frac{1+2 \theta \phi+\theta^{2}}{1-\phi^{2}} \quad \text { and } \quad \gamma(1)=\sigma_{w}^{2} \frac{(1+\theta \phi)(\phi+\theta)}{1-\phi^{2}}
\\\\
当h>1:
\\
\gamma (h)=E(x_tx_{t-h})=E((\phi x_{t-1}+\theta w_{t-1}+w_{t})x_{t-h})=\phi \gamma (h-1)+0
\\
\gamma (h)=\gamma(1)\cdot \phi ^{h-1}=\sigma_{w}^{2} \frac{(1+\theta \phi)(\phi+\theta)}{1-\phi^{2}} \phi^{h-1}
\\
\\
\therefore \rho(h)=\gamma (h)/\gamma (0)=\frac{(1+\theta \phi)(\phi+\theta)}{1+2 \theta \phi+\theta^{2}} \phi^{h-1}, \quad h \geq 1
\end{array}
$$

### ii

$$
\begin{array}{l}
ARMA(1,0):(\theta =0)
\\
\rho(h)= \phi^{h}, \quad h \geq 1
\\ \\
ARMA(0,1):(\phi =0)
\\
\rho(h)=\frac{\theta}{1+\theta^{2}} \phi^{h-1}, \quad h \geq 1
\end{array}
$$

ARMA(1,0)与ARMA(0,1)是ARMA(1,1)中某个参数取零的特殊情况.

<div STYLE="page-break-after: always;"></div>

### iii

```R
plot.ts(ARMAacf(0.6,0.9,lag.max = 10 ),col='black',lwd=2,ylab='ACF',xlab='lag')
lines(ARMAacf(ar=0.6,lag.max = 10 ),col='blue',lwd=2)
lines(ARMAacf(ma=0.9,lag.max = 10 ),col='red',lwd=2)
legend('topright', inset=.01,bty='n', legend=c("ARMA(1,1)","ARMA(1,0)","ARMA(0,1)"),,cex=0.7,col=c('black','blue','red'),lwd=c(1.5,1.5,1.5))
```

<img src="E:\华为云盘\2022春\时间序列\作业\04\hw4.assets\image-20220401162223090.png" alt="image-20220401162223090" style="zoom:50%;" />

从图上可见ACF诊断能力由强到弱依次为ARMA(0,1), ARMA(1,0), ARMA(1,1). 定性的话，ARMA(0,1)诊断能力强而后两者诊断能力弱。

<div style='page-break-after:always'> 

## 2

![image-20220331202623630](E:\华为云盘\2022春\时间序列\作业\04\hw4.assets\image-20220331202623630.png)

### a

反证法.假设$c_2\ne\bar{c}_1$, 也即$c_1=a+bi,c_2=d+ei$, a=d和b=-e不同时满足:

当h=0: $\rho(0)=c_1+c_2\in R \, \Rightarrow b=-e $;

当h=1: $\rho(1)=c_1z_1^{-1}+c_2z_2^{-1}=\frac{c_1z_2+c_2z_1}{z_1z_2}$

令$z_1=x+yi,z_2=x-yi$,则:
$$
\begin{array}{l}
&\rho(1)z_1z_2=(ax+by)+(bx-ay)i+(dx-ey)+(dy+ex)i\in R
\\
\Rightarrow  & bx-ay+dy+ex=0
\\
\Rightarrow  & (b+e)x-(a-d)y=0
\\
\because &b=-e 且该通解形势下y\ne 0
\\
\therefore &a=d
\end{array}
$$
产生矛盾,原假设错误,因此$c_2=\bar{c}_1$.

### b

设$z_1=x+yi,z_2=x-yi$,

则$z_1=|z_1|e^{i\theta},z_2=|z_1|e^{-i\theta},\quad \theta=argcos(\frac{x}{\sqrt{x^2+y^2}})$

进而设$c_1=a+di,c_2=a-di$,

则$c_1=Ke^{ib},c_2=Ke^{-ib}, \quad K=|c_1|,b=argcos(\frac{a}{\sqrt{a^2+d^2}})$

因此$\rho(h)=K|z_1|e^{i(\theta h)+ib}+K|z_1|e^{-i(\theta h)-ib}=2K\left|z_{1}\right|^{-h} \cos (h \theta+b)$

从而只需求出$c_1$即可算出h和b的值,而$c_1$ 可从初始条件中求出,得证.

### c

```R
z = c(1,-1.5,.75) # coefficients of the polynomial
(a = polyroot(z)[1]) # print one root = 1 + i/sqrt(3)
par(mfrow=c(2,1))
arg = Arg(a)/(2*pi) # arg in cycles/pt
set.seed(8675309)
ar2 = arima.sim(list(order=c(2,0,0), ar=c(1.5,-.75)), n = 144)
plot(ar2, axes=FALSE, xlab="Time")
axis(2); axis(1, at=seq(0,144,by=12)); box()
abline(v=seq(0,144,by=12), lty=2)
ACF = ARMAacf(ar=c(1.5,-.75), ma=0, 50)
plot(ACF, type="h", xlab="lag")
abline(h=0)
```

<img src="E:\华为云盘\2022春\时间序列\作业\04\hw4.assets\image-20220401170505800.png" alt="image-20220401170505800" style="zoom: 50%;" />

ACF在幅度方面始终衰减;而衰减的同时体现出了比较强的余弦周期性.

