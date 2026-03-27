## Temas especiales

### FOR
La estructura de la sentencia FOR tendrá el siguiente formato 
                         
     FOR Variable = Expresion  TO Expresion  [ Step  Cte ] 
   
     NEXT Variable 
 
La variable en la instrucción NEXT deberá ser la misma que la variable contadora de la cláusula 
FOR. 

Los [] indican que los pasos son opcionales. En caso que no se indique nada, por default asumirá 
pasos de 1 en 1. 

### Longitud
Esta función calcula la longitud de una lista 
 
**Ejemplo:**
```
long ([a,b,c,e]) = 4 
```
### Ciclo Especial 
La estructura de la sentencia será 
 
    WHILE 
      Variable IN  [ Lista de Expresiones] 
    DO 
       Sentencias 
     ENDWHILE
     
Lista de expresiones es una lista de expresiones separadas por comas. 

### MOD/DIV
MOD : módulo, tendrá el siguiente formato  expresión1 MOD expresión2. Deberá dar como resultado 
el resto de la división entre expresion1 y expresion2.

DIV   : división entera, tendrá el siguiente formato expresion1 DIV expresion2. Deberá dar como 
resultado la división entera entre expresion1 y expresion2.
