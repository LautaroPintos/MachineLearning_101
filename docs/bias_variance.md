### Bias-Variance trade-off (notes)


#### Introducción

Si resumiesemos el espectro de modelos de machine learning que existen podemos detecatar dos grandes grupos: Modelos de aprendizaje supervisado y modelos de aprendizaje no supervisado. La idea del primero grupo es que vamos a partir de una serie de datos etiquetados donde conocemos la respuesta correcta y queremos encontrar la forma de predecir dicha respuesta. En el segundo grupo, no vamos a contar con datos etiquetados (Ej: No vamos a tener un marca que nos diga si una operación es fraudulenta) sino que vamos a tratar de deducir patrones en los datos.

El trade-off entre sesgo y varianza cobra principal importancia en el primer grupo. Este concepto surge a partir de describir la relación entre la habilidad que tiene un modelo de aprender de los datos de entrenamiento y la capacidad de que tiene el modelo de generalización (entender nueva información). Es decir, es la relación entre la complejidad del modelo y su capacidad de generalización.


#### Sesgo y varianza

El **sesgo** es la diferencia entre el valor esperado (promedio) de la predicción de un modelo y el valor real. Es decir, el sesgo es la incapacidad del modelo de predecir las verdaderas relaciones de la data. Un modelo con "high-bias" seguramente sea muy simple y no capture la verdadera relación entre las variables, presentará mucho error en el dataset de entrenamiento y en el de testeo.

La **varianza** representa la sensibilidad de un modelo a pequeñas variaciones en los datos de entrenamiento. Su definición es exactamente igual a la de la varianza estadística (la suma de las distancias entre una variable y su media, todo al cuadrado) pero en este caso la variable aleatoria es la predicción del modelo. No obstante, no tenemos que confundir que este caso la varianza hace referencia a la diferencia en el ajuste de un modelo entre el dataset de entrenamiento y el de testeo. En otras palabras, un modelo con "high-variance" va a aprender muy bien de los datos de entrenamiento (overfitting, posiblemente la suma de los cuadrados sea cercana a 0) pero va a peder capacidad de generalización y no va aprender también de los datos de testeo.

Estos conceptos se asocian al **error cuadrático medio** de un modelo. El error cuadrático medio mide el promedio de la diferencia entre el estimador de una variable aleatoria y su valor real. Este concepto se puede descomponer como la suma de la varianza y el sesgo al cuadrado. Por esto es que el *mejor modelo es el que presente menor error cuadrático medio.*

En líneas generales, modelos con "low-bias" suelen presentar "high-variance" y modelos con "high-bias" suelen presentar "low-variance"


#### Punto óptimo entre sesgo y varianza

Para encontrar el punto óptimo entre sesgo y varianza existen varias ténicas pero en particular podemos ver: Cross-validation y regularization.

**Cross-validation** es una técnica que nos permite evaluar el modelo sobre distintas particiones de la data. De esta forma, podemos elegir de manera más óptima los distintos hiperparámetros del modelo que minimicen el error cuadrático medio

**Regularization** es una técnica que añade un término de penalización a la función de costo del modelo para evitar que el mismo se vuelva muy complejo


#### ¿Cómo esto se ve en al realidad?

| Ejemplo   | High V - Low B| High B - Low V | High V - High B| Low V - Low B|
|-----------|---------| ---------| ---------| ---------|
| ECM train | 1%      |15%     | 15%     | 1%     |
| ECM test  | 15%     |16%     | 35%     | 1.5%     |


