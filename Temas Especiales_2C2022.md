## Temas especiales

### #Iguales
Esta función del lenguaje tomará como entrada una expresión (pivot)  y una lista de expresiones. Devolverá la cantidad de elementos iguales al pivot que se encuentran en la lista. La cantidad de listas es indefinida.

**Ejemplo:**

`#Iguales ( a+w/b, [(d-3)*2,e,f] )  = 2 si  (a+w/b = (d-3)*2 ) & (a+w/b =f) & (a+w/b ≠ e)`

### AllEqual
Esta función del lenguaje tomará como entrada dos a más listas de expresiones y devolverá verdadero si cada elemento en orden posicional es igual a su par correspondiente en cada   una de las listas. Caso contrario: Falso. La cantidad de listas es indefinida.

**Ejemplo:**

`AllEqual ( [a+w,b,c], [(d-3)*2,e,f], [g,h,i] )  es True si (a+w = (d-3)*2 = g) & (b = e = h) & (c=f=i)
`

### Case
Se deberá implementar la sentencia DO CASE con la última cláusula DEFAULT, que será opcional
Ejemplo:

```
DO a
CASE a=101
…
CASE a>202
…
DEFAULT ## opcional
ENDDO

```
### Repeat Inline

Esta función del lenguaje repetirá un conjunto de una o más sentencias [sentencias, la cantidad de veces indicada por la constante entera ctentera

`REPEAT ctentera [sentencias]
