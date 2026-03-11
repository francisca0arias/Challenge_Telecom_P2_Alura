# Challenge_Telecom_P2_Alura
El proyecto busca crear modelos predictivos para anticipar la cancelación de clientes en Telecom X, usando datos demográficos, contractuales y de consumo. El objetivo estratégico es adelantarse a la pérdida de clientes y activar acciones de retención basadas en información confiable
Este es una propuesta de **README profesional** con un lenguaje de **Senior Data Scientist**. Se ha eliminado el exceso de iconos y se ha estructurado como un informe de arquitectura técnica y estratégica, ideal para un portafolio de grado ejecutivo.



**Proyecto de Finalización - Programa Oracle ONE | Alura Latam** **Unidad de Análisis:** Telecom X — Región LATAM

## 1. Resumen Ejecutivo

El presente proyecto establece un framework analítico para abordar el fenómeno de la deserción de clientes (*Churn*) en Telecom X. Mediante la implementación de un pipeline de Machine Learning de extremo a extremo, se transformaron datos demográficos, contractuales y de consumo en una herramienta de soporte a decisiones. El objetivo central es la transición de una cultura reactiva a una estrategia de retención proactiva basada en la probabilidad de abandono.

## 2. Definición del Problema y Objetivos

### 2.1 Propósito Estratégico

Anticipar la pérdida de clientes mediante el modelado de variables latentes, permitiendo la optimización del presupuesto de marketing y fidelización al dirigir esfuerzos exclusivamente a los segmentos de alto riesgo y valor.

### 2.2 Objetivos Analíticos

* **Identificación de Drivers:** Determinar las variables con mayor peso estadístico en la decisión de cancelación.
* **Modelado Predictivo:** Desarrollar y validar algoritmos de clasificación binaria (Supervisados).
* **Benchmarking de Modelos:** Comparar la capacidad de generalización y métricas de desempeño entre arquitecturas lineales y basadas en conjuntos (*Ensembles*).
* **Generación de Insights de Negocio:** Traducir métricas técnicas en recomendaciones accionables.

## 3. Ingeniería de Características (Feature Engineering)

Para garantizar la convergencia de los modelos y la integridad del análisis, se aplicó un tratamiento riguroso de los datos:

* **Taxonomía de Variables:** Clasificación exhaustiva entre atributos categóricos (métodos de pago, tipos de servicio) y métricas cuantitativas (`tenure`, `MonthlyCharges`).
* **Codificación (Encoding):** Implementación de *One-Hot Encoding* para variables nominales, transformando dimensiones cualitativas en vectores numéricos aptos para el procesamiento tensorial.
* **Estrategia de Partición:** División de los datos en conjuntos de Entrenamiento (70%) y Prueba (30%). Se aplicó una **estratificación del target** para preservar la distribución original del Churn (~26.5%) y mitigar sesgos de selección.
* **Escalamiento y Normalización:** Aplicación de `StandardScaler` en modelos sensibles a la magnitud (Regresión Logística), manteniendo la integridad original para modelos no paramétricos basados en árboles.

## 4. Implementación y Evaluación de Modelos

Se seleccionaron dos arquitecturas con naturalezas matemáticas distintas para evaluar el compromiso entre interpretabilidad y potencia predictiva:

1. **Regresión Logística:** Utilizada como base de comparación por su alta interpretabilidad a través de los *odds ratios* y coeficientes.
2. **Random Forest (Ensemble Learning):** Implementado para capturar relaciones no lineales y dependencias complejas entre variables.

### 4.1 Métricas de Desempeño

La validación no se limitó al *Accuracy*, sino que se priorizó un análisis multidimensional:

* **Recall & F1-Score:** Cruciales para minimizar los falsos negativos (clientes que se van sin ser detectados).
* **Área bajo la curva (ROC-AUC):** Evaluación de la capacidad de discriminación del modelo.
* **Diagnóstico de Ajuste:** Análisis detallado de *Overfitting* y *Underfitting* mediante la comparación de curvas de aprendizaje entre los sets de entrenamiento y testeo.

