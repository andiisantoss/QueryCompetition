LIMPIEZA DE DATOS 🩹

El archivo inicial de COVID 19 contiene una base con datos difíciles de trabajar, con falta de coherencia, con espacios de más,
datos faltantes, y esto complica el posterior análisis si se pretende exportar a otra plataforma donde se pueda consultar información.

Para poder evitar fallas debido a la corrupción en los datos, es necesario limpiar la base, para lo cual se usa Excel, ya que su 
interfaz es relativamente fácil de utilizar y tiene fórmulas muy prácticas que pueden ser de ayuda para el propósito de la limpieza.

En primer lugar se observa que existen caracteres irreconocibles para el mismo Excel, el más frecuente es el que se muestra en la imagen.
Para poder eliminarlo se usa la herramienta "buscar y reemplazar" y se reemplaza por un espacio normal.

![1](https://github.com/andiisantoss/QueryCompetition/assets/147234584/5801caaf-9eb4-4785-bdf8-6a396149ebe5)

Luego de reemplazar los caracteres no reconocidos, se filtran las columnas para detectar registros vacíos en todos los campos, a 
la vez se puede identificar cuáles son los campos que ya están listos y no requieren mayor limpieza.

![2](https://github.com/andiisantoss/QueryCompetition/assets/147234584/57525cc6-0229-43c0-9b8c-5eb624ced658)

En el campo de “Province” se puede detectar que hay algunas separaciones por comas que pudieran ser perjudiciales para el correcto 
trabajo de los datos, así que se deben eliminar esas partes.

Esto se hace mediante la herramienta de “Texto en columnas”.

Se configura la división utilizando las “comas” como separadores, de esta forma quedan los nombres largos de las provincias en diferentes
columnas, y dado que la información después de la coma se considera irrelevante para el caso de estudio, se eliminan las columnas
secundarias. 

![3](https://github.com/andiisantoss/QueryCompetition/assets/147234584/33c65900-d3bd-4572-9344-817427ccfd77)


![4](https://github.com/andiisantoss/QueryCompetition/assets/147234584/8eb0eba3-1a77-45f7-9d76-818d03748025)


En la figura se observa un ejemplo de las columnas divididas, donde se conserva la columna de la izquierda y se elimina la de la derecha.

![5](https://github.com/andiisantoss/QueryCompetition/assets/147234584/17995156-4cd0-4ae9-a0cd-f61e49b9106f)


Se toma una columna extra para poder proceder con la limpieza, esta vez se eliminan espacios innecesarios mediante la fórmula “Espacios”,
y se corre dicha fórmula hacia abajo para poder realizar el mismo proceso a todos los registros del campo requerido.

Nuevamente utilizando filtros, se pueden observar inconsistencias en los campos de latitud y longitud. 
Para el objetivo de este ejercicio la longitud y latitud son sumamente importantes, así que es necesario indagar en la limpieza de los
mismos. Se notan registros vacíos y esto no debe de ocurrir.

![6](https://github.com/andiisantoss/QueryCompetition/assets/147234584/414f7622-42e3-4dc3-8874-2f7d76980903)


Se filtran los datos a partir del campo “Region” para poder identificar de manera más clara cuales son los registros vacíos que existen
en la parte de Latitud y Longitud. Una vez identificado este dato, se rellenan los registros faltantes ubicando su latitud y 
longitud correspondiente, basada en otros datos encontrados en la misma base.

![7](https://github.com/andiisantoss/QueryCompetition/assets/147234584/1531d876-b5eb-4a15-9639-b78391aa4298)


Como último paso en el procedimiento de limpieza, se revisa el campo de Fecha, donde se notan inconsistencias con respecto al orden del 
formato de fecha. Algunos datos están ordenados en el formato (DD/MM/AAAA) y otros en el formato (MM/DD/AAAA), y se requiere la homologación.

![8](https://github.com/andiisantoss/QueryCompetition/assets/147234584/1c9e66a5-3e78-4f40-a72f-0489657bc8ed)


Para realizar la limpieza, filtramos los registros erróneos que se ven en la lista (los que tienen denotada la hora). 
Nuevamente se utiliza la herramienta “Texto en columnas” para separar los días, meses y años. Se utiliza posteriormente la 
fórmula “Fecha” para reacomodar el orden en: DD/MM/AAAA y se copia esa columna en valores sobre la columna anterior para poder 
unificarla al mismo campo.
Una vez realizado este procedimiento de limpieza, se puede notar que existe ahora una base de datos lista para trabajarse en 
cualquiera de las dos plataformas, MySQL o Mongo DB.

El archivo después de la limpieza se observa de la siguiente manera:

![25](https://github.com/andiisantoss/QueryCompetition/assets/147234584/79198bd6-a10d-490b-965e-95c008dd25d0)

Archivo:

[covid_limpia_buena.xlsx](https://github.com/andiisantoss/QueryCompetition/files/14392272/covid_limpia_buena.xlsx)




