Ejercicio 1
Se deberá crear un repositorio y realizar una serie de operaciones desde 
la consola de
comandos sobre el mismo para posteriormente subir el repositorio a 
Github.
Se deberá entregar a través del formulario de prácticas indicando la URL 
del repositorio. En el
repositorio, deberá existir un archivo readme.md con las respuestas a 
las siguientes preguntas:
- ¿Qué comando utilizaste en el paso 11? ¿Por qué?
Utilizamos el comando git reset - - hard HEAD ~ 1,  porque queremos 
revertir.
Para deshacer el último commit tenemos varias opciones, utilizar el hash 
(id), el head~, tags…
En este caso usaremos el git reset head~1 (que irá hacía atrás 1 
posición), también necesitaremos el parámetro --hard para que nos 
eliminé los cambios realizado en el working copy.
- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
Primeramente un git reflog para ver todos los movimientos, escogeremos 
el id del movimiento que queremos deshacer y así volver a como estaba en 
aquél momento. Y una vez conocemos el id, el rehacer, se puede realizar 
de varias formas:
•	La primera, mirando el identificador del último commit: ejemplo 
git reset - - hard <id>
•	La segunda forma, con git reset - - hard HEAD@{1} 

Ambas formas, nos retornará al mismo punto donde nos encontrábamos en el 
apartado 10 (ya que nada ha cambiado) como si no hubiéramos pasado por 
los puntos 11 y 12. Aunque sí que lo hemos hecho, y eso se refleja en el 
reflog aunque no en la apariencia ya que no existe ninguna diferencia 
con el punto 10 (a excepción que hagamos un reflog que sí que guarda 
dichos movimientos).

Si ejecutamos ahora de nuevo un git status, podemos comprobar que no 
tenemos archivos en el staging área, y si ejecutamos el comando cat 
(para que nos muestre el contenido del archivo git-nuestro.md) vemos que 
se ha restaurado correctamente.
 
- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
Vamos a hacer primeramente un análisis la rama en la que estamos tiene 
que absorber a la que le indiquemos en el merge. Como en este caso, 
queremos desplazar master a la posición de styled. 
Hay que recalcar que en el grafo(también conocido como dibujo de 
jerarquía o estructura) es la rama hija siempre apunta al padre y no a 
la inversa aunque se común verlo al revés.
Si lo hiciéramos al revés, no podríamos absorber nada ya que ya tenemos 
las propiedades por lo tanto, se quedaría igual.

Debemos de desplazar la rama master a styled. Por tanto, lo primero de 
todo es situarnos en la rama master. Para ello, primeramente, debemos 
comprobar en que rama nos encontramos.
Desafortunadamente, no estamos en master. Como queremos que master 
absuelva a styled, vamos a cambiar la rama a master (en la que nos 
hagamos el checkout situarnos vamos será la que absuelva cuando 
realicemos el merge).
Revisamos que el cambio se ha hecho correctamente.
Una situado en la rama que queremos que absuelva, vamos a seleccionar la 
rama que va a ser absorbida (en este caso la master). Utilizando el 
comando git merge.
Si ahora hacemos un git log (en este caso de la rama master).
Ahora hacemos un git log (en este caso de la rama styled).

Realmente si os fijáis el resultado es el mismo. Es más, cuando haces un 
git log cualquiera, podemos ver que ya no nos muestra solo master o 
styled sino ambas (ya que están al mismo nivel jerárquicamente 
hablando). 
Si nos fijamos no ha habido conflicto alguno. Debido a que no hay 
problema en absorber una rama  con un grafo lineal.
 
- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
No, no causará conflicto debido a que estamos tratando de absorber una 
rama superior en styled.
- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?
No, no muestra error debido a que tratamos de absorber una rama 
superior.
Si por cualquier cosa tratamos de añadir una rama superior a una 
inferior, nos mostrará por pantalla "Already up-to-date" quiere decir 
que tu rama actual, ya contiene el trabajo de la rama master, por lo que 
no hay nada que absorber (nada de lo que hacer merge). Pero esto es un 
poco de culturilla, sería el merge inverso (comparado con el del 
ejercicio) realmente.
- ¿Qué comando o comandos utilizaste en el paso 25?
git log --graph aunque también se puede usar git log --oneline --graph 
–all
Porque necesitamos mostrar una gráfica de la estructura del grafo de 
nuestro directorio git y para realizarlo se utiliza el –graph.
- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
Sí, pero no se produciría el efecto que caracteriza a no fast forward y 
no se realizaría un commit donde podríamos escribir una descripción. En 
cambio, con fast foward, solamente desplazaríamos el puntero.
- ¿Qué comando o comandos utilizaste en el paso 27?
git reset --soft HEAD~1 
- - soft : con esta opción estamos indicando que retrocedemos a el commit 
HEAD~1 y no perdemos los cambios de los commits posteriores. Todos los 
cambios aparecerán como pendientes para realizar un commit.
- ¿Qué comando o comandos utilizaste en el paso 28?
Git checkout – git-nuestro.md
- ¿Qué comando o comandos utilizaste en el paso 29?
Si trato de eliminar una rama que no está completamente mergeada 
tendremos que usar git branch –D nombre ya que  hay parte de nuestro 
trabajo que no va a quedar en tierra de nadie (con tierra de nadie me 
refiero a fuera de las ramas) y como solo tendremos acceso desde git 
reflog para restaurarlo git nos muestra el error. Por lo que se podría 
decir que es un “error medio” y un “medio aviso”. Si yo intento eliminar 
una rama desde otra que ya ha absorbido su trabajo la puedo eliminar sin 
problemas sino git nos indica que podemos dejar trabajo sin rama y 
aunque se puede recuperar con reflog git nos advierte. Lo que pasa es 
que no podemos hacerlo desde otra rama superior cosa que nos obliga a 
realizar el git branch –D nombre obligatoriamente.
Por lo tanto git branch -D
- ¿Qué comando o comandos utilizaste en el paso 30?
git reset --hard 966b762
- ¿Qué comando o comandos usaste en el paso 32?
git reset --hard 56a8c73234816994c127f7168b0468bc7fa9d247
- ¿Qué comando o comandos usaste en el punto 33?
git reset --hard HEAD@{1}

