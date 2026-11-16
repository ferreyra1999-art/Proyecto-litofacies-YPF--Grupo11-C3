# Proyecto de Clasificación de Litofacies y Electrofacies mediante Machine Learning 🛢️📊

Repositorio  del **Grupo 11** para el desarrollo del proyecto de predicción y análisis de facies utilizando registros de pozos. Este proyecto integra enfoques tanto de **aprendizaje supervisado** como de **aprendizaje no supervisado** para caracterizar la columna estratigráfica y optimizar la zonificación de reservorios.


---

## 📂 Estructura del Repositorio

El repositorio se encuentra organizado de forma modular según las sucesivas etapas de avance del proyecto:
* `Pre-entrega 2/`: Exploración inicial de datos, limpieza y análisis exploratorio (EDA) de los registros de pozo.
* `Pre-entrega 3/`: Implementación y optimización de modelos de **aprendizaje supervisado** para la predicción de litofacies a partir de datos etiquetados.
* `Pre-entrega 4/` : Implementación de flujos de **aprendizaje no supervisado** (Ingeniería de características, PCA y K-Means) para la definición de electrofacies y validación estratigráfica.

---

## 🚀 Metodología y Flujo de Trabajo

## Origen del Dataset
El conjunto de datos utilizado proviene de registros de pozos estándar de la industria hidrocarburífera (empleando variables petrofísicas clásicas como Rayos Gamma, Densidad, Neutrón, etc.), facilitados en el marco del curso de Data Science de Fundación YPF.
'https://www.kaggle.com/code/imeintanis/log-facies-nn-bayesian-optimization-skopt'

### 1. Aprendizaje Supervisado (Pre-entregas 2 y 3)
* **Objetivo:** Predecir las litofacies originales definidas por descripción de testigos (coronas).
* **Proceso:** 
  * Limpieza y tratamiento de valores nulos en registros convencionales (Rayos Gamma, Resistividad, Densidad, Neutrón, Factor Fotoeléctrico, etc.).
  * Ingeniería de características orientada a capturar gradientes verticales y respuestas litológicas.
  * Entrenamiento y validación de modelos de clasificación supervisada para el reconocimiento de facies sedimentarias.

### 2. Aprendizaje No Supervisado y Zonificación (Pre-entrega 4)
* **Objetivo:** Agrupar los datos en *electrofacies* de manera ciega (sin requerir etiquetas previas) para evaluar la ciclicidad sedimentaria y la respuesta volumétrica de los registros.
* **Proceso:**
  * **Ingeniería de Características:** Generación de variables aumentadas (derivadas espaciales, estadísticas móviles y estandarización por formación) sobre 41 atributos originales.
  * **Reducción de Dimensionalidad (PCA):** Compresión del espacio multivariado reteniendo el **92.57% de la varianza total en 10 componentes principales**, separando eficazmente los controles litológicos principales (siliciclásticos vs. carbonáticos).
  * **Clustering (K-Means):** Optimización mediante el método del codo y el coeficiente de silueta, determinando una partición óptima en **$K = 5$ electrofacies**.
  * **Validación Estratigráfica:** Construcción de matrices de contingencia y perfiles de correlación vertical por pozo para contrastar las electrofacies estadísticas frente a las litofacies geológicas de referencia.

---

## 📊 Principales Conclusiones

1. **Eficiencia del PCA:** Las primeras componentes principales capturan con gran fidelidad el contraste físico de la cuenca entre intervalos arcillosos/siliciclásticos (altos valores de GR) y carbonatos limpios (altos valores de PE e ILD).
2. **Coherencia de K-Means ($K=5$):** 
   * *Clústeres 0 y 1:* Dominio siliciclástico (limolitas y areniscas).
   * *Clústeres 2 y 3:* Dominio carbonático (separando alta energía/carbonatos bioconstruidos de mudstones/wackestones y lutitas).
   * *Clúster 4:* Intervalos transicionales y dolomíticos de alta frecuencia.
3. **Complementariedad:** El enfoque no supervisado demuestra ser una herramienta robusta para la zonificación preliminar y la definición de unidades de flujo cuando no se dispone de núcleos de perforación, sirviendo como un excelente complemento a los modelos supervisados.

---

## 🛠️ Requisitos y Entorno de Ejecución

El proyecto está desarrollado en **Python** y requiere las siguientes librerías principales para la ejecución de los notebooks:
* `pandas`, `numpy` (Manipulación y análisis de datos)
* `scikit-learn` (Escalamiento, PCA y K-Means)
* `scipy` (Procesamiento numérico)
* `matplotlib`, `seaborn` (Visualización de datos y perfiles de pozo)

---

## 👥 Autores
* **Grupo 11** — Integrantes: Biaiñ Joaquin, Facenda Selena y Ferreyra iara.
