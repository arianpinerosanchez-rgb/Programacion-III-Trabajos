**Ejercicio 4**



**a-** Utilizaría estructura if-else en situaciones donde tenga mas de una condición, sino seria else.



**b-** Utilizaría estructura switch en situaciones donde el programa es como algún tipo de menú donde hay mas de una opción, por lo tanto habría que realizar una accion en el caso de cada una e incluso un default si el usuario llegara a ingresar en el cuestionario alguna opción inexistente.



**c-** me resultaron mas útiles consultas como sobre corregir la sintaxis de mi código y para definir variables.



**d-** La IA como asistente de programación es útil únicamente para errores de sintaxis la cual nos parezca muy confuso resolver si el código llega a ser relativamente enorme y para consultar estructuras de código que no nos lleguemos a acordar. 



## **Chat de IA:**



**Usuario:**



Por que la cuarta condición para identificar si se ingreso algún número negativo no funciona? Explicame cual fue el problema, como lo corregirias y por que utilizaste cierta cosa



**ChatGPT:**



El problema está en el orden de las condiciones.



Tu código evalúa los if y else if de arriba hacia abajo. Cuando ingresas -1, JavaScript pregunta:



if(stock < 3)



Como -1 < 3 es verdadero, entra inmediatamente en ese bloque:



estado = "Pedido urgente"



Y ya no sigue revisando los demás else if, incluyendo este:



else if(stock < 0)



Por eso nunca llega a mostrar el error.



Ejemplo paso a paso con stock = -1

stock < 3 → verdadero

Se ejecuta "Pedido urgente"

Se ignoran todos los demás else if

Resultado: aparece "Pedido urgente"

Cómo corregirlo



La validación de números negativos debe ir primero:



if(stock < 0){

&#x20;   console.log("Error, no puedes ingresar números negativos.");

}

else if(stock < 3){

&#x20;   estado = "Pedido urgente";

}

else if(stock <= 10){

&#x20;   estado = "Stock bajo, considerar reponer";

}

else{

&#x20;   estado = "Stock suficiente";

}

¿Por qué funciona ahora?



Porque ahora, si el usuario escribe -1:



if(stock < 0)



es verdadero desde el principio, entonces muestra el error y no entra en ninguna otra categoría de stock.



Otra mejora



No hace falta escribir:



else if(stock > 10)



porque si ya descartaste:



stock < 0

stock < 3

stock <= 10



lo único que queda es que sea mayor que 10.



Por eso puede simplificarse a:



else{

&#x20;   estado = "Stock suficiente";

}



Esto hace el código más limpio y fácil de leer.



También te recomiendo declarar la variable estado antes de los if:



let estado = "";



porque actualmente la estás usando sin declararla, y eso puede darte problemas en programas más grandes.



**Usuario:**



Me aparece un error de que la variable estado no está definida



**ChatGPT:**



Eso ocurre porque estado solo recibe un valor dentro de algunos bloques if, pero nunca fue creada previamente.



Por ejemplo, si tienes:



if(stock < 3){

&#x20;   estado = "Pedido urgente";

}



JavaScript busca una variable llamada estado. Si no existe, te mostrará algo como:



ReferenceError: estado is not defined



La solución es crearla antes de usarla:



let estado = "";



Quedaría así:



let componente = prompt("Ingrese el nombre del componente");

let stock = parseInt(prompt("Ingrese la cantidad actual en stock"));

let estado = "";



if(stock < 0){

&#x20;   console.log("Error, no puedes ingresar números negativos.");

}

else if(stock < 3){

&#x20;   estado = "Pedido urgente";

}

else if(stock <= 10){

&#x20;   estado = "Stock bajo, considerar reponer";

}

else{

&#x20;   estado = "Stock suficiente";

}



console.log(

&#x20;   "Resumen:\\nComponente: " + componente +

&#x20;   "\\nCantidad actual: " + stock +

&#x20;   "\\nEstado: " + estado

);



Además, si ingresas un número negativo, estado quedará vacío porque mostraste un error y no asignaste ningún estado. Podrías hacer:



if(stock < 0){

&#x20;   estado = "Dato inválido";

}



o directamente no mostrar el resumen cuando el dato sea inválido.



¿El error te aparece en la consola del navegador o VS Code te lo marca con una línea roja antes de ejecutar el programa?

