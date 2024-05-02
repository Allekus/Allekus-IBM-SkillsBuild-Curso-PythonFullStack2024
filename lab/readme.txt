_________________________________

Índice
------
Introducción 
Seguimiento de archivos 
Copia de respaldo 
_______

*Introducción
Para comenzar un proyecto con GIT, abriremos cualquier consola de comandos con la que trabajemos, 
nos situaremos en directorio de trabajo ej. 'test_git_github, es decir, el directorio en el que 
tenemos nuestro proyecto y desde allí, ejecutaremos el comando:

git init

Este comando sólo se ejecuta una vez, al principio de nuestro proyecto o cuando queremos que GIT
comience a hacer un seguimiento de nuestro proyecto. 
Introduciendo este comando por consola lo que conseguiremos es que GIT cree, de forma transparente 
al usuario, dos áreas donde irá almacenando los archivos. 
Estas dos áreas son:
- el área de ensayo (o staging area) y 
- el área de repositorio local.

El área de ensayo, como su propio nombre indica es un área donde se van a almacenar los archivos de 
forma temporal. Este paso es muy útil para que podamos ver qué archivos tienen seguimiento por 
parte de GIT, en qué estado se encuentran…etc.

En el área de repositorio local es donde se almacenan esas instantáneas que va haciendo GIT a 
nuestros archivos y es aquí desde donde las podremos rescatar cuando nosotros queramos.


*Seguimiento de archivos
El siguiente paso sería decirle a GIT que haga un seguimiento de todos los archivos de mi proyecto (o 
sólo de alguno en concreto).
Para hacer un seguimiento de todos los archivos existentes en el directorio del proyecto, usaremos el 
comando:

git add .

Para añadir solamente un archivo en concreto, añadiremos el nombre del archivo:

git add nombreDelArchivo

Con esto conseguimos que GIT lleve estos archivos desde el directorio de trabajo al área de ensayo y 
haga un seguimiento de los cambios que se produzcan. No es que los mueva físicamente, los archivos 
siguen estando en el directorio de trabajo, pero internamente GIT los trata como archivos listos 
para trabajar con ellos en el staging area.
A continuación, haremos un:

git commit

Con lo que nuestros archivos pasarán (de nuevo de forma transparente para nosotros) al área del 
repositorio local.

Es aquí donde GIT crea la instantánea del estado actual de nuestros archivos. Es decir, donde se crea 
el respaldo (la copia) de nuestro proyecto.


*Copia de respaldo
A partir de este momento, podemos obtener una copia de respaldo de cómo se encontraban esos archivos 
al momento de hacer dicho respaldo.

Veamos un ejemplo de lo dicho anteriormente:

Crearemos un directorio de trabajo para nuestro proyecto al que llamaremos por ejemplo “Proyecto 
GIT”.

Crearemos o copiaremos los archivos de nuestro proyecto. Para nuestro ejemplo hemos creado tres 
archivos, un .html, un .css y un .js 

Desde dentro de nuestro directorio de trabajo pulsaremos el botón derecho del ratón y, si hemos 
hecho la instalación de GIT correctamente, nos debería salir en el menú la opción “Git Bash Here”. 

Al pulsar sobre esta opción se nos abrirá la consola de Git Bash con la ruta de nuestro proyecto ya 
predefinida:

'miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT'

Ejecutamos el comando git init para que GIT comience a hacer un seguimiento de nuestro proyecto.

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git init
Initialized empty Git repository in G:/WORKSPACE/011 Github/Proyecto GIT.git

Es la carpeta que usará GIT para crear las áreas de ensayo local y de repositorio.

Ahora debemos especificarle a GIT sobre qué archivos tiene que hacer el seguimiento:

Para ver el estado en el que se encuentran nuestros archivos usaremos el comando:

git status          (nos dará información más detallada de los archivos)
git status -s       (nos dará información esquematizada)

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git status -s
?? estilo.css
?? index.html
?? main.js

Como podemos ver, nos da un listado de todos los archivos que forman parte de nuestro proyecto.
Los interrogantes ?? nos indican que ninguno de nuestros archivos está siendo sometido a 
seguimiento por parte de GIT.

Para ir practicando, vamos a decirle a GIT que le haga un seguimiento sólo al archivo index.html

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git add index.html

Si volvemos a hacer un “git status -s”:

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git status -s
A index.html
?? estilo.css

Veremos que ahora sale una A que nos indica que está haciendo el seguimiento del archivo index.html. 
Dicho archivo ahora está en el staging área, el área de ensayo.

