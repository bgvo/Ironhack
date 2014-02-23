#Workflow
##Bower
Bower es un instalador de paquetes de Javascript.
Instalar el CLI:

	npm install -g bower

	bower install
	bower install <package-name>
	bower search [<name>]
	bower uninstall

En nuestro caso, hacemos 

	vagrant up
	vagrant ssh
Una vez dentro de la máquina vagrant instalamos bower con `npm` y después 

	bower install jquery

en /vagrant hacemos

	bower init

El bower init lo que hace es crear una librearía. Te pide una serie de campos para describir la librearía.

Una vez creada, existe un archivo dentro del directorio donde hemos inicializado bower llamado bower.json (el directorio donde se supone que tenemos nuestra librería).

##Grunt
Automatiza tareas.

Grunt cuenta realiza dos tareas importantes:

	concat
Concatena archivos y los concatena en uno sólo para to tener que poner una sola ruta en tu html.

	uglify

Los "chorros de código" (archivos minimificados) te los pone de manera decente.

Para que grunt realice estas tareas hay que crear el archivo de configuración (Gruntfile.js). Este archivo tiene que estar alojado en la carpeta del proyecto (de tu librería).

En Gruntfile.js especificamos el nombre que le daremos al script principal, que viene determinado en el archivo `package.json`.

En package.json:

{
  "name": "vagrant",
  "version": "0.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "BSD-2-Clause",
  "devDependencies": {
    "grunt": "~0.4.2"
  }
}

Este archivo se genera al ejecutar el comando

	npm install grunt --save-dev

Si queremos instalar dependencias para poder realizar tareas con grunt, como `concat` o `uglify`, deberemos poner, en vez de grunt el comando anterior, el siguiente:

	npm install grunt-contrib-uglify --save-dev

#HTML5 enhances

##Cache

	<html manifest="cache.appcache">

Con este comando le decimos al explorador que todo lo que haya en el archivo `cache.appcache`sea cacheado (si o si). Luego el explorador, según su política, cachearía si no lo pusieras o no. Pero así te aseguras de que lo va a cachear.

#Patterns
Javascript no es malo (se supone). Simplemente se presta mucho a hacerlo mal.

##Qué es un patrón?
Se trata de problemas que te encuentras a menudo a la hora de desarrollar código. Tienes que realizar una y otra vez la misma historia. Eso es un patrón. A estos problemas se les puede dar una solución reusable. El agrupar soluciones a patrones se les llama Frameworks.

Existen varios tipos de patrones:

* Creative Design Patterns
* Structural Design Patterns
* Behavioural Design Patterns

##Constructor Pattern
Este es el más familiar.Este patrón se da en la vida cotidiana.

Para asimilarse a OOP, Javascript utiliza  funciones para crear instancias de clases, pero no tiene clases.

##Singleton Pattern
Sólo queremos tener UNA sola cosa. Una sóla instancia.

##The Module Pattern
Este patrón es MUY utilizado. La única manera de aislar cosas en Javascript es mediante funciones. ¿Cómo devolvemos cosas en Javascript de ese entorno aislado? Sólo con return.

El patrón módulo lo que consigue es que partes de una función sólo sean accesibles pero otras no.

Toda definición de función **tiene** que tener un nombre. Para poder crear una función sin nombre tenemos que usar un pequeño "truquito".

	(function () {})

Con los paréntesis, Javascript se cree o acepta que es una función aunque no haya nombre. 

Para llamar a una función sin nombre tenemos que añadir los paréntesis (`()`) al final como si de una función normal se tratase:

	(function () {console.log('cosa); })()

que es lo mismo que (cuestión de gustos):

	(function () {console.log('cosa); }())

La función puede ser asignada a una variable…la función tiene nombre:

	f() {console.log('hola')}
	(f)()
	"hola"
A todo esto, que es un patrón, se le llama **autofunción**.

El objeto global es `window`. Pues bien, se puede operar con pasándolo a una función.

A continuación vamos a crear un módulo (módulo es un objeto que tiene dentro una funcionalidad):

##Factory Pattern
Las factorías siempre son funciones. ¿Para qué se usan?



