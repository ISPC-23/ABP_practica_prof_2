# Reporte de Datos

Este documento contiene los resultados del análisis exploratorio de datos.

## Resumen general de los datos

En esta sección se presenta un resumen general de los datos. Se describe el número total de observaciones, variables, el tipo de variables, la presencia de valores faltantes y la distribución de las variables.
### Descripción de las características
- **age**: Edad del estudiante.
- **gender**: Maculino/Femenino/Otro.
- **study_hours_per_day**: Promedio de horas de estudio por dia.
- **social_media_hours**: Tiempo que los estudiantes pasan usando redes sociales (Hs)
- **netflix_hours**: Tiempo promedio que pasan diariamente viendo Netflix.
- **part_time_job**: Se refiera a si el estudiante tiene trabajo de media jornada.
- **attendance_percentage**: Porcentanje de asistencia a clases.
- **sleep_hours**: Promedio de horas de sueño por estudiante.
- **diet_quality**: Calidad de la dieta, baja, media, buena.
- **exercise_frequency**: Cantidad de veces por semana que hace ejercicio.
- **parental_education_level**: Nivel de educación de los padres. Secundario, universitario, otro.
- **internet_quality**: Calidad de internet. Bueno, promedio, otro.
- **mental_health_rating**: Calificación de salud mental, en escala de 1-10
- **extracurricular_participation**: Realiza actividades extracurriculares fuera del colegio.
- **exam_score**: Puntuación on nota en el examen final (0-100)

## Resumen de calidad de los datos

* **parental_education_level:** 91 datos de la serie son valores nulos, y representan el 9,1% de los datos, nos conviene imputarlos con la moda de dicha serie. Si es bimodal, asignaremos aleatoriamente los dos valores, respetando su proporción.

## Variable objetivo

### Nos importa la distribución de la variable respuesta por:
1. Elección del modelo
Algunos algoritmos hacen supuestos sobre la distribución de la variable respuesta. Por ejemplo:

En regresión lineal, se asume que los residuos (errores) están normalmente distribuidos.

En regresión logística, se espera que la variable respuesta sea binaria o categórica.

En modelos probabilísticos (como Naive Bayes), la distribución afecta directamente las predicciones.

2. Transformaciones y normalización (para regresión)
Si la variable respuesta tiene una distribución muy sesgada (skewed), puede perjudicar el rendimiento de algunos modelos. En ese caso, se pueden aplicar transformaciones como:

Logarítmica (log(y)),

Box-Cox,

Raíz cuadrada, etc.

Estas transformaciones ayudan a que el modelo aprenda mejor si se necesita una distribución más normal.

3. Evaluación y validación
Conocer la distribución ayuda a:

Dividir mejor los datos (por ejemplo, usar estratificación si hay clases desbalanceadas),

Interpretar correctamente errores o métricas,

Detectar si el modelo sobreajusta o no generaliza bien en ciertas partes del espacio de salida.

4. Interpretabilidad
Saber cómo se distribuye la variable objetivo permite:

Identificar outliers o valores atípicos,

Detectar patrones anómalos,

Ajustar expectativas sobre el modelo (por ejemplo, si la mayoría de los valores de y están entre 10 y 20, pero hay algunos de 1000, podrías necesitar un enfoque especial).

Vemos un sesgo positivo y que los datos están muy aglomerados entorno a la media, como es esta variable la que nos interesa predecir. queremos que sea lo mas normal en lo posible para tener mejor control sobre la variable, entonces normalizamos los datos. Vamos a aplicar una normalización logarítmica y de raíz cuadrada para comparar.

Para hacer una prueba a que distribucion se aproxima mas nuestra variable respuesta usamos fitter.


