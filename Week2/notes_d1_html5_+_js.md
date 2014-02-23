#HTML5+Javascript
Desde el 2005 el paradigma ha cambiado mucho. Al ser tan complicada la gestión de recursos en front-end, estos se gestionan con modelos MV* (MVC, MVP, …).

###Callback
Es un concepto importante en Javascript. Se trata de qué queremos hacer cuando ocurra un evento.

##Web Storage (storing data in our computer)
Hay cosas que se pueden hacer con cache y otras que es mejor hacerlas con local storage (en el navegador de un ordenador concreto). Por ejemplo, que mis preferencias son en español. O un gmail offline: puedo redactar los mensajes nuevos, que se almacenen estos datos y que, cuando vuelva online se manden.

##Web SQL Database
Base de datos en el navegador. Ya casi no se usa. Para lo que se usa en el cliente es casi matar moscas a cañonazos. En desuso.

##Web Storage
El web storage tiene sus ventajas y desventajas. 

###Ventajas
* Fácil de usar
* Crossbrowser

###Desventajas
* Sólo se puede almacenar strings los objetos hay que serializarlos)
* Datos no estructurados (sin posibilidad de indexación o formas de búsqueda)

###localStorage
Los datos persistentes. No desaparecen hasta que los borremos.

	window.localStorage.setItem(KEY,VALUE);

###sessionStorage
DEsaparece cuando cerramos el navegador.

	window.sessionStorage.setItem(KEY,VALUE);

###indexedDB
Para baplicaciones más grandes, donde necesitemos algo más que "localStorge" (más capacidad a parte del key-value pair).


##Web Workers
En el navegador, para cada pestaña tenemos un hijo de ejecución. Si por ejemplo, estamos atendiendo eventos del usuario (onclick, etc…) y a la vez tenemos un proceso que muestra los números primos, por ejemplo…esto no puede hacerse. No puede realizarse más de un proceso a la vez. Para solucionar esto puede tenerse subhilos que hagan diferntes tareas y luego vuelva al principal devolviendo diferntes tipos de datos.

Creamos hilo. El nuevo script que asumirá el papel de nuevo hilo se designa con el parámetro dentro de `Worker`:

	var worker = new Worker('task.js');

Pasamos info al hilo (`task.js`):

	worker.postMessage('data');

Dos formas equivalentes de recibir mensajes en la clase que ejecuta el hilo:

	worker.onmessage = function(event) {code};
	worker.addEventListener("message", function(event) 	{code});

en task.js:

	self.onmessage = function(event){
		//do something
		//pasamos mensaje al hilo principal
		self.postMessage("recived: " + event.data);
	};

##Notifications
Las notificaciones web notifican a nivel sistema operativo. Para ello, la web pregunta directamente si se quiere aceptar las notificaciones.

Primero comprobamos si hay capacidad de hacerlo (si existe el objeto):

	if (window.webkitNotifications) {
		console.log("Notifications are supported!");
	}
Después pedimos permiso al usuario (debe aceptar):

	if (window.webkitNotifications.checkPermission() == 0){
		/*0 is PERMISSION_ALLOWD*/
		console.log("Notifications are supported!");
	}

Una vez el usuario ha aceptado, aplicamos notificaciones:
window.webkitNotifications.createNotification(INCON, TITLE, )

Existe un "bug" (en chrome) que el `checkPermissions` no se puede ejecutar en el evento `load`. Tendremos que pedir permiso en otro momento, por ejemplo cuando se guarda una peli u otro evento.

##Geolocalización
Agnósticos al dispositivo, ya que es el sistema operativo el encargado de decidir cuál es la mejor manera de calcularla.

##Forms
Desde HTML5 son más "divertidos". Se facilita más las validaciones con los diferentes tipos de inputs, etc.

	<progress />
	<meter />
	<datalist />
	<keygen />
	<output />

Nuevos inputs para móvil que hacen que los widgets (teclado por ejemplo) se adapten al tipo de input. También hacen validación (si metes un número de teléfono en uno deicado a meter un num. de tlf no te va a dejar enviar si no está rellenado de acuerdo al patrón especificado).

##DOMHandler
###quoJS
Un jquery mucho más ligero, hecho para móvil. 