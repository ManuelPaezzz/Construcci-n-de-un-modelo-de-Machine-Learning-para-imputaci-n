# Imputación de Datos Hidrometeorológicos con Machine Learning

Este proyecto aborda un problema clásico y crítico en la ciencia de datos ambientales: la pérdida de información en sensores meteorológicos debido a fallas técnicas, falta de mantenimiento o cortes de energía. 

Utilizando datos históricos diarios de la estación 25015 de CONAGUA (Sinaloa), este repositorio implementa un modelo de **Machine Learning** orientado a la imputación de valores faltantes para cuatro variables climáticas clave: Precipitación, Evaporación, Temperatura Máxima y Temperatura Mínima.

##  Objetivo
Construir datos sintéticos precisos que preserven la distribución original, varianza y estacionalidad de las series de tiempo, evitando los sesgos que introducen las técnicas clásicas de rellenado (como promedios simples o interpolación lineal).

## Metodología

El núcleo del proyecto utiliza **Random Forest Regressor** debido a su capacidad para:
* Manejar relaciones altamente no lineales entre variables climáticas.
* Operar sin supuestos estrictos de distribución normal (ideal para los datos de precipitación).
* Ser robusto ante valores atípicos.

### Feature Engineering Destacado
Para lograr que el modelo comprenda la continuidad del tiempo (estacionalidad), se implementó una **codificación cíclica temporal**. Se utilizaron transformaciones trigonométricas (seno y coseno) sobre el día del año y el mes, permitiendo al algoritmo entender que el 31 de diciembre y el 1 de enero son fechas climáticamente contiguas.

## Validación y Métricas
El modelo fue evaluado introduciendo vacíos artificiales en un subconjunto de datos limpios, logrando excelentes resultados validados mediante:
* **R² (Coeficiente de Determinación):** Excelente captura de variabilidad, especialmente en variables térmicas.
* **RMSE (Raíz del Error Cuadrático Medio):** Mantenimiento de un margen de error bajo en las mismas unidades de medición (°C y mm).
* **MAE (Error Absoluto Medio)** y **MSE**.

## Tecnologías y Librerías Utilizadas
* **Lenguaje:** Python
* **Manipulación de Datos:** Pandas, NumPy
* **Machine Learning:** Scikit-learn
* **Visualización:** Matplotlib, Seaborn
* **Entorno:** Jupyter Notebook
