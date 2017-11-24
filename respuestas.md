# Preguntas de materia certamen 2 IA

## Certamen 2013-1 (respuestas de la pauta)
### Verdadero Y Falso

- **El movimiento genera el vecindario de soluciones factibles en algoritmos de búsqueda local**

  **Falso**, el movimiento genera el vecindario, el cual puede estar formado por cadidatas a solución factibles e infactibles.

- **Al usar la lista de referencia en el algoritmo genético para el TSP se logró reducir la epistásis**

  **Falso**, la epiptásis es una característica del problema relacionado con las restricciones. Al usar lista de referencia se pudo usar el cruzamiento standard (cruzamiento en un punto) obteniendo siempre candidatas a solución factibles. Se logró manejar la epiptásis, no reducirla.

- **Hill Climbing posee un paralelismo implícito cuando realiza varios re-starts**

  **Falso**, el paralelismo implícito implica realizar una búsqueda simultánea por el espacio de búsqueda y no secuencial como lo hace Hill Climbing aún con varios re-start.

- **La opción para manejar las restricciones en Simulated Annealing es usar una función  de evaluación que incluya penalizaciones**

  **Verdadero|Falso**, esa es una de varias opciones. También se puede hacer en el movimiento y la representación.     

- **Al hacer re-start se mantienen los elementos en la lista tabú de la solución anterior en tabú search**

  **Falso**, los elementos de la lista tabú están asociados a la solución inicial usada. El mantenerla no tiene sentido porque impediría realizar movimientos beneficiosos para la solución actual.

- **Solo Tabú Search y Hill Climbing pueden usar las estrategias mejor-mejora y alguna-mejora. En cambio Simulated Annealing sólo se basa en alguna-mejora**

  **Falso**, Tabú Search se basa sólo en mejor-mejora. Simulated Annealing en su versión standard se basa en alguna-mejora, pero es posible aplicarlo usando de base mejor-mejora.

### Argumente

**¿Qué opina de un algoritmo basado en Simulated Annealing, para el problema de la mochila, que usa Swap como movimiento?.¿Sería eficiente o en ese caso es mejor usar Tabú Search**

Es un movimiento ineficiente en este caso, tanto para SA como para TS, ya que buscará soluciones solamente considerando el número de objetos que inicialmente está llevando la mochila y dejaría de buscar en otras partes del espacio de búsqueda.

**¿Para qué sirve Monitorear?**

Sirve para observar la búsqueda y permitir tomar decisiones respecto a acciones a realizar, como por ejemplo cambios en los valores de los parámetros para permitir una buena intensificación y diversificación de la búsqueda.

## Certamen 2012-1

### Preguntas

**k-tournament es un operador de selección que elige aleatoriamente k individuos de la población y selecciona como padre aquel de mejor calidad. ¿En qué caso la presión de selección es mayor, para k=2 ó para k=4?**

Para k = 4, dado que todos tienen la misma probabilidad de ser elegidos para participar en el torneo, con un k mayor aumentan la probabilidad de que el mejor individuo sea seleccionado entre los k individuos, lo que haría que los peores individuos no sean seleccionado, es decir, se aumenta la presión de selección.

**En Simulated Annealing cuando la temperatura es baja se tiende a diversificar más la búsqueda**

Al contrario, al bajar la temperatura se tiende a intensificar la búsqueda, puesto que baja la probabilidad de aceptar una solución de peor calidad, lo que concentra la búsqueda en una región del espacio de búsqueda.

**Los operadores de transformación de un algoritmo genético estándar pueden ser fácilmente adaptados para resolver problemas con pocas restricciones**

No necesariamente, dependiendo del problema y la representación puede ser muy difícil adaptar los operadores de transformación de AGE. Por ejemplo, para un TSP con representación de lista con tour de ciudades, no se puede utilizar el cruzamiento en un punto porque produciría soluciones infactibles. Se puede cambiar la representación a una lista de referencia, pero se perdería información (cruzamiento diversificaría), por lo que se debería modificar el operador de cruzamiento para intensificar.

**Los algoritmos Greedy utilizan la función Miope para seleccionar vecinos de mejor calidad**

No, la función miope se utilizan para construir soluciones donde se toman decisiones localmente óptimas, en base a la calidad. Cuando uno habla de vecinos es porque está considerando soluciones completas.

