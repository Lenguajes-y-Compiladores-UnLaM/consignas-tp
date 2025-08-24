## Temas especiales

### equalExpressions
Se desea implementar una función llamada equalExpressions cuya finalidad es determinar si en una lista de expresiones matemáticas existe más de una expresión que sea equivalente a otra.

La función recibirá como único parámetro una lista de expresiones matemáticas (variables, constantes, operaciones aritméticas, etc.).

La función evaluará las expresiones y verificará si hay al menos dos que sean iguales en valor.

El resultado de la función será un valor booleano:
- `true` si existen dos o más expresiones iguales.
- `false` si todas las expresiones son diferentes.

El valor booleano resultante podrá ser utilizado directamente como condición en sentencias de control como IF y WHILE.

**Ejemplo:**
```
Integer a := 2;
Integer b := 3;
Boolean y;
y := equalExpressions(a + b, 5, b * 2, 3 + 2, a + b)  // y := true por igualdad en 1er, 2do, 4to y 5to termino
y := equalExpressions(0, -5, a + b)  // y := false ya que todos los terminos son distintos
```
### isZero
Se desea implementar una función llamada isZero que, dada una expresión numérica, determine si su valor es igual a cero.

La función recibirá como único parámetro una expresión numérica, compuesta por:
- Constantes y/o variables enteras o flotantes.
- Operadores aritméticas básicos: +, -, *, /.
  
La función devolverá un valor booleano:

-- `true` si la expresión se evalúa en 0.
-- `false` en caso contrario.

El valor podrá ser usado directamente en condiciones de estructura IF y WHILE.

**Ejemplos:**
```
Integer contador := 10;
WHILE isZero( contador - 10 ) DO
   print("El contador vale 10")
   contador := contador - 1
ENDWHILE

Integer s := 3;
Integer h := 44;
IF (isZero( s*7+1-h/2 )) THEN
   print("La expresion es igual a cero")
ENDIF
```
### 
**Ejemplo:**
```
Integer a := 2;
Integer b := 3;
Boolean y;
y := equalExpressions(a + b, 5, b * 2, 3 + 2, a + b)  // y := true por igualdad en 1er, 2do, 4to y 5to termino
y := equalExpressions(0, -5, a + b)  // y := false ya que todos los terminos son distintos
```
### 
**Ejemplo:**
```
Integer a := 2;
Integer b := 3;
Boolean y;
y := equalExpressions(a + b, 5, b * 2, 3 + 2, a + b)  // y := true por igualdad en 1er, 2do, 4to y 5to termino
y := equalExpressions(0, -5, a + b)  // y := false ya que todos los terminos son distintos
```
