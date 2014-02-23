#JavaScript
##1. Lista de Tareas
En este ejercicio vamos a hacer una lista de tareas tal como está en 
##Introducción
###Defer
El `defer` sirve para indicar al explorador que ejecute el script después de cargar la página.

	<script defer src="todolist.js" type="text javascript"></script>


En la consola de Chrome, para crear múltiples líneas hay que pulsar:
	SHIFT+ENTER
Una vez queramos ejecutar pulsamos 
	ENTER
Si creamos una variable:
	var variable = 1;
Y luego, en la misma consola, introducimos los primeros caracteres y pulsamos tab, la consola autocompletará. Cada página crea un entorno de ejecución, donde podremos almacenar lo que queramos.
###Uso estricto
La expresión:
	'use strict';
Dicta al navegador que debe adaptarse a las buenas prácticas. Por ejemplo, no poner var antes de una variable es una mala práctica. Sólo funciona en exploradores modernos. ¿Por qué es importante esto? Porque así podemos controlar algunas cosas como el scope de las variables.

###Diferencia entre array y lista
En Javascript un array tiene un tamaño definido y que no puede ser cambiado. En cambio, a una lista si puedes añadir más contenido.

###Objetos
A la izquierda sólo podemos poner cadenas (sin comillas si cumple con los requisitos de definición de variables).

	var object = {
		nombre: "Borja",
		edad: 24
	}
A cada llave se le llama "propiedad". A la propiedad podemos acceder con
	object.propiedad
o bien
	object['propiedad']

###Expresiones y condiciones

	function setSalario(trabajador, cantidad) {
		cantidad = cantidad || 100;
		trabajador.salario = cantidad;
	}

Si no pasamos cantidad en la función, cantidad será `undefined`, con lo que devolverá 100, ya que es un `truthy`.

###Funciones
Una función puede asignarse a una variable.

###Interaciones con Documento
Todas las interacciones con el documento se hace mediante accesos al DOM (Document Object Model).

####Funciones importantes
######getElementById
	var result = document.getElementById('my_id')

######querySelector
	result = document.querySelector('#mi_id')
`querySelector` funciona para todos los tags, clases, ids. 

También se puede usar `querySelectorAll` para acceder a todos los elementos que tengan asignados la clase pasada como argumento.

######innerHTML

	element.innerHTML = ''

Todo lo que haya "debajo" del elemento con el id llamado con `getElementById` desaparece, ya que lo cambiamos por `''`.

######outerHTML
No solo coge lo anidado dentro del elemento sino también el propio elemento.

######setAttribute
Sirve para asignar atributos a elementos del DOM.
	result.setAttribute

######style

	p1.style.backgroundColor = "#ff0";

######listClass
Sobre el elemento aplicado devuelve una lista "inteligente" de clases asignadas al elemento en cuestión.

	p1.listClass.toggle('danger')
Le aplicamos la función `toggle` a esta lista. En el snippet anterior, si la clase 'danger' no está la añade al elemento `p1 .

######createElement()
	var newP = document.createElement('p');

Crea un nuevo elemento. En este caso un párrafo.

	var n = document.createElement('strong')
	n.textContent = "negrita";
Hemos creado el elemento strong con el texto negrita dentro.

	p1.children
Muestra los hijos del elemento sobre el que se llama. Es una lista, con la que podemos hacer un for:

	document.body.insertBefore(elemento1,elemento2)

######trim()
Quitar espacios.

####Parsing
La siguiente imagen muestra cómo y cuando se ejecuta los scripts en una html:

![image](parser.png)

La barra azul representa la carga del script (descarga del servidor). La roja la ejecución del script. La verde el "parseo" del html.

Lo más recomendable es ponerle el atributo defer: para que todo el DOM esté listo cuando ejecutemos el script.

####Modelo de Eventos
El modelo de eventos sirve para reaccionar ante acciones del usuario.
Hay dos modelos de eventos: <http://codepen.io/lodr/pen/CAtID>
1. Capturing (de "arriba" a "abajo")
2. Bubbling (de "abajo" a "arriba")

En este ejemplo, cuando se clica sobre d3, d3 es el target. Se mira si el target tiene a alguien a quien avisar (de lo más profundo a lo más alto o alejado). 

	p1.onclick = function(evt){
	console.log(evt);
	}
Cuando se pinche en p1 (si se pincha en un hijo, el click subirá (efecto "bubbling")).

	p1.addEventListener('click',a, useCapture)
`addEventListener` añade "escuchadores de eventos" al elemento sobre el que llamamos a la función. `click` es el evento ante el cual la función `a` reaccionará. `useCapture` es un booleano. `true` usa capturing (el elemento interceptará el evento de "arriba" a "abajo"); `false` al revés, usando "bubbling".

####Testing y depurador
Cuando se ejecuta un script en Chrome, si vamos a la consola podemos determinar puntos concretos donde queremos que la ejecución se pare:

//imagen_debug_con_flecha_azul

Una vez se ha parado, podemos entrar dentro de esa llamada para inspeccionar con más profundidad qué está pasando si pinchamos sobre el incono //icono_flecha_abajo:

//imagen_en_funcion_con_variables

Como puede apreciarse, en el panel de la derecha hay una serie de pestañas. Una de ellas es la de "Scope Variables". Si pinchamos sobre ella podemos ver las variables locales y las globales.

#####Depuración "a ciegas"
Esta técnica de depuración consiste en dejar trazas en el código mediante la función `console.log()`.






