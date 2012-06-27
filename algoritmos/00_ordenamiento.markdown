# Algoritmos de ordenamiento

## Introducción

Los algoritmos de ordenamiento son una clase definida de procedimientos que tienen como objetivo reacomodar los elementos dentro de una colección dada para que respeten cierta relación de órden determinada entre ellos.

> **En un tweet**  
> Son algoritmos que permiten disponer los elementos de una colección bajo cierto orden determinado, relativo entre ellos 

Ahora bien, ¿a qué nos referimos cuando hablamos de una relación de órden? Es muy sencillo, aunque el concepto se torna bastante riguroso: una **relación de órden** es tal que *dados dos elementos comparables entre sí, existe una forma bien definida de conocer cuál de ellos antecede al otro, según algún aspecto a evaluar que les sea inherente*.

Con una serie de ejemplos seguramente se comprenderá mejor:

* Si nos referimos a números (elementos comparables entre sí), podemos decir que el 23 es más pequeño que el 42. La relación de órden es rigurosa y definida matemáticamente.

	23 < 42 → [ 23 , 42 ]

* Si en cambio comparamos personas (no es bueno andarse comparando, pero síganme el juego) podemos decir que mi padre es más grande que yo. Esta vez, la relación de órden se define por las edades individuales.

	edad(yo) < edad(mi padre) → [ yo , mi padre ]

* Podríamos tomar el ejemplo anterior y comparar por otro atributo, como ser las alturas. En este caso el órden relativo se revierte: yo soy más alto que mi padre.

	altura(yo) > altura(mi padre) → [ mi padre , yo ]

Por supuesto, *el órden relativo puede darse tanto de menor a mayor, como de mayor a menor*. Los ejemplos se han brindado del primer modo, pero podrían reformularse sin dificultad según el segundo.

Es importante destacar que los algoritmos de ordenamiento no deben efectuar cambios sobre los elementos de la colección sino simplemente sobre el órden de los mismos.

---

Resumamos la esencia del comportamiento de los algoritmos de ordenamiento de esta manera:

* La colección de entrada es la misma que la de salida, aunque con los elementos dispuestos de cierto modo.
* La nueva organización de los elementos responde a una relación de orden bien definida. Generalmente, de menor a mayor.

---

Los algoritmos de ordenamiento son generalmente la primera *familia de algoritmos* que se aprenden/enseñan en los cursos de programación. También es la familia con más miembros y alternativas. Entonces vale preguntarse: ¿por qué se estudian primero, si son tantos y tan variados?  
Para responder a esa pregunta debemos comprender que los algoritmos de ordenamiento muchas veces no tienen sentido por sí mismos, sino como preparación de la colección para un nuevo fin. Éste puede ser alguno de los siguientes:

- Organizar la colección para ser presentada a un destinatario humano (es común ver listados y querer organizarlos bajo algún criterio determinado).
- Preparar la disposición de los elementos para la consecuente ejecución de un algoritmo de corte de control, que requiere un lote de datos ordenados.
- Optimizar las búsquedas dentro de una colección de elementos, permitiendo utilizar el algoritmo de *búsqueda binaria* por ejemplo.

## Relevancia

El área de los algoritmos de ordenamiento es una de las más exploradas e interesantes. Podríamos pensar *'¿para qué queremos más algoritmos de ordenamiento, si con un par alcanza?'*.  
Pues no es suficiente, y es bueno que así sea: La experimentación constante y la manipulación de los algoritmos existentes, la búsqueda desesperada por una solución más eficiente que reduciera los tiempos o esfuerzos para ordenar una colección, es lo que llevó al descubrimiento de técnicas de optimización y fragmentos de código que trascendieron esta familia de algoritmos para contagiar a muchos otros.

## Estudio

El estudio de los algoritmos de ordenamiento es fundamental para conocer técnicas de programación un poco más sofisticadas que las convencionales, y aprovechar todo el saber que ya hay volcado en esta área de la computación nutriéndose con sus herramientas.

Cuando se estudian los algoritmos de ordenamiento no alcanza con conocer el código: ése es sólamente el primer paso.  
De hecho mis estudiantes pueden constatar que, para mí, es el último paso. Los conceptos fundamentales son las motivaciones, las analogías en las que se basó el algoritmo, la metodología de operación, el estudio de casos, el seguimiento del comportamiento, el análisis de los rendimientos. Sólamente llegado ese punto ya se tiene suficiente conocimiento del algoritmo como para desarrollarlo sin necesidad de que se nos provea el código, e incluso para proponer mejoras sobre él.

Al analizar a los miembros de esta singular familia (imaginemos al 'tío burbujeo', un borracho sin cura... o a la 'abuela selección', para la cual ninguna candidata era suficientemente buena para nosotros) tenemos que considerar una buena cantidad de aspectos que estudiaremos sobre los algoritmos en particular:

* **Complejidad computacional** en el caso más favorable, más adverso y en el caso promedio tanto para comparaciones como para intercambios.
* **Utilización de memoria**, ya que no es lo mismo utilizar sólo la memoria inevitablemente comprometida por el arreglo que tener que disponer de aún más espacio para poder ejecutarse
* **Si son o no recursivos**, dado que generalmente la recursividad dificulta el entendimiento del código (aunque puede mejorar notablemente el desempeño del algoritmo).
* **Si son o no sensibles al órden**, es decir, que si la colección está ordenada en un principio, lo detecte y no continúe con el proceso.

## Nota

Como ya mencionamos hay una gran variedad de algoritmos de ordenamiento. Los hay primitivos, más sofisticados, algunos con rendimientos muy pobres pero de trivial implementación y otros con buen desempeño pero mucho más complejos.
Nos proponemos analizar en profundidad algunos, y mencionar aquellos que resulten de interés o dispongan de ciertos datos curiosos.

## Bibliografía recomendada

* Sedgewick, Robert; Wayne, Kevin (2011). *Algorithms* (4th ed.). Adison-Wesley Professional. p. 242

## Links de interés

* Wikipedia contributors, "Sorting algorithm", *Wikipedia, The Free Encyclopedia*, <http://en.wikipedia.org/wiki/Sorting_algorithm> (accedido el 17 de junio de 2012)
* Martin, David R., "Sorting Algorithms Animations", *Sorting Algorithms Animations*, <http://www.sorting-algorithms.com> (accedido el 17 de junio de 2012)