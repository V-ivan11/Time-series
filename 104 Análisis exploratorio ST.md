# Análisis exploratorio para series de tiempo

Una de las medidas importantes para las series de tiempo es calcular la auto correlación con precisión, con ello medimos la dependencia entre los valores de la serie.

Se complica medir dicha dependencia porque regularmente esta dependencia cambia a lo largo del tiempo.

## Interpolación

En varios casos pueden haber datos faltantes a lo largo de la serie, para completarlos se usa la técnica de interpolación, donde se busca un valor razonable que pueda ir ahí de acuerdo a los datos alrededor de él.

### Interpolación lineal

Dado 2 puntos de la serie de tiempo $(t_0, X_{t_0})$ y $(t_1, X_{t_1})$ la interpolación lineal entre estos 2 puntos es la linea que los une, por lo que tenemos la siguiente ecuación:
$$
X_t = \frac{X_{t0}(t_1-t)+X_{t_1}(t-t_0)}{t_1-t_0}
$$

> **df.interpolate**(method = "linear")

## Estabilizar la varianza

En casos donde la serie de tiempo no es estacionaria, esta no puede ser representada mediante un comportamiento lineal, por lo que transformar la serie haciendo una varianza más constante a lo largo de la serie puede ayudar a tratar estas series, una transformación útil es:
$$
Y_t=\log(X_t)
$$

## Transformación de potencias

Otras opciones para estabilizar la varuanza son las tranformaciones de potencias de la familia **Box-Cox** de la forma:
$$
Y_t=
$$

## Suavizado

Suavizar una serie de tiempo puede ayudar a encontrar ciertos patrones a lo largo del tiempo, donde recordemos que el método más usado para suavizar es la técnica de las medias móviles.
$$
M_t=\sum_{j=-k}^ka_jX_{t-j}
$$

### Suavizado kernel

Este tipo de suavizado igualmente se basa en la técnica de medias móviles, sin embargo, de lugar de usar el valor en la ecuación, usa pesos, dados por:
$$
w_i(t)=\frac{K\left(\frac{t-i}{b}\right)}{\sum_{j=1}^nK\left(\frac{t-j}{b}\right)}
$$

### Lowess

Este es otro tipo de suavizado que usa el método de $k$ vecinos cercanos a lo largo de la serie de tiempo.

![image-20230316074201621](/home/ivn/snap/typora/76/.config/Typora/typora-user-images/image-20230316074201621.png)

## Relaciones no lineales

Para encontrar estas relaciones en series de tiempo no lineales,usamos el método anterior de Lowess, de acuerdo al comportamiento de los datos.

> Para realizar un análisis en la serie de tiempo, es necesario que esta ya esté transformada hacia una serie de tiempo estacionaria.

## Detectar una serie de tiempo estacionaria

1. Usando **una gráfica** de la serie a lo largo del tiempo para observar su comportamiento a largo plazo para ver si cumple con los requisitos de una serie estacionaria
2. Observando el gráfico de la **función de la autocorrelación**, y si los valores tienden a cero rápidamente ($1/x$), la serie es una función estacionaria, si no, estos valores van a tender a cero muy lentamente ($-ax$).

## Eliminar las tendencias

La forma más fácil de describir una serie de tiempo no estacionaria es de la forma:
$$
X_t=\mu_t+Y_t
$$
donde $X_t$ son observaciones y $\mu_t$ es su tendencia, donde podemos descriir esta tendencia como una caminata aleatoria con drft.
$$
\mu_t = \delta+\mu_{t-1}+W_t
$$
Si ahora restamos con el otro valor, queda un proceso estacionario:
$$
\begin{eqnarray}
X_t-X_{t-1} &=& (\mu_t+Y_t)-(\mu_{t-1}+Y_{t-1})\\
&=&
\end{eqnarray}
$$
Por lo que resumiendo el modelo, para cada punto en el tiempo se resta el valor anterior.

## Estacionariedad por intervalos

Ahora supongamos que tenemos una serie de tiempo que se modela a partir del modele con ruido
$$
\mu_t=A\cos(2\pi wt+\phi) = A\cos\left(2\pi w\left(t\frac{1}{w}+\phi\right)\right)
$$
Donde la diferencia sería $t-\frac 1 w$ para obtener el proceso estacionario, lo que es:
$$
X_t-X_{t-\frac 1 w} = (\mu_t+Y_t)-\left(\mu_{t-\frac 1 w}+Y_{t-\frac 1 w}\right)
$$
Lo que es igual a $Y_t-Y_{t-\frac 1 w}$

Resumiendo este método, ahora se le resta el valor anterior pero antes del anterior ciclo

## Diferienciación

La diferenciación juega un rol central en el análisis de series de tiempo, por loq ue recibe su propia notación, el cual se llama *operador backshift* o *operador lag*.
$$
\nabla^d= (1-B)^d
$$
