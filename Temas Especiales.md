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

### binaryCount
La funcion especial binaryCount cuenta la cantidad de numeros binarios en una lista y devuelve un entero corresponde a esa cantidad
```
x = 3 // asignaciones a fines de entender los ejemplos
y = binaryCount([110,1,0,5,x,10101100,-1])  // y = 4
```
