# Predicción Automática de Litofacies en Pozos Petroleros 🛢️📊
Integrantes: Biaiñ Joaquin, Facenda Selena y Ferreyra iara

## 1. Origen del Dataset
El conjunto de datos utilizado proviene de registros de pozos estándar de la industria hidrocarburífera (empleando variables petrofísicas clásicas como Rayos Gamma, Densidad, Neutrón, etc.), facilitados en el marco del curso de Data Science de Fundación YPF.
'https://www.kaggle.com/code/imeintanis/log-facies-nn-bayesian-optimization-skopt' 

## 2. Resumen y Objetivo del Proyecto
El objetivo principal de este proyecto es desarrollar un modelo de Machine Learning supervisado capaz de automatizar la clasificación de litofacies en intervalos de pozos donde no se cuenta con testigos corona físicos. Esto permite optimizar la interpretación geológica y petrofísica del subsuelo de manera eficiente y precisa.

## 3. Hallazgos del Análisis Exploratorio (AED)
A través de la exploración de datos con Pandas y visualizaciones estadísticas, se identificó que las variables petrofísicas presentan correlaciones directas con las distintas litologías. Asimismo, se detectaron superposiciones en las respuestas de las herramientas para ciertas facies intermedias, lo que anticipó los desafíos que luego enfrentarían los modelos predictivos en dichas clases.

## 4. Modelos Ajustados y Resultados
* **Preprocesamiento:** Se implementó un pipeline robusto utilizando `ColumnTransformer` para escalar variables numéricas (`StandardScaler`) y codificar variables categóricas, evitando la fuga de datos (*data leakage*).
* **Modelo Baseline:** Se entrenó un clasificador basado en **Random Forest**, obteniendo un *Accuracy* inicial de **0.74**.
* **Optimización:** Se aplicó una búsqueda de hiperparámetros mediante `GridSearchCV` con validación cruzada (`cv=5`), determinando una configuración óptima de 200 árboles (`n_estimators: 200`).
* **Evaluación Visual:** Mediante una matriz de confusión normalizada, se comprobó que el modelo clasifica con alta precisión las facies extremas y que las confusiones remanentes se concentran entre litofacies de respuestas petrofísicas similares, respaldando la coherencia geológica de las predicciones.
