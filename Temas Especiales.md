## Temas especiales

### LastIndexOf
La función LastIndexOf devuelve el primer índice encontrado del pivot en una lista. LastIndexOf funciona de forma tal que el pivot es comparado con cada elemento de la lista, retornando el indice del primer elemento encontrado. Si no encuentra ninguna ocurrencia la variable no modifica su valor.
Ejemplo:

```
a=3;
x = LastIndexOf(a; [1,2,b,-5,z,C]) // Asigna el valor de la variable "-5" a la variable "x"
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
