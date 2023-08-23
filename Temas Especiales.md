## Temas especiales

### FirstIndexOf
La función FirstIndexOf devuelve el índice del primer elemento encontrado en la lista que coincida con el valor del primer parametro. FirstIndexOf funciona de forma tal que el valor del pivot (primer parámetro de la función) es comparado con el valor de cada elemento de la lista, retornando el indice del primer elemento encontrado. Si no encuentra ninguna ocurrencia la variable resultado no modifica su valor. El indice del primer elemento es igual a 1 (a partir de ahi se incrementa hasta el fin de la lista).

Ejemplo:
```
z=x=0;
a=b=2;
C=-5;
x = FirstIndexOf(a; [1,b,2,-5,z,C]) // x = 2 ya que a == b es verdadero y es la primer coincidencia de la lista.
```

### Timer
La función especial Timer realiza un bucle hasta cumplir con la condicion realizando una operacion en su segundo parametro. La condicion siempre será un entero positivo (validar) y arranca a contar desde el número cero.

```
Timer(5, WRITE "Hello World")
```

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
