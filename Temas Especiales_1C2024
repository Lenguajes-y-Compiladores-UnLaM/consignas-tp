## Temas especiales

### ContarPrimos
Dada una lista de expresiones (de variables y constantes), la funcion contarPrimos devolvera la cantidad de numeros primos encontrados.

**Ejemplo:**
```
z=x=0;
a=b=2;
C=-53;
x = ContarPrimos([11,b+8,2,55,z*b+7,C]) // x = 4
```

### UntilLoop
Esta función realiza un bucle hasta cumplir con la condicion realizando una operacion en su segundo parametro. La condicion siempre será un entero positivo mayor a la variable que recibe el resultado de la operacion.

**Ejemplo:**
```
x = 0;
UntilLoop(11>x, x=3+x)
```

### BuscoYReemplazo
Esta función, de tipo Integer, toma tres parámetros de tipo String (constantes o variables): Se buscará en el segundo String lo q tenga el primero. Si coincide, devolverá 0 y además, reemplazara la cadena encontrada por el tercer String. Sino la encuentra, devolverá -1. Y si la encuentra más de una vez, reemplazara a la última coincidencia, retornando el valor entero del orden coincidente.

**Ejemplo:**

```
buscar = "buscar";
en = "Hola, quiero buscar una palabra y reemplazarla en este texto.";
reemplazo = "reemplazo";

resultado = buscoYReemplazo(buscar, en, reemplazo); // Devuelve "0".
```

### AplicarDescuento
Esta función recibe el monto de descuento (como constante reai, siendo este valor comprendido entre 0 a 100), la lista de precios y el índice a partir del cual se aplicarán los descuentos por porcentaje. Antes de este índice, se aplica el descuento por monto, mientras que a partir de este índice se aplica el descuento por porcentaje (inclusive). La función maneja los casos en los que la lista está vacía o el índice es mayor o igual al tamaño de la lista, mostrando un mensaje de error en esos casos. Caso contrario, se debe imprimir el descuento final por lista de precios.

**Formato función:**
```
aplicarDescuento(float montoDescuento, [ List<Float> listaPrecios ], int indice)
```

**Ejemplos:**
```
aplicarDescuento(27.5, [500, 305, 79.4, 10], 3)        // El resultado de la función será "472.5, 277.5, 57.56, 7.25"
```
- El descuento para el primer elemento: 500 - 27.5 = 472.5
- El descuento para el segundo elemento: 305 - 27.5 = 277.5
- El descuento para el tercer elemento: 79.4 * 27.5 / 100 = 57.56
- El descuento para el cuarto elemento: 10 * 27.5 / 100 = 7.25

```
aplicarDescuento(50, [100, 200, 300], 4)        // ERROR; el indice es mayor a la cantidad de elementos
```
```
aplicarDescuento(50, [], 1)        // ERROR; lista vacía.
```
