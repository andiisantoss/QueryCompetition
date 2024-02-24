CONSULTAS EN MONGODB COMPASS (DESARROLLO 1/2) 🧿

Una vez teniendo el archivo de excel limpio, se debe importar en la plataforma de consultas, en este caso se usa 
MongoDB Compass para darle solución a la problemática inicial. Es importante comentar que el archivo de Excel 
debe exportarse con formato CSV, para que pueda ser admitido por Mongo.

En Mongo se debe crear una nueva base de datos, y dentro de una colección nueva importar el archivo. Ya que 
este paso está realizado se usa la herramienta "Agregaciones" creando una nueva "pipeline" para poder ir 
desglosando respuesta por respuesta.

1.- Para saber la fecha inicial de registro en la base de datos, es necesario ordenar la base de menor a mayor 
según el número de contagios confirmados, y esto se ejecuta creando un nuevo stage en el pipeline con el comando
$sort. El código de dicho stage es el siguiente:

{
  Confirmed: 1,
}

![9](https://github.com/andiisantoss/QueryCompetition/assets/147234584/cf0dd89c-1637-4ec4-a400-1770108551a9)


Para resolver las siguientes tres preguntas planteadas, es necesario agregar un nuevo stage utilizando la 
función $group para agrupar los documentos mediante la Region a la que pertenecen.También se deben crear
tres nuevos campos que indiquen la cantidad máxima de contagios en esa región (Max_C), la cantidad máxima
de muertes (Max_M) y la cantidad máxima de recuperaciones (Max_R). Esto se hace de la siguiente forma:
siguiente forma:

Group
{
  _id: "$Region",
  Max_C: {
    $max: "$Confirmed",
  },
  Max_M: {
    $max: "$Deaths",
  },
  Max_R: {
    $max: "$Recovered",
  },
}

![10](https://github.com/andiisantoss/QueryCompetition/assets/147234584/2bde2a27-e008-417e-a236-507a20ad48b6)

No es relevante obtener los datos mínimos, ya que por lógica se puede deducir que para todos los casos será 0.

2,3,4.- Las tres preguntas siguientes se contestan de forma similar, agregando dos nuevos stages para cada una.
Uno contiene la función $sort y el otro $limit. Con Sort se ordenan los datos de mayor a menor para los 3 casos
que se requieren, los contagios, las muertes y las recuperaciones. Y con limit se filtra a manera que solo
se proyecten los primeros 5 datos. El código se observa de la siguiente forma:

2.-
Sort
{
  Max_C: -1,
}
Limit
5

3.-
{
  Max_M: -1,
}
Limit
5

4.-
{
  Max_R: -1,
}
Limit
5

5.- La respuesta a esta pregunta se obtiene agregando un nuevo stage con el comando $match, aprovechando la 
agrupación anteriormente hecha en otro stage. A través del campo "_id" se va a buscar la región "México" 
para observar la cantidad de contagios existentes en ese país.

Match
{
  _id: "Mexico",
}

![11](https://github.com/andiisantoss/QueryCompetition/assets/147234584/876bdd24-cad4-435a-b3a7-650877211d74)


Se elige Mongo para las primeras 5 preguntas porque es más práctico a la hora de tratar consultas de este tipo.
Una vez llegando aquí es necesario exportar como csv el archivo que arroja a partir del stage 2 (después de
hacer la agrupación) para tratar esa información más adelante.