**Es posible utilizar un método de sintonización para cambiar el largo de la lista durante la búsqueda de Tabú Search**

Sintonización de parámetros busca encontrar el mejor valor para un parámetro que se mantendrá fijo durante la búsqueda. Para cambiar un parámetro durante la ejecución del algoritmo se debe utilizar control de parámetros, en este caso un control adaptativo.

**Hill Climbing con alguna-mejora es más eficiente que Hill Climbing con mejor mejora, pero no asegura encontrar el óptimo global.**

Como ambas técnicas son de búsqueda local ninguna asegura encontrar el óptimo global. Por un lado, HC con alguna-mejora puede ser más eficiente siempre y cuando no se esté en el óptimo local, pues en dicho caso ambos algoritmos funcionan de la misma manera.

**Un buen operador de mutación siempre produce un hijo de mejor calidad que el padre.**

El operador de mutación no tiene nada que ver con los padres del individuo, si no con una modificación al mismo individuo. Por otro lado, no se puede asegurar que el aplicar un operador de mutación mejore la aptitud del individuo.

**En Tabú Search siempre se deben almacenar las soluciones visitadas completas pues es la única forma de asegurar que no se visiten otra vez**

No, en la práctica se almacena una codificación que permina no caer en una solución ya visitada, para así mejorar la eficiencia de la solución. Por ejemplo, en el problema de la mochila utilizando Bit-Flip como movimiento, se puede guardar en la cola el bit donde se realizó el flip. De esta manera no se vuelve a caer en la solución anterior y no es necesario guardar la solución completa.

**El operador de elitísmo en algoritmos genéticos permite guardar el mejor óptimo encontrado en la búsqueda para entregarlo como resultado al final del proceso.**

###### No estoy seguro de esto.
El objetivo del operador de elitísmo es pasar a la siguiente generación el mejor individuo de la generación actual. Por lo que si permitiría guardar el mejor óptimo de la búsqueda y entregarlo como resultado.

**Trabajar con una población de gran tamaño asegura encontrar soluciones de buena calidad en un algoritmo genético**

No lo asegura, el hecho de tener un gran tamaño de población favorece la diversificación, por lo que es probable de que el algoritmo no explote de buena manera el espacio de búsqueda y no pueda llegar a buenas soluciones.





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

## Certamen 2010-1 (respuestas de la pauta)

### Preguntas

**¿Cómo se realiza exploración en un algoritmo Hill-Climbing?**

HC no realiza exploración. HC + re-start realiza exploración en cada re-start cuando se genera una nueva solución inicial aleatoria.

**¿Cuál es la mejor combinación entre exploración y explotación?. Explique**

Siempre es bueno comenzar explorando para encontrar zonas atractivas que explotar en el espacio de búsqueda.

**¿Qué ventaja(s) poseen las técnicas de búsqueda completas comparadas con las técnicas incompletas?**

* Las técnicas de búsqueda completas son capaces de encontrar el óptimo global y/o determinar que el problema no tiene solución. Una técnica incompleta sólo es capaz de encontrar óptimos locales.

* Las técnicas de búsqueda completa son métodos deterministas, es decir, en todas las ejecuciones entregan el mismo resultado. Las técnicas de búsqueda incompletas son métodos estocásticos, por lo tanto, en cada ejecución entregan resultados diferentes.

**¿Qué se entiende por presión de selección?. ¿Cómo se relaciona con el proceso de exploración/explotación en un algoritmo genético?**

La presión de selección se entiende como la tendencia a considerar o no la calidad de los individuos en el proceso de selección en un algoritmo evolutivo. Se dice que la presión de selección es alta cuando la calidad de los individuos es importante al momento de seleccionar los individuos, esto favorece la explotación en el algoritmo. Se dice que la presión de selección es baja cuando la selección de individuos se realiza casi de forma indiferente con respecto a su calidad, esto favorece la exploración en el algoritmo.

**¿Cómo se promueve la explotación en un algoritmo Simulated Annealing?. ¿Cómo se promueve la exploración en un algoritmo Simulated Annealing?**

En el algoritmo Simulated Annealing se controla el balance entre explotación y exploración a traves de la temperatura. Una alta temperatura permite aceptar más movimientos que empeoran la calidad de la solución, por lo tanto favorece la exploración en el algoritmo. Por otro lado, cuando la temperatura es baja, pocos movimientos que empeoran la calidad de la solución serán aceptados, por lo tanto se favorece el proceso de explotación.

