Tecnologias:
Node.js
MobX (frontend)
Redis
Gulp para el transpilado a ES6

Servicio a utilizar:
https://developer.forecast.io/

Descripcion:
mostrar en pantalla completa la hora y la temperatura de las siguientes ciudades:

Santiago (CL), Zurich (CH), Auckland (NZ), Sydney (AU), Londres (UK), Georgia (USA)

Las latitudes y longitudes de cada ciudad deben ser guardadas en Redis al momento de iniciar la aplicacion.

Cada request de la API debera ir a Redis, sacar las latitudes y longitudes correspondientes, y hacer las consultas necesarias al servicio de Forecast.io.

Cada request a la API tiene un 10% de chances de fallar, al momento de hacer el request debera suceder lo siguiente:

if (Math.rand(0, 1) < 0.1) throw new Error('How unfortunate! The API Request Failed')

Esto nos simulara un fallo del 10%~, la aplicacion debera rehacer el request las veces que sea necesario para tener una respuesta correcta, cada fallo debera guardarse en Redis dentro de un hash llamado "api.errors", la llave debera ser el timestamp y el contenido debe ser relevante al error. El handler de error debera capturar solamente este error y no otro con diferente clase o mensaje.

Los cambios del frontend deberan ser manejados con MobX y solamente cambiar el contenido visto dependiendo de la respuesta de la API, no olvidar algun indicador de carga entre request!

El temas el diseño esta 100% en tus manos, nos interesa mas la funcionalidad y orden más que cuan bonito se ve.
