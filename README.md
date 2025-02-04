# Clasificación de imágenes con Redes Neuronales Convolucionales

## Descripción del proyecto
Este proyecto aborda la clasificación de imágenes del conjunto de datos CIFAR-10, explorando diferentes arquitecturas de redes neuronales convolucionales (CNNs) y técnicas de regularización, data augmentation y ajuste del learning rate para mejorar la precisión en el reconocimiento de diez clases (animales y vehículos).

## Objetivos
- Comparar distintos modelos (básico, avanzado y superior) en términos de arquitectura, regularización y uso de data augmentation.
- Analizar el impacto de Batch Normalization, Dropout, regularización L2 y learning rate scheduler en la precisión y la generalización.
- Alcanzar la mayor accuracy posible, comprendiendo qué técnicas impulsan el desempeño y por qué.

## Flujo de trabajo
1. **Preparación de Datos:**
   - Cargar el dataset CIFAR-10.
   - Dividirlo en entrenamiento, validación y test.
   - Normalizar las imágenes.

2. **Entrenamiento de Modelos:**
   - Modelo A: Arquitectura CNN básica sin BatchNorm ni L2.
   - Modelo B: CNN con BatchNorm, L2 regularization, más capas/filtros.
   - Modelo C: Añade data augmentation, learning rate scheduling y ajuste de dropout.

3. **Evaluación**:
   - Monitoreo de loss y accuracy
   - Uso de EarlyStopping y ModelCheckpoint para guardar el mejor modelo
   - Obtención de métricas en validación y test

4. **Análisis de Resultados**:
   - Comparación de exactitud entre modelos.
   - Discusión sobre el efecto de cada técnica.

## Resultados
- Modelo básico alcanzó aproximadamente un 78% de precisión.
- Modelo avanzado mejoró hasta 82–83% gracias a BatchNorm y L2.
- Modelo superior, con data augmentation y scheduler, llegó a ~85–86%, mostrando la relevancia de aumentar y ajustar adecuadamente los datos.

| **Modelo**       | **Capas Conv** | **Dropout**    | **Epochs** | **Overfitting** | **Batch Norm** | **Regularización L2** | **Data Aug** | **Precisión en Test** | **F1-Score Macro** | **Mejores Clases**      | **Peores Clases**      |
|-------------------|----------------|----------------|------------|-----------------|----------------|------------------------|------------------------|-----------------------|--------------------|------------------------|-----------------------|
| **CNN básica**    | 3              | (0.3, 0.5)     | 50     | Ligero      | No             | No                     | No                     | **78.5%**             | 0.78               | Coche, Barco, Camión    | Gato, Ave, Perro      |
| **CNN avanzada**  | 4              | (0.25, 0.4)    | 85     | Leve        | Sí             | Sí                     | No                     | **82.8%**             | 0.82               | Coche, Barco, Camión    | Gato, Perro, Ave      |
| **CNN superior**  | 4              | (0.2, 0.3)     | 100   | Mínimo      | Sí             | Sí                     | Sí                     | **85.6%**             | 0.85               | Coche, Barco, Camión    | Gato, Perro, Ave      |

## Próximas mejoras
- Explorar arquitecturas más profundas (ResNet, VGG, etc) para lograr superar el 90% de exactitud.
- Ajustar aún más la intensidad de data augmentation o usar técnicas adicionales.
- Experimentar con otros optimizadores (SGD con momentum, RMSProp, etc) y diferentes planes de learning rate.
