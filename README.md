## Comparación-de-Modelos-Supervisados-usando-CV
Por: Juan Guillermo Marulanda Mesa

## Descripción del Dataset
El dataset utilizado en este proyecto es el **Bitcoin Historical Data**, obtenido de Kaggle a través de `kagglehub`. Contiene datos históricos minuto a minuto del precio de Bitcoin (BTC/USD).
- **Muestra utilizada**: 100,000 registros iniciales.
- **Variable Objetivo**: Tendencia alcista (1 si el precio de cierre siguiente es mayor al actual, 0 en caso contrario).
- **Features**: Open, High, Low, Close y Volume.

## Objetivo del Trabajo
Diseñar y ejecutar un experimento de aprendizaje supervisado para comparar el rendimiento de modelos clásicos (Regresión Logística, Árbol de Decisión y KNN) utilizando **Validación Cruzada (K=5)** y la métrica **ROC AUC**. Se aplicó una partición de datos estratificada 60/20/20.

## Resultados Obtenidos

| Modelo | ROC AUC Train | ROC AUC Val | CV Mean AUC | CV Std AUC |
| :--- | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 0.5875 | 0.6191 | **0.5853** | 0.0371 |
| **Decision Tree** | 0.8464 | 0.5066 | 0.4434 | 0.0527 |
| **KNN** | 0.5982 | 0.5310 | 0.5264 | 0.0074 |

## Principales Hallazgos y Conclusiones

1.  **Detección de Sobreajuste**: El **Árbol de Decisión** presentó un sobreajuste significativo (Train: 0.84 vs CV: 0.44). Esto demuestra que, sin una poda adecuada o ajuste de hiperparámetros, los árboles tienden a memorizar el ruido de datos volátiles como los de criptoactivos.
2.  **Consistencia y Generalización**: La **Regresión Logística** demostró ser el modelo más robusto, manteniendo un rendimiento estable en todos los conjuntos (Train, Val y CV). Su cercanía entre el promedio de CV (0.5853) y el conjunto de validación (0.6191) confirma su capacidad de generalización.
3.  **Estabilidad del Modelo**: Aunque **KNN** fue el modelo con menor varianza entre folds (Std: 0.0074), su desempeño global fue inferior al de la Regresión Logística.
4.  **Desempeño Final**: El modelo seleccionado (Regresión Logística) fue evaluado en el conjunto de prueba (Test), obteniendo un **ROC AUC final de 0.5743**, validando los hallazgos de la fase de experimentación.

--- 
*Este trabajo fue desarrollado como parte del curso de Ciencia de Datos 2.*
