#ML es el futuro

"""Actualmente generamos demasiados datos de informacion
Hasta 2005 los humanos hemos creado 130 ExaBytes de datos"""

"""una letra->byte
una pagina de aprox 1000 letras->kylobyte
un libro de 1000 paginas->megabyte"""

#El adn humano se podria codificar=>Gygabyte

#Grabar la vida de una persona(80 años)=>Therabyte

#2010=>se generaron 1200 Exabytes
#2015=>7900 Exabytes
#2020=>se preveen 40900 Exabytes

#Ir al navegador y descargar anaconda python

#-instalar anaconda
#-ejecutar anaconda navigator(esta en programas)
#-Se habran instalado varios ides
#-utilizaremos spyder
#-views->panes->iPython console
#-views->panes->variable explorer
#-views->panes->object inspector
#-views->panes->editor
#-views->panes->file explorer

#->tools->preferences->editor->cambiamos fuentes

#En el editor escribimos el codigo python y para ejecutar Ctrl+Enter


#INSTALAR R

"""ir a la pagina oficial de R
http://cran.r-project.org
luego elegir la instalacion para nuestro SO
ya que esto solo es el lenguaje de programacion
pero tenemos que descargar el ide(R studio)
http://www.rstudio.com"""


#Herramientas utiles para chatear con otras personas "Discord"

#PROPROCESADO DE CONJUNTOS DE DATOS

#Columnas variables
#filas observaciones

"""Determinar variables dependientes e independientes
Las variables dependientes son las que intentamos predecir a travez de machine learn inyectando las variables independientes."""

"""Importar Librerias
para importar las librerias es algo similar a java pero sin el punto y coma y podemos ponerle un alias con la palabra reservada as"""

# Cómo importar las librerías
#import <nombre_libreria> as <alias>
#La libreria numpy nos servira para el calculo numerico, la libreria matplotlib para los graficos y panda para la carga de datos	
import numpy as np
import matplotlib.pyplot as plt #En este caso utilizamos su sublibreria con el operador . en este caso solo utilizaremos su libreria para graficos
import pandas as pd 

PASAR ARGUMENTOS A UN SCRIPT DE PYTHON
from sys import argv

Como importar datos
Leer un csv

dataset = pd.read_csv('Data.csv')

obtener filas y columnas independientes
#La sintaxis para obtener filas y columnas de un dataset(puede tener cualquier nombre la var)
#es la siguiente name_var = nombre_data.iloc[inicio_fila:fin_fila,inicio_col:fin_col]
#Al no indicarle un rango de fila le estamos indicando que queremos todas
#Al solo indicarle el -1 le estamos diciendo que queremos todas las columnas menos la ultima
#iloc quiere decir indexlocation
#tanto filas como columnas comienzan desde cero
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, 3].values
#DATOS DESCONOCIDOS EN EL CSV O DATASET
NAN es la ausencia de valores en casillas y se pueden tomar distintos enfoques para remediar esa situacion 
1. uno de los enfoques es eliminar la fila completa de un valor desconocido
2. colocar la media de valores de esa columna en el valor desconocido

IMPORTAR LIBRERIA PARA PREPROCESADO 
Si solo queremos una sublibreria entonces se utiliza la siguiente sintaxis que utilizamos para el preprocesado de datos
#1 importamos una clase para preprocesar los datos es decir solventar el problema de los NAN

from sklearn.preprocessing import Imputer

#2 tomar un enfoque en nuestro caso indicarle al objeto imputer de la clase imputer que al encontrar valores perdidos(NAN) los remplace por la media
# y por ultimo indicar si remplazamos por la media de la fila o columna en este caso como es columna ponemos el valor 0 ya que 0 hace referencia a x 
# y 1 hace referencia a Y

imputer = Imputer(missing_values = "NaN", strategy = "mean", axis = 0)

#3 indicar a que columnas de esa tabla vamos a aplicar el imputer o estrategia
#en el siguiente ejemplo se lo aplicaremos a las columnas 1 y 2 pero en python el extremo superior superior del intervalo no es tomado por ello ponemos 3
# para que tome el 1,2 y sin embargo el tres por se extremo superior no lo tomara

imputer = imputer.fit(X[:, 1:3])

#Por ultimo el imputer ya tiene el ajuste o estrategia aplicada sin embargo la matriz  original X aun tiene los NAN por tanto tenemos que 
#sobreescribir los valores del imputer sobre la matriz  original es decir la X 
X[:, 1:3] = imputer.transform(X[:,1:3])

Por tanto el ejemplo anterior quedaria de la siguiente manera

import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

# Importar el data set
dataset = pd.read_csv('Data.csv')
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, 3].values

# Tratamiento de los NAs
from sklearn.preprocessing import Imputer
imputer = Imputer(missing_values = "NaN", strategy = "mean", axis = 0) 
imputer = imputer.fit(X[:, 1:3])
X[:, 1:3] = imputer.transform(X[:,1:3])

