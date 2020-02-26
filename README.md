Explicación de logging-espree.js:

En addLogging primero convierte code en un elemento procesable en tiempo de ejecución y lo guarda en ast. Luego mediante estraverse.traverse divide el código en partes a las que se puede acceder. Al encontrar una función ejecuta addBeforeCode sobre ésta.
Una vez en addBeforeCode comprueba si se ha encontrado un nombre para la función y si no es así (node.id haría de false) se le da el nombre <anonymous function>. Acaba construyendo el console.log correspondiente y añadiéndolo al principio de la función. Tras todo esto se devuelve el resultado.
Finalmente, en addLogging, mediante escodegen.generate se reconvierte ast a su estado inicial (pero con las modificaciones) y se devuelve.
