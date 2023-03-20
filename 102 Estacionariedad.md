# Estacionariedad

Este es un concepto importante en el campo de el análisis de series de tiempo para saber si los datos son estacionarios.

Una **serie de tiempo estrictamente estacionaria** dado cualquier comportamiento de valores $x_{t_i}$ es idéntica al conjunto $x_{t_1+h}$.
$$
P(x_s\le x) = P(x_t\le x)
$$


## Estacionariedad de segundo orden

1. La media $\mu_t$ es constante por lo que no depende del tiempo.
2. La varianza $\sigma^2$ es finita
3. La función de autocovarianza, $\gamma(s,t)$ depende de $s$ en $t$ solo con su diferencia $|s-t|$

## Autocovarianza y Autocorrelación de una serie estacionaria de tiempo

La función de autocovarianza estacionaria de una serie de tiepo puede ser escrita como:
$$
\gamma(h) = cov(X_{t+h}, X_t)= E[(X_{t+h})(X_t-\mu)]
$$
La función de autocorrelación de una serie de tiempo estacionaria puede ser escrito como:
$$
\rho(h) =\frac{\gamma(t+h,t)}{\sqrt{\gamma(t+h,t+h)\gamma(t,t)}} = \frac{\gamma(h)}{\gamma(0)}
$$

## Tendencia estacionaria

Un proceso estocástico es tendencia estacionaria si sobreponemos 
$$
Y_t=f(t)+X_t
$$
Donde $f(t)$ es cualquier función $f:\R \rightarrow\R$ y $X_t$ es un proceso estocaśtico estacionario con una media cero.

## Estacionariedad por temporadas

Un proceso estocástico es temporal si la distribución conjunta de cualquier conjunto de datos es invariante sobre el cambio del tiempo $mP$, donde $m\in \Z$.

## Importancia de estacionanariedad para estimaciones

A pesar de que la autocorrelación y la correlación cruzada son útiles para describir propiedades de modelos hipotéticos, la mayoría de los análisis deben de funcionar usando datos de la muestra.

### Estimación con valor esperado

Algunas veces no contamos con las funciones de distribución de probabilidad de nuestros datos, teniendo sólo algunos datos disponibles de nuestra muestra, teniendo la media constante a lo largo del tiempo, por lo que para estimar valores podemos usar:
$$
\bar{X}=\frac 1 N \sum_{i=1}^N X_i
$$

### Estimación con la varianza

En algunos coasos necesitamos calcular la varianza a partir de cun conjunto de datos, donde tenemos 2 casos:
$$
s^2(X)=\frac 1 N \sum_{i=1}^N(X_i-\bar{X})^2
$$

$$
s^2(X)=\frac {1} {N-1} \sum_{i=1}^N(X_i-\bar{X})^2
$$

## Función de la autocovarianza

Dada la varianza, esta es la estimación del sesgo, sin el sería dividido por $N-h-1$
$$
\hat \gamma = \frac 1 N \sum_{i=1}^{N-h}(X_{t+h}-\bar{X})(X_t-\bar{X})
$$
La funcón de autocovarianza $\gamma(h)$, de un proceso estacionario es no negativo, asegurando que las varianzas de una combinación de variables $X_t$, nunca será negativa.
$$
\bar{\rho}(h)=\frac{\bar\gamma(h)}{\bar\gamma(0)}
$$
