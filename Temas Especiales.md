## Temas especiales

### equalExpressions
Se desea implementar una función llamada equalExpressions cuya finalidad es determinar si en una lista de expresiones matemáticas existe más de una expresión que sea equivalente a otra.

La función recibirá como único parámetro una lista de expresiones matemáticas (variables, constantes, operaciones aritméticas, etc.).

La función evaluará las expresiones y verificará si hay al menos dos que sean iguales en valor.

El resultado de la función será un valor booleano:

true si existen dos o más expresiones iguales.

false si todas las expresiones son diferentes.

El valor booleano resultante podrá ser utilizado directamente como condición en sentencias de control como IF y WHILE.


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
Nota: la lista reordenada (en caso de haya sucedido) debe mostrarse/visualizarce de alguna manera al momento de hacer la GCI:

### sliceAndConcat
La funcion especial sliceAndConcat recibe 5 parámetros:

limiteInicial (entero): Posición de inicio para realizar un corte en una de las cadenas.\
limiteFinal (entero): Posición final para el corte en una de las cadenas.\
palabra1 (String): La primera palabra que se utilizará para el corte.\
palabra2 (String): La segunda palabra en la que se concatenará el resultado del corte.\
concatenarEnPalabra1 (boolean): Determina si el corte se realizará sobre palabra1 y el resultado se concatenará a palabra2 (si es false), o si el corte se realizará sobre palabra2 y el resultado se concatenará a palabra1 (si es true).

La función debe hacer un corte (slice) en la cadena indicada por los parámetros limiteInicial y limiteFinal y luego concatenar el segmento obtenido a la otra palabra, según el valor de concatenarEnPalabra2. La cadena resultante debe ser devuelta.
```
y = sliceAndConcat(3, 6, "amarillo", "verde", 0)
```
La función debe devolver el resultado de cortar el texto "amarillo" desde el índice 3 hasta el 6 ("rill") y concatenarlo con "verde", resultando en: "verderill".

### negativeCalculation 
Implemente una función llamada negativeCalculation que reciba como único parámetro una lista de variables y/o constantes de tipo Float, donde los elementos pueden ser tanto negativos como positivos.

La lista estará encerrada entre paréntesis y sus elementos estarán separados por comas.\
La función debe analizar la cantidad de valores negativos dentro de la lista:\
Si la cantidad de números negativos es par, la función deberá sumar todos los valores negativos y devolver el resultado en una variable.\
Si la cantidad de números negativos es impar, la función deberá multiplicar todos los valores negativos y devolver el resultado en una variable.\
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
