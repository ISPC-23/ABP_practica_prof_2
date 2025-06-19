# Project Charter - Entendimiento del Negocio

## Nombre del Proyecto

Predicción Justa del Rendimiento Académico Estudiantil

## Objetivo del Proyecto

Desarrollar un modelo predictivo basado en técnicas de regresión para estimar el rendimiento académico de estudiantes según sus hábitos diarios. Este modelo se diseñará con el propósito de ser la base para una futura aplicación que brinde recomendaciones personalizadas a estudiantes, ayudándolos a mejorar su desempeño. Además, se controlarán posibles sesgos por género y niveles de estrés, garantizando que las predicciones sean justas y equitativas.
## Alcance del Proyecto

### Incluye:

- Datos disponibles del dataset Student Habits vs Academic Performance (Kaggle), con información sobre hábitos como sueño, actividad física, uso del teléfono, horas de estudio, estrés, entre otros.
- Desarrollo de un modelo de regresión con métricas técnicas y de equidad.
- Registro del experimento con MLflow y análisis de equidad con Fairlearn.
- Recomendaciones generales basadas en los resultados para guiar futuras intervenciones educativas.

### Excluye:

- Desarrollo completo de una aplicación funcional.
- Validaciones longitudinales o seguimiento a largo plazo.
- Recolección de nuevos datos o encuestas.

## Metodología

Se utilizará la metodología TDSP (Team Data Science Process) para estructurar el flujo de trabajo. Se registrarán experimentos con MLflow y se evaluará la equidad de las predicciones utilizando Fairlearn, con foco en la variable de género y nivel de estrés.

## Cronograma

| Etapa | Duración Estimada | Fechas |
|------|---------|-------|
| Análisis Exploratorio (EDA) y Fairlearn | 2 semanas | del 1 al 15 de mayo |
| PPreparación de Datos (limpieza, codificación, mitigación de sesgos, feature engineering) | 2 semanas | del 16 al 30 de mayo |
| Modelado Inicial y Experimentación con MLflow | 2 semanas | del 1 al 15 de junio |
| Despliegue del Modelo en Producción (API / App Web con MLflow) | 2 semanas | del 16 al 30 de junio |
| Evaluación y entrega final | 3 semanas | del 1 de agosto al 21 de agosto |

Hay que tener en cuenta que estas fechas son de ejemplo, estas deben ajustarse de acuerdo al proyecto.

## Equipo del Proyecto

- Project Manager: TEJEDA Romina Soledad
- Data Engineer: CABRERA Marcos Rodrigo
- Data Scientist: BLASICHE Andrés
- Ethical Reviewer: PALOMEQUE Dalila Macarena

## Presupuesto

|    Etapa          | Costo estimado  |
|-------------------|-----------------|
| Análisis inicial  | 1500 - 3000 USD |
| Modelo predictivo | 2500 - 5000 USD |
| Desarrollo app web| 3000 - 6000 USD |
| Pruebas y ajustes | 1000 - 2000 USD |

## Stakeholders

- **Profesor**
**Cargo:** Coordinadora Académica  
 **Relación con el proyecto:** Es la usuaria final del modelo predictivo. Colabora en la definición de los objetivos pedagógicos y evalúa la utilidad del modelo para el ámbito educativo.  
 **Expectativas:** Espera recibir información clara y accionable sobre qué hábitos influyen en el rendimiento académico, para diseñar programas de mejora o intervención.  

- **Estudiantes de nivel secundario**
 **Cargo:** Sujetos del análisis / Beneficiarios  
 **Relación con el proyecto:** Son las personas sobre las cuales se aplica el modelo predictivo. Sus datos son utilizados para entrenar y validar el sistema.  
 **Expectativas:** Esperan recibir recomendaciones personalizadas que les ayuden a mejorar sus hábitos y, con ello, su rendimiento académico.

- **Equipo de Ciencia de Datos**  
 **Cargo:** Data Scientist, Data Engineer, Project Manager  
 **Relación con el proyecto:** Son responsables del diseño, desarrollo, entrenamiento, validación y documentación del modelo predictivo.  
 **Expectativas:** Desean desarrollar un modelo técnicamente sólido, interpretable y justo, que logre un impacto positivo y medible en la comunidad educativa.

## Aprobaciones

- [Nombre y cargo del aprobador del proyecto]
- [Firma del aprobador]
- [Fecha de aprobación]
