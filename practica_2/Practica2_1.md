
<style>h1,h2,h3,h4 { border-bottom: 0; } </style>

&nbsp;

&nbsp;

&nbsp;

<div style="text-align: center;">
<img src="logo_iteso.jpg" alt="drawing" style="width:200px;"/>
</div>

<h1 style="text-align: center;">Práctica 2. Análisis de Regresión</h1>

<H2 style="text-align: center;">Nombre: Gregorio Alberto Alvarez Alvarez</H2>

<H2 style="text-align: center;">Materia: Análisis estadístico multivariable</H2>



<div style="page-break-after: always"></div>


<H2>Introducción</H2>

En este estudio se buscó explicar la relación lineal entre las variables dependientes e independientes, de una base de datos, y la valides de los modelos encontrados mediante regresión lineal. Esto se realizó mediante múltiples pruebas aplicadas a los valores de los residuales.

El estudio fue realizado a partir de la regresión univariable y multivariable, utilizando una base de datos libre.


<H2>Descripción de la base de datos</H2>

Para este estudio se utilizó la base de datos "Happiness and Corruption 2015-2020", la cual tiene el fin de dar material para analizar y encontrar variables que afecten el puntaje de felicidad.

La base de datos fue obtenida de kaggle [1]. Dicha base de datos contiene las siguientes variables:

- **Country**: Contiene el nombre de los países que se presentados.
- **happines_score**: score: Promedio de las respuestas de índice de felicidad. Tiene un rango entre 0 y 10. obtenidos de la encuesta 'Gallup Wold Poll (GWP)'.
- **gdp_per_capita**: El radio para el cual el Producto interno bruto de un pais contribuye para el cálculo del puntaje de felicidad.
- **family** : El radio para el cual la familia contribuye para el cálculo del puntaje de de felicidad.
- **health**: El radio para el cual la esperanza de vida es utilizado para calcular el puntaje de felicidad
- **freedom**:El radio para el cual la libertad, es utilizado para calcular el puntaje de felicidad
- **generosity**: valor numérico calculado con la percepción de las personas sobre el nivel de generosidad del país en el que vive el encuestado. Obtenido en una encuesta.
- **government_trust**:  El radio para el cual la confianza hacia el gobierno contribuye para el cálculo del puntaje de felicidad.
- **dystopia_residual**: Puntaje basado en la comparación con el hipotético caso del país más triste del mundo.
- **continent**: Continente el nombre del continente presentado.
- **Year**: Año en el que se hizo la encuesta
- **social_support**: No especificado
- **cpi_score**: índice con el cual se califica el grado de corrupción en un país en específico (CPI por sus siglas en ingles).

<div style="page-break-after: always"></div>

<H2>Desarrollo</H2>

<H3>Regresión univariante</H3>

Se tomo a la variable de índice CPI como variable de salida y el puntaje de felicidad como variable de entrada.

Se obtuvo la gráfica de distribución de los datos para cada variable.

Se escogió una muestra aleatoria de la base de datos con 80% de los datos para el set de entrenamiento para la variable dependiente e independiente. Con el resto de los datos se creó el set de prueba.

Se normalizaron la variable de entrada con el fin de encontrar coeficientes significativamente grandes.

Se utilizo la librería de regresión lineal de *Scikit learn* y *statsmodels* para ajustar los datos

<H3>Regresión multivariable</H3>

Se removió la variable de país del set de variable independientes y se convirtió la variable de continente a variable categórica. Las variables independientes se normalizaron nuevamente.

Se aplico la regresión lineal con la función de la librería de *statsmodels*.

<H2>Resultados</H2>

<H3>Regresión univariante</H3>

Después de aplicar la regresión lineal con las dos librerías, se encontraron los mismos coeficientes para $\beta_0$ y $beta_1$, ~3.70 y ~54.23 consecutivamente y un valor de $R^2$ de 0.54 para el set de entrenamiento y 0.46 para el set de prueba, lo que indica que en primera instancia indica que el modelo encontrado no representa la tendencia de los datos.

Mediante la librería *statsmodels* se obtuvo un resumen de múltiples pruebas estadísticas (tabla 1)

<div style="margin-left: auto;
            margin-right: auto;
            width: 30%">

| Prueba         | Valor   | Prueba            | Valor    |
|:--------------:|:-------:|:-----------------:|:--------:|
| const: P>\|t\| | 0.00    | x1: P>\|t\|       | 0.00     |
| Adj. R-squared | 0.464   | F-statistic       | 548.5    |
| log-Likelihood | -774.01 | Prob(F-statistic) | 9.09e-88 |
| Omnibus        | 17.091  | Prob(Omnibus)     | 0.000    |
| Durbin-Watson  | 1.918   | Breush-Pagan      | 3.2e-4   |
| AIC            | 1552    | BIC               | 1561     |