| sumsquare_error	| aic | bic	| kl_div | ks_statistic	| ks_pvalue |
|------|------|------|------|------|-------|
| **norm** |	0.005190	| 985.702409	| 995.517920 |	inf	 | 0.035864	 | 1.490117e-01 |
| **gamma** |	0.005201 |	993.216125 |	1007.939391	| inf	| 0.039076 |	9.189001e-02 |
| **chi2** |	0.005255 |	996.480514 |	1011.203780 |	inf |	0.041500 |	6.206239e-02 |
| **logistic** |	0.005271 |	981.866178 |	991.681688 |	inf |	0.043740 |	4.229109e-02 |
| **beta** | 	0.005544 |	972.664744 |	992.295765 |	inf |	0.054228 |	5.370036e-03 |
| **cauchy** |	0.006324 |	1008.839400 |	1018.654911 |	inf |	0.106730 |	2.252889e-10 |
| **powerlaw** |	0.007239 |	932.140185 |	946.863451 |	inf |	0.142039 |	4.573714e-18 |
| **exponpow** |	0.015709 |	967.897851 |	982.621116 |	inf |	0.299856 |	3.104356e-80 |
| **expon** |	0.018121 |	950.524097 |	960.339607 |	inf |	0.331476 |	2.035064e-98 |

vemos que la distribución nomarl es la que mejor se ajusta, ya que la suma de los errores cuadráticos es la menor, los criterios de Akaike(aic) y Bayesiano (bic) que penalizan por complejidad de modelo son los mas bajos y el test de kolmogorov-Smirnov (ks-statistics) el cual mide la funcion distribucion acumulada real vs la teorica, osea por ejemplo, en la normal teorica me dice que el 25% está abajo de 65 puntos y mis datos dicen que el 30% estan por debajo, entonces hace esa diferencia. además el valor p para ks es mayor a 0.05 por lo tanto la distribución normal es la que mejor ajusta

## Variables individuales

| student_id |	gender |	part_time_job |	diet_quality |	parental_education_level |	internet_quality |	extracurricular_participation |
|-----|-----|-----|-----|-----|-----|-----|
| **count** |	1000 |	1000 |	1000 |	1000 | 1000 |	1000 |	1000 |
| **unique** |	1000 |	3 |	2 |	3 |	3 |	3 |	2 |
| **top** |	S1999 |	Female |	No |	Fair |	High School |	Good |	No |
| **freq** |	1 |	481 |	785 |	437 |	442 |	447 |	682 |

**student_id** la eliminamos porque no aporta información relevante


## Ranking de variables

En esta sección se presenta un ranking de las variables más importantes para predecir la variable objetivo. Se utilizan técnicas como la correlación, el análisis de componentes principales (PCA) o la importancia de las variables en un modelo de aprendizaje automático.

## Relación entre variables explicativas y variable objetivo

Se nos hizo interesante mostrar la relación entre el nivel educativo de los padres y el rendimiento estudiantil en términos de género. En general, observamos que a medida que aumenta el nivel educativo de los padres, los puntajes de los estudiantes tienden a aumentar.

### Cómo están relacionadas nuestras variables categóricas con los puntajes de examen?

- diet_quality  
categorías: ['Fair', 'Good', 'Poor']  
Cantidad de grupos: 3  
p-valor: 0.2824

- parental_education_level  
categorías: ['Bachelor', 'High School', 'Master']  
Cantidad de grupos: 3  
p-valor: 0.3412

- internet_quality  
categorías: ['Average', 'Good', 'Poor']  
Cantidad de grupos: 3  
p-valor: 0.2320

- part_time_job  
categorías: ['No', 'Yes']  
Tamaño grupos: 785 y 215  
p-valor: 0.4006

- extracurricular_participation   
categorías: ['No', 'Yes']  
Tamaño grupos: 682 y 318  
p-valor: 0.9778

- gender  
categorías: ['Female', 'Male', 'Other']  
Cantidad de grupos: 3  
p-valor: 0.8674

Estos p-valores altos (todos mayores a 0.05) indican que no hay evidencia estadísticamente significativa de que las variables categóricas estén asociadas con el puntaje del examen (exam_score)
