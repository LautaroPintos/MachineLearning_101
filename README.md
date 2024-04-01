## Python fundamentals for Machine Learning

El objetivo del repositorio es que sirva como guía de las principales cuestiones que tenemos que tener en cuenta al momento de comenzar un modelado de datos (data analysis) o al momento de querer realizar un modelo de machine learning.

En la sección [notebooks](https://github.com/LautaroPintos/MachineLearning_101/tree/main/notebooks) se podrán encontrar distintos códigos con conceptos esenciales para el análisis de datos previo a la construcción de modelos de machine learning, como también, la aplicación de distintos modelos de machine learning.

En la sección [docs](https://github.com/LautaroPintos/MachineLearning_101/tree/main/docs) se podrán encontrar notas sobre conceptos fundamentales a tener en cuenta a la hora de la construcción de un modelo de machine learning.

En la sección [data](https://github.com/LautaroPintos/MachineLearning_101/tree/main/data) se podrán encontrar las distintas fuentas con las cuales se contruyeron las notebooks.

#### Primeros pasos

Lo primero que tenemos que hacer es configurar el ambiente para que podamos trabajar como lo haría un analista de datos. Para esto ya vamos a tener que tener instalado Python y un IDE (de preferencia VScode)

```python
sudo apt install python3-pip
sudo apt install python3-virtualenv
```
*Nota: En windows se debería hacer instalado la versión de pip sin problemas y solo debería instalar virtualenv con un pip install.

Luego nos paramos en el directorio donde vamos a trabajar y creamos el ambiente donde vamos a instalar todas las librerías. En este caso el ambiente se va a llamar env:
```python
virtualenv env
```

Una vez creado el ambiente lo que hacemos es activarlo para luego instalar las librerías necesarias para realizar el análisis
```bash
source env/bin/activate
```

Una vez activo el ambiente vamos a instalar las librerías necesarias para realizar los análisis. Para esto vamos a trabajar con el requirement.txt que dejo en este repositorio:
```python
pip install -r requirements.txt
```

Para abrir el entorno de jupyter para trabajar con las notebooks del repositorio o en caso de querer crear nuestras propios notebooks para otro tipo de análisis lo que vamos a hacer es escribir:
```python
jupyter lab --no-browser
```

Cuando querramos cerrar el ambiente lo que tenemos que escribir en la consola es:
```bash
deactivate
```


#### Créditos (citations)

* https://librovivodecienciadedatos.ai/


