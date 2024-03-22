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

### BuscoYReemplazo
Esta función, de tipo Integer, toma tres parámetros de tipo String (constantes o variables): Se buscará en el segundo String lo q tenga el primero. Si coincide, devolverá 0 y además, reemplazara la cadena encontrada por el tercer String. Sino la encuentra, devolverá -1. Y si la encuentra más de una vez, reemplazara a la última coincidencia, retornando el valor entero del orden coincidente.

**Ejemplo:**

```
String buscar = "buscar";
String en = "Hola, quiero buscar una palabra y reemplazarla en este texto.";
String reemplazo = "reemplazo";

int resultado = buscoYReemplazo(buscar, en, reemplazo); // Devuelve "0".
```

### EstaContenido
La función verificará si cadena2 contiene la subcadena cadena1 o viceversa. Si está presente, la función devuelve true. De lo contrario, devuelve false. Esta funcion DEBE usarse en estructuras condicionales, ya sea IF, WHILE, etc. Puede combinarse con otras condiciones.

**Ejemplo:**

```
IF(EstaContenido("Homplato", "plato")) // Devuelve true.
```
