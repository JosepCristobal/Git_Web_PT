# Git_Web_PT

## Entrega de la práctica de Git del BootCamp Web X

### Ejercicio 1
Según nos piden en el enunciado de la práctica, se deberá crear un repositorio y realizar una serie de operaciones desde la cónsola de comandos sobre el mismo, para posteriormente subir el repositorio a gitHub.

+ En primer lugar creamos un repo en gitHub y lo sincronizamos con una carpeta creada en nuestro ordenador local para la realización de la práctica.
+ Los comandos utilizados son los siguientes:

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git clone https://github.com/JosepCristobal/Git_Web_PT.git

		Clonando en 'Git_Web_PT'...`


+ A continuación, en el punto 2 creamos un archivo git-web-pt.md con el contenido del anunciado y lo añadimos al staging area en el punto 3.

	código
	
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ nano git-web-pt.md
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git add git-web-pt.md 
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git status

+ En el punto 4 movemos lo que hay en el staging area al repository.

	`(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git commit -m "Creación del archivo git-web-pt.md (4)"`

+ (5) Creamos una rama llamada "styled" y (6) listamos todas las ramas.

	
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch styled
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch

+ (7) Nos movemos a la rama styled y (8) comprobamos que estamos en la rama correcta.


		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout styled
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch`


+ Verificamos que el asterico está en la rama style y a continuación (9) modificamos  el archivo git-web-pt.md según las especificaciones de la práctica.

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ nano git-web-pt.md

+ (10) Añadimos los cambios al staging area y luego los pasamos al repository.
 
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git add git-web-pt.md 
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git commit -m "modificación 1 del archivo en rama styled"

+ (11) **Deshacemos el último commit, perdiendo los cambios realizados en el working copy**
	+ ¿Que comando utilizaste en el paso 11? ¿Por qué?
		+ En este paso hemos aplicado un git reset --hard HEAD~1 para volver al commit anterior y --hard para que los cambios afecten al working copy.
		
		
				(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reset --hard HEAD~1
				HEAD está ahora en 5b13445 Creación del archivo git-web-pt.md (4)
		
+ (12) Rehacer el último commit (el que acabamos de deshacer).
	+ ¿Que comando o comandos utilizaste en el paso 12? ¿Por qué?
		+ En este caso hemos utilizado el comando reflog para buscar el identificador del commit anterior y hemos aplicado el comando git reset --hard af00bed para volver al estado anterior y que este también afecte al working copy.
		
		
				(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reflog
				4cfe44f (HEAD -> styled, main) HEAD@{0}: reset: moving to HEAD~1
				b21bd93 HEAD@{1}: commit: modificación 1 del archivo en rama styled
				4cfe44f (HEAD -> styled, main) HEAD@{2}: checkout: moving from main to styled
				4cfe44f (HEAD -> styled, main) HEAD@{3}: commit: Creación del archivo git-web-pt.md (4)
				343a470 (origin/main) HEAD@{4}: Branch: renamed refs/heads/master to refs/heads/main
				343a470 (origin/main) HEAD@{6}: commit (initial): first commit


				(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reset --hard af00bed
				HEAD está ahora en af00bed modificación 1 del archivo en rama styled 
		

+ (13) **Hacemos un merge con master (styled absorbe a master)**
	+ En este paso lo primero que hacemos es verificar que estamos en la rama "styled" para poder absorber a master y lo hacemos de la siguiente forma.
	

			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
			master
			*styled
	
+ El merge del paso 13, ¿Causó algún conflicto?¿Por qué? 
	+ En este merge no ha habido ningún conflicto debido a que las modificaciones del archivo han sido realizadas en la rama "style" respetando el texto original y añadiendo contenido nuevo.

			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git merge master
			Ya está actualizado.

+ (14) Volvemos a la rama master.

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout master
		Cambiado a rama 'master'
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
		* master
		styled

+ (15) Creamos una nueva rama llamada "htmlify".

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch htmlify
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
		htmlify		
		* master
		styled

+ (16) Cambiamos a la rama htmlify y (17) modificamos el archivo git-web-pt.md con el texto según el enunciado de la práctica.

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch htmlify
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
		htmlify		
		* master		
		styled	
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout htmlify
		Cambiado a rama 'htmlify'		
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ nano git-web-pt.md

+ (18) Una vez modificado el fichero, procedemos a hacer el "git add" y el "git commit".

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git commit -m "Modificamos en rama htmlify git-web-pt"

+ (19) **Hacer un merge de "htmlify" en "styled" (styled absorbe a htmlify).**
	+ El merge del paso 19, ¿Causó algún conflicto?¿Por qué?
		+ En este paso nos situamos en la rama "styled" ya que es la va a absorber a "htmlify".
	
				(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout styled
				Cambiado a rama 'styled'	
				(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
				htmlify		
				master		
				* styled			
				(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git merge htmlify		
				Auto-fusionando git-web-pt.md
				CONFLICTO (contenido): Conflicto de fusión en git-web-pt.mdFusión automática 				falló; arregle los conflictos y luego realice un commit con el resultado.

+ Al hacer el merge nos ha saltado un conflicto entre las dos versiones, el mismo fichero con dos versiones distintas y modificadas con sustitución de texto.

+ (20) Para solucionar el conflicto anterior, hemos editado el fichero con nano y hemos dejado el contenido que originalmente tenía el de la rama "styled" y borrado el resto. A continuación, hemos hecho un "git add" y un "git commit". Con ello, hemos dejado resuelto el conflicto.

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git add git-web-pt.md
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git commit -m "Merge con conflicto de 		styled - htmlify"	
		[styled 6b707cc] Merge con conflicto de styled - htmlify	

+ (21) **Desde "master", hacer un merge con "styled".**
 + Nos situamos en la rama master y hacemos el merge de styled.
 + El merge del paso 21, ¿Causó algún conflicto?¿Por qué? 
 		+ Al hacer el merge, no ha saltado ningún conflicto y se ha realizado un merge Fast-forward. El contenido de master estaba contenido en el segundo fichero sin alteración. El segundo fichero tenía valores añadidos, pero sin modificar los originales.
 		
 		
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git merge styled
		Actualizando 5b13445..6b707cc
		Fast-forward
		git-web-pt.md | 18 +++++++++---------
		1 file changed, 9 insertions(+), 9 deletions(-)
 	
 
+ (22) Creamos una rama "title" y cambiamos a esta rama y (23) añadimos un título al archivo git-web-pt y hacemos un commit.(24) Y volvemos a la rama master con "git checkout master" y verificamos que estamos en ella con "git branch".

+ (25) **A continuación dibujamos un diagrama con el siguiente comando.**

instrucción
	
	(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git log --graph --pretty=oneline
	*   6b707ccb44d4efcf44542cfefb828bf53d022c11 (HEAD -> master, title, styled) Merge con conflicto de 	styled - htmlify
	|\  
	| * 1e0321267f69e5b5d5aa4d19e18e18306080aace (htmlify) Modificamos en rama htmlify git-web-pt
	* | af00bedd239562a611cfd51db1469b6d06edec7b modificación 1 del archivo en rama styled
	|/  
	* 5b1344572382c06b1cdb5d56e1888ca8e2e00e97 Creación del archivo git-web-pt.md (4) en master

+ (26) **Hacemos un merge "no fast-forward" de "title" en "master (master absorbe a title)".**
	+ El merge del paso 26, ¿Podría ser fast forward?¿Por qué?
		+ Creo que si hubiera sido posible hacerlo como fast forward, por el motivo de el fichero solo ha sido modificado una vez en la rama title y master no ha sido modificado.
		
				(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git merge --no-ff title
				Ya está actualizado.
	
+ (27) **Desharemos el merge sin perder los cambios del working copy.**
	+ En este caso aplicaremos un git reset HEAD~1 para retroceder a un estado anterior.
	
	código
	
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reset HEAD~1
		Cambios fuera del área de stage tras el reset:
		M	git-web-pt.md
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git status
		En la rama master
		Cambios no rastreados para el commit:
  		(usa "git add <archivo>..." para actualizar lo que será confirmado)
  		(usa "git restore <archivo>..." para descartar los cambios en el directorio de trabajo)
		modificado:     git-web-pt.md

		sin cambios agregados al commit (usa "git add" y/o "git commit -a")
		
+ (28) **Descartamos los cambios.**

	+ Para descartar los cambios tenemos dos opciones, si disponemos de las últimas versiones de git.
	+ La que funciona en todas las versiones en con "git checkout git-web-pt.md" o bien "git restore git-web-pt.md".
	
	`(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git restore git-web-pt.md`
	
	+ Editamos nuestro fichero actual y vemos que ha desaparecido el título que habíamos añadido anteriormente en el merge de master y title.
	

+ (29) **A continuación eliminamos la rama "title"**
	+ En este caso ejecutaremos el comando git branch -D title. Previamente nos aseguraremos de que no estamos en la rama que vamos a eliminar.
	
	código
	
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch -D title
		Eliminada la rama title (era 6b707cc)..
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
 		 htmlify
		* master
  		styled
  		
  	+ Observamos que la rama title ha desaparecido.
 
+ (30) **Rehacer el merge que hemos deshecho, es la siguiente tarea.**
	+ El comando utilizado ha sido el git reset --hard bd91d8c para volver a "master absorbe a title"
	
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reset --hard bd91d8c
			HEAD está ahora en bd91d8c merge master absorbe title
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git status
			En la rama master
			nada para hacer commit, el árbol de trabajo está limpio
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
  			htmlify
			* master
  			styled

+ (31) Volvemos a master y eliminamos el resto de ramas.
	
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch -D htmlify
		Eliminada la rama htmlify (era 1e03212)..
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch -D styled
		Eliminada la rama styled (era 6b707cc)..
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git branch
		* master

+ (32) **Volvemos al commit inicial cuando se creó el poema.**
		el comando utilizado es el siguiente:
		
		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reset --hard 5b13445
		HEAD está ahora en 5b13445 Creación del archivo git-web-pt.md (4) en master

+ (33) **Volvemos al estado final, cuando pusimos el título al poema.**

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reset --hard bd91d8c
		HEAD está ahora en bd91d8c merge master absorbe title

+ (34) Creamos los siguientes tags:
	+ inicial: en el primer commit
	+ styled: modificación del paso 10
	+ htmlify: modificación del paso 17-18
	+ title: modificación del paso 30
	
	+ Para poder cambiar los tags, lo tenemos que hacer posicionando el head en cada rama y en su último commit.
	+ Nos vamos moviendo por nuestra estructura a través de los identificadores obtenidos con las diferentes consultas con el comando git reflog y git checkout <identificador>

			
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout af00bed
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git tag styled
			
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout 1e03212
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git tag htmlify
			
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout 6b707cc
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git tag title
			
			(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git tag
			htmlify
			inicial
			styled
			title


+ (35) Y por último, nos vamos al tag htmlify.

		(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git checkout htmlify

En el punto 33 hemos editado el fichero y este tenía un título mas el texto inicial,
al cambiar en el paso 35 al tag htmlify, al volver a editar el fichero git-web-pt.md, el texto ha cambiado y nos aparece tal y como lo modificamos originalmente en la rama htmlify.
Para sincronizar con nuestro repositorio y al estar en una rama desacoplada, pasamos a la rama master para subir el repo.
Lo subimos tal y como está ahora.

Adjunto el reflog final

	(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git reflog
	2bff46f (HEAD -> master, origin/master) HEAD@{0}: pull --allow-unrelated-histories origin master: Merge made by the 'recursive' strategy.
	bd91d8c HEAD@{1}: checkout: moving from 1e0321267f69e5b5d5aa4d19e18e18306080aace to master
	1e03212 (tag: htmlify) HEAD@{2}: checkout: moving from 6b707ccb44d4efcf44542cfefb828bf53d022c11 to htmlify
	6b707cc (tag: title) HEAD@{3}: checkout: moving from 1e0321267f69e5b5d5aa4d19e18e18306080aace to 6b707cc
	1e03212 (tag: htmlify) HEAD@{4}: checkout: moving from af00bedd239562a611cfd51db1469b6d06edec7b to 1e03212
	af00bed (tag: styled, styled) HEAD@{5}: checkout: moving from master to af00bed
	bd91d8c HEAD@{6}: reset: moving to bd91d8c
	5b13445 (tag: inicial) HEAD@{7}: reset: moving to 5b13445
	bd91d8c HEAD@{8}: reset: moving to bd91d8c
	6b707cc (tag: title) HEAD@{9}: reset: moving to HEAD~1
	bd91d8c HEAD@{10}: commit: merge master absorbe title
	6b707cc (tag: title) HEAD@{11}: checkout: moving from title to master
	6b707cc (tag: title) HEAD@{12}: checkout: moving from master to title
	6b707cc (tag: title) HEAD@{13}: merge styled: Fast-forward
	5b13445 (tag: inicial) HEAD@{14}: checkout: moving from styled to master
	6b707cc (tag: title) HEAD@{15}: commit (merge): Merge con conflicto de styled - htmlify
	af00bed (tag: styled, styled) HEAD@{16}: checkout: moving from htmlify to styled
	1e03212 (tag: htmlify) HEAD@{17}: commit: Modificamos en rama htmlify git-web-pt
	5b13445 (tag: inicial) HEAD@{18}: checkout: moving from master to htmlify
	5b13445 (tag: inicial) HEAD@{19}: checkout: moving from styled to master
	af00bed (tag: styled, styled) HEAD@{20}: reset: moving to af00bed
	5b13445 (tag: inicial) HEAD@{21}: reset: moving to HEAD~1
	af00bed (tag: styled, styled) HEAD@{22}: commit: modificación 1 del archivo en rama styled
	5b13445 (tag: inicial) HEAD@{23}: checkout: moving from master to styled
	5b13445 (tag: inicial) HEAD@{24}: commit (initial): Creación del archivo git-web-pt.md (4) en master
	
Al hacer la sincronización con gitHub se ha producido un error que al final lo he solucionado

	Desde https://github.com/JosepCristobal/Git_Web_PT
 	* branch            master     -> FETCH_HEAD
	fatal: rehusando fusionar historias no relacionadas


Lo he solucionado aplicando la siguiente instrucción

	(base) MacBook-Pro-de-Josep:Git_Web_PT jcm$ git pull --allow-unrelated-histories origin master
	

+ Adicionalmente a la práctica, he recuperado la rama styled y posteriormente la he renombrado a styled_new porque quería subir los tags creados y me daba un error de ambiguedad.

+ He subido al repo de gitHub la rama styled_new y un tag de styled.

Aqui doy por concluida la primera parte de mi práctica.

Muchas gracias por todo.
		












		


		
