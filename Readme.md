
## **_PROYECTO INDIVIDUAL 01 - Machine Learning Operations (MLOps)_**

---

## INTRODUCCIÓN
Me llamo Alex Ezequiel Dalpiaz, este es el primer proyecto individual realizado durante el Bootcamp de Data Science de SoyHenry.  
El proyecto tiene como objetivo desarrollar un sistema de recomendación de películas mediante la aplicación de diversas técnicas de limpieza y transformación de datos. Estos procesos se llevan a cabo utilizando la biblioteca Pandas de Python, que nos permite realizar un análisis exploratorio de los datos, así como realizar tareas de extracción, transformación y carga (ETL). Una vez procesados los datos, se utiliza la biblioteca FastAPI para construir una API que permita realizar consultas y acceder a las recomendaciones de películas generadas por el sistema. Esta API puede ser consultada tanto de forma local como a través de medios remotos, proporcionando así una interfaz accesible para los usuarios.

## Objetivo

El objetivo de este proyecto es crear un sistema de recomendacion de peliculas y hacer un deploy utilizando FastAPI y Render.


## Links de Consignas y Explicación del Proyecto

|                  Descripción                  |                          Link                           | Plataforma |
| :-------------------------------------------: | :-----------------------------------------------------: | :--------: |
|    Consignas del proyecto de MLOPS    | [Repositorio](https://github.com/HX-PRomero/PI_ML_OPS/) |   Github   |
| Video explicativo del desarrollo del proyecto |                  [Video](link)                   |  YouTube   |

## ETAPAS DEL PROYECTO

---

### **1) Estudio de la fuente de datos y EDA (Exploratory Data Analysis)**

El proceso comienza realizando un análisis exploratorio de los datos presentes en el archivo "movies_dataset.csv". Se utiliza la biblioteca pandas para examinar los datos, identificar duplicados y revisar los tipos de datos y los valores faltantes. Se toman las acciones necesarias para manejar los valores faltantes y se extraen las primeras conclusiones para preparar los datos para su posterior ingestión en la base de datos. Todo este análisis se lleva a cabo en un entorno de Jupyter Notebook, proporcionando una interfaz interactiva y facilitando la visualización y comprensión de los datos.

### **2) ETL (Extract, Transform and Load)**

Algunos campos, como belongs_to_collection, production_companies y otros (ver diccionario de datos) están anidados, esto es o bien tienen un diccionario o una lista como valores en cada fila, ¡deberán desanidarlos para poder y unirlos al dataset de nuevo hacer alguna de las consultas de la API! O bien buscar la manera de acceder a esos datos sin desanidarlos.

Los valores nulos de los campos revenue, budget deben ser rellenados por el número 0.

Los valores nulos del campo release date deben eliminarse.

De haber fechas, deberán tener el formato AAAA-mm-dd, además deberán crear la columna release_year donde extraerán el año de la fecha de estreno.

Crear la columna con el retorno de inversión, llamada return con los campos revenue y budget, dividiendo estas dos últimas revenue / budget, cuando no hay datos disponibles para calcularlo, deberá tomar el valor 0.

Eliminar las columnas que no serán utilizadas, video,imdb_id,adult,original_title,vote_count,poster_path y homepage.


### **3) Creación de una API con FastAPI**

Se utiliza el framework FastAPI para la creación de dicha aplicación en el script `main.py`. En la etapa de desarrollo y prueba se realizaron las funciones necesarias para ejecutar las consultas y testeos de manera local. Las responses de la API.
Las funciones (Método `GET`) con las que cuenta la API son:

- **startup:** función de arranque donde la API pone a disposición la fuente de datos ya transformado para la aplicación de las consultas

- **index:** función de bienvenida con un HTML response

- **def peliculas_mes(mes)**: '''Se ingresa el mes y la funcion retorna la cantidad de peliculas que se estrenaron ese mes historicamente''' return {'mes':mes, 'cantidad':respuesta}

- **def peliculas_dia(dia)**: '''Se ingresa el dia y la funcion retorna la cantidad de peliculas que se estrebaron ese dia historicamente''' return {'dia':dia, 'cantidad':respuesta}

- **def franquicia(franquicia)**: '''Se ingresa la franquicia, retornando la cantidad de peliculas, ganancia total y promedio''' return {'franquicia':franquicia, 'cantidad':respuesta, 'ganancia_total':respuesta, 'ganancia_promedio':respuesta}

- **def peliculas_pais(pais)**: '''Ingresas el pais, retornando la cantidad de peliculas producidas en el mismo''' return {'pais':pais, 'cantidad':respuesta}

- **def productoras(productora)**: '''Ingresas la productora, retornando la ganancia total y la cantidad de peliculas que produjeron''' return {'productora':productora, 'ganancia_total':respuesta, 'cantidad':respuesta}

- **def retorno(pelicula)**: '''Ingresas la pelicula, retornando la inversion, la ganancia, el retorno y el año en el que se lanzo''' return {'pelicula':pelicula, 'inversion':respuesta, 'ganacia':respuesta,'retorno':respuesta, 'anio':respuesta}

- **def recomendacion('titulo')**: '''Ingresas un nombre de pelicula y te recomienda las similares en una lista de 5 valores''' return {'lista recomendada': respuesta}


### **4) Deploy del proyecto en Render**

Se utilizo render que permite realizar el deploy de un proyecto en la nube para que se pueda consumir en forma remota con el domain que entrega al crear el servicio.

[link de render](https://pimlops-xonb.onrender.com)



## STACK TECNOLÓGICO

---

- Jupyter notebook
- Python
- Pandas
- FastAPI
- sklearn
