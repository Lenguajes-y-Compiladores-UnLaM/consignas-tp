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

### triangulo
La función especial triángulo recibe tres parámetros que pueden ser constantes, variables u operaciones aritméticas y retorna una constante string que será "equilátero", "isóceles" o "escaleno". Cada parámetro representa el lado de un tríangulo y si los tres lados son de igual medida, se llaman equiláteros; si los dos lados son de igual medida, se llaman isósceles y si los tres lados son de diferente medida, se llaman escalenos.
```
x = 2, z = 3 // asignaciones a fines de entender los ejemplos
y = triangulo(x, 1+1, x)  // y = "equilatero"
y = triangulo(0, 1/x, 0) // y = "isóceles"
y = triangulo((32+5+x)*z, 1/x, 100) // y = "escaleno"
```

### binaryCount
La funcion especial binaryCount cuenta la cantidad de numeros binarios en una lista y devuelve un entero corresponde a esa cantidad
```
x = 3 // asignaciones a fines de entender los ejemplos
y = binaryCount([110,1,0,5,x,10101100,-1])  // y = 4
```
