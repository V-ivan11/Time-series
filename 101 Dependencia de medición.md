La descripción de una serie de tiempo es un conjunto de variables aleatorias maestreadas sucesivamente, $t_1, t_2, \cdots, t_n$, para cada $n$ se tiene una función de distribución conjunta.
$$
F(c_1, c_2, \cdots, c_n)=P(x_{t_1}<c_1, x_{t_2}<c_2,\cdots, x_{t_n}<c_n)
$$

## El valor esperado

El valor esperado de una variable aleatoria continua está definida por:
$$
\mu_{xt}=E(x_t)=\int_{-\infty}^\infty x f_t(x)dx
$$
Asumimos que tenemos ruido blanco $W_t\sim N(0, \sigma_W)$ y calculamos:

1. El valor esperado de las medias móviles está definido por:
   $$
   V_t=\frac 1 3 [W_{i-t}+W_t+W_{t+1}] \qquad = 0
   $$

*Al calcular la integral del valor esperado por partes, se llega a que el valor esperado depende de cada $W_t$, la cual está definida por la normal con la media cero, concluyendo que el valor esperado es $0$*.

2. EL valor esperado de la caminata aleatoria con derrape definido por:
   $$
   X_t = \delta_t+\sum_{j=1}^j W_j \qquad = \delta t
   $$

*Recordemos que el valor esperado de una constante es la propia constante, y tomando en cuenta que el valor esperado de $W_t$ es $0$*.

## Autocovarianza

La función de autocovarianza mide la dependencia lineal entre 2 puntos en la misma serie observada a diferentes tiempos, la cual está definida por:
$$
\gamma_x(s,t) = cov(x_s, x_t)= E[(x_s-\mu_s)(x_t-\mu_t)]
$$
Por lo que, si deseamos calcular la autocovarianza de una misma variable, serie la varianza de la propia variable.

Ahora, asumimos que el ruido blanco $W_t\sim N(0, \sigma_W)$ 

1. Calcule la autocovarianza del modelo de ruido blanco:
   $$
   cov(W_s, W_t) \qquad = 0 \qquad W_s \ne W_t
   $$

2. 

*Como son variables independientes, nos da un producto de Esperanzas las cuales son cero si estas variables son diferentes.*

1. Pruebe la igualdad escrita debajo por la autocovarianza del modelo de medias móviles:
   $$
   cov(V_s, V_t)=cov\left(\frac 1 3 (w_{s-1}+w_s+w_{s+1}), \frac 1 3 (w_{t-1}+w_t+w_{t+1})\right)
   $$

   $$
   E\left(\frac 1 3 (w_{s-1}+w_s+w_{s+1})\times \frac 1 3 (w_{t-1}+w_t+w_{t+1})\right)\\
   E\left(\frac 1 9 (W_{s-1}W_t-1)+\frac 1 9 (W_{s}W_t)+\frac 1 9 (W_{s+1}W_t+1)\right)
   $$

   ![image-20230223080056201](/home/ivn/snap/typora/76/.config/Typora/typora-user-images/image-20230223080056201.png)

*Recordemos que cuando los tiempos son diferentes, los valores esperados son $0$, por lo que dependiendo de los productos y del tiempo a los que estemos calculando, sólo los productos que dan consigo mismo van a dar como resultado la varianza y nuestra constante $\frac 1 9$*

## Autocorrelación

La autocorrelación mide la predictibilidad lineal de una serie a tiempo $t$, digase $X_t$, usando sólo el valor a tiempo $s$, digamos $X_s$ y está definida por:
$$
\rho_x(s,t)=\frac{\gamma_x(s,t)}{\sqrt{\gamma(s,s)\gamma(t,t)}} \le 1
$$
La desigualdad de Cauchy-Schwartz establece que dada 2 variables aleatorias, $X$ y $Y$ con un espacio de probabilidad común dado:
$$
|E[XY]| \le \sqrt{E[X^2]E[Y^2]}
$$
probemos que:
$$
-1\le \rho(s,t) \le 1
$$


### Croscovarianza

La croscovarianza de 2 series esta dada por:
$$
\gamma_{XY}(s,t)=cov(X_s,Y_t)=E[(X_s-\mu_{X_s})(Y_t-\mu_{Y_t})]
$$
Sirve para medir la predictibilidad de una serie $Y$ a partir de otra serie $X$.
$$
\rho_{XY}(s,t)=\frac{\gamma_{XY}(s,t)}{\sqrt{\gamma_{X}(s,s)\gamma_Y(t,t)}}
$$
