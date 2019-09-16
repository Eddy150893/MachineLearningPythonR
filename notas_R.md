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

Se crear un archivo de tipo R script

En R no es necesario importar las librerias y en la vista de packetes de R studio nos muestra las librerias que estan disponibles para utilizar directamente de hecho en la pestaña package existe un boton install para instalar mas libreriras.

Como importar datos
Leer datos de un csv

# Importar el dataset
dataset = read.csv('Data.csv')
En R es mucho mas sencillo pues no se tiene que indicar las filas independientes y las dependientes
#Los indices en R comienzan desde 1 en los dataset a diferencia de python que comienzan en 0
NOTA: para ejecutar los script de R se debe seleccionar toda la parte del script y luego pulsar
Ctrl+Enter

#DATOS DESCONOCIDOS EN EL CSV O DATASET
NAN es la ausencia de valores en casillas y se pueden tomar distintos enfoques para remediar esa situacion 
1. uno de los enfoques es eliminar la fila completa de un valor desconocido
2. colocar la media de valores de esa columna en el valor desconocido

#1. Para acceder a una columna en R de un dataset(variable a la cual se le asigno lo que se leyo de un csv)

dataset.$nombrecolumna
#2. Al escoger la estrategia de poner el promedio en los na entonces utilizamos un operador ternario donde:
ifelse(validacion,validacion=verdadero,validacion_falso)
Ejemplo
dataset$Age = ifelse(is.na(dataset$Age),
					 ave(dataset$Age, FUN = function(x) mean(x, na.rm = TRUE)),
					 dataset$Age)
#La columna Age perteneciente al dataset la igualamos a este operador ternario
#validacion: validamos si el campo es Nan(na) e ingresamos el campo a validar
#validacion=verdadero: Si es NAN entonces hacemos un promedio que recibe dos argumentos
ave(col_a_promediar,funcion que realiza el promerio)
#por tanto el promedio a hacer es de la columna dataset$age y la funcion que se le aplicara
#a ese promedio es que por cada x tomaremos la media(mean) de los valores que no sean nan 
#na.rm = TRUE
#validacion=false: si el valor de la columna no es nan pues esa casilla toma el mismo valor 
#que tenia desde el principio
#NOTA: este preprocesamiento solo se aplico a una columna por tanto por cada columna hay que 
#realizar el mismo proceso con su nombre de columna respectivo

toca el video 22