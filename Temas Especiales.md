## Temas especiales

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

### ConcatenarConRecorte
Esta función toma tres parámetros: cadena1 y cadena2, que son las dos cadenas de texto que deseas concatenar, y posicionRecorte, que es la posición en la que se desea recortar cadena1 antes de concatenarla con cadena2. La función comprueba que posicionRecorte esté dentro del rango válido de posiciones de cadena1 y de cadena2, y si no lo está, devolverá un mensaje de error. Luego se recortaran ambas cadenas. Finalmente, la función devuelve la cadena concatenada resultante.

**Ejemplo:**

```
cadenaResultante = ConcatenarConRecorte("Hola", "Mundo", 2) // Devuelve "lando".
```

### EstaContenido
La función verificará si cadena2 contiene la subcadena cadena1 o viceversa. Si está presente, la función devuelve true. De lo contrario, devuelve false. Esta funcion DEBE usarse en estructuras condicionales, ya sea IF, WHILE, etc. Puede combinarse con otras condiciones.

**Ejemplo:**

```
IF(EstaContenido("Homplato", "plato")) // Devuelve true.
```