</div>

<p style="text-align: center;">Tabla 1. Pruebas estadísticas de la regresión univariante</p>

De la primera fila de la tabla 1 se puede observar que tanto para el valor de p value de la prueba de T student $\beta_0$ como el valor de $\beta_1$ son igual a cero, lo que indica, que se puede rechazar la hipótesis nula de $\beta_1$ ($H_0: \quad \beta_1 = 0$) y la hipótesis nula de $\beta_0$ ($H_0: \quad \beta_0 = 0$). Esto quiere decir que el modelo lineal tiene una pendiente que no pasa por el origen. Esto se puede comprobar visualmente mediante el grafico 2 en el que se muestra dicho comportamiento.

![](lin_reg_uni.png)

Como es de esperarse, se obtuvo un valor de $R^2$ ajustado muy cercano a $R^2$, pues para el ajuste se utiliza una sola variable, por lo tanto $R^2$ ajustado no penaliza variables no representabas agregadas.

Los valores de log-likelihood y F-statistic son muy lejanos a cero, lo que nos puede decir que el modelo encontrado no sigue la tendencia de los datos, es decir que no se obtendría valores acertados si el modelo se utilizara para predecir nuevos datos. Este comportamiento se puede comprobar con la Probabilidad de F-statistic (p-value), el cual es muy cercano a cero, con lo que se rechaza la hipótesis nula que dice que el modelo encontrado es adecuado para predecir nuevos datos.

De la prueba Omnibus y su p-value, se obtuvo un valor de 17.091 y 0 consecutivamente. Con dicho p-value se rechaza la hipótesis de normalidad.
Una prueba visual existe en el grafico Q-Q del gráfico 3, donde se muestra una diferencia mayor, con la distribución normal, en las colas. Esta diferencia está por debajo de la normal, del lado positivo y por encima de la normal del lado negativo del gráfico, siendo la distribución del error menor al esperado con una distribución normal, lo que indica que una curtosis positiva, es decir que la distribución es más 'apuntada' que 'achatada'. Esto se comprueba con el valor obtenido de la prueba de *statsmodel* con una Curtosis de 3.440 y un sesgo de -0.356.

![](resid.png)
<p style="text-align: center;">Gráfico 3. Izquierda, Histograma de distribución de los residuos. Derecha, Grafico Q-Q.</p>

En el histograma que se encuentra en el mismo gráfico, se observa la distribución asimétrica de los residuos, con un sesgo hacia la izquierda, lo que indica que tenemos más probabilidad de encontrar valores atípicos, para el modelo, del lado izquierdo que del derecho.

Para conocer si los datos tienen una distribución homocedastica, se utilizó el estadístico Durbin Watson y Breush Pagan. Para la prueba de Durbin Watson con un rango entre 0 y 4, se espera un valor de 2, valor para el cual se tiene una varianza constante a traves de los residuos. Por otra parte, con el estadístico Breush Pagan se obtiene un valor de probabilidad con el que se rechazar o fallar a rechazar la hipótesis de homocedasticidad de los datos.

En este caso se obtuvo un valor de Durbin Watson de 1.918 y un valor de Breush Pagan de 3.20e-4. Aunque el valor del estadístico de Durbin Watson es cercano a 2, se rechazo la hipótesis de homocedasticidad con el estadístico de Breush Pagan, con lo cual se puede asumir la presencia de heterocedasticidad en los datos y poca autocorrelación entre los residuos. 

En el grafico 4 se puede observar que existe un cambio en la varianza de los residuos, con lo que se comprueba de manera visual la presencia de Heterocedasticidad en los datos.

![](residual_hetero.png)

<H3>Regresión univariante</H3>

De la regresión de todas las variables independientes de la base de datos, se obtuvieron los estadísticos de *statsmodel* (Tabla 2, 3 y 4).

<center>

| Prueba             |          valor |
|:-------------------|---------------:|
| R-squared:         |      1         |
| Adj.R-squared:     |      1         |
| F-statistic:       |      1.723e+27 |
| Prob(F-statistic): |      0         |

</center>

<p style="text-align: center;">Tabla 2. Pruebas estadísticas de la regresión multivariante</p>

