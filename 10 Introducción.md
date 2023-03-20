# 1.0 Introducción

El análisis de series de tiempo es una manera específica de analizar una secuencia de datos recopilados a lo largo de un intervalo de tiempo.

Este análisis puede mostrarte cómo las variables cambian a través del tiempo, como las acciones del mercado

## Características

- Correlación introducida por una muestra de puntos adyacentes
- Tiempo
- Frecuencia

Una serie de tiempo puede ser definida como una colección de variables aleatorias indexadas de acuerdo al orden que se obtuvo con respecto al tempo, por ejemplo: $x_1, x_2, x_3,\cdots, x_n$.

## Modelos estadísticos de series de tiempo

El objetivo principal del análisis de series de tiempo es desarrollar modelos matemáticos que dan descripciones del fenómeno.

### White Noise (ruido blanco)

Sólo variables que n están correlacionadas entre ellos, media cero y varianza finita $\sigma^2$
$$
W_i \sim_{i.d.d} N(0, \sigma_W)
$$

### Moving averages and Filtering

Un segundo modelo estadístico es mover las medias. Esto es usualmente usado para suavizar las series.
$$
Y_i = \frac{X_1+X_2+\cdots+X_n}{n}
$$

### Autoregressions

El siguiente modelo estadístico es la autoregresiva. Si nosotros queremos expresar un valor futuro en términos de valores pasados, este modelo es la opción:
$$
X_i=\phi X_{i-1}+\phi X_{i-2}+\cdots+\phi_p X_{i-p}+W_i
$$

###  Random Walk With Drift

Un modelo para analizar  la tendencia de una caminata aleatoria con *drift model* está dado por:
$$
X_t = \delta+_{t-1}+W_t
$$
para $t=1,2,\cdots$ con una condición inicial $X_0=0$. La constante $\delta$ es lo que llamamos el $drift$ (pendiente) es llamada una caminata aleatoria simple. Esto peude ser rescrito como:
$$
X_t=\delta t+\sum_{j=1}^t W_j
$$

### Signal with Noise

Varios modelos realisticos para generar series de tiempo a asume una señal que está debajo de una variación constante, 
$$
X_t = A \cos(2\pi wt)+W_t
$$
Donde $A$ es la amplitud, $\omega$ es la frecuencia y $\phi$ es la fase.

