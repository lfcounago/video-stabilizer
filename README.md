# Video stabilizer
Video stabilization using OpenCV library

En este proyecto se desarrolla un código para la estabilización de un video a través de paralelismo, SSE. Para ello hará uso de tres funciones; en las que se compararan los bloques, se calculará el desplazamiento y se aplicará el desplazamiento para centrar la imagen.



--Función main()--

Comenzaremos por la función main(). Antes de empezar, lo primero que realizamos es comprobar el número de argumentos que recibe esta función [línea 36], y cargamos la imagen según sea este número.

Una vez creada la imagen tras la comprobación anterior, extraeremos el primer frame, para tomarlo como guía y poder calcular el desplazamiento del resto de imágenes que iremos extrayendo frame a frame [línea 62].

Cuando hayamos superado con éxito los pasos anteriores, inicializaremos el contador de tiempo para saber en cuanto tarda en ejecutarse el programa [línea 66].

Para finalizar, comenzamos el bucle principal del programa, que se ejecutará mientras se puedan obtener nuevos frames a partir del video estabilizacion2.avi. En este bucle, se carga en cada iteración una imagen del video sobre la cual se van a realizar las siguientes operaciones de calcularDesplazamiento() y aplicarDesplazamiento() [línea 68].

Para terminar, una vez recorridos todos los frames del video y ejecutadas todas las funciones correspondientes, mostramos el tiempo de ejecución.



--Función calcularDesplazamiento()--

Con esta función [línea 83], calcularemos el número de filas y columnas que se ha desplazado la imagen con respecto a la primera que habíamos guardado en el main() para comparar con el resto de frames que iremos obteniendo. Para ello, comprobamos el bloque central de ambas imágenes, sin embargo, el bloque del frame actual lo desplazamos hasta que la diferencia con el de la primera imagen sea 0 (usando la función compararBloques() en cada desplazamiento).

Cuando tengo calculado el desplazamiento del frame (guardado en las variables desplazamientoX y desplazamientoY), muevo el frame a la posición central para poder estabilizar la imagen.



--Función compararBloques()--

Utilizamos esta función [línea 97] para analizar, respecto a un bloque dado, la tonalidad de otros, determinando la diferencia de tono que hay entre ambas, y así, poder encontrar el bloque que se corresponde a la posición central que se ha determinado con anterioridad.



--Función aplicarDesplazamiento()--

Con la funcion aplicarDesplazamiento() [línea 112]. Primero, creamos una imagen auxiliar donde aplicaremos el desplazamiento. A continuación, recorremos esta imagen y le vamos copiando lo que corresponda. Para esto, usamos la posición en la que estamos y el desplazamiento en esa imagen. Si se cumplen algunas de las condiciones (ver código), esa posición será de color negro, sino copio el trozo de la imagen que corresponde en esa posición.
