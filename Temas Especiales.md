## Temas especiales

### ListIndexOfLast
Esta función del lenguaje tomará como entrada una expresión (pivot) y una lista de variables o constantes numéricas. Compara la expresión con el valor de cada elemento de la lista y devolverá el último índice que sea coincidente con la expresión. Si no hay coincidencia el valor a asignar es 0.

**Ejemplo:**

```
x = ListIndexOfLast([x+1], [a, b, 3, d]) // Asumiendo que a=d=2 y la expresion x+1 es igual a 2, se devolveria el ultimo indice de valor que sea igual a la expresion, en este caso sería x = d
```

### PrintReverseStringN
Esta función del lenguaje tomará como entrada una lista de caracteres y una constante entera. Luego la función se sencargara de imprimir de atrás para adelante cada uno de los caracteres de la lista según la cantidad especificada en el segundo parámetro.

**Ejemplo:**

```
PrintReverseStringN(['d','l','r','o','w',' ','o','l','l','e','h'], 2) // Imprime "Hello world" dos veces.
```

### ElementInTheMiddle
La función ElementInTheMiddle devuelve el elemento que se encuentra en el medio de la lista. Para calcular el elemento que se encuentra exactamente en el medio, la cantidad de elementos debe ser mayor que cero e impar y la fórmula es la siguiente (cantidad_elementos/2) + 1 redondeando la división para abajo.
Ejemplo:

```
x = ElementInTheMiddle(a, b, c, 1.0, d, 99, 100, -5, e) // Asigna el valor de la variable "d" a la variable "x"
```

### FIB

La función especial Fibonacci (sucesión de Fibonacci) tendrá el siguiente formato:

```
FIB(n)
```

Tomará como entrada un número natural "n", y devolverá el enésimo término de la sucesión, sabiendo que los dos primeros términos de la misma son 0 y 1, y cada uno de los demás es igual a la suma de los dos anteriores. El resultado deberá operar en cualquier expresión numérica.
