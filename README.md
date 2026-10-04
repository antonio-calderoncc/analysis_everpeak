# 📊 Análisis de Comportamiento de Clientes - ConnectaTel

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es realizar un análisis exploratorio y un diagnóstico de calidad sobre el ecosistema de datos de **ConnectaTel**, una empresa de telecomunicaciones en Latinoamérica. A través de la limpieza de datos, la ingeniería de características y la segmentación demográfica y transaccional, el proyecto busca identificar patrones de consumo reales, aislar comportamientos atípicos (outliers) con potencial riesgo de fraude o reventa, y traducir estos hallazgos estadísticos en conclusiones ejecutivas accionables que optimicen la oferta de planes comerciales y aumenten la retención de clientes.

---

## 💾 Datasets Utilizados
El análisis se basa en tres conjuntos de datos con información registrada hasta el año 2024:
*   **`plans.csv`**: Información técnica y comercial de los planes actuales (precio base mensual, minutos y mensajes incluidos, y costos por consumos excedentes).
*   **`users_latam.csv`**: Datos demográficos y contractuales de la base de usuarios (ID de cliente, nombre, edad, ciudad, fecha de registro, tipo de plan contratado y estado de cancelación/churn).
*   **`usage.csv`**: Registro detallado y transaccional del uso real de los servicios (identificador único, tipo de consumo—llamada o SMS—, fecha, duración en minutos y longitud en caracteres).

---

## 🛠️ Etapas del Análisis Realizadas

1.  **Carga y Exploración Inicial:** Validación de la carga en memoria de los tres datasets, inspección de sus estructuras generales (`.shape`), tipos de datos primarios (`.info()`) y primeras filas.
2.  **Diagnóstico de Calidad de Datos:** Identificación cuantitativa de valores faltantes y detección de anomalías lógicas, errores de captura o valores *sentinel* (numéricos y de texto).
3.  **Limpieza Básica de Datos:** 
    *   Tratamiento del sentinel de edad (`-999`) mediante imputación con la mediana de la población (48 años).
    *   Estandarización y corrección de la variable geográfica (`city`) removiendo caracteres inválidos (`"?"`).
    *   Corrección temporal mediante la asignación de valores nulos (`NA`) con `.loc` para fechas imposibles o futuras (año 2026) en la columna `reg_date`.
4.  **Estadística Descriptiva y Agrupación:** Construcción de una tabla agregada por usuario para calcular métricas de consumo histórico (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`).
5.  **Análisis de Distribuciones e Identificación de Outliers:** Evaluación visual (histogramas y boxplots) y matemática (método del Rango Intercuartílico - IQR) para definir umbrales de consumo normal y aislar comportamientos extremos.
6.  **Segmentación Estratégica:** Creación de variables de negocio basadas en perfiles demográficos (`grupo_edad`) y niveles de actividad transaccional (`grupo_uso`).
7.  **Generación de Insights y Recomendaciones:** Traducción de hallazgos estadísticos en una presentación ejecutiva orientada a la toma de decisiones de negocio.

---


## 🚀 Cómo abrir el notebook en Google Colab

Haz clic en el siguiente botón para ejecutar el análisis de forma interactiva:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://google.com)

O:

1. Abre el archivo `everpeak_analysis.ipynb` aquí en GitHub.
2. Haz clic en el botón **Open in Colab** que aparece en la parte superior del archivo.

## 📘 Cómo reproducir el análisis

1. Abre el archivo `everpeak_analysis.ipynb` en tu entorno local o en la nube.
2. Ejecuta las celdas en orden secuencial (`Shift + Enter`).
3. El notebook cargará automáticamente los datasets desde la ruta correspondiente del repositorio para asegurar la consistencia de los resultados.
