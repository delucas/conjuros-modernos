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
> TODO: continuar
### Caso más favorable
> TODO: continuar
### Caso promedio
> TODO: continuar
### Caso más desfavorable
> TODO: continuar
### Resumen
> TODO: continuar

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
	    intercambiar(i, posicionMinimo);
	  }
	}

## Mejoras
> TODO: continuar

## Bibliografía recomendada

* Sedgewick, Robert; Wayne, Kevin (2011). *Algorithms* (4th ed.). Adison-Wesley Professional. p. 248

## Links de interés

* Wikipedia contributors, "Selection sort", *Wikipedia, The Free Encyclopedia*, <http://en.wikipedia.org/wiki/Selection_sort> (accedido el 17 de junio de 2012)
* Martin, David R., "Selection sort", *Sorting Algorithms Animations*, <http://www.sorting-algorithms.com/selection-sort> (accedido el 17 de junio de 2012)