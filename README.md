# Heart Disease Prediction - Kaggle

![image](https://github.com/user-attachments/assets/88041c4e-bd35-41e3-b71b-620187a9c93c)

Este repositorio presenta mi participación en la predicción de enfermedades cardíacas utilizando aprendizaje automático, en la [competencia de Kaggle "EC524: Heart-disease classification"](https://www.kaggle.com/competitions/ec524-heart-disease/data). El objetivo es predecir si un paciente tiene riesgo de sufrir una enfermedad cardíaca a partir de un conjunto de datos clínicos.

Ver Proyecto en este [enlace](https://colab.research.google.com/drive/1UHydEELy6iqEZIkrGGehctVWT2MyUNAU?usp=sharing). 

## Descripción del Proyecto

El proyecto utiliza un conjunto de datos con 14 características relacionadas con la salud del corazón, incluyendo información demográfica, resultados de pruebas médicas y factores de riesgo. La tarea es clasificar si un paciente tiene o no una enfermedad cardíaca (clasificación binaria).

La competencia se centra en construir un modelo de clasificación capaz de predecir si un paciente está en riesgo de sufrir una enfermedad cardíaca. Para esto, se utiliza **XGBoost**, un algoritmo de aprendizaje automático basado en la implementación de árboles de decisión con potenciación por gradiente.

## Metodología KDD

Este proyecto sigue la metodología **KDD (Knowledge Discovery in Databases)**, que consta de las siguientes etapas:

1. **Selección de Datos**: Selección de un subconjunto relevante de datos clínicos, como características demográficas, resultados de pruebas médicas y factores de riesgo.
2. **Preprocesamiento de Datos**: Limpieza y transformación de los datos, manejando valores faltantes, normalizando variables y convirtiendo las características en un formato adecuado para el modelo.
3. **Transformación de Datos**: Creación de nuevas características o transformación de las existentes para mejorar el rendimiento del modelo de predicción.
4. **Minería de Datos**: Aplicación de algoritmos de aprendizaje automático, como **XGBoost**, para entrenar el modelo y hacer predicciones basadas en los datos.
5. **Evaluación**: Evaluación del rendimiento del modelo utilizando métricas como la **precisión** para determinar su capacidad de generalización y evitar el sobreajuste.
6. **Presentación de Resultados**: Presentación de las predicciones y los resultados del modelo para facilitar la toma de decisiones.

## Conjunto de Datos

El conjunto de datos incluye las siguientes características clínicas:

- **age**: Edad del paciente
- **sex**: Género del paciente
- **chest_pain**: Tipo de dolor en el pecho
- **resting_bp**: Presión arterial en reposo
- **cholesterol**: Colesterol sérico en mg/dl
- **high_sugar**: Indicador de si el azúcar en sangre en ayunas es mayor a 120 mg/dl
- **ecg**: Resultados del electrocardiograma en reposo
- **max_rate**: Frecuencia cardíaca máxima alcanzada
- **exercise_angina**: Angina inducida por ejercicio
- **st_depression**: Depresión del segmento ST inducida por ejercicio
- **slope**: Pendiente del segmento ST del ejercicio máximo
- **vessels**: Número de vasos principales coloreados en la fluoroscopia
- **thalium_scan**: Escaneo cardíaco de talio

## Objetivo

El objetivo es predecir si un paciente tiene riesgo de sufrir una enfermedad cardíaca (0: No, 1: Sí).

## Tecnología Utilizada

- **Lenguaje**: Python
- **Librerías**: Pandas, Numpy, Seaborn, Scikit-learn, Matplotlib
- **Entorno de trabajo**: Google Colaboratory

## Resumen general

- En la primera etapa Selección de datos comenzó con la lectura del dataset, el cual tiene por nombre **train.csv**.
- Se determinaron la cantidad de registros, información por columna y los indicadores de las variables cuantitativas, destacando la presencia de nulos en las columnas **vessels** y **thalium_scan**
  
  ![image](https://github.com/user-attachments/assets/c4b85949-2101-4745-8a44-dc8483c37fe9)

- Se analizaron las variables que se consideraron relevantes en el dataset, a través de histogramas, gráficos de barras y pie charts.

![image](https://github.com/user-attachments/assets/184857cd-2eee-4db0-a791-a9b71685741e)

- En la segunda etapa Pre-Procesamiento se detectaron los valores nulos/incompletos y se usó el criterio de la Moda para la imputación de datos

![image](https://github.com/user-attachments/assets/7a72c32b-3c13-4d4f-a5e9-0581efcb6f45)

- Se detectaron y procesaron los outliers, los cuales se mostraron en las variables **resting_bp** y **cholestoral**. Se procedió a reemplazarlos con el percentil 95

![image](https://github.com/user-attachments/assets/28496630-198a-44b9-bfed-fbb9e925e401)

- Para el Feature Engineering, se identificaron tres variables categóricas que podrían simplificarse para una mejor interpretación y uso en modelos predictivos (vessels, thalium_scan y ecg). Básicamente, se crearon nuevas columnas para que estos campos se agrupen en valores binarios, donde 0 representa que no hay vasos afectados y resultados normales; mientras que 1 simboliza que hay al menos un vaso afectado y resultados con defecto/anormales.

  ![image](https://github.com/user-attachments/assets/29912685-1df0-49b6-a86d-a4c27e8457e4)

- Se continuó a verificar la influencia de cada variable respecto al target (heart_disease). Por ejemplo, en la siguiente imagen, se observa que a mayor número de vasos afectados, mayor fue la tendencia a padecer de una ataque cardiaco.

![image](https://github.com/user-attachments/assets/04c50aae-806b-4f42-8809-4802ee69d364)

- Cerrando la segunda etapa, se procedió a normalizar la data usando MinMaxScaler de la librería sklearn.preprocessing, ya que el objetivo era balancear columnas individuales al rango [0,1].

![image](https://github.com/user-attachments/assets/55eb7cb0-7072-4696-ab58-be208e11d8c7)

- En la tercera etapa Transformación de Datos se definieron las variables predictoras (x) y la variable objetivo (y), para llevar a cabo la partición de datos de entrenamiento. En este caso, se dividió la data en un 80-20, debido a que esta proporción asegura que se tenga suficiente para entrenar sin comprometer la evaluación.

![image](https://github.com/user-attachments/assets/582c184a-57ca-4476-bb40-80058215cc97)

- En la cuarta etapa de Minería de Datos, se entrenó el modelo de clasificación usando el algoritmo XGBoost, debido a su capacidad para manejar datos no lineales y su resistencia al sobreajuste.
  
- Es importante resaltar que se ajustaron los hiperparámetros acorde a las      características del dataset (tamaño, tipo de clasificación, etc), para        optimizar los resultados

![image](https://github.com/user-attachments/assets/99fbbb77-1abd-4538-9d6b-8362d8247690)

- En la quinta etapa de Evaluación se obtuvieron las métricas para determinar el rendimiento del modelo, como Accuracy, Precision, Recall y F1-Score. Como resultado, el modelo predijo correctamente en el 85% de los casos (Por ejemplo, de 100 registros, 85 se predijeron de forma acertada). En la sección de Resultados de este README puedes ver la matriz de confusión.

![image](https://github.com/user-attachments/assets/0c7581b2-95be-4991-955f-eabd5ee03eb8)

- En la última etapa, Presentación de Resultados, se optó por mostrar la Curva ROC para ilustrar gráficamente el rendimiento del modelo en términos de sensibilidad y especificidad.

- Además, se procesaron los datos contenidos en el archivo original **test.csv**, proporcionado por la competición de Kaggle. Dado que este archivo no contenía las columnas binarias creadas durante las etapas previas de preprocesamiento (como thalium_scan_binary y ecg_binary), fue necesario aplicar las mismas transformaciones utilizadas en el conjunto de entrenamiento. El resultado de este proceso fue un archivo llamado **test_preprocesado.csv**, que sirvió como base para aplicar el modelo Random Forest.

- Finalmente, al cargar las predicciones generadas por el modelo en la competición de Kaggle, se obtuvo un Score de 0.86792, demostrando un buen desempeño del modelo en el contexto del problema planteado.

![image](https://github.com/user-attachments/assets/cd5220ea-89c3-4471-8b10-9daedf7d1e2d)


## Resultados

![image](https://github.com/user-attachments/assets/1683d3d2-26ef-4d4d-8757-64e315b78df2)

Análisis de las métricas para el presente modelo:
- Accuracy: El modelo tiene una precisión global del 84.8%, prediciendo correctamente 39 de 46 casos para el conjunto de prueba.
- Precisión (Clase 0): El 84% de las predicciones de la clase 0 fueron correctas.
- Precisión (Clase 1): El 86% de las predicciones de la clase 1 fueron correctas.
- Recall (Clase 0): El modelo identificó correctamente el 88% de los casos reales de la clase 0.
- Recall (Clase 1): El modelo identificó correctamente el 82% de los casos reales de la clase 1.
- F1-Score: Para ambas clases, los valores son similares, lo que muestra que el modelo tiene un rendimiento consistente.

## Curva ROC

![image](https://github.com/user-attachments/assets/c7cba8bb-71c8-489a-a536-7559678abd67)

- La gráfica ROC muestra la capacidad de discriminación de nuestro modelo Random Forest.
- La curva azul representa la relación entre la Tasa de Verdaderos Positivos (True Positive Rate) y la Tasa de Falsos Positivos (False Positive Rate) en diferentes umbrales de decisión.
- El AUC (Área Bajo la Curva) de 0.88 indica que nuestro modelo tiene un buen rendimiento en la clasificación, distinguiendo correctamente entre clases positivas y negativas la mayor parte del tiempo.

## Envío

Mi archivo enviado es: **predicciones_xgb.csv**


