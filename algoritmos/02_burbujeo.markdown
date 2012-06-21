# Ordenamiento por Burbujeo (Bubble Sort)

## Introducción

TODO: continuar

### Idea
TODO: continuar

> **En un tweet**  
> Recorrer el arreglo evaluando cada pasada si las dos posiciones adyacentes están ordenadas. Si no es así, intercambiar y repetir el proceso.

TODO: continuar

## Seguimiento
> TODO: escanear imágenes y redactar en consecuencia

## Análisis
TODO: continuar

### Cantidad de búsquedas
TODO: continuar

### Cantidad de intercambios
TODO: continuar

### Memoria utilizada
TODO: continuar

### Análisis de casos típicos

#### Caso más favorable
En el caso más favorable, cuando los elementos están ordenados, tenemos que:

* Cantidad de búsquedas: O(n)
* Cantidad de intercambios: O(1)
* Cantidad de memoria adicional: O(1)

#### Caso promedio
En el caso promedio, cuando los elementos están distribuidos en forma aleatoria, tenemos que:

* Cantidad de búsquedas: O(n<sup>2</sup>)
* Cantidad de intercambios: O(n)
* Cantidad de memoria adicional: O(1)

#### Caso más desfavorable
En el caso más favorable, cuando los elementos en órden inverso, tenemos que:

* Cantidad de búsquedas: O(n<sup>2</sup>)
* Cantidad de intercambios: O(n<sup>2</sup>)
* Cantidad de memoria adicional: O(1)

---

TODO: continuar

### Resumen
> TODO: continuar

## Algoritmo
El algoritmo de ordenamiento por burbujeo más sencillo es el siguiente:

	public void sort(int[] arreglo) {
	  boolean huboIntercambios = true;
	  while (huboIntercambios) {
	    huboIntercambios = false;
	    for (int i = 0; i < arreglo.length; i++) {
	      if (arreglo[i] > arreglo[i + 1]) {                          
	        intercambiar(arreglo, i , i + 1);
	        huboIntercambios = true;
	      }
	    }                
	  }
	}

> En rigor, hay una versión más sencilla, que no es sensible a si hubo o no intercambios y continúa recorriendo el arreglo n veces. Ese algoritmo carece de interés para este apunte, por ser demasiado simple y redundante.

## Mejoras
> TODO: continuar

## Bibliografía recomendada



## Links de interés

* Wikipedia contributors, "Bubble sort", *Wikipedia, The Free Encyclopedia*, <http://en.wikipedia.org/wiki/Bubble_sort> (accedido el 19 de junio de 2012)
* Martin, David R., "Bubble sort", *Sorting Algorithms Animations*, <http://www.sorting-algorithms.com/bubble-sort> (accedido el 19 de junio de 2012)