De la tabla 2 se puede observar que se obtienen valores de $R^2$ y $R^2$ Ajustada de 1. Así mismo se obtiene un valor de F-statistic muy grande y su probabilidad de 0, lo que indica que toda la varianza de los datos es explicada con el modelo encontrado, esto ligado al sobre ajuste del modelo con las variables independientes escogidas.

<center>

| Parametro               |       coef |   std err |         t | P>\|t\| |
|:-----------------------:|:----------:|:---------:|:---------:|:-------:|
| const                   |  4.889e-12 |  2.45e-10 |  0.02     |   0.984 |
| gdp_per_capita          |  1.776e-14 |  1.45e-12 |  0.012    |   0.99  |
| family                  | -3.73e-14  |  1.28e-12 | -0.029    |   0.977 |
| health                  |  5.24e-14  |  1.27e-12 |  0.041    |   0.967 |
| freedom                 |  1.776e-15 |  8.37e-13 |  0.002    |   0.998 |
| generosity              |  6.573e-14 |  1.01e-12 |  0.065    |   0.948 |
| government_trust        | -1.243e-14 |  8.63e-13 | -0.014    |   0.989 |
| dystopia_residual       |  3.153e-14 |  7.23e-13 |  0.044    |   0.965 |
| Year                    | -1.592e-12 |  2.45e-10 | -0.006    |   0.995 |
| social_support          | -1.421e-14 |  1.01e-12 | -0.014    |   0.989 |
| cpi_score               | 91         |  1.2e-12  |  7.61e+13 |   0     |
| continent_Asia          | -2.665e-15 |  4.56e-13 | -0.006    |   0.995 |
| continent_Australia     |  1.066e-14 |  1.16e-12 |  0.009    |   0.993 |
| continent_Europe        |  1.288e-14 |  5.19e-13 |  0.025    |   0.98  |
| continent_North_America | -2.398e-14 |  9.47e-13 | -0.025    |   0.98  |
| continent_South_America |  3.997e-15 |  5.03e-13 |  0.008    |   0.994 |

</center>

<p style="text-align: center;">Tabla 3. Pruebas estadísticas de la regresión multivariante</p>

En la tabla 3 se puede observar que todos las variables con excepción de 'cpi_score’ han aceptado la hipótesis nula, por lo tanto no se encontró una relación con la variable de salida. Esto se puede observar con el valor del coeficiente y el error estándar encontrado el cual es muy cercano a cero para todos estos casos.

<center>

| Prueba         |   valor  | Prueba           |       valor |
|:---------------|---------:|:-----------------|------------:|
| Omnibus:       |   34.233 | Durbin-Watson:   |    0        |
| Prob(Omnibus): |    0     | Jarque-Bera(JB): |   35.018    |
| Skew:          |   -0.482 | Prob(JB):        |    2.49e-08 |
| Kurtosis:      |    2.638 | Cond.No.         | 5600        |
| AIC:           | -39560   | BIC:             | -39480      |
| Log-Likelihood:|  19796   | Breusch-Pagan    | 0 |

<p style="text-align: center;">Tabla 4. Pruebas estadísticas de la regresión multivariante</p>

</center>

Finalmente, con la tabla 3 se puede observar que se rechaza la hipótesis de la normalidad en los residuos mediante la Probabilidad de Ominus y Jarque-Bera.

Se obtiene un valor de Log-verosimilitud lejano a 0, lo que indica que el modelo encontrado no es válido y no será útil para predecir nuevos datos.

De la prueba de Durbin Watson se obtiene un valor igual a 0, lo que indica una alta correlación entre las variables, esto se puede sustentar con el valor de AIC y BIC, los cuales tienen un valor absoluto más de 2 veces mayor al obtenido con una sola variable. El estadístico Breusch-Pagan demuestra que no existe homocedasticidad en los residuos.

<div style="page-break-after: always"></div>

## Conclusiones

Mediante pruebas estadísticas a los residuos, producto de modelos lineales, se encontró que ninguno de los modelos antes obtenidos se puede esperar una buena predicción de nuevos datos.
No se cumple el supuesto de normalidad, ni de varianza constante a través de los valores predichos.
Así mismo se encontró que el modelo univariante es tiene mejor poder predictivo que el modelo multivariable, siendo el índice de corrupción la única variable encontrada con relación en los datos.
En un estudio futuro se buscará remover valores atípicos y utilizar un procedimiento de selección de variables para encontrar las variables que mejor representen a la variable de salida.

## Enlaces

Base de datos

[1] https://www.kaggle.com/datasets/eliasturk/world-happiness-based-on-cpi-20152020

Código

[2] 
