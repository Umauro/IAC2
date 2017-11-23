# Preguntas de materia certamen 2 IA

## Certamen 2011-1

**¿Cómo se podría variar el tamaño de la lista tabú para mejorar el proceso de búsqueda realizado por tabú search? Explique.**

Se podría ir disminuyendo el largo de la lista tabú después de aceptar un número "n" de mejoras, porque reducir el tamaño de la lista favorece la intensificación. Por otro lado, se debería aumentar el tamaño de la lista cuando se aceptan muchas soluciones de peor calidad, pues aumentar el tamaño de la lista favorece la diversificación.

**Explique las ventajas y desventajas del uso de la representación ordinal para resolver el problema del vendedor viajero en algoritmos genéticos**

Una ventaja es que se pueden utilizar movimientos de mutación conocidos para problemas de ordenamiento, sin tener que pensar en movimientos propios, como por ejemplo _**Swap**_, _**K-OPT**_, etc.

Una desventaja que tiene es al momento de considerar el movimiento de cruzamiento, los movimientos clásicos (Cruzamiento en 1 punto, Cruzamiento Uniforme, etc) obtienen hijos infactibles en la gran mayoría de los casos. Se podría arreglar esto utilizando una codificación de lista de referencia, pero se perdería información al hacer el cruzamiento, haciendo que este diversifique en vez de intensificar.

**¿Cuál es la ventaja de utilizar un operador 2-opt comparado con un operador swap en el problema del vendedor viajero? Explique**

La ventaja que tiene 2-opt sobre swap para la representación clásica del TSP (lista con el tour de ciudades a visitar) es que altera menos la solución que un swap. 2-OPT produce solo dos cambios en la solución, lo que permite generar vecinos más cercanos que al utilizar swap, lo que favorece la explotación del espacio de búsqueda.

**¿Por qué es importante el enfriamiento de la temperatura en Simulated Annealing?. ¿Cuál sería el efecto de volver a elevar la temperatura cada k iteraciones?**

La temperatura en SA controla el que se acepten o no soluciones de peor calidad, a medida que se avanza en la búsqueda se deberían ir obteniendo soluciones de mejor calidad, por lo que es necesario ir enfriando la temperatura para dejar de aceptar soluciones que empeoren la calidad.

Si se vuelve a elevar la temperatura se volverían a aceptar soluciones de peor calidad, lo que favorece la exploración del algoritmo.

**¿Cómo se relaciona la tasa de mutación con el proceso de exploración/explotación de un algoritmo genético? Explique**

Una alta tasa de mutación favorece la exploración del algoritmo genético, ya que al generar soluciones sin considerar la información existente en la población lo que produce son saltos en el espacio de búsqueda. De manera inversa, si la tasa de mutación es baja se favorece la intensificación, pues el algoritmo no se desplazaría tanto por el espacio de búsqueda.

**¿El proceso de selección por ranking es siempre más explotativo que el proceso de selección por ruleta? Explique**

No, como selección por ruleta asigna la probabilidad de ser seleccionado de acuerdo a la calidad del individuo, si un individuo posee una calidad muy grande será seleccionado con una gran calidad, por lo que se explotaría de gran manera el espacio de búsqueda donde se encuentra dicho individuo. En cambio, bajo la misma situación, al utilizar ranking la diferencia entre probabilidades de selección no será tan distante entre individuos, lo que desfavorece la explotación.

**¿Qué ventajas poseen las técnicas de búsqueda incompletas comparadas con las técnicas de búsqueda completas? Explique**

Permiten encontrar una solución de buena calidad (no asegura la óptima) en un tiempo computacional reducido, para una instancia grandes de un problema en particular, donde una técnica de búsqueda completa no obtiene solución. Esto lo logran utilizando heurísticas, las cuales son eficientes computacionalmente.

**¿Qué se entiendo por genotipo y fenotipo en un algoritmo genético? Explique**

Genotipo vendría a ser el conjunto de genes que componen la solución (la representación de esta), el fenotipo es la expresión del genotipo, el cual corresponde al valor de la función de evaluación/aptitud para el genotipo de la solución.

## Certamen 2008-1
