## Temas especiales (v2)

### Asignación Compleja 
La función asignación compleja asigna la primera posicion de la lista de variables con la primera posicion de la lista de variables o constantes de la segunda lista y asi sucesivamente. Ambas listas estan balanceadas sintácticamente. Se debe verificar que la segunda lista solo trabaje con variables y/o constantes, verificando tipos.

Ejemplo:
```
AsigComp([a, b, c, d] : [1, b, 2.5, z]) // a=1, b=b, c=2.5, d=z
```

### Contar Distinto
La función especial cont devuelve la cantidad de elementos cuyo valor no coincide con la expresión del primer parametro. En el caso particular que el resultado de la expresion se encuentre en toda la lista se devuelve el numero -1. La lista del segundo parametro solo trabaja con variables y constantes.

```
c = !cont(a+b+3/c :: [a,b,c,2,3]);
```

### SetSwitch
La sentencia SET SWITCH permite ejecutar una de entre varias acciones en función del valor de una expresión. Es una
alternativa a if then else cuando se compara la misma expresión con diferentes valores.
-Se evalúa la expresión, dando como resultado un número.
-Luego, se recorren los "Case" dentro de la estructura buscando que el número coincida con uno de los valores.
-Cuando se encuentra la primera coincidencia, se ejecuta el bloque de sentencias correspondiente y se sale de la
estructura SET SWITCH.
-Si no se encuentra coincidencia con ningún valor, se ejecuta el bloque de sentencias de la sección ELSE CASE.

**Ejemplo:**

```
SET SWITCH ( a + b * 21)
    CASE 10: z = 200
             a = 100
    CASE 22: z = a + b
    CASE 30: z = a
    ELSECASE: a = 0
ENDSETCASE
```

### Fibonacci
La función especial Fibonacci (sucesión de Fibonacci) tendrá el siguiente formato:

**Ejemplo:**

```
FIB (n)
```

Tomará como entrada un número natural "n", y devolverá el enésimo término de la sucesión, sabiendo que los dos primeros términos de la misma son 0 y 1, y cada uno de los demás es igual a la suma de los dos anteriores. El resultado deberá operar en cualquier expresión numérica.