## Temas especiales

### equalExpressions
Se desea implementar una función llamada equalExpressions cuya finalidad es determinar si en una lista de expresiones matemáticas existe más de una expresión que sea equivalente a otra.

La función recibirá como único parámetro una lista de expresiones matemáticas (variables, constantes, operaciones aritméticas, etc.).

La función evaluará las expresiones y verificará si hay al menos dos que sean iguales en valor.

El resultado de la función será un valor booleano:

true si existen dos o más expresiones iguales.

false si todas las expresiones son diferentes.

El valor booleano resultante podrá ser utilizado directamente como condición en sentencias de control como IF y WHILE.

**Ejemplo:**
```
Integer a := 2;
Integer b := 3;
Boolean y;
y := equalExpressions(a + b, 5, c * 2, 3 + 2, a + b)
```

### charRepeat
Se desea implementar una función llamada charRepeat que determine si un carácter aparece en una cadena una cantidad de veces igual a la indicada por una constante o variable entera.

La función recibirá tres parámetros:

Un carácter (ejemplo: 'a').

Una cadena (ejemplo: "banana").

Una variable o constante entera que indica la cantidad de repeticiones esperadas (ejemplo: 3).

La función devolverá un valor booleano:

true si el carácter aparece en la cadena exactamente la cantidad de veces indicada por el entero.

false en caso contrario.

Este valor podrá ser utilizado directamente como condición en estructuras de control IF y WHILE.
**Ejemplo:**
```
y := charRepeat('a', "banana", 3)
```

### IsolatingX 
Se desea implementar una función llamada isolatingX que, dadas dos ecuaciones matemáticas que contienen una única variable X, resuelva el sistema obteniendo el valor de dicha variable al despejar X.

La función recibirá dos expresiones que representan ecuaciones con X:

Ecuación 1 (ejemplo: 2/43(14X - 3)).

Ecuación 2 (ejemplo: (8 + 17X) : 11/6).

La función devolverá el valor numérico de X (puede ser entero o flotante), obtenido al resolver la igualdad entre ambas ecuaciones.

Este resultado podrá usarse como valor en asignaciones, expresiones o condiciones.
**Ejemplo:**
```
r := isolatingX( 2/43(14X - 3) = (8 + 17X) : 11/6 )
```

### PalindromeCheck
Se desea implementar una función llamada palindromeCheck que determine si una cadena de caracteres es un palíndromo, es decir, si se lee igual de izquierda a derecha que de derecha a izquierda.

La función devolverá un valor booleano:

true si la cadena es un palíndromo.

false en caso contrario.

El resultado podrá utilizarse como condición en estructuras IF y WHILE.

**Ejemplo:**
```
y := palindromeCheck("neuquen")
```
