# Regresión Lineal

## Típica regresión lineal en series de tiempo

Supongamos que tenemos una serie de tiempo dependiente, digamos $X_t$, para $t = 1, 2, \cdots, n$ siendo influenciada por una colección de posibles entradas o series de tiempo independientes, digamos $Z_t^{(1)}, Z_t^{(2)}, \cdots, Z_t^{(n)}$.

Por lo que expresamos estas relaciones como:
$$
X_t=\beta_0+\beta_1Z_t^{(1)}+\cdots+\beta_qZ_t^{(q)}+W_t
$$
expresada de forma vectorial:
$$
X_t = \beta^TZ_t+W_t
$$
Por lo que, para modelar la **regresión lineal** queremos buscar el mínimo del error a partir de los $\beta$'s calculados, llegando a:
$$
\hat{\beta}=(Z^TZ)^{-1}Z^TX
$$
![image-20230303090706708](/home/ivn/snap/typora/76/.config/Typora/typora-user-images/image-20230303090706708.png)

El error esta denotado por (error cuadrático medio)
$$
SSE = \frac 1 N\sum_{i=1}^N\left(X_t-\hat{\beta}^TZ_t\right)^2
$$

Y el estimador sin sesgo de la varianza está dado por:
$$
s^2_W=MSE = \frac{SSE}{N-(q+1)}
$$
Donde $MSE$ es el error cuadrático medio.

## Análisis de varianza (ANOVA)

Varios modelos de interés tratan de aislar o seleccionar el mejor subconjunto de variables independientes. Suponga que proponemos un modelo que especifica que un sólo subconjunto $r<q$ independientes variables, es influenciada por una variable dependiente $X_T$, donde su modelo reducido es:
$$
X=Z_r\hat{\beta}+W\qquad (1)
$$


La hipótesis nula esta dada por:
$$
H_0 : \beta_{r+1}=\cdots=\beta_q=0
$$
Podemos probar el modelo reducido bajo F
$$
F = \frac{(SSE_r-SSE)/(q-r)}{SSE/(N-q-1)} = \frac{\text{Mean Squared Regression}}{\text{Mean Squared Error}}
$$
Bajo la hipótesis nula, $F$ tiene distribución central con $q-r$ y $N-q-1$ grados de libertad, si $(1)$ es un  modelo correcto.

La hipótesis es rechazada a nivel $\alpha$ si $F>F_{N-q-1}^{q-r}$, el percentil $1-\alpha$ de la distribución $F$ con $q-r$ en el numerador y $N-q-1$ en el denominador de grados de libertad.

El número de combinaciones a calcular está dado por:
$$
c = \sum_{i=1}^N\begin{pmatrix}N\\i\end{pmatrix}
$$

Por lo que, todas estas combinaciones lo convierte en una desventaja por el poder de cómputo necesario.

![image-20230309071741708](/home/ivn/snap/typora/76/.config/Typora/typora-user-images/image-20230309071741708.png)

Obteniendo la tabla anterior para buscar los parámetros óptimos para minimizar el error.

## Métrica $R^2$

Podemos medir la proporción de la variación de acuerdo a las variables que estamos usando:
$$
R^2=\frac{SSE_0-SSE}{SSE_0}
$$
donde los residuales de la suma de los cuadrados es reducida al siguiente modelo:
$$
SSE_0=\sum_{i=1}^N(X_t-X)^2
$$
Esta métrica es llamada como **coeficiente de determinación**

Una técnica alternativa es sólamente evaluar el modelo por sí mismo, por lo que consideremos una regresión normal con $k$ coeficientes y denota el estimador de máxima verosimilitud para la varianza:
$$
\hat{\sigma_k}^2=\frac{SSE(k)}{N}
$$
Después tenemos los siguientes criterios de selección del modelo.

### Criterio de información de Akaike

$$
AIC = \log(\hat\sigma_k^2)+\frac{N+2k}{N}
$$

El valor de $k$ que alcance el mínimo $AIC$ nos dice el mejor modelo.

### AIC con sesgo corregido

$$
AICc = \log(\hat\sigma_k^2)+\frac{N+2k}{N-k-2}
$$



### Criterio de información Bayesiana

$$
BIC = \log(\hat\sigma_k^2) +\frac{k\log(N)}{N}
$$

Este criterio también es llamado **Criterio de Schwartz**.

**BIC** es usado normalmente para conjuntos de datos más pequeños.
