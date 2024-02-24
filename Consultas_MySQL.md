[Promedio.csv](https://github.com/andiisantoss/QueryCompetition/files/14392460/Promedio.csv)[Promedio.csv](https://github.com/andiisantoss/QueryCompetition/files/14392456/Promedio.csv)[Promedio.csv](https://github.com/andiisantoss/QueryCompetition/files/14392455/Promedio.csv)CONSULTAS EN MYSQL WORKBENCH 🔎

El archivo que anteriormente se exporta desde el MongoDB, con el filtro aplicado para agrupar,
ayuda bastante a simplificar los datos y tratarlos con más facilidad en MySQL. 
Para comenzar a realizar las consultas entonces se importa dicho archivo.

Una vez importado se comienza con el código. Por cuestiones de orden se le aplica un comando
a la tabla para ordenar los datos alfabéticamente a partir del campo "Región". 


USE covid19;

DESCRIBE contagios;


SELECT *

FROM contagios

WHERE Max_C ORDER BY Region asc;

![12](https://github.com/andiisantoss/QueryCompetition/assets/147234584/78a2677d-f085-4b12-abf1-4ce89c7a9381)

6.- Se requiere saber la cantidad de Regiones que están consideradas en la base de datos, 
y para ello se debe consultar con el siguiente código:

SELECT COUNT(Region) AS Muestra

FROM contagios;

El resultado se almacena en el campo Muestra.

![13](https://github.com/andiisantoss/QueryCompetition/assets/147234584/f7cf45ac-dd8b-4d7a-977a-831dbf9579f4)


7.- Para saber el número total de contagios, es necesario contar todo el campo "Confirmed"
Se hace mediante el siguiente código y se almacena en el campo Totcont:

SELECT SUM(Max_C) AS Totcont

FROM contagios;

![14](https://github.com/andiisantoss/QueryCompetition/assets/147234584/c845de37-91e9-48df-9dea-486c3438959c)


8.- Se conoce el promedio de contagios, utilizando la fórmula básica del promedio y los dos 
datos extraídos anteriormente. El código es el siguiente y se almacena en el campo "Promcont":

SELECT SUM(Max_C)/ COUNT(Region) AS PromCont

FROM contagios;

![15](https://github.com/andiisantoss/QueryCompetition/assets/147234584/37d58895-5eba-47ff-9608-b8c7ccc2600a)


9,10.- Por último es requerido obtener el porcentaje de muertes y recuperaciones con respecto
a los contagios que hubo. Para ello se sigue el siguiente código, que para ambas cuestiones 
es muy similar:

SELECT SUM(Max_M) AS Totmuertes

FROM contagios;

SELECT SUM(Max_R) AS Totrec

FROM contagios;

SELECT (100*SUM(Max_M)/(SUM(Max_C))) AS PorcM

FROM contagios;

SELECT (100*SUM(Max_R)/(SUM(Max_C))) AS PorcR

FROM contagios;

![16](https://github.com/andiisantoss/QueryCompetition/assets/147234584/f8f04080-4eb0-4126-b2ae-e16ed99e18aa)

![17](https://github.com/andiisantoss/QueryCompetition/assets/147234584/2fbdb255-e832-4881-9f48-ebbd4c5b7206)


De esta manera se terminan de resolver las preguntas planteadas en un inicio. 
En el apartado siguiente se pueden observar los archivos derivados de las 
consultas usadas en MySQL.

[TablaOrdenada.csv](https://github.com/andiisantoss/QueryCompetition/files/14392451/TablaOrdenada.csv)

[TotalContagios.csv](https://github.com/andiisantoss/QueryCompetition/files/14392453/TotalContagios.csv)

[TotalRegiones.csv](https://github.com/andiisantoss/QueryCompetition/files/14392454/TotalRegiones.csv)

[Promedio.csv](https://github.com/andiisantoss/QueryCompetition/files/14392461/Promedio.csv)

