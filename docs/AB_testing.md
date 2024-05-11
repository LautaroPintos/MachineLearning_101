### A/B testing (notes)

#### Introducción
El A/B testing es una técnica o metodología utilizada para comprar dos poblaciones y determinar cual de ellas tiene mejor desempeño en términos de algún parámetro o métrica que querramos medir.

El **primero paso** que tenemos que tener en cuenta es entender el problema y cual es la métrica que queremos mover aplicando las acciones correspondientes. El **segundo paso** es definir cual va a ser nuestro test de hipótesis en términos de hipotesis nula e hipotesis alternativa. El **tercer paso** es diseñar el experimento. En este parte es donde nosotros definimos los parámetros para construir los grupos dos grupos aleatorios (A y B). El **cuarto paso** es correr el experimiento. En esta etapa tenemos que estar muy seguros de como vamos a poder recopilar los resultados del experimiento para luego, en el **quinto paso** hacer validaciones sobre como se implemento el experimiento. Este paso es escencial para entender si hubo algún tipo de sesgo en la muestra que pueda invalidar los resultados. El **sexto paso** es el de interpretar los resultados y, por último, el **septimo paso** es el de tomar una decisión en función de los resultados.

Cuando estamos trabajando en áreas de marketing o de negocios, el punto 1 es sumamente crucial para entender correctamente que pregunta queremos responder y que indicador queremos mover. Una cosa sumamente importante que tenemos que hacer en áreas de growth u originación es entender el **recorrido del usuario** o la **experiencia del cliente** en nuestra aplicación. En esta etapa, entender en un gráfico de **funnel** el camino del cliente a lo largo del producto y/o aplicación es sumamente importante.

#### ¿Qué características tiene que tener la métrica que deseamos mover?

* Medible: El comportamiento del cliente tiene que poder trackearse a través de la data que tenemos disponible.
* Atribuible: Tenemos que poder linkear directamente (o facilmente) el comportamiento del cliente (efecto) con el experimiento en en acción (causa)
* Sensibilidad: La métrica tiene que tener poca variabilidad para así nosotros podemos distinguir entre los distintos grupos de análisis. Si la métrica que seleccionamos es muy volatil podemos tener diferencias hasta en el grupo de control.
* Iteratividad: Los experimientos tienen que desarrollarse rapidamente y mostrar resultados rapidamente dado que son procesos iterativos. Queremos que esta métrica pueda generar cambios en el corto plazo.

#### ¿Cómo definimos el test de hipótesis que queremos realizar?

En estos casos, lo usual es comparar las medias entre ambas muestras. Por ende, podemos tener que nuestra **hipótesis nula** puede ser que el **promedio de nuestra métrica entre el grupo de testeo y el de control son iguales** y nuestra hipótesis alternativa es que el promedio en ambos grupos son distintos.

En este momento también tenemos que definir el nivel de significancia (alpha) del modelo donde si el test de hipótesis nos arroja un valor menor a este podemos rechazar la hipótesis nula del modelo y avanzar por la hipótesis alternativa de que el experimiento tendría efecto. Hay que recordar que el estadístico alpha no habla de la probabilidad de tener error de tipo 1.

Otros parámetros a definir son: "statistical power" (la probabilidad de detectar un efecto dado que la hipótesis alternatva es cierta es iguala al ... 80%) y el "minimum detectable effect (MDE)" (Generalmente es una variación mínima en el indicador que estamos mirando...1%)

¿Cómo se interpreta el "statistical power?

Basicamente, el p-value de la distribución de la hipotesis nula (alpha) nos habla del **error de tipo 1** (los falsos positivos o la probabilidad de encontrar un **falso positivo**). Por ejemplo, en un modelo de score sería la probabilidad de encontrar una operación mala pero que el modelo califique como buena.

Por ende, el beta nos habla de la probabilidad de encontrar un **error tipo 2**. Esto quiere decir, la probabilidad de encontrar un **falso negativo** que por ejemplo en un modelo de score es una operación buena que el modelo clasifico como mala. Por ende, "1-beta" son todas las operaciones que estamos rechazando correctamente la hipotesis nula. A esto se lo conocemo como el **poder del estadístico**. En otras palabras el error de tipo 2 hace referencia a rechazar la hipótesis nula cuando la hipótesis alternativa es correcta (falso negativo).

Para encontrarlo, tenemos que saber conocer el valor crítico (dado alpha) de la distribución de la hipótesis nula y evaluarlo en la distribución alternativa. La región a la derecha de este valor es el poder del estadístico.

<img src ="/home/lautipintos/Documentos/MachineLearning_101/src/power_stat.png">



#### ¿Cómo definimos el experimiento?

Lo primero que hacemos es definir la unidad sobre la cual vamos a realizar la aleatoriedad. En este caso, lo más común es elegir aleatoriamente **clientes** dado que es la unidad que nos permitiría evaluar el comportamiento. Con esto, asignamos aleatoriamente a clientes entre el grupo A de testeo y el grupo b de control.

Una vez que hicimos esto tenemos que ver a que **target de usuarios** queremos aplicarle la política. Esto no es más que definir dentro del ciclo de vida del cliente en el producto en que etapa del funnel van a participar. Por ejemplo, queremos evaluar solamente a los clientes que "navegan por una determinada pantalla de la app". Esto es importante porque va a filtrar la cantidad de clientes que se van a randomizar entre los distintos grupos.

Luego determinamos el tamaño de la muestra. Para esto existen distintas metodologías que se pueden basar en estadísticos de la muestra. Además, tenemos que determinar cuanto va a durar nuestro experimiento (1 o 2 semanas.)

En este video encontramos un ejemplo práctico de como determinar el tamaño de la muestra:

* https://www.youtube.com/watch?v=KC1nwY7YCUE&t=28s


#### Inicializamos el experimiento

En este caso, lo más importante de todo es que mantengamos la estratégia inicial que adoptamos y la sigamos a lo largo de todo el experimiento hasta que el mismo termine.

Existen muchas variables que nos pueden llevar a tomar decisiones erroneas. Por ejemplo, el tamaño muestral que adoptamos puede ser lo suficientemente chico y si constantemente estamos observando el p-value podemos llegar a conclusiones erroneas por no dejar desarrollar el experimiento.

#### Chequeos de integridad de la información

En este caso tenemos que validar que el experimiento haya sido ejecutado sin ningún tipo de inconveniente. Para esto tenemos que revisar:

* Inconvenientes que hayamos tenido en la aplicación que pueden modificar la experiencia del usuario. Por ejemplo, fallas en la aplicación o también nuevas modificaciones a la misma que alteren el comportamiento del usuario.
* Factores externos como fines de semana largos, feriados, factores macroeconómicos, etc.
* Sesgos en la distribución de los grupos. La distribución entre ambos grupos tiene que ser homogenea antes y después del experimiento. Para esto se realizan AA test
* Realizar "sample ratio mismatch". Acá lo que tenemos que verificar es que ambos grupos tengan la misma cantidad de clientes que puede no ocurrir producto de fallas en los algorítmos de randomization. Para esto se realizan pruebas de hipótesis de Chi-cuadrado que evalua el ratio muestral.

#### Interpretación de resultados

En la interpretación de resultados será sumamente importante tener en cuenta un intervalo de confianza y estar alineados en mantener la estratégia de MDE. Podemos superar nuestro target de MDE en términos de variación relativa entre grupos pero posiblemente los intervalos de confianza no terminen de arrojar un resultado consistente producto del gran desvío que tiene el resultado.


