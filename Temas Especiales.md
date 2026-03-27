## Temas especiales

### FOR
La estructura de la sentencia FOR tendrá el siguiente formato 
                         
     FOR Variable = Expresion  TO Expresion  [ Step  Cte ] 
   
     NEXT Variable 
 
La variable en la instrucción NEXT deberá ser la misma que la variable contadora de la cláusula 
FOR. 

Los [] indican que los pasos son opcionales. En caso que no se indique nada, por default asumirá 
pasos de 1 en 1. 

**Ejemplos:**
```
FOR i = 1 TO 5
   PRINT i
NEXT i 
```
Salida: 1 2 3 4 5

```
FOR i = 1 TO 10 STEP 2
   PRINT i
NEXT i
```
Salida: 1 3 5 7 9

### Longitud
Esta función calcula la longitud de una lista.
La lista puede contener expresiones, no solo valores.
Puede utilizarse dentro de otras expresiones.

**Ejemplos:**
```
long ([a,b,c,e]) = 4 
```
```
long([1+2, 3*4, x, y+z]) = 4
```
```
IF long(lista) > 3 THEN
   PRINT "Lista grande"
ENDIF
```

### Ciclo Especial 
La estructura de la sentencia será 
 
    WHILE 
      Variable IN  [ Lista de Expresiones] 
    DO 
       Sentencias 
     ENDWHILE
     
Lista de expresiones es una lista de expresiones separadas por comas. 

**Ejemplos:**
```
WHILE x IN [1,2,3]
DO
   PRINT x
ENDWHILE
```
Salida: 1 2 3

```
WHILE x IN [1+1, 2+2, 3+3]
DO
   PRINT x
ENDWHILE
```
Salida: 2 4 6

```
WHILE x IN [1,2,3,4]
DO
   IF x MOD 2 = 0 THEN
      PRINT x
   ENDIF
ENDWHILE
```
Salida: 2 4

### MOD/DIV
MOD : módulo, tendrá el siguiente formato  expresión1 MOD expresión2. Deberá dar como resultado 
el resto de la división entre expresion1 y expresion2.

DIV   : división entera, tendrá el siguiente formato expresion1 DIV expresion2. Deberá dar como 
resultado la división entera entre expresion1 y expresion2.

Se pueden usar dentro de expresiones.
Deben respetar precedencia de operadores.
Manejo de error: división por cero.

**Ejemplos:**
```
IF x MOD 2 = 0 THEN
   PRINT "Par"
ENDIF
```

```
int x

x = (10 DIV 3) + (10 MOD 3)   // 3 + 1 => x = 4
```
