# Ordenamiento por Inserción (Insertion Sort)

## Introducción

Simple, efectivo y vistoso, el ordenamiento por inserción es, dentro de los algoritmos de ordenamiento básicos, uno de los más interesantes y utilizados.

### Idea
Esta es la forma en que ordenamos las cartas de una baraja, por lo que a aquellos que alguna vez jugamos con naipes nos va a resultar más que familiar.  
La idea es tomar los naipes desordenados en una mano, e ir pasándolos uno a uno hacia la otra, **insertándolos** en el lugar correcto a medida que vamos aumentando la cantidad de cartas del mazo -correctamente ordenado- en la nueva mano y reduciendo la cantidad en el mazo original. Por supuesto, una vez pasado el último naipe hacia la mano que contiene el mazo ordenado, el proceso ha finalizado y queda completamente acomodado cada elemento.

> **En un tweet**  
> Agregar los elementos del array uno a uno, y a su vez dejarlos en orden relativo a los elementos previamente incorporados.

En forma de algoritmo es muy eficiente con elementos físicos, pero al implementarlo en una computadora corremos con la desventaja de que hay que *hacer lugar* para el elemento a insertar cada vez que conocemos la posición relativa del nuevo miembro del subconjunto ordenado.  
Esa operación por lo general es costosa (salvo con listas enlazadas), por lo que el algoritmo pierde eficacia al tener que desplazar tantas veces, en promedio, cada elemento.

## Seguimiento
> TODO: escanear imágenes y redactar en consecuencia

## Análisis
Similar al comportamiento de selección, este algoritmo tiene como primera consecuencia que los elementos del arreglo incorporados al segmento ordenado están ordenados relativamente entre ellos. A diferencia de aquel algoritmo, esta vez no están en su posición definitiva, por lo que aún es probable que sigan desplazándose.

En el caso del ordenamiento por inserción, el tiempo de ejecución (búsquedas más intercambios) está ligado al orden inicial del arreglo. Si observamos los casos típicos, veremos que en el mejor caso no hace intercambios, y en el peor hace n veces n intercambios.

### Cantidad de búsquedas
La cantidad de búsquedas dependerá del caso particular que estemos analizando, y a cuál de los tres casos emblemáticos se asemeje más. Para analizarlo, debemos considerar que al menos visitará una vez cada elemento, y por cada elemento nuevo, podrá evaluarlo hasta n - 1 veces (si es que no está en su lugar correcto) o una sóla vez si es que está en su posición definitiva.  
Como podemos apreciar, es bastante variable pero el problema es acotado y bien definido.

### Cantidad de intercambios
Como podemos imaginar, nuevamente la cantidad de intercambios está reglada por las condiciones iniciales que tengamos al procesar el arreglo. Ante un arreglo que esté ordenado, evidentemente no necesita hacer ningún intercambio. Ante uno invertido, necesitará recorrer n veces el arreglo, moviendo n - 1 veces cada elemento. Eso nos arroja un resultado proporcional a O(n<sup>2</sup>). En el análisis de casos típicos podemos comprobarlo.

### Memoria utilizada
Estos algoritmos simples no necesitan memoria adicional al espacio previamente utilizado por el arreglo que se va a ordenar, ya que ordenan sobre el mismo conjunto de datos. Por ello, la memoria utilizada es siempre proporcional a O(1).

### Análisis de casos típicos

#### Caso más favorable
En el caso más favorable, cuando los elementos están ordenados, tenemos que:

* Cantidad de búsquedas: O(n)
* Cantidad de intercambios: O(1)
* Cantidad de memoria adicional: O(1)

#### Caso promedio
En el caso promedio, cuando los elementos están distribuidos en forma aleatoria, tenemos que:

* Cantidad de búsquedas: O(n<sup>2</sup>)
* Cantidad de intercambios: O(n<sup>2</sup>)
* Cantidad de memoria adicional: O(1)

#### Caso más desfavorable
En el caso más favorable, cuando los elementos en órden inverso, tenemos que:

* Cantidad de búsquedas: O(n<sup>2</sup>)
* Cantidad de intercambios: O(n<sup>2</sup>)
* Cantidad de memoria adicional: O(1)

---

Ser sensible al conjunto ordenado es un factor a favor del algoritmo en aproximadamente el 50% de los casos (¿por qué?).

La pregunta es: ¿es preferible tener un rendimiento notablemente peor que otro algoritmo el 50% de las veces, sólo por tener uno mucho mejor el otro 50%?  
Y la respuesta, como siempre, es *depende*: Si sabemos que el conjunto de datos estará mayormente ordenado, o es pequeño quizás convenga priorizar este algoritmo frente al de selección. Sin embargo, al saber que los datos vendrán mayormente desordenados (o en orden inverso, en el peor de los casos) priorizar algoritmos más primitivos, como el de selección, pero que optimicen la cantidad de intercambios, puede ser una mejor opción.

### Resumen
El algoritmo de ordenamiento por selección tiene buen desempeño en arreglos que no sean del todo aleatorios, sin importar su tamaño.
En la práctica es común este tipo de configuración de elementos, por lo que es uno de los algoritmos más utilizados.  
Además, es muy bueno en los casos en que hay muchos elementos repetidos, respetando incluso el orden relativo de los elementos que se considerarían iguales (**estabilidad**)

## Algoritmo
El algoritmo de ordenamiento por inserción más sencillo es el siguiente:

	public void sort(int[] arreglo) {
	  for (int i = 1; i < arreglo.length; i++) {
	    for (int j = i; j > 0 && arreglo[j] < arreglo[j - 1]; j--) {
	        intercambiar(arreglo, j , j - 1);
	    }                
	  }
	}

## Mejoras
> TODO: continuar con Shell sort

## Bibliografía recomendada

* Sedgewick, Robert; Wayne, Kevin (2011). *Algorithms* (4th ed.). Adison-Wesley Professional. p. 250

## Links de interés

* Wikipedia contributors, "Insertion sort", *Wikipedia, The Free Encyclopedia*, <http://en.wikipedia.org/wiki/Insertion_sort> (accedido el 21 de junio de 2012)
* Martin, David R., "Insertion sort", *Sorting Algorithms Animations*, <http://www.sorting-algorithms.com/insertion-sort> (accedido el 21 de junio de 2012)