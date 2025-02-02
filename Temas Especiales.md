## Temas especiales

### negativeCalculation 
Implemente una función llamada negativeCalculation que reciba como único parámetro una lista de variables y/o constantes de tipo Float, donde los elementos pueden ser tanto negativos como positivos.

La lista estará encerrada entre paréntesis y sus elementos estarán separados por comas.
La función debe analizar la cantidad de valores negativos dentro de la lista:
Si la cantidad de números negativos es par, la función deberá sumar todos los valores negativos y devolver el resultado en una variable.
Si la cantidad de números negativos es impar, la función deberá multiplicar todos los valores negativos y devolver el resultado en una variable.
Se debe garantizar que la función maneje correctamente listas con distintos casos, incluyendo aquellas sin valores negativos.

**Ejemplos:**
```
a := 4.1
b := -1.5

x = negativeCalculation(3.5, -2.0, a, b, -3.0)  
// Cantidad de negativos: 3 (impar)  
// x := (-2.0) * (-1.5) * (-3.0) = -9.0
```
```
c := -1.7

x = negativeCalculation(-4.0, 2.3, c, 5.6)  
// Cantidad de negativos: 2 (par)  
// x := (-4.0) + (-1.7) = -5.7  
```

### sumFirstPrimes
Implementar una función llamada sumFirstPrimes que calcule la sumatoria de los N primeros números primos.

La función debe recibir un número entero N como parámetro y devolver la suma de los N primeros números primos.

**Ejemplo:**
```
x = sumFirstPrimes(5)  // x = 2 + 3 + 5 + 7 + 11 = 28
```

### reorder
La función especial reorder recibe tres parámetros:
*Lista de expresiones: La lista está entre corchetes y las expresiones separadas por comas.
*Valor booleano: Un valor que indica la dirección del reordenamiento. Si el valor es 1, la parte de la lista que debe reordenarse será la que está a la izquierda del pivote. Si el valor es 0, será la de la derecha.
*Entero pivote: Un valor entero que marca la posición en la lista desde la cual se inicia el reordenamiento. Este índice actúa como punto de referencia para dividir la lista en dos partes.

La función reorder tomará la lista de expresiones y, dependiendo del valor del booleano, realizará un reordenamiento de las expresiones a partir de la posición indicada por el pivote. Si el valor booleano es 1, la parte de la lista a la izquierda del pivote debe ser reordenada de forma que la primera expresión ocupe la posición del pivote, la segunda la posición anterior, y así sucesivamente. Si el valor booleano es 0, se reordenará la parte de la lista a la derecha del pivote de forma similar.
Se debe validar que el valor del pivote no exceda la cantidad de expresiones.

**Ejemplos:**
```
reorder([x+3, 1+1, 9-x],1,2)  // la primer posición es cero

//[9-x, 1+1, x+3]  luego de reordenar
```
```
reorder([r*j-2, x+3, 1+1, 9-x],0,2)  // la primer posición es cero

//[r*j-2, x+3, 9-x, 1+1]  luego de reordenar
```
```
reorder([r*j-2, x+3, 1+1, 9-x],0,3)  // no reordena porque no hay expresiones del lado izq del pivote
```
```
reorder([r*j-2, x+3, 1+1, 9-x],1,0)  // no reordena porque no hay expresiones del lado derecho del pivote
```

### binaryCount
La funcion especial binaryCount cuenta la cantidad de numeros binarios en una lista y devuelve un entero corresponde a esa cantidad
```
x = 3 // asignaciones a fines de entender los ejemplos
y = binaryCount([110,1,0,5,x,10101100,-1])  // y = 4
```
