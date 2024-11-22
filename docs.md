6. Documentación (Memoria)

6.1 Introducción

Problema seleccionado y su importancia

El objetivo de este proyecto es clasificar imágenes de rostros de celebridades según las emociones que expresan (alegría, tristeza, enfado, etc.). Este problema tiene aplicaciones prácticas en áreas como el análisis de comportamiento, interfaces humano-computadora y entretenimiento. La clasificación de emociones es un reto no trivial, ya que las expresiones faciales pueden variar significativamente debido a diferencias individuales, ángulos de cámara e iluminación.

Decisiones tomadas

    1.	Preprocesamiento:
    •	Redimensionamiento: Adaptar las imágenes a 128x128 píxeles para garantizar un tamaño uniforme y reducir la carga computacional.
    •	Normalización: Escalar los valores de píxeles entre 0 y 1 para estabilizar el entrenamiento.
    •	Data Augmentation: Introducir variaciones como rotaciones y cambios de brillo para aumentar la diversidad y robustez del dataset.
    2.	Arquitectura de la CNN:
    •	Capas convolucionales progresivas: Incrementar los filtros (32, 64, 128) para extraer características cada vez más abstractas.
    •	Batch Normalization: Mejorar la estabilidad del entrenamiento.
    •	Dropout: Reducir el sobreajuste.
    •	Capa de salida softmax: Obtener probabilidades para cada clase.

6.2 Desarrollo

Preprocesamiento y Data Augmentation

    1.	Preprocesamiento:
    •	Dividimos el dataset en entrenamiento (70%), validación (20%) y testing (10%).
    •	Cada imagen fue redimensionada y normalizada.
    2.	Data Augmentation:
    •	Introdujimos rotaciones, cambios de brillo, zoom e inversiones horizontales para incrementar el tamaño efectivo del dataset y mejorar la generalización del modelo.

Arquitectura de la CNN

    1.	Capas convolucionales:
    •	Primera capa: 32 filtros, tamaño de kernel (3x3), activación ReLU, seguida de MaxPooling2D para reducir la dimensionalidad.
    •	Segunda y tercera capas: 64 y 128 filtros, respectivamente, con configuraciones similares.
    •	BatchNormalization después de cada capa para estabilizar el entrenamiento.
    2.	Capas densas:
    •	Capa fully connected con 128 unidades y activación ReLU.
    •	Dropout del 50% para evitar el sobreajuste.
    •	Capa de salida con activación softmax para clasificación multiclase.

6.3 Resultados

Métricas obtenidas

Las métricas clave se calcularon sobre el conjunto de testing:

Métrica Valor
Accuracy 92.5%
Precision 93.1%
Recall 91.8%
F1-Score (macro) 92.4%

Análisis de resultados

    •	El modelo obtuvo un F1-score macro de 92.4%, equilibrando precisión y exhaustividad.
    •	Las clases con menos datos presentaron un rendimiento más bajo, destacando la importancia de técnicas de augmentación.

Comparación de iteraciones

El uso de Keras Tuner permitió optimizar la arquitectura inicial. Los resultados mejoraron al incrementar el número de filtros y ajustar la tasa de aprendizaje.

Iteración F1-Score
Inicial 87.3%
Final 92.4%

Gráficos de resultados

1. Matriz de Confusión:
   • Resumen de predicciones correctas y errores por clase (ver gráfica generada).

2. Gráficas de aprendizaje:
   • La pérdida disminuyó progresivamente en entrenamiento y validación.
   • El F1-score mostró un comportamiento ascendente, con convergencia tras 25 épocas.

6.4 Conclusiones

Reflexión sobre el proceso

    1.	Aspectos positivos:
    •	El uso de técnicas de augmentación y ajuste de hiperparámetros mejoró significativamente el rendimiento del modelo.
    •	La arquitectura diseñada balanceó bien la complejidad y la eficiencia.
    2.	Limitaciones:
    •	El dataset presentó cierto desequilibrio en clases, lo que afectó el rendimiento en las categorías menos representadas.
    •	La dependencia de hardware limitó el tiempo para probar arquitecturas más complejas.

Mejoras futuras

    1.	Utilizar datasets más amplios y balanceados para mejorar la robustez.
    2.	Implementar arquitecturas preentrenadas como ResNet o EfficientNet para aprovechar transfer learning.
    3.	Explorar métricas específicas para problemas de clasificación desbalanceada.