Una vez que nuestro archivo está en el staging área, para hacer una instantánea de su contenido 
usaremos el comando “commit” que veremos en el siguiente tema.

_______________________

Índice
------
Definición 
Uso de commit
_______________________

*Definición
El comando git commit captura una instantánea de los cambios realizados actualmente en nuestro 
proyecto. Las instantáneas creadas con commit se pueden considerar como versiones "seguras" de un 
proyecto. Git nunca las cambiará a menos que se lo solicitemos explícitamente.

Antes de la ejecución de git commit, se usa el comando git add "preparar" cambios en el proyecto 
que se almacenarán en nuestro repositorio.

Estos dos comandos git commit y git add son dos de los más utilizados.


*Uso de commit
En el anterior tema habíamos dejado nuestro archivo en el stage área. 

Para hacer una instantánea de su contenido usaremos el comando “commit”.

La primera vez que hacemos un “commit” se nos pedirá nuestro mail y nombre. 

Git sólo pedirá estos datos la primera vez que lo usemos en un equipo:



Una vez introducidos los datos siguiendo las indicaciones que nos muestra GIT, volvemos a 
ejecutar el “commit”. Deberemos añadir también una descripción para la instantánea, en nuestro caso le 
pondremos, por ejemplo, “Version 1.0.0”

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git commit -m “Version 1.0.0”
[master (root-commit) 00350f8] Version 
1.0.0
1 file changed, 0 insertions(+), 0 
deletions(-)
Créate mode 100644 index.html

****** en mi caso la salida es:
git commit -m "Version 1.0.0"
[master (root-commit) 6c2e669] Version 1.0.0
 4 files changed, 11 insertions(+)
 create mode 100644 estilo.css
 create mode 100644 index.html
 create mode 100644 test.js
 create mode 100644 test.pyls

Ya tenemos guardada una primera instantánea de nuestro proyecto, es decir, una copia de nuestro 
código tal y como está en el momento actual.
Si más adelante necesitásemos volver a la versión del proyecto tal y como estaba en el momento actual, 
podríamos recuperarla.

Si ahora hacemos un “git status -s”:

miPC@miPC MINGW64 /g/WORKSPACE/011 
GitHub/Proyecto GIT (master)
$ git status -s
?? estilo.css
?? main.js

++++++++ en micaso:
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        readme.txt

Es la carpeta que usará GIT para crear las áreas de ensayo local y de repositorio.

Veremos que nuestro archivo ha desaparecido del listado. Esto se produce porque en el momento en que 
se agrega un archivo al repositorio y ya hay una copia de respaldo, el archivo deja de estar en el 
stage área y, por lo tanto, ya no nos lo mostrará. 

Con el comando “git status -s” sólo obtendremos información de aquello que no está en el repositorio.

Si hiciésemos algún cambio en el contenido de nuestro archivo y ejecutásemos de nuevo un 
“git status -s”:

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git status -s
M index.html
?? estilo.css
?? main.js

********* en micaso:
M index.html
?? readme.txt

Veríamos que ahora sí que nos informa del estado. Concretamente la M nos indica que el archivo ha sido 
modificado y tiene cambios que no han sido respaldados aún.

Si quiero hacer un respaldo del archivo con las modificaciones nuevas tendremos que poner el archivo 
en el área de ensayo y ejecutar el comando:

git commit -m “nueva descripción”

Es decir, que para cada cambio que hagamos, tenemos que pasar de nuevo por el stage área (con lo 
que lo veríamos con una M) y luego hacer un commit.

Stage área:

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git add index.html

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git status -s

M index.html
?? css/
?? js/

Veremos que ahora sale una A que nos indica que está haciendo el seguimiento del archivo index.html. 
Dicho archivo ahora está en el staging área, el área de ensayo.

Commit:
miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git reset –hard 093f1c5
HEAD is now at 093f1c5 Version 1.0.0

Llegado este punto tendríamos almacenadas dos instantáneas de nuestro archivo index.html. 
Para sacar un listado de todas las copias que tenemos en el repositorio local usaremos el 
comando:

git log 

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git log oneline
934978a (HEAD -> master) Version 1.0.1
093f1c5 Version 1.0.0

++++++++en micaso (con el parametro online no funciona):
$ git log (y devuelve:)

commit 923a6142644c780293afe3151641aa95a3fffc46 (HEAD -> master)
Author: Allekus <allekus@gmail.com>
Date:   Thu May 2 11:53:26 2024 +0200

    Version 1.0.3

