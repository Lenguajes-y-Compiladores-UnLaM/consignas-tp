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

### EQUMAX y EQUMIN 
EQUMAX( expresión ; [lista de variables o ctes]) 
EQUMIN( expresion ; [lista de variables o ctes]) 
 
La función será verdadera o falsa, si expresión es igual al máximo o mínimo de la lista de variables o 
constantes. 
La lista debe estar separada por comas y delimitada por corchetes. 
Esta función deberá operar únicamente en condiciones. 

**Ejemplo:**
```
var1=120 
IF EQUMAX(10+101; [100, 111, var1] ) ## será falsa 
```
