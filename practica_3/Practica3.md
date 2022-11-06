
<style>h1,h2,h3,h4 { border-bottom: 0; } </style>

&nbsp;

&nbsp;

&nbsp;

<div style="text-align: center;">
<img src="imagenes/logo_iteso.jpg" alt="drawing" style="width:200px;"/>
</div>

<h1 style="text-align: center;">Práctica 2. Análisis de la Varianza</h1>

<H2 style="text-align: center;">Nombre: Gregorio Alberto Alvarez Alvarez</H2>

<H2 style="text-align: center;">Materia: Análisis estadístico multivariable</H2>

<div style="page-break-after: always"></div>

<div style="page-break-after: always"></div>

<H2>Introducción</H2>


Los datos fueron extraidos de la base de datos de la Universidad de California Irvine [1](https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29)  que a su vez fue extraído del estudio [2](https://arxiv.org/abs/1506.06297). El propósito del estudio en [2] fue el de encontrar una relación entre el perfil de personalidad y el riesgo de consumo de drogas, para esto se utilizaron 12 atributos de cada participante y tres grupos de drogas.
Al final del estudio se concluyó que existe una relación entre los factores de personalidad y el consumo de varias drogas. Así mismo se mapeo el riesgo de consumo de cada una de estas sustancias con los factores de personalidad, el rango de edad y genero del individuo.

A partir de la base de datos antes mencionada y con el fin de identificar los grupos, por edad y nivel de educación, con mayor riesgo de desarrollar una dependiente a sustancias adictivas, en este estudio se busca indagar sobre la relación entre el número de drogas consumidas y el rango de edad y educación al que pertenecen los individuos.

Este tipo de estudios son utilizados en los Estados Unidos [3](https://store.samhsa.gov/product/Substance-Misuse-Prevention-for-Young-Adults/PEP19-PL-Guide-1), para apoyar a los grupos mas vulnerables de manera temprana. [4](https://www.samhsa.gov/data/release/2018-national-survey-drug-use-and-health-nsduh-releases) expresa que el grupo más vulnerable para el consumo de drogas se encuentra contenido en la transición hacia la adultes.
Esta problemática se ha estudiado en [5](https://pubmed.ncbi.nlm.nih.gov/26215473/) y [6](https://journals.tubitak.gov.tr/elektrik/vol22/iss3/14/) donde se encontró que la edad es un factor importante para predecir el riesgo a la disposición a las drogas.

<div style="page-break-after: always"></div>

## Objetivo

Mediante el análisis de la varianza (ANOVA), encontrar si los grupos de edad y nivel de educación son distintos o iguales ante el número de drogas consumidas para cada grupo y en caso de que sean iguales, cuales son estos grupos.

Primeramente, encontrar si las distribuciones de los grupos cumplen con el supuesto de normalidad de los grupos y homocedasticidad entre los grupos.

A partir de ahí, encontrar el grado de relación entre los niveles a estudiar con la prueba ANOVA y una prueba no paramétrica (Kruskal).

Mediante pruebas de Turkey, comparar y encontrar diferencias significativas entre grupos, así como analizar la diferencia entre las medias.

Finalmente, aplicar ANOVA bidireccional a las variables de grupos edad y nivel de educación, y numero de drogas consumidas, con el fin de analizar la interacción de cada una de las variables y sus grupos.

<div style="page-break-after: always"></div>

## Descripción y análisis de la base de datos

la base de datos fue obtenida de [1](https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29), que a su vez fue tomada de [2](https://arxiv.org/abs/1506.06297),
el cual forma parte de una investigación aprobada por el grupo asesor ético de psicología forense () de la Universidad de Leicestr.
Los datos fueron obtenidos entre marzo del 2011 y marzo del 2012, periodo en el que se encuestaron a 2051 participantes, por medio de una encuesta anónima. Las personas encuestadas fueron recrutadas para participar durante 12 meses. Después de revisar la viabilidad de los datos, se eligieron datos de 1885 participantes.

Esta tabla contiene 12 atributos de cada participante, entre las que se encuentran los puntajes de las pruebas psicológicas aplicadas y datos de los participantes como su género y edad.

Las siguientes pruebas 

Pruebas de personalidad obtenidas mediante el inventario NEO-FFI-R, la cual contiene múltiples preguntas, con una escala de 1 al 4, desde 'en desacuerdo' hasta 'fuertemente de acuerdo'. Como aparecen en []():

- Nscore: Neurotismo. Tendencia a largo plazo a experimentar emociones negativas como nerviosismo, tension, ansiedad y depresión. 

- Escore: Extraversión. Se manifiesta al presentar características calidad, activas, abiertas, asertivas, alegres, en busca de estímulo, entre otras.

- Oscore: Abertura a la experiencia. Los individuos que la presentan, suelen tener una apreciación general por el arte, ideas inusuales, imaginación y creatividad, intereses varios y poco convencionales.

- Ascore: Simpatía (Agreeableness). Es una dimensión de las relaciones interpersonales, caracterizada por el altruismo, la confianza, modestia, amabilidad, compasión y cooperatividad.

- Cscore: Escrupulosidad (Conscientiousness). Una tendencia a ser organizado y dependiente, persistente, eficiente, fidedigno y de mucha fuerza de voluntad.

- Impulsive: proviene de la prueba de *'Barratt inpulsiveness Scale (BIS-11)'* la cual mide el constructo condicional de impulsividad y contiene preguntas como la prueba anterior.

- SS: Proviene de la prueba ImpSS, la cual mide rasgos de búsqueda de sensaciones y contiene preguntas de verdadero falso.

Atributos no psicológicos

- Edad: De cada participante se recabo el rango de edad en el que se encuentra, con las siguientes opciones: 18-24, 25-34, 35-44, 44-55, 55-64 y 65+. Siendo el rango de 18 a 24 con más entradas.
Para este estudio se juntó el grupo de 45 a 54, de 55 a 64 y 65 y más como un solo grupo renombrado como 45+.

- Genero: F para femenino y M para masculino

- Educación: grado máximo de estudio cursado, que contiene las siguientes entradas: Dejo la escuela antes de los 16 años, dejo la escuela a los 16 años, dejo la escuela a los 17 años, dejo la escuela a los 18 años, certificado o diploma profesional, alguna universidad sin diploma o certificado, grado universitario, maestría y doctorado.
Con el fin de equilibrar los rangos de participantes en cada grupo, en este estudio se acumularon los datos de los grupos desde dejo la escuela antes de los 16 años hasta dejo la escuela a los 18 años y se renombro como dejo la escuela antes de o a los 18 años.
Así mismo, se acumularon los grupos de grado de maestría y grado de doctorado como maestría y doctorado.

Uso de drogas.

- 18 drogas psicoactivas del sistema nervioso fueron analizadas.
Entre las depresivas se encuentra el alcohol, nitrito de amilo, benzodiazepinas, tranquilizantes,
solventes e inhalantes gamma-hidroxibutirato y opiáceos como heroína y metadona/opiáceos recetados.
Los estimulantes contienen a la nicotina, anfetamina, cocaína en polvo, crack cocaine, cafeína y chocolate.
En los alucinógenos se encuentran los hongos alucinógenos, cannabis, éxtasis, ketamina, LSD y 
legal Higs como el mefedrone, la salvia y otras mezclas para fumar legales.

1. La información que se recabo acerca de estas variables fue la última vez que se consumió la sustancia, con las siguientes opciones: el día anterior (CL6), la semana pasada (CL5), el mes pasado (CL4), el año pasado (CL3), la década pasada (CL2), hace más de una década (CL1) y nunca consumido (CL0)

2. Para este estudio, cada una de estas variables se convirtió a valores numéricos, de la siguiente forma:
Del rango de CL6 a CL4 se asignó el valor de 1 (Consumidores).
Al valor CL3 se asignó 0.5 (Con posibilidad de ser consumidor).
Del rango de CL2 a CL0 se asignó el valor de 0 (No consumidores).

3. Después de aplicar la conversión numérica a estas variables, se acumularon con una suma de forma transversal (Suma de sustancias para cada participante), con lo que se obtuvo la variable de consumo, con un rango de 0 a 18, lo cual representa la cantidad de sustancias consumidas por cada participante.

<div style="page-break-after: always"></div>

## Desarrollo y resultados.

Como se mencionó anteriormente, se eligió el número de drogas consumidas como variable dependiente y el grupo de edad y nivel de educación como variable categorica independiente.

### Analisis por grupo de Edad

**Primeras pruebas**

Se visualizo la cantidad de entradas por grupo de edad (Figura 1) y se optó por elegir una muestra aleatoria de 300 participantes para cada categoría.

![pob_grupo_edad](imagenes/poblacion_por_edad.png)
<p style="text-align: center;">Figura 1. Cuentas por grupo de edad de toda la base de datos. </p>

Una primera visualización de la distribución de los datos, se obtuvo con un gráfico de boxplot (Figura 2). De esta primera prueba se ve que las medias entre los grupos son distintas, con una diferencia considerablemente distinta entre el grupo 18-24 y el resto de los grupos. Se puede observar que la distribución de los grupos 18-24 y 25-34 tienen una varianza considerablemente mayor a los grupos 35-44 y 45+. Para estos últimos grupos se puede observar una cantidad mayor de valores atípicos, lo que indica que su distribución no es normal.

![boxplot_por_edad](imagenes/boxplot_por_edad.png)
<p style="text-align: center;">Figura 2. Gráfico de Boxplot agrupado por Edad.</p>

Se obtuvieron las varianzas de cada grupo (Tabla 1). De aquí se observó que existen grupos (18-24 y 25-34) en los que su varianza es 2 veces mayor a el grupo con menor varianza (45+), lo que suma a la hipótesis de varianza no constante a través de la variable independiente.

<center>

| Age   |   Varianza    |
|:------|--------------:|
| 18-24 |       7.42447 |
| 25-34 |       7.05546 |
| 35-44 |       3.56745 |
| 45+   |       1.96505 |

</center>
<p style="text-align: center;">Tabla 1. Datos de varianza por grupo de Edad.</p>

Se sabe que los datos deben de tener una distribución normal y la varianza entre los grupos debe de ser constante, por lo que se revisara esto mediante pruebas estadísticas.

**Pruebas estadísticas**

Para probar la normalidad de las distribuciones se utilizó la prueba de Shapiro-Wilk (Tabla 2). Con esta prueba se obtuvo que ninguna variable sigue una distribución normal (todos los p-values menores a 0.05), por lo que se utilizara una prueba no paramétrico para revisar la homocedasticidad (Levene) y se comparara el modelo ANOVA con un análisis de varianza no paramétrico, para acreditar la confiabilidad de este.

<center>

|       |        W |        pval | normal   |
|:------|---------:|------------:|:---------|
| 25-34 | 0.913851 | 4.23381e-12 | False    |
| 35-44 | 0.845494 | 1.18604e-16 | False    |
| 18-24 | 0.981889 | 0.000763397 | False    |
| 45+   | 0.84482  | 1.08931e-16 | False    |

</center>
<p style="text-align: center;">Tabla 2. Prueba de Shapiro-Wilk utilizada para probar normalidad en la distribución de grupos. </p>

Se aplico la prueba de Levene (Tabla 3), de ahí se obtiene un p-value menor al 5%, lo que indica que se ha rechazado la hipótesis nula de Homocedasticidad en la variable dependiente, afirmando las pruebas anteriores.

<center>

|        |       W |       pval | equal_var   |
|:-------|--------:|-----------:|:------------|
| levene | 46.1968 | 3.0025e-28 | False       |

</center>
<p style="text-align: center;">Tabla 3. Prueba de Levene. Utilizada para probar varianza constante entre grupos. </p>

A continuación se aplicó el análisis de la varianza, con el modelo ANOVA de la libreria `statsmodel`. Con lo que se obtuvo la tabla 4. De ahí se puede observar que el valor de la probabilidad de F es muy cercano a cero, rechazando la hipótesis de medias iguales entre grupos.

<center>

|          |   sum_sq |   df |       F |        PR(>F) |
|:---------|---------:|-----:|--------:|--------------:|
| Age      |  2172.02 |    3 | 144.712 |   5.35034e-80 |
| Residual |  5983.71 | 1196 | nan     | nan           |

</center>
<p style="text-align: center;">Tabla 4. Prueba ANOVA. De aquí se observa que los grupos no tienen la misma media</p>

Para obtener más información acerca de las variables que no cumplen la suposición de media igual, se procederá a utilizar la prueba post hoc de Tukey.
De (Tabla 5). De esta tabla se puede observar que todos los grupos tienen medias significativamente diferentes entre si. La variable 'meandiff' se calcula substrayendo la media del grupo 2 del grupo 1, lo que significa que, en este caso, los grupos más jóvenes consumen más tipos de drogas que su contraparte más vieja. De ahí se puede deducir que la edad esta correlacionada negativamente con el número de drogas consumidas.

<center>

| group1   | group2   |   meandiff |   p-adj |   lower |   upper | reject   |
|:---------|:---------|-----------:|--------:|--------:|--------:|:---------|
| 18-24    | 25-34    |    -1.8817 | -0      | -2.3515 | -1.4118 | True     |
| 18-24    | 35-44    |    -2.9833 | -0      | -3.4532 | -2.5135 | True     |
| 18-24    | 45+      |    -3.515  | -0      | -3.9848 | -3.0452 | True     |
| 25-34    | 35-44    |    -1.1017 |  0      | -1.5715 | -0.6318 | True     |
| 25-34    | 45+      |    -1.6333 | -0      | -2.1032 | -1.1635 | True     |
| 35-44    | 45+      |    -0.5317 |  0.0192 | -1.0015 | -0.0618 | True     |
</center>
<p style="text-align: center;">Tabla 5. Prueba Tukey. Se observa que ningun par de tratamientos muestra una media significativamente cercana entre si.</p>

Nuevamente se incita a utilizar pruebas no paramétricas para revisar la confiabilidad de la prueba ANOVA Y Tukey antes realizadas.
Como contraparte no paramétrica de ANOVA se utiliza la prueba de Kruskal, con lo que se obtiene un p-value de ~3.07e-64 lo cual rechaza la hipótesis nula de medias significativamente cercanas y afirma lo obtenido por la prueba ANOVA.
Se obtiene la prueba ad hoc no paramétrica de Bonferroni (Tabla 6), en la que se obtiene que todas las medias son distintas entre si, afirmando lo obtenido por la prueba de Tukey.

<center>

|        |   25-34     |       35-44 |       18-24 |        45+  |
|-------:|------------:|------------:|------------:|------------:|
|  25-34 | 1           | 3.70825e-07 | 2.94194e-20 | 3.35637e-18 |
|  35-44 | 3.70825e-07 | 1           | 3.63585e-46 | 0.00196355  |
|  18-24 | 2.94194e-20 | 3.63585e-46 | 1           | 1.65755e-67 |
|  45+   | 3.35637e-18 | 0.00196355  | 1.65755e-67 | 1           |

</center>
<p style="text-align: center;">Tabla 6. Prueba Bonferrori. Se observa que ningun par de tratamientos muestra una media significativamente cercana entre si, confirmando lo obtenido con la prueba Tukey.</p>

### Análisis por nivel de educación.

A partir de los mismos datos (Figura 3), se obtuvo una muestra de 250 participantes para cada grupo de nivel de educación.

![poblacion_por_nived](imagenes/poblacion_por_nived.png)
<p style="text-align: center;">Figura 3. Cuentas por grupo de nivel de educación de toda la base de datos.</p>

Para analizar rápidamente la distribución y las medias de cada grupo, se obtuvo el grafico de boxplot agrupado por nivel de educación. Aquí se encontró que los grupos Maestría o doctorado, Profesional con certificado y Grado universitario muestran medias parecidas, siendo los últimos 2 los que presentan una distribucion similar en el cuartil 2 y 3.

![boxplot_por_nived](imagenes/boxplot_por_nived.png)
<p style="text-align: center;">Figura 2. Gráfico de Boxplot agrupado por nivel de educación.</p>

De la prueba de varianza por grupo, se encontró que ningun grupo tiene una varianza mayor a dos veces la varianza del grupo con menor varianza, por lo que hasta el momento, se puede suponer una varianza constante a través de la variable de nivel de educación.

| Education                         |   Consumption |
|:----------------------------------|--------------:|
| Left school at or before 18       |       7.41221 |
| Master or Doctorate degree        |       5.00562 |
| Professional certificate/ diploma |       5.68877 |
| Some co. or un. no certificate    |       7.37968 |
| University degree                 |       6.7258  |

De la prueba de normalidad se encontró que ningún grupo sigue una distribución normal. Al aplicar la prueba de homocedasticidad no paramétrica, se encontró varianza no constante a través de la variable de nivel de educación.

|                                   |        W |        pval | normal   |
|:----------------------------------|---------:|------------:|:---------|
| Master or Doctorate degree        | 0.806162 | 6.04665e-17 | False    |
| Professional certificate/ diploma | 0.856744 | 1.74596e-14 | False    |
| Left school at or before 18       | 0.926749 | 8.82353e-10 | False    |
| University degree                 | 0.826929 | 5.35033e-16 | False    |
| Some co. or un. no certificate    | 0.984261 | 0.00733695  | False    |

|        |       W |        pval | equal_var   |
|:-------|--------:|------------:|:------------|
| levene | 6.42073 | 4.09948e-05 | False       |

De la prueba ANOVA, se observa que existe al menos un tratamiento que no tiene la misma media que el resto del grupo. De la prueba de Tukey se confirma la suposición antes hecha sobre que las de los grupos Maestría o doctorado, Profesional con certificado y Grado universitario son similares.

|          |   sum_sq |   df |       F |        PR(>F) |
|:---------|---------:|-----:|--------:|--------------:|
| Age      |  2427.07 |    3 | 147.464 |   8.95036e-82 |
| Residual |  6835.86 | 1246 | nan     | nan           |

| group1                           | group2                           |   meandiff |   p-adj |   lower |   upper | reject   |
|:---------------------------------|:---------------------------------|-----------:|--------:|--------:|--------:|:---------|
| Left-school-at-or-before-18      | Master-or-Doctorate-degree       |     -1.386 |  0      | -2.0062 | -0.7658 | True     |
| Left-school-at-or-before-18      | Professional-certificate-diploma |     -0.934 |  0.0004 | -1.5542 | -0.3138 | True     |
| Left-school-at-or-before-18      | Some-co.-or-un.-no-certificate   |      1.388 |  0      |  0.7678 |  2.0082 | True     |
| Left-school-at-or-before-18      | University-degree                |     -0.996 |  0.0001 | -1.6162 | -0.3758 | True     |
| Master-or-Doctorate-degree       | Professional-certificate-diploma |      0.452 |  0.2709 | -0.1682 |  1.0722 | False    |
| Master-or-Doctorate-degree       | Some-co.-or-un.-no-certificate   |      2.774 | -0      |  2.1538 |  3.3942 | True     |
| Master-or-Doctorate-degree       | University-degree                |      0.39  |  0.4232 | -0.2302 |  1.0102 | False    |
| Professional-certificate-diploma | Some-co.-or-un.-no-certificate   |      2.322 | -0      |  1.7018 |  2.9422 | True     |
| Professional-certificate-diploma | University-degree                |     -0.062 |  0.9988 | -0.6822 |  0.5582 | False    |
| Some-co.-or-un.-no-certificate   | University-degree                |     -2.384 | -0      | -3.0042 | -1.7638 | True     |

Aplicando la prueba no parametrica de Kruskal se encuentra un p-value de ~1.71e-38 lo que confirma el resultado de ANOVA. Aplicando la prueba no parametrica ad hoc Bonferroni, se encuentran los mismos resultados que los obtenidos con Tukey, lo cual confirma la fiabilidad de estos modelos (ANOVA y Tukey).

|    |           M-D |           P_C_D |           L_S_18 |           U_D |           S_C_U/NoCert |
|---:|------------:|------------:|------------:|------------:|------------:|
|  M-D | 1           | 0.0690168   | 1.03946e-10 | 0.802839    | 6.65223e-35 |
|  P_C_D | 0.0690168   | 1           | 0.000340189 | 1           | 1.48034e-22 |
|  L_S_18 | 1.03946e-10 | 0.000340189 | 1           | 3.62014e-06 | 1.91936e-08 |
|  U_D | 0.802839    | 1           | 3.62014e-06 | 1           | 1.18428e-26 |
|  S_C_U/NoCert | 6.65223e-35 | 1.48034e-22 | 1.91936e-08 | 1.18428e-26 | 1           |


<div style="page-break-after: always"></div>

### Conclusiones

De las pruebas antes aplicadas se encontró que todos las medias de los grupos de número de drogas consumidas son distintos entre si. por lo que la variable categórica podría ser añadida a un modelo para predecir el número de drogas consumidas dada una edad. De esta sección se encontró que los grupos que consumen mayor numero drogas son los más jóvenes, sin embargo no se puede concluir que son el grupo más vulnerable para desarrollar dependencia a estas sustancias, ya que no se solo se consideró una sola variable para este análisis.

Por otra parte, se encontró que los grupos con mayor grado de educación presentan una media significativamente similar. Estos grupos son los que consumen una cantidad de drogas menor al resto de grupos.

Se sabe que el estudio no es lo suficientemente robusto para predecir, debido a que no se toman en cuenta otros factores de cada individuo, como los atributos psicológicos o factores socioeconómicos, por lo que se esperó obtener los mejores resultados basándose en la aleatoriedad de los datos tomados. Se espera aplicar ANOVA bivariado en un próximo estudio para conocer la interdependencia entre las variable independientes analizadas en este estudio.

### Referencias.

[1](https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29) https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29

[2](https://arxiv.org/abs/1506.06297) https://arxiv.org/abs/1506.06297

[3](https://store.samhsa.gov/product/Substance-Misuse-Prevention-for-Young-Adults/PEP19-PL-Guide-1) https://store.samhsa.gov/product/Substance-Misuse-Prevention-for-Young-Adults/PEP19-PL-Guide-1

[4](https://www.samhsa.gov/data/release/2018-national-survey-drug-use-and-health-nsduh-releases) https://www.samhsa.gov/data/release/2018-national-survey-drug-use-and-health-nsduh-releases

[5](https://pubmed.ncbi.nlm.nih.gov/26215473/) https://pubmed.ncbi.nlm.nih.gov/26215473/

[6](https://journals.tubitak.gov.tr/elektrik/vol22/iss3/14/) https://journals.tubitak.gov.tr/elektrik/vol22/iss3/14/

**Referencia hacia el código**

[git](https://github.com/Gegori1/analisis-estadistico-multivariado/tree/master/practica_3) https://github.com/Gegori1/analisis-estadistico-multivariado/tree/master/practica_3

<style>h1,h2,h3,h4 { border-bottom: 0; } </style>