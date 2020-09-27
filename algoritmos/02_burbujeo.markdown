# Ordenamiento por Burbujeo (Bubble Sort)

## Introducción

Este algoritmo se basa en una analogía muy sutil, y logra el resultado esperado - ordenar la colección - con mucho estilo. Como todos los algoritmos de ordenamiento tiene sus problemas, pero no nos adelantemos a esos asuntos.

### Idea
Tomando la idea del champagne, podemos observar que los elementos *más livianos* van desplazándose hacia arriba como las burbujas presentes en esta bebida - el ejemplo aplica a las bebidas gaseosas en general, pero es más interesante con un champagne de por medio.  
De ese modo, una vez finalizado el proceso, **las burbujas se encontrarán esparcidas en forma acorde a su liviandad**.  
Muchas veces se pretende dar la analogía opuesta, la de "hundimiento", pero ésta es más apropiada para otro tipo de algoritmos, como ser el de ordenamiento por inserción.

> **En un tweet**  
> Recorrer el arreglo evaluando cada pasada si las dos posiciones adyacentes están ordenadas. Si no es así, intercambiar y repetir el proceso.

Lograr este efecto es muy simple aunque no siempre intuitivo, y el tweet nos ayuda a tomar una primera aproximación. Lo que sucede gracias a este algoritmo es que se comparan sucesivamente las posiciones adyacentes, haciendo un intercambio cuando sea necesario.  
Cada nueva iteración nos acerca más al resultado, dado que el mismo efecto de intercambio hará que los elementos se aproximen a su posición definitiva - y en última instancia, *estar en su posición definitiva*.

## Seguimiento
> TODO: escanear imágenes y redactar en consecuencia

## Análisis
Es fácil notar que luego de cada iteración uno de los elementos queda ubicado en su posición definitiva. Consecuencia de esto es que al volver a iterar la colección, se considera una posición menos: de no tener un elemento en su ubicación final esto desencadenaría un error irrecuperable.

Otra consecuencia es que con cada pasada, el resto de los elementos pueden quedar mucho más cerca de su posición de orden: es un efecto de arrastre, como cuando limpiamos el suelo y nuestro objetivo son los escombros más visibles *pero también nos llevamos los menos visibles con cada barrida*.  
Esto no quiere decir que siempre suceda, ya que analizando un caso de elementos completamente desordenados notamos que se alejan antes que acercarse; sin embargo, en el caso promedio se comporta del modo beneficioso.

Nuevamente y al igual que el ordenamiento por selección, vemos cómo el algoritmo genera dos sub-colecciones, una ordenada (con los elementos que van "ascendiendo" primero) y con cada miembro en su posición definitiva, y otra desordenada pero en vías de ordenarse, sujeta a una inestabilidad que no garantiza que los elementos estén - o al menos más cerca - de su posición definitiva. 

Por otro lado, la idiosincrasia de este algoritmo nos lleva a encontrarnos ante un problema denominado *de liebres y tortugas*: al analizar el conjunto de datos siempre en el mismo sentido, habrá elementos que debiendo desplazarse la misma cantidad de posiciones tarden mucho más tiempo en llegar a su ubicación definitiva.  
Es claro que a medida que un elemento avanza, uno retrocede. Si siempre avanza el mismo, el que retrocederá será uno distinto en cada ocasión, impidiéndole acercarse más rápidamente.

### Cantidad de búsquedas
Partiendo de la base común para estos análisis de que en el mejor de los casos (ante el conjunto ordenado) el algoritmo es sensible y corta la ejecución, notamos que cada elemento se evalúa al menos una vez por pasada, y como máximo n veces. Podemos asumir que con n / 2 búsquedas un elemento queda ubicado en su posición definitiva, en el caso promedio.  
Dado que se necesitan n pasadas para ordenar los n elementos, las búsquedas son proporcionales a <code>n&times;(n/2)</code>, que es O(n<sup>2</sup>).

### Cantidad de intercambios
Si evaluamos el caso en extremo optimista no se necesitarán intercambios. En cambio, si consideramos el caso más pesimista los intercambios serán uno por cada búsqueda, es decir <code>n&times;n</code>.  
En el caso promedio se hará necesitará intercambiar el elemento el 50% de las veces, es decir que habrá <code>n&times;(n/2)</code> intercambios, o lo que es lo mismo, O(n<sup>2</sup>)

### Memoria utilizada
Como todos los algoritmos simples que estamos analizando, no necesitaremos memoria adicional para ordenar el arreglo (salvo por supuesto la posición temporal para intercambios, pero ésta es por lo general despreciable en comparación con el tamaño de la colección)

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

Como ya fuimos anticipando, el algoritmo es sensible al orden: si el arreglo ya está ordenado, no efectuará intercambios y terminará su ejecución.

Si bien es simple de implementar, este algoritmo pierde eficacia muy rápidamente, y por ello no se acostumbra a implementar sino que se prefiere el de inserción.  
De hecho, Donald Knüth argumenta que no hay razones para recomendar este algoritmo. Por mi parte, esgrimo que como ejercicio mental es muy bueno, aunque no me animo a discutirle a Donald.

### Resumen
Del análisis se desprende que no es de los mejores algoritmos, y su rendimiento pierde - por lejos - ante los más modernos en su especie.  
Sin embargo, el interés académico no deja de ser un buen motivo para seguir estudiándolo y analizándolo.

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

> **Nota**: 
> En rigor, hay una versión más sencilla, que no es sensible a si hubo o no intercambios y continúa recorriendo el arreglo n veces. Ese algoritmo carece de interés para este apunte, por ser demasiado simple y redundante.

## Mejoras
> TODO: continuar con cocktail sort

## Bibliografía recomendada



## Links de interés

* Wikipedia contributors, "Bubble sort", *Wikipedia, The Free Encyclopedia*, <http://en.wikipedia.org/wiki/Bubble_sort> (accedido el 19 de junio de 2012)
* Martin, David R., "Bubble sort", *Sorting Algorithms Animations*, <http://www.sorting-algorithms.com/bubble-sort> (accedido el 19 de junio de 2012)
* Astrachan, Owen, "Bubble sort, An Archaeological Algorithmic Analysis", *Duke University*, <http://www.cs.duke.edu/~ola/papers/bubble.pdf> (accedido el 25 de junio de 2012) 