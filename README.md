# VC_P2

## Tarea 1

En primer lugar, se convierte la imagen original a escala de grises para poder localizar mejor los cambios de tonalidad y, por ende, los contornos.

Posteriormente, se obtienen dichos contornos utilizando el operador Canny con los umbrales 100 y 200, mostrando el resultado.

La tarea consistía en realizar el conteo de píxeles blancos, que se traducen en contorno, por cada fila. Para ello se realiza una serie de modificaciones con respecto al conteo de columnas mostrado en el enunciado de la práctica. En la función "reduce()", el segundo parámetro se cambia de 0 (columnas) a 1 (filas). Por otro lado, en la normalización se realiza el conteo con todos los píxeles divididos entre 255 por el numero de columnas. 

Sumado a esto, la tarea también pide obtener el número de filas que superen un umbral del 90% de esta en blanco, para ello se realiza una simple multiplicación entre ese 90% (0,9) y el valor máximo de píxeles blancos en una fila que hay en toda la imagen. Con estos datos se muestra la información y se dibuja una línea horizontal en las filas que cumplen con esta condición.

## Tarea 2

Para esta tarea hay que obtener el umbralizado tanto de la herramienta Sobel en 8 bits como de la imagen con Canny obtenido en la tarea anterior. Para ambos el proceso es el mismo, pero primero se explicará cómo obtener la imagen con Sobel en 8 bits.

Se parte de la imagen en gris y se suaviza con una función "Gaussiana", calculando posteriormente la imagen tanto en horizontal como en vertical con la herramienta "Sobel". En esta función se utilizan los dos últimos parámetros para decidir entre filas (1, 0) o columnas (0, 1). Se combinan ambos resultados con la función "add" y finalmente, se convierte a 8 bits utilizando la función de OpenCV "convertScaleAbs", mostrando el resultado en pantalla.

A partir de aquí, el tratamiento para ambas imágenes Sobel y Canny es el mismo. Lo primero es aplicar el umbral, para ello se utilizó la función de OpenCV "threshold" con unos valores entre 130 y 255, buscando los puntos blancos en un fondo negro.

Lo siguiente es realizar el mismo conteo de filas y columnas para ambas imágenes realizado anteriormente en el enunciado de la primera tarea, así como en la propia tarea. Se muestra una serie de gráficas para ambas herramientas y para cada eje. Se puede comprobar como la herramienta Canny otbiene unos valores mucho más elevados que Sobel, traduciéndose en una mayor densidad de píxeles obtenidos en el primer caso.

Finalmente, se buscan los valores máximos de filas y columnas para aplicar el umbral del 90% de píxeles tanto para filas como columnas, mostrando los resultados obtenidos y dibujando líneas horizontales y verticales para ambas imágenes. 

En estos se puede observar como, al haber una mayor densidad de píxeles en Canny, su umbral del 90% es mucho menor y por ende encuentra muchas filas y columnas que alcancen este. Por otro lado, las filas encontradas para ambas imagenes residen en la misma zona aproximandamente, siendo esta la superior donde se encuentra el pelo. Para el caso de las columnas, difieren bastante ya que para el caso de Sobel solamente encuentra una columna en la zona derecha cerca de la nariz.

Como conclusión, considero que la herramienta Canny es mucho más efectiva ya que las zonas que se encuentran entre los valores marcados coinciden con los ojos, nariz y boca, por lo que confío mucho más en este algoritmo para encontrar estos patrones en cualquier imagen. La herramienta Sobel consigue acercarse en las filas pero no es tan preciso y falla completamente con las columnas.

## Tarea 3