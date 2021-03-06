# Ordenamiento por Selección (Selection Sort)

## Introducción

Uno de los algoritmos de ordenamiento más sencillos es el de selección. Aún así es utilizado para ciertos casos muy particulares, dado que tiene una característica, que ya veremos, que lo hace bastante eficiente.

### Idea
Dada una colección de elementos, se busca el más pequeño y se lo intercambia por aquel que esté en la primera posición (incluso si ya estuviera en dicho lugar). Luego, se procede de la misma manera, pero esta vez buscando el más pequeño del conjunto restante y colocándola en la siguiente posición.  
Se continúa hasta evaluar la última posición de la colección. Una vez llegado este punto, el conjunto de elementos se encuentra ordenado.

> **En un tweet**  
> Buscar sucesivamente el elemento más pequeño del array y colocarlo al principio del conjunto analizado, excluyéndolo en la siguiente vuelta.

Como podemos intuír, este algoritmo es muy simple y de fácil entendimiento. Aún así, es la base para muchos otros algoritmos de ordenamiento.  
Veamos cómo funciona haciéndole un seguimiento...

## Seguimiento
> TODO: escanear imágenes y redactar en consecuencia

## Análisis
Lo primero que podríamos destacar al momento de analizar el comportamiento de este algoritmo es el hecho de que cada elemento intercambiado dentro de la colección pasa a ocupar su posición definitiva y nunca la abandona.

Si vemos el seguimiento anterior, notaremos que este suceso trae una inmediata consecuencia: el arreglo parecería dividirse en dos partes mientras dura el proceso de ordenamiento. La primera, totalmente ordenada y con cada elemento en su posición definitiva, y la segunda probablemente desordenada, y en vías de revertir esa condición.  
Podemos resumir esa idea diciendo que **por cada búsqueda** del elemento más pequeño, **el conjunto de elementos a ordenar se reduce en una unidad**. Por lo tanto, luego de n búsquedas, un conjunto de n elementos estará ordenado en su totalidad.

### Cantidad de búsquedas
Podemos notar que la primera búsqueda se hará entre n elementos, la siguiente entre n-1 elementos, la siguiente entre n-2 y así sucesivamente hasta la última búsqueda, que se realizará (virtualmente) entre 1 sólo elemento, el de la última posición.  
Si cada vez que se busca un elemento el conjunto de datos es menor, y sabiendo que debemos hacerlo por cada elemento, podemos calcular que evaluaremos n * ( n / 2 ) elementos. Siguiendo los lineamientos del cálculo de complejidad, encontramos que:
> La cantidad de búsquedas es proporcional a O(n<sup>2</sup>).

### Cantidad de intercambios
Cuando analizamos la cantidad de intercambios establecidos por el algoritmo, cualquiera sea la longitud del arreglo, notamos que intercambia cada elemento exactamente una vez. Por ello, y nuevamente con la notación anterior, decimos que:
> La cantidad de intercambios es proporcional a O(n).

### Memoria utilizada
De más está decir que como todos los algoritmos, utiliza como base la memoria ocupada por la colección. Sin embargo, este algoritmo tiene la particularidad de que no utiliza memoria adicional. Decimos que:
> La cantidad de memoria adicional es proporcional a O(1)

### Análisis de casos típicos

#### Caso más favorable
En el caso más favorable, cuando los elementos están ordenados, tenemos que:

* Cantidad de búsquedas: O(n<sup>2</sup>)
* Cantidad de intercambios: O(n)
* Cantidad de memoria adicional: O(1)

#### Caso promedio
En el caso promedio, cuando los elementos están distribuidos en forma aleatoria, tenemos que:

* Cantidad de búsquedas: O(n<sup>2</sup>)
* Cantidad de intercambios: O(n)
* Cantidad de memoria adicional: O(1)

#### Caso más desfavorable
En el caso más favorable, cuando los elementos en órden inverso, tenemos que:

* Cantidad de búsquedas: O(n<sup>2</sup>)
* Cantidad de intercambios: O(n)
* Cantidad de memoria adicional: O(1)

---

Como podemos notar, el algoritmo en su estado puro es absolutamente insensible al conjunto ingresado: Independientemente de cómo se presente la colección se comporta del mismo modo.

### Resumen
En suma, el algoritmo de ordenamiento por selección es simple, y tiene un comportamiento que no presenta sorpresas: *su tiempo de ejecución sólo depende de la cantidad de elementos*, la cantidad de *intercambios siempre permanecerá constante, así como la cantidad de búsquedas*.  
Además la cantidad de movimientos que afectan a cada elemento es la mínima (o casi): *cada uno cambia su posición una sóla vez*, para ocupar su posición definitiva.

## Algoritmo
El algoritmo de ordenamiento por selección más sencillo es el siguiente:

	public void ordenar(int[] arreglo) {
	  int posicionMinimo;
	  for(int i = 0; i < arreglo.length - 1; i++) {
	    posicionMinimo = i;
	    for(int j = i + 1; j < arreglo.length; j++) {
	      if(arreglo[j] < arreglo[posicionMinimo]) {
	        posicionMinimo = j;
	      }
	    }
	    intercambiar(arreglo, i, posicionMinimo);
	  }
	}

## Mejoras
> TODO: continuar con cycle-sort, o min-máx

## Bibliografía recomendada

* Sedgewick, Robert; Wayne, Kevin (2011). *Algorithms* (4th ed.). Adison-Wesley Professional. p. 248

## Links de interés

* Wikipedia contributors, "Selection sort", *Wikipedia, The Free Encyclopedia*, <http://en.wikipedia.org/wiki/Selection_sort> (accedido el 17 de junio de 2012)
* Martin, David R., "Selection sort", *Sorting Algorithms Animations*, <http://www.sorting-algorithms.com/selection-sort> (accedido el 17 de junio de 2012)