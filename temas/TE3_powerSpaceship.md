# TE3 - powerSpaceship

**Operadores de potencia y de comparación de tres vías**

> Inspirado en el operador de potencia `**` de **Python**, **Ruby** y **Fortran**, y en el operador de comparación de tres vías `<=>` de **C++20**, **Ruby** y **PHP**, apodado *spaceship operator*.

## Descripción

Se deberán incorporar al lenguaje dos **operadores binarios** que se suman a los cuatro de los temas comunes. Cada uno aporta una dificultad distinta al analizador de expresiones:

- **Potencia**: eleva el primer operando a la potencia indicada por el segundo. Su interés está en que es el único operador del lenguaje con **asociatividad a derecha** y con la **precedencia más alta**.
- **Comparación de tres vías**: compara dos expresiones y devuelve `-1`, `0` o `1` según el primer operando sea menor, igual o mayor que el segundo. Su interés está en que **colapsa tres comparaciones en un único valor entero** reutilizable.

## Componentes

Cada operador se ubica entre dos expresiones:

```
<expresión> <operador de potencia> <expresión>
<expresión> <operador de comparación> <expresión>
```

Los operandos pueden ser constantes, variables u otras expresiones que combinen operadores.

## Reglas de funcionamiento

### Operador de potencia

- Tiene la **precedencia más alta** del lenguaje: mayor que la multiplicación y la división, y por lo tanto mucho mayor que la suma y la resta.
- Es **asociativo a derecha**. Esto lo diferencia de todos los demás operadores del lenguaje:

  | Expresión | Se agrupa como | Resultado |
  |---|---|---|
  | `2 ** 3 ** 2` | `2 ** (3 ** 2)` | `512` |
  | `-2 ** 2` | `-(2 ** 2)` | `-4` |
  | `2 * 3 ** 2` | `2 * (3 ** 2)` | `18` |

- El exponente debe ser un **entero mayor o igual a cero**. Con exponente `0` el resultado es `1`, cualquiera sea la base.
- El tipo del resultado es el tipo de la base: si la base es entera el resultado es entero, si es flotante el resultado es flotante.

### Operador de comparación de tres vías

- Tiene la **precedencia más baja** de los operadores aritméticos: menor que la suma y la resta, de modo que `a + 1 <=> b * 2` compara los dos resultados.
- **No es asociativo**: encadenar dos comparaciones en la misma expresión sin paréntesis es un error de sintaxis.
- El resultado es siempre de tipo **entero** y vale exactamente `-1`, `0` o `1`.
- Al ser un valor entero, puede usarse en cualquier expresión, asignarse a una variable o compararse dentro de una condición. Por ejemplo, `(a <=> b) == 0` equivale a preguntar si `a` es igual a `b`.

## Validaciones

| Validación | Momento |
|---|---|
| El exponente debe ser de tipo entero | Semántico |
| El exponente no puede ser una constante negativa | Semántico |
| El resultado de la potencia debe respetar las cotas del tipo de la base | Semántico / Ejecución |
| Los dos operandos de la comparación deben ser del mismo tipo | Semántico |
| Ningún operando de ambos operadores puede ser de tipo string | Semántico |
| El resultado de la comparación sólo puede asignarse a una variable entera | Semántico |
| Encadenar dos comparaciones de tres vías sin paréntesis | Sintáctico |

## Adaptación al lenguaje asignado

El tema es **independiente de la sintaxis concreta**. Cada grupo debe elegir símbolos o palabras reservadas coherentes con el estilo de su lenguaje, definido en [Temas Comunes](../Temas%20Comunes.md) y en los ejemplos de [lenguajes/](../lenguajes/). A modo orientativo:

| Lenguaje | Potencia | Comparación de tres vías |
|---|---|---|
| [L1_aho](../lenguajes/L1_aho) | `a ** b` | `a <=> b` |
| [L2_lam](../lenguajes/L2_lam) | `a ^^ b` | `a <=> b` |
| [L3_sethi](../lenguajes/L3_sethi) | `a ** b` | `a <?> b` |
| [L4_ullman](../lenguajes/L4_ullman) | `$a .POW. $b` | `$a .CMP. $b` |

Estas formas son sugerencias: lo que se evalúa es que los operadores respeten la semántica, la precedencia y la asociatividad descritas, y que sean coherentes con el estilo del lenguaje asignado.

## Ejemplos por lenguaje

### L1_aho

**Ejemplo 1 — Asociatividad a derecha y precedencia de la potencia**

```
#+ La potencia agrupa de derecha a izquierda y tiene la precedencia mas alta +#
x := 2 ** 3 ** 2        #+ 2 ** (3 ** 2) = 512 +#
y := (2 ** 3) ** 2      #+ los parentesis alteran el orden = 64 +#
z := 2 * 3 ** 2         #+ 2 * (3 ** 2) = 18 +#
w := 5 ** 0             #+ exponente cero = 1 +#
```

**Ejemplo 2 — Comparación de tres vías con sus tres resultados**

```
#+ Devuelve -1, 0 o 1 segun la relacion entre los operandos +#
a := 3
b := 7
r := a <=> b            #+ r = -1 porque a es menor que b +#
r := b <=> a            #+ r =  1 porque b es mayor que a +#
r := a <=> 3            #+ r =  0 porque son iguales +#
r := a + 1 <=> b - 3    #+ compara 4 contra 4, r = 0 +#
```

**Ejemplo 3 — Ambos operadores dentro de condiciones**

```
#+ El resultado de la comparacion se usa como cualquier entero +#
if ((a <=> b) == 0)
{
    write("a y b son iguales")
}
while (base ** 2 < limite)
{
    base := base + 1
}
```

### L2_lam

**Ejemplo 1 — Asociatividad a derecha y precedencia de la potencia**

```
<* La potencia agrupa de derecha a izquierda y tiene la precedencia mas alta *>
x =: 2 ^^ 3 ^^ 2 ;      <* 2 ^^ (3 ^^ 2) = 512 *>
y =: (2 ^^ 3) ^^ 2 ;    <* los parentesis alteran el orden = 64 *>
z =: 2 * 3 ^^ 2 ;       <* 2 * (3 ^^ 2) = 18 *>
w =: 5 ^^ 0 ;           <* exponente cero = 1 *>
```

**Ejemplo 2 — Comparación de tres vías con sus tres resultados**

```
<* Devuelve -1, 0 o 1 segun la relacion entre los operandos *>
a =: 3 ;
b =: 7 ;
r =: a <=> b ;          <* r = -1 porque a es menor que b *>
r =: b <=> a ;          <* r =  1 porque b es mayor que a *>
r =: a <=> 3 ;          <* r =  0 porque son iguales *>
r =: a + 1 <=> b - 3 ;  <* compara 4 contra 4, r = 0 *>
```

**Ejemplo 3 — Ambos operadores dentro de condiciones**

```
<* El resultado de la comparacion se usa como cualquier entero *>
IF ((a <=> b) == 0) THEN
BEGIN
    write("a y b son iguales") ;
END

WHILE (base ^^ 2 < limite) DO
BEGIN
    base =: base + 1 ;
END
```

### L3_sethi

**Ejemplo 1 — Asociatividad a derecha y precedencia de la potencia**

```
(: La potencia agrupa de derecha a izquierda y tiene la precedencia mas alta :)
x <- 2 ** 3 ** 2        (: 2 ** (3 ** 2) = 512 :)
y <- (2 ** 3) ** 2      (: los parentesis alteran el orden = 64 :)
z <- 2 * 3 ** 2         (: 2 * (3 ** 2) = 18 :)
w <- 5 ** 0             (: exponente cero = 1 :)
```

**Ejemplo 2 — Comparación de tres vías con sus tres resultados**

```
(: Devuelve -1, 0 o 1 segun la relacion entre los operandos :)
a <- 3
b <- 7
r <- a <?> b            (: r = -1 porque a es menor que b :)
r <- b <?> a            (: r =  1 porque b es mayor que a :)
r <- a <?> 3            (: r =  0 porque son iguales :)
r <- a + 1 <?> b - 3    (: compara 4 contra 4, r = 0 :)
```

**Ejemplo 3 — Ambos operadores dentro de condiciones**

```
(: El resultado de la comparacion se usa como cualquier entero :)
IF ((a <?> b) == 0) ->
    write("a y b son iguales")
FI

DO (base ** 2 < limite) ->
    base <- base + 1
OD
```

### L4_ullman

**Ejemplo 1 — Asociatividad a derecha y precedencia de la potencia**

```
/% La potencia agrupa de derecha a izquierda y tiene la precedencia mas alta %/
2 .POW. 3 .POW. 2 => $x        /% 2 .POW. (3 .POW. 2) = 512 %/
(2 .POW. 3) .POW. 2 => $y      /% los parentesis alteran el orden = 64 %/
2 * 3 .POW. 2 => $z            /% 2 * (3 .POW. 2) = 18 %/
5 .POW. 0 => $w                /% exponente cero = 1 %/
```

**Ejemplo 2 — Comparación de tres vías con sus tres resultados**

```
/% Devuelve -1, 0 o 1 segun la relacion entre los operandos %/
3 => $a
7 => $b
$a .CMP. $b => $r              /% r = -1 porque a es menor que b %/
$b .CMP. $a => $r              /% r =  1 porque b es mayor que a %/
$a .CMP. 3 => $r               /% r =  0 porque son iguales %/
$a + 1 .CMP. $b - 3 => $r      /% compara 4 contra 4, r = 0 %/
```

**Ejemplo 3 — Ambos operadores dentro de condiciones**

```
/% El resultado de la comparacion se usa como cualquier entero %/
WHEN (($a .CMP. $b) == 0) :
    write("a y b son iguales")
ENDWHEN

REPEAT ($base .POW. 2 < $limite) :
    $base + 1 => $base
ENDREPEAT
```

## Casos de prueba obligatorios

El archivo `test.txt` deberá incluir, como mínimo:

- Una potencia simple con base y exponente constantes, y otra con variables.
- Una **potencia encadenada sin paréntesis** (`2 ** 3 ** 2`), que demuestre la asociatividad a derecha con el resultado `512`.
- Una expresión que combine la potencia con multiplicación y suma, demostrando que su precedencia es la más alta.
- Una expresión donde los paréntesis alteren el orden de evaluación de la potencia.
- Una potencia con exponente cero.
- Una comparación de tres vías asignada a una variable, con los tres resultados posibles (`-1`, `0` y `1`).
- Una comparación de tres vías cuyos operandos sean expresiones aritméticas.
- Un uso del resultado de la comparación dentro de la condición de un IF y de un WHILE.
- Comentados, los casos de error: exponente flotante, exponente constante negativo, operandos de distinto tipo en la comparación y dos comparaciones de tres vías encadenadas sin paréntesis.

## Alcance por entrega

- **Entrega 1 (AL y AS)**: reconocimiento léxico de ambos operadores e incorporación a la gramática de expresiones. Es el punto crítico del tema: la potencia obliga a agregar un nivel de precedencia por encima del de multiplicación y a declararlo asociativo a derecha, mientras que la comparación exige un nivel por debajo del de suma y declararlo no asociativo.
- **Entrega 2 (GCI)**: generación del código intermedio de ambas operaciones. La potencia se resuelve con un ciclo de multiplicaciones sucesivas sobre variables auxiliares; la comparación de tres vías, con dos comparaciones y saltos que asignan `-1`, `0` o `1` a una variable auxiliar.
- **Entrega 3 (Assembler)**: traducción a assembler y ejecución correcta del programa de prueba.