**¿Cómo podría variar el tamaño de la población en un algoritmo genético de forma de promover la debida exporación/explotación de la búsqueda?. Justiﬁque.**

Una población de gran tamaño favorece el proceso de exploración y una población pequeña favorece el proceso de explotación, por lo tanto, sería sensato comenzar con una población grande e ir reduciendo el tamaño a medida que avanza la búsqueda.

**¿Por qué no es recomendable seleccionar exclusivamente los mejores individuos en el proceso de selección de un algoritmo genético?**

 Esto implicaría una altísima presión se selección que llevaría a una convergencia prematura del algoritmo.

## Certamen 2008-1

### Verdadero y Falso
#### Las preguntas que no están acá es porque no recuerdo haberlas visto en clases ni las ppt.

* **A medida que se aumenta la temperatura en Simulated Annealing el algoritmo comienza a hacer una búsqueda más completa.**  

  **Falso**, el aumento de la temperatura permite que se acepten soluciones de peor calidad, lo que aumenta la exploración del algoritmo, pero como solo se genera un vecino a la vez, y de manera aleatoria, el algoritmo nunca va a cubrir todo el espacio de búsqueda (al menos para instancias grandes).

  SA no realiza búsqueda completas [respuesta 2003-1](#certamen-2003-1-respuestas-de-la-pauta)

* **El mecanismo que utiliza tabú search para escapar de óptimos locales es la lista tabú**

  **Falso**, la lista tabú se utiliza para que no se formen ciclos en la búsqueda. Lo que hace tabú search para escapar de óptimos locales es permitir soluciones de peor calidad.

* **Conviene penalizar la función objetivo cuando se desea manejar las restricciones duras**

  ###### No estoy seguro de esto
  **Depende**, si el algoritmo utilizado permite moverse por el espacio de soluciones infactibles si es buena idea penalizar estas en la función objetivo. Si el algoritmo se mueve por el espacio de restricciones factibles, es mejor utilizar una representación y/o movimientos que no acepten soluciones que rompan las restricciones duras (o simplemente descartar las que no cumplan).

  **Falso**, Si son duras lo más conveniente es manejarlas con los operadores y la representación. [respuesta 2003-1](#certamen-2003-1-respuestas-de-la-pauta)


* **Un algoritmo genético es ciego respecto al fenómeno de epistásis.**

  **Verdadero**, porque el algoritmo no toma en cuenta las restricciones cuando busca el óptimo. [respuesta 2003-1](#certamen-2003-1-respuestas-de-la-pauta)

* **Los operadores de tipo cruzamiento exploran**

  **Falso**, generalmente los operadores de cruzamiento **explotan**, debido a que utilizan información conocida para obtener a los nuevos individuos (estructura).

  **Verdadero o Falso**, dependiendo de la forma en que se deﬁne el operador tipo cruzamiento, este podría explorar como es el caso al usar la lista de referencia en TSP. [respuesta 2003-1](#certamen-2003-1-respuestas-de-la-pauta)

* **La estrategia de monitorear en un algoritmo evolucionista es para lograr una mejor sintonización de los parámetros**


  **Falso**, es para lograr un mejor control de parámetros

* **Siempre que se aplica re-start en un algoritmo Hill-Climbing se está ayudando a explorar más**

  **Falso**, no siempre, se puede dar el caso (muy poco probable) donde se caiga en una región ya explorada por el algoritmo.

## Certamen 2004-1

### Verdadero y Falso (Son las respuestas de la pauta)

* **Las metaheurísticas  tratan de encontrar el mejor óptimo local**

  **Verdadero**, las metaheurísticas no pueden asegurar la obtención del óptimo global, sin embargo tratan de encontrar el Mejor óptimo local, que en el caso ideal corresponde al óptimo global

* **El cruzamiento en un punto no es útil para la resolución de problemas de optimización**

  **Falso**, cuando el problema no tiene restricciones es una buena Metaheurística.

* **La mutación en un algoritmo genético standard es un algoritmo de búsqueda local**

  Falso, la búsqueda local trata de optimizar la búsqueda en un vecindario, la mutación no tiene objetivo de optimización.

### Preguntas (respuestas de la pauta)

**¿Qué alternativas tiene para manejar las restricciones en Simulated Annealing?. Ejemplifique**

Función objetivo + Penalización (por restricciones insatisfechas), Movimiento (que el movimiento no permita soluciones infactibles), Representación (que la representación no permita soluciones infactible), Descarte posterior al movimiento previa condición de aceptación.

**Compare Simulated Annealing con Tabu Search**

* **Aspectos Comunes:** Búsqueda Local dentro de un vecindario, requieren una solución completa inicial.
* **Diferencias:** Criterio de aceptación del movimento y forma de elegir soluciones candidatas. Simulated Annealing solo genera un vecino y tabu search genera un vecindario. SA acepta soluciones de peor calidad dependiendo de una probabilidad y tabú search siempre las acepta (si no están en la lista tabú).
* **Mecanismo de exploración:** En SA la temperatura, en TS la forma de elegir el siguiente movimiento.

## Certamen 2003-1 (respuestas de la pauta)

### Verdadero y Falso

* **A medida que se aumenta la temperatura en Simulated Annealing el algoritmo comienza a hacer una búsqueda más completa**

  **Falso**, SA no realiza búsquedas completas

* **El mecanismo que usa Tabu Search para escapar de óptimos locales es la lista tabú.**

  **Falso**, lista tabú impide los ciclo, aceptar soluciones diferentes (de peor calidad) impide el estancamiento en un óptimo local.

* **Conviene penalizar la función objetivo cuando se desea manejar las restricciones duras**

  **Falso**, Si son duras lo más conveniente es manejarlas con los operadores y la representación.

* **Un algoritmo genético es ciego respecto al fenómeno de epistásis.**

  **Verdadero**, porque el algoritmo no toma en cuenta las restricciones cuando busca el óptimo.

* **Los operadores tipo cruzamiento exploran.**

  **Verdadero o Falso**, dependiendo de la forma en que se deﬁne el operador tipo cruzamiento, este podría explorar como es el caso al usar la lista de referencia en TSP.

* **La estrategia de monitorear en un algoritmo evolucionista es para lograr una mejor sintonización de los parámetros.**

  **Falso**, eso es para el control de parámetros, no sintonización.

* **Siempre que se aplica re-start en un algoritmo hill-climbing se está ayudando a explorar más.**

  **Falso**, si el punto de partida es el mismo, por ejemplo usando un algoritmo greedy se volverá a realizar el mismo proceso.

### Preguntas

**Dada la representación por lista de referencia para el problema del vendedor viajero, considere 6 ciudades y responda.**

- **¿Esta representación es adecuada para una algoritmo de tipo Simulated Annealing?**  
Es adecuada siempre y cuando el movimiento que se deﬁne maneje la representación y la factibilidad. Sin embargo, no es adecuada si se piensa en el costo en codiﬁcar y decodiﬁcar la solución para realizar su evaluación

- **Se define el cruzamiento en dos puntos como:**
  - **Seleccionar aleatoriamente 2 puntos de corte**
  - **Intercambiar la parte central de los dos padres**  

  **Cree Ud. que este operador realiza una mejor explotación que el corte en un solo punto con esta representación para el TSP?, Compare**  
  Independiente del número de cortes, este operador usando la representación por lista de referencia sólo explora con respecto al problema.

**¿En qué se parecen Simulated Annealing con Tabú Search?**

Ambos aceptan soluciones peores a la actual para lograr explorar y salir de óptimos locales, ocupando diferentes métodos cada uno, exploran más al inicio y finalizan con una mayor explotación.

**¿Qué se entiende por Computación Evolutiva?**

Son los algoritmos que se basan en la teoría de la evolución, donde el más apto es el que sobrevive y tiene más posibilidades de tener descendencia. Esto es usado para resolver problemas, teniendo poblaciones de individuos donde la función de evaluación determina qué tan apto es el individuo para el caso.

**Defina control de parámetros adaptativo y determinístico**

El control de parámetros adaptativo va ajustando los parámetros del algoritmo en base a la retroalimentación del comportamiento que este tenga. El control de parámetros determinístico cambia los valores de los parámetros según una función preestablecida al comienzo de la ejecución de este, independientemente del estado del algoritmo en cada momento.  
