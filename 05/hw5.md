# 时间序列hw5

> 18300290007 加兴华

## 1

### Generate

```R
n <- 100
ar <- arima.sim(list(order=c(1,0,0), ar=c(0.6)), n=n)
ma <- arima.sim(list(order=c(0,0,1), ma=c(0.9)), n=n)
arma <- arima.sim(list(order=c(1,0,1), ar=c(0.6), ma=c(0.9)), n=n)
```

参数均小于1, 因此模型causal 和 invertible.

### ACF

```R
par(mfrow=c(3,1))
acf(ar,main='ACF for AR(1)')
acf(ma,main='ACF for MA(1)')
acf(arma,main='ACF for ARMA(1,1)')
```

<img src="https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410045423742.png" alt="image-20220410045423742" style="zoom: 50%;" />

**AR(1):**$$\rho(h)= \phi^{h}, \quad h \geq 0$$

指数衰减趋于0, 符合理论值.

**MA(1):**$$\rho(0)=1;\quad \rho(1)=\frac{\theta}{1+\theta^2};\quad \rho(h)=0 ,\quad h\geq2$$

只在0和1处显著,符合理论值.

**ARMA(1,1):**$$\rho(0)=1;\quad
\rho(h)=\frac{(1+\theta \phi)(\phi+\theta)}{1+2 \theta \phi+\theta^{2}} \phi^{h-1} ,\quad h \geq 1$$

指数衰减趋于0, 符合理论值.


### PACF

```R
par(mfrow=c(3,1))
acf(ar,main='ACF for AR(1)')
acf(ma,main='ACF for MA(1)')
acf(arma,main='ACF for ARMA(1,1)')
```

<img src="https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410045455917.png" alt="image-20220410045455917" style="zoom: 50%;" />

**AR(1):**$$\phi_{11}=\phi;\quad \phi_{ii}=0,\quad i\geq1$$

只在1处显著,符合理论值.

**MA(1):**$$\phi_{hh}=-\frac{(-\theta )^h(1-\theta^2)}{1-\theta ^{2h+2}} ,\quad h\geq1$$

来回震荡幅度衰减到0,符合理论值.

**ARMA(1,1):**可逆ARMA模型有一个AR($\infty$)表示,从而理论上不会截尾.

来回震荡幅度衰减到0,符合理论值.



### 和表 3.1 对比

纵观所有图,只有AR(1)的样本PACF和MA(1)的样本ACF在lag=1发生截尾, 其余图都算tails off, 和表结论一致.

<div style='page-break-after:always'>

## 2

![image-20220410180955437](https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410180955437.png)

<div style='page-break-after:always'>

## 3

![image-20220410181032859](https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410181032859.png)

<div style='page-break-after:always'>

## 4

![image-20220410181055734](https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410181055734.png)

<div style='page-break-after:always'>

## 5

![image-20220410181118890](https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410181118890.png)

<div style='page-break-after:always'>

## 6

![image-20220410181148866](https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410181148866.png)

![image-20220410182801645](https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410182801645.png)

![image-20220410183106435](https://raw.githubusercontent.com/huakyouin/md-img/main/img/image-20220410183106435.png)

