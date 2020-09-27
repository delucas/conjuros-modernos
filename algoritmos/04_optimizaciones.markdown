# Algoritmos Optimizados

Contribución especial de Pablo Matías Mariani, ex alumno de la materia.

## Introducción
Esta sección trata sobre los algoritmos de ordenamiento y los algoritmos de búsqueda optimizados. Se explicará en detalle por qué son más rápidos y eficientes que los originales, así como también su forma de operar.


Para analizar la complejidad del algoritmo, se tienen en cuenta el número de comparaciones y el numero de intercambios, aunque también se suele agregar en el caso de Java, la cantidad de peticiones de longitud de los arreglos (cosa que puede evitarse de forma muy sencilla). La cantidad de comparaciones y de intercambios se traduce en tiempo de procesador.

## Algoritmo de Ordenamiento por Selección
El algoritmo de selección, utilizado para ordenar elementos en un arreglo, no tiene optimización alguna, por tal motivo no aparece en esta sección. Este algoritmo es imposible de modificar de tal forma que corte su ejecución al estar el arreglo ya ordenado. Tampoco se logra
una mejora en el rendimiento si en lugar de buscar el mínimo en cada iteración, se buscara el mínimo y el máximo, pues la cantidad de iteraciones se reduce a la mitad, pero la cantidad de comparaciones aumenta y la cantidad de intercambios se mantiene igual, por lo que se empeora el rendimiento del algoritmo.

## Algoritmo de Ordenamiento por Burbujeo
El algoritmo de burbujeo optimizado suele llamarse “algoritmo de burbujeo bidireccional” o en inglés “cocktail sort” (ordenamiento por cocktail).

1. Este algoritmo aplica un ordenamiento de burbujeo ordinario yendo de izquierda a derecha.
2. Al llegar a la derecha realiza el mismo procedimiento pero para ir de derecha a izquierda, partiendo de la anteúltima posición ( n – 1 ), porque en la última esta el máximo valor.
3. Luego de la primera iteración, los valores mínimo y máximo quedan en los extremos. 
4. En la segunda iteración se realiza lo mismo que lo descripto anteriormente, pero partiendo de izquierda a derecha desde la posición 1 y de derecha a izquierda desde la posición n - 2, dejando los segundos mínimos y máximos en sus respectivos lugares.
5. El algoritmo finaliza cuando se detecta que el arreglo esta ordenado, o cuando se llega al centro del arreglo.

Este algoritmo es más eficiente que el de burbujeo original por lo siguiente:

1. Corta su ejecución al detectar ordenado el arreglo.
2. En cada iteración deja los máximos y mínimos en los extremos del arreglo y esto presenta una gran mejora: por ello el algoritmo termina de ordenar un arreglo más rápidamente que el original salvo en el peor de los casos, que es cuando el arreglo está ordenado al revés de cómo se pretende, caso en que ambos tardan los mismo.

Haremos un ejemplo para evidenciar el segundo punto. Considérese el siguiente arreglo: <pre>[0, 1 , 2 , 3 , 9 , -1]</pre> y queremos ordenarlo de menor a mayor de izquierda a derecha.

Con el algoritmo de burbujeo original el 9 quedará en su lugar en la primer iteración, pero el -1 llegará a su posición (la posición 0) recién en la última iteración. Si aplicamos el algoritmo de burbujeo
optimizado, en la primera iteración el 9 quedará en su posición y el -1 también, por lo que en la primera iteración el arreglo quedará completamente ordenado.
Se requieren 15 comparaciones y 5 iteraciones para ordenar el arreglo utilizando el algoritmo sin optimizar, mientras con el algoritmo optimizado se requiere de 13 comparaciones y una sola iteración.
Este tipo de casos es el que se presentará con mayor probabilidad. Con esto se deduce que el algoritmo de burbujeo optimizado a lo sumo tarda lo mismo que el original, pero nunca más que eso.


Hay una optimización más sencilla la cual consiste que el algoritmo corte la ejecución al detectar ya ordenado el arreglo, es decir, sin agregar el ida y vuelva. De esta manera se logra una mejora (no tan buena como la anteriormente mencionada) sin necesidad de complicarse con el código.

### Código

	public int [] ordenar ( int [] arreglo ) {
	  int cantPosiciones = arreglo.length;
	  int aux = 0 ;
	  boolean ordenado = false;
	  int i = 1;
	  while (!ordenado && i < cantPosiciones - 1 ){
	    ordenado = true;
	    for ( int j = 0 ; j < cantPosiciones - i ; j++ ){
	      if ( arreglo [j] > arreglo [j+1]){
	        ordenado = false;
	        aux = arreglo [j+1];
	        arreglo [j+1]= arreglo [j];
	        arreglo [j]= aux;
	      }
	    }		
	    if (!ordenado){
	      ordenado = true;
	      for ( int j = cantPosiciones - i - 1 ; j >= i ; j-- ){
	        if ( arreglo [ j ] < arreglo [ j - 1 ] ){
	          ordenado = false;
	          aux = arreglo [j];
	          arreglo [j] = arreglo [j-1];
	          arreglo [j-1] = aux;
	        }
	      }
	    }
	    i++;
	  }
	  return arreglo;
	}

## Algoritmo de Ordenamiento por Inserción

El algoritmo de inserción optimizado, a diferencia del original, elimina los intercambios, por lo que el arreglo se ordena de manera más rápida. Este algoritmo en promedio mantiene la misma cantidad de comparaciones que el algoritmo de inserción original, pero elimina los
intercambios.

### Descripción
Al igual que el algoritmo de inserción original, este algoritmo va tomando sub-arreglos del arreglo original y coloca el nuevo elemento agregado en el subconjunto viejo, en el lugar que debe estar para que el arreglo este ordenado.

La diferencia radica en la forma en cómo lo hace:
En lugar de realizar intercambios hasta colocar el elemento en el sitio que le corresponde, lo que hace es comparar el elemento nuevo con cada elemento del subconjunto viejo yendo de izquierda a derecha.
Apenas se encuentra el primer elemento mayor al elemento que uso para comparar, se coloca en esa posición al elemento y se corre una posición hacia la derecha a todos los elementos que están a la derecha de la posición donde va el elemento a insertar.

