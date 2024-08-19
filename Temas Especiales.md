## Temas especiales

### getPenultimatePosition 
Dado 2 parametros, un pivote (cte entero) y una lista de numeros (constantes enteras y flotantes), la función getPenultimatePosition devolverá el valor de la lista a traves de la posición dada. Si el valor del pivote es menor a 1 (uno) o excede la cantidad de elementos, devuelve cero (0).

**Ejemplo:**
```
x = getPenultimatePosition(3; [3,8.2,2,55.5,7,252]) // x = 2
```

### sumaLosUltimos
Dado 2 parametros, un pivote (cte entero) y una lista de numeros (constantes enteras y flotantes), la función sumaLosUltimos devolverá la sumatoria d elementos a partir del valor del pivote. Si el valor del pivote es menor a 1 (uno) o excede la cantidad de elementos, devuelve cero (0).

**Ejemplo:**
```
x = sumaLosUltimos(4; [28,13.5,4,5.5,17,52])  // x = 74.5
```

### triangulo
La función especial triángulo recibe tres parámetros que pueden ser constantes, variables u operaciones aritméticas y retorna una constante string que será "equilátero", "isóceles" o "escaleno". Cada parámetro representa el lado de un tríangulo y si los tres lados son de igual medida, se llaman equiláteros; si los dos lados son de igual medida, se llaman isósceles y si los tres lados son de diferente medida, se llaman escalenos.
```
x = 2, z = 3 // asignaciones a fines de entender los ejemplos
y = triangulo(x, 1+1, x)  // y = "equilatero"
y = triangulo(0, 1/x, 0) // y = "isóceles"
y = triangulo((32+5+x)*z, 1/x, 100) // y = "escaleno"
```

### subListString
La funcion especial subListString devuelve un string que se forma a partir de un indice especificado en la lista (inclusive) e incluye un contador respecto a cuantas veces aparecio el valor del índice en la palabra formada.
```
x = 3 // asignaciones a fines de entender los ejemplos
y = subListString(x, [1, 2, h, x, l, l, o])  // y = "hxllo - 0"
y = subListString(4, [1, 2, 3, 100, 150, 500, 4, 5002, 4) // y = "150500450024 - 2"
```