## 5. Hallazgos Críticos (Insights del EDA)

El Análisis Exploratorio de Datos reveló patrones determinantes para la retención:

* **Fragilidad Contractual:** Los contratos de renovación mensual (*Month-to-Month*) actúan como el principal predictor de fuga.
* **Vulnerabilidad en el Servicio:** Existe una correlación positiva inesperada entre el servicio de **Fibra Óptica** y el churn, sugiriendo una posible brecha de calidad o precio frente a la competencia.
* **Efecto Antigüedad:** El riesgo de cancelación decrece exponencialmente con el incremento de la tenencia (*tenure*), validando la importancia del *onboarding* inicial.

## 6. Conclusiones y Recomendaciones Ejecutivas

El modelo de **Regresión Logística** demostró ser el más equilibrado para este caso de uso, proporcionando una base sólida para la explicación de fenómenos de negocio.

**Recomendaciones para el Negocio:**

1. Incentivar la migración de contratos mensuales a contratos anuales mediante beneficios de lealtad.
2. Auditar la satisfacción técnica de los usuarios de fibra óptica.
3. Promover el uso de métodos de pago automáticos para reducir la rotación pasiva.

---

**Stack Tecnológico:** Python (Pandas, NumPy, Scikit-Learn), Matplotlib, Seaborn.

**Estructura de Archivos:** El repositorio incluye el notebook de análisis (`.ipynb`), el dataset procesado (`.csv`) y los activos visuales de validación técnica.
🚀 Pipeline de Ejecución: Ordenamiento Operativo
Para reproducir el análisis de Telecom X, sigue este flujo secuencial:

Fase 1: Configuración del Entorno (Setup)
Antes de iniciar, se deben consolidar las dependencias técnicas. El proyecto utiliza un stack basado en estabilidad y análisis estadístico.

Instalación: Ejecutar el comando de gestión de paquetes.

Bash
pip install pandas numpy scikit-learn matplotlib seaborn
Importación: Carga de módulos de preprocesamiento, modelos (Linear & Ensemble) y métricas de validación.

Fase 2: Ingesta y Preparación de Datos (ETL)
El flujo de datos está diseñado para ser directo y reproducible:

Extracción: Carga automatizada del dataset datos_tratados.csv mediante la URL de Google Drive integrada en el script.

Taxonomía: Clasificación automática de variables en Categóricas (Encoding) y Numéricas (Scaling).

División Estratégica: Partición del dataset en un ratio 70/30 utilizando stratify=y. Esto garantiza que la proporción de Churn (~26.5%) se mantenga idéntica tanto en el entrenamiento como en la validación.

Fase 3: Modelado y Benchmarking
Se ejecutan dos experimentos en paralelo para comparar rendimiento:

Modelo Lineal (Regresión Logística): Se entrena para obtener coeficientes interpretables. Se aplica StandardScaler para normalizar las magnitudes de cargos y antigüedad.

Modelo de Conjunto (Random Forest): Se ejecuta para capturar relaciones no lineales complejas entre servicios contratados y permanencia.

Fase 4: Evaluación y Diagnóstico
Métricas de Performance: Cálculo de ROC-AUC, Recall y F1-Score.

Análisis de Varianza: Comparación de resultados entre Train y Test.

Resultado esperado: Identificación de la estabilidad de la Regresión Logística frente al sobreajuste del Random Forest.

Visualización de Errores: Generación de la Matriz de Confusión para cuantificar la capacidad de detección de falsos negativos.

Fase 5: Interpretación y Cierre (Insights)
Jerarquización de Variables: Extracción de pesos para determinar que el Tenure es la palanca principal de retención.

Recomendaciones Ejecutivas: Generación de la hoja de ruta para la migración de contratos y optimización de servicios (Fibra Óptica).