commit 00fae2e240cf3ef53218753cf092eeeb8d14dd70
Author: Allekus <allekus@gmail.com>
Date:   Thu May 2 11:37:40 2024 +0200

    Version 1.0.1

commit 6c2e66944f5463edf2227ad5bfce9678d9e6c3db
Author: Allekus <allekus@gmail.com>
Date:   Thu May 2 11:26:28 2024 +0200

    Version 1.0.0


Como vemos, en nuestro caso tenemos dos versiones del archivo, la V1.0.0 y la V1.0.1
Si quisiésemos restaurar el archivo a la primera versión que teníamos, es decir, hacer una 
restauración del archivo, deberíamos usar el comando:

git reset –hard 093f1c5

Como vemos, hay que pasarle el código alfanumérico de la instantánea que queremos recuperar.

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git commit -m “Version 1.0.1”
[master 934978a] Version 1.0.1
1 file changed, 1 insertion(+), 1 
deletion(-1)

*******en micaso:
debo utilizar el parámetro con dos guiones --hard 
$ git reset --hard 6c2e66944f5463edf2227ad5bfce9678d9e6c3db

Con esto ya tendríamos nuestro archivo index.html restaurado a la primera versión.

***** OJO:
$ git log (veremos que ahora solo muestra una version)

commit 6c2e66944f5463edf2227ad5bfce9678d9e6c3db (HEAD -> master)
Author: Allekus <allekus@gmail.com>
Date:   Thu May 2 11:26:28 2024 +0200

    Version 1.0.0

Hay que señalar que, al haber retrocedido a la primera instantánea que teníamos (la V1.0.0), la 
segunda versión de mi archivo (la V1.0.1) ya no existe, no está disponible, desaparece. Es decir, 
podemos volver atrás a una versión anterior, pero una vez hecho esto perderemos todas las versiones 
posteriores a dicha versión.

Hemos visto cómo hacer un seguimiento a un archivo en concreto. Para hacer un seguimiento a todos 
los archivos de nuestro proyecto usaremos el comando:

git add .

GitHub/Proyecto GIT (master)
$ git add .

Con esto habremos añadido todos mis archivos al stage area.
Si hacemos un git status -s veremos que Git le está haciendo seguimiento a todos los archivos de n
uestro directorio de trabajo.

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git status -s
A estilo.css
A main.js

Si ahora hacemos cambios en el contenido de los archivos index.html y estilo.cs, al guardar dichos 
cambios y hacer un git status -s

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git status -s

Veremos que Git nos indica con M los archivos que hemos modificado. 

Para hacer una nueva instantánea del proyecto incluyendo los últimos cambios realizados, 
deberíamos hacer dos pasos:
- Hacer un add para que vuelva a añadir ambos archivos al staging área
- Hacer un commit para que nos pase los archivos a nuestro repositorio.

En casos como este, en el que tenemos que hacer un add y un commit, podemos hacer ambas operaciones 
en un solo paso, usando el comando:

git commit -am “descripción”

miPC@miPC MINGW64 /g/WORKSPACE/011 GitHub/Proyecto GIT (master)
$ git commit -am “Version 1.0.2”
[master fd8ada9] Version 1.0.2
3 files changed, 5 insertions(+)
create mode 100644 estilo.css
create mode 100644 main.js

Si hacemos ahora un status no debería aparecer nada porque ya están todos los archivos agregados al 
repositorio.

++++++ en micaso:
$ git status -s
M readme.txt

$ git log
commit ab7e251cf5f45015a9605a75e674ecce3b903da1 (HEAD -> master)
Author: Allekus <allekus@gmail.com>
Date:   Thu May 2 12:28:33 2024 +0200

    Versión 1.0.1

commit 6c2e66944f5463edf2227ad5bfce9678d9e6c3db
Author: Allekus <allekus@gmail.com>
Date:   Thu May 2 11:26:28 2024 +0200

    Version 1.0.0

Llegado este punto tenemos varias instantáneas de 
nuestro código en el repositorio local, es decir, en 
nuestro equipo. Pero no están subidas a la nube. 

Para ello, usaremos más adelante GitHub. 


_________________________________

Índice
------
Push 
Uso de git push 
Pull 
Uso de git pull 
Fork 
Operativa de Pull request 
Cómo hacer un fork en GitHub 
Clone 
Diferencia entre fork y clone 8
_______



IBM-SkillsBuild-Curso-PythonFullStack2024

