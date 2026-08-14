# TE4 - aggregate

**Función de agregación sobre lista de expresiones**

> Inspirado en las funciones de agregación `SUM`, `MIN`, `MAX`, `AVG` y `COUNT` de **SQL**, y en las operaciones `sumOf`, `minOf`, `maxOf` y `average` de **Kotlin** y **Python**.

## Descripción

Se deberá implementar una **función propia del lenguaje** que reduzca una lista de expresiones a un único valor, según la **operación de agregación** que se le indique como primer parámetro.

Lo que distingue a este tema de una función común es que el primer parámetro no es un valor, sino una **palabra reservada que selecciona el comportamiento**. Una sola regla gramatical debe resolver cinco operaciones distintas, cada una con su propio tipo de resultado.

## Componentes

La función se compone de:

1. Un **identificador** de la función, que es palabra reservada del lenguaje.
2. Un **selector de operación**, que es una de las cinco palabras reservadas de la tabla siguiente.
3. Un **separador** entre el selector y la lista.
4. Una **lista de expresiones**, delimitada y con sus elementos separados entre sí. Cada elemento puede ser una constante, una variable o una operación aritmética completa.

## Operaciones de agregación

| Selector | Devuelve | Tipo del resultado |
|---|---|---|
| **SUM** | La suma de todos los elementos | El de mayor rango entre los elementos |
| **MIN** | El menor de los elementos | El de mayor rango entre los elementos |
| **MAX** | El mayor de los elementos | El de mayor rango entre los elementos |
| **AVG** | El promedio de los elementos | Siempre flotante |
| **COUNT** | La cantidad de elementos de la lista | Siempre entero |

"El de mayor rango" significa que si todos los elementos son enteros el resultado es entero, pero si al menos uno es flotante el resultado es flotante.

## Reglas de funcionamiento

- La lista debe admitir una **cantidad indefinida de elementos**, con un mínimo de uno. No hay un máximo fijo.
- Cada elemento se evalúa **una sola vez**, en orden de aparición, antes de aplicarse la operación.
- **COUNT** cuenta los elementos escritos en la lista, sin evaluar sus valores: `COUNT` sobre una lista de tres elementos devuelve `3` aunque los tres valgan lo mismo.
- **AVG** devuelve siempre un valor flotante, incluso si todos los elementos son enteros y la división es exacta.
- El resultado **puede usarse en cualquier lugar donde se admita una expresión**: en el lado derecho de una asignación, como operando de una operación aritmética, dentro de una condición de IF o WHILE, o como argumento de la sentencia de salida.
- Las llamadas pueden **anidarse**: un elemento de la lista puede ser a su vez una llamada a la función.

**Ejemplo conceptual**, con `a` valiendo `2` y `b` valiendo `3`:

```
agregar( SUM   , [ a , b * 2 , 4 ] )   -->  12
agregar( MIN   , [ a , b * 2 , 4 ] )   -->  2
agregar( MAX   , [ a , b * 2 , 4 ] )   -->  6
agregar( AVG   , [ a , b * 2 , 4 ] )   -->  4.0
agregar( COUNT , [ a , b * 2 , 4 ] )   -->  3
```

## Validaciones

| Validación | Momento |
|---|---|
| El selector debe ser una de las cinco palabras reservadas admitidas | Sintáctico |
| La lista debe tener al menos un elemento | Sintáctico |
| Todas las variables usadas en la lista deben estar declaradas | Semántico |
| No se admiten elementos de tipo string en ninguna de las operaciones | Semántico |
| El resultado de **AVG** no puede asignarse a una variable entera | Semántico |
| El resultado de **COUNT** no puede asignarse a una variable de tipo string | Semántico |
| El resultado de **SUM** debe respetar las cotas del tipo resultante | Semántico / Ejecución |

## Adaptación al lenguaje asignado

El tema es **independiente de la sintaxis concreta**. Cada grupo debe elegir el nombre de la función, el delimitador de la lista y el separador entre parámetros de forma coherente con el estilo de su lenguaje, definido en [Temas Comunes](../Temas%20Comunes.md) y en los ejemplos de [lenguajes/](../lenguajes/). A modo orientativo:

| Lenguaje | Forma sugerida |
|---|---|
| [L1_aho](../lenguajes/L1_aho) | `agg(SUM, [a, b * 2, 4])` |
| [L2_lam](../lenguajes/L2_lam) | `AGG(SUM : [a, b * 2, 4])` |
| [L3_sethi](../lenguajes/L3_sethi) | `agg(SUM ; <a, b * 2, 4>)` |
| [L4_ullman](../lenguajes/L4_ullman) | `AGGREGATE(SUM, [$a, $b * 2, 4])` |

Estas formas son sugerencias: lo que se evalúa es que la función respete la semántica descrita y sea coherente con el estilo del lenguaje asignado.

## Ejemplos por lenguaje

### L1_aho

**Ejemplo 1 — Las cinco operaciones sobre la misma lista**

```
#+ Con a = 2 y b = 3, la lista vale [2, 6, 4] +#
total := agg(SUM, [a, b * 2, 4])        #+ 12 +#
menor := agg(MIN, [a, b * 2, 4])        #+ 2 +#
mayor := agg(MAX, [a, b * 2, 4])        #+ 6 +#
media := agg(AVG, [a, b * 2, 4])        #+ 4.0 +#
cant := agg(COUNT, [a, b * 2, 4])       #+ 3 +#
```

**Ejemplo 2 — Tipos del resultado según los elementos**

```
#+ AVG siempre devuelve flotante, aunque los elementos sean enteros +#
media := agg(AVG, [1, 2, 4])            #+ 2.33 +#
total := agg(SUM, [1, 2.5, 3])          #+ 6.5 porque hay un elemento flotante +#
entero := agg(SUM, [1, 2, 3])           #+ 6, todos enteros +#
unico := agg(MAX, [x])                  #+ lista de un solo elemento +#
```

**Ejemplo 3 — Anidamiento y uso dentro de condiciones**

```
#+ Una llamada puede ser elemento de la lista de otra +#
combinado := agg(SUM, [agg(MAX, [a, b]), agg(MIN, [c, d]), 10])

if (agg(COUNT, [a, b, c]) > 2)
{
    write(combinado)
}

while (agg(SUM, [i, j]) < limite)
{
    i := i + 1
}
```

### L2_lam

**Ejemplo 1 — Las cinco operaciones sobre la misma lista**

```
<* Con a = 2 y b = 3, la lista vale [2, 6, 4] *>
total =: AGG(SUM : [a, b * 2, 4]) ;         <* 12 *>
menor =: AGG(MIN : [a, b * 2, 4]) ;         <* 2 *>
mayor =: AGG(MAX : [a, b * 2, 4]) ;         <* 6 *>
media =: AGG(AVG : [a, b * 2, 4]) ;         <* 4.0 *>
cant =: AGG(COUNT : [a, b * 2, 4]) ;        <* 3 *>
```

**Ejemplo 2 — Tipos del resultado según los elementos**

```
<* AVG siempre devuelve flotante, aunque los elementos sean enteros *>
media =: AGG(AVG : [1, 2, 4]) ;             <* 2.33 *>
total =: AGG(SUM : [1, 2.5, 3]) ;           <* 6.5 porque hay un elemento flotante *>
entero =: AGG(SUM : [1, 2, 3]) ;            <* 6, todos enteros *>
unico =: AGG(MAX : [x]) ;                   <* lista de un solo elemento *>
```

**Ejemplo 3 — Anidamiento y uso dentro de condiciones**

```
<* Una llamada puede ser elemento de la lista de otra *>
combinado =: AGG(SUM : [AGG(MAX : [a, b]), AGG(MIN : [c, d]), 10]) ;

IF (AGG(COUNT : [a, b, c]) > 2) THEN
BEGIN
    write(combinado) ;
END

WHILE (AGG(SUM : [i, j]) < limite) DO
BEGIN
    i =: i + 1 ;
END
```

### L3_sethi

**Ejemplo 1 — Las cinco operaciones sobre la misma lista**

```
(: Con a = 2 y b = 3, la lista vale <2, 6, 4> :)
total <- agg(SUM ; <a, b * 2, 4>)           (: 12 :)
menor <- agg(MIN ; <a, b * 2, 4>)           (: 2 :)
mayor <- agg(MAX ; <a, b * 2, 4>)           (: 6 :)
media <- agg(AVG ; <a, b * 2, 4>)           (: 4.0 :)
cant <- agg(COUNT ; <a, b * 2, 4>)          (: 3 :)
```

**Ejemplo 2 — Tipos del resultado según los elementos**

```
(: AVG siempre devuelve flotante, aunque los elementos sean enteros :)
media <- agg(AVG ; <1, 2, 4>)               (: 2.33 :)
total <- agg(SUM ; <1, 2.5, 3>)             (: 6.5 porque hay un elemento flotante :)
entero <- agg(SUM ; <1, 2, 3>)              (: 6, todos enteros :)
unico <- agg(MAX ; <x>)                     (: lista de un solo elemento :)
```

**Ejemplo 3 — Anidamiento y uso dentro de condiciones**

```
(: Una llamada puede ser elemento de la lista de otra :)
combinado <- agg(SUM ; <agg(MAX ; <a, b>), agg(MIN ; <c, d>), 10>)

IF (agg(COUNT ; <a, b, c>) > 2) ->
    write(combinado)
FI

DO (agg(SUM ; <i, j>) < limite) ->
    i <- i + 1
OD
```

### L4_ullman

**Ejemplo 1 — Las cinco operaciones sobre la misma lista**

```
/% Con a = 2 y b = 3, la lista vale [2, 6, 4] %/
AGGREGATE(SUM, [$a, $b * 2, 4]) => $total       /% 12 %/
AGGREGATE(MIN, [$a, $b * 2, 4]) => $menor       /% 2 %/
AGGREGATE(MAX, [$a, $b * 2, 4]) => $mayor       /% 6 %/
AGGREGATE(AVG, [$a, $b * 2, 4]) => $media       /% 4.0 %/
AGGREGATE(COUNT, [$a, $b * 2, 4]) => $cant      /% 3 %/
```

**Ejemplo 2 — Tipos del resultado según los elementos**

```
/% AVG siempre devuelve flotante, aunque los elementos sean enteros %/
AGGREGATE(AVG, [1, 2, 4]) => $media             /% 2.33 %/
AGGREGATE(SUM, [1, 2.5, 3]) => $total           /% 6.5 porque hay un elemento flotante %/
AGGREGATE(SUM, [1, 2, 3]) => $entero            /% 6, todos enteros %/
AGGREGATE(MAX, [$x]) => $unico                  /% lista de un solo elemento %/
```

**Ejemplo 3 — Anidamiento y uso dentro de condiciones**

```
/% Una llamada puede ser elemento de la lista de otra %/
AGGREGATE(SUM, [AGGREGATE(MAX, [$a, $b]), AGGREGATE(MIN, [$c, $d]), 10]) => $combinado

WHEN (AGGREGATE(COUNT, [$a, $b, $c]) > 2) :
    write($combinado)
ENDWHEN

REPEAT (AGGREGATE(SUM, [$i, $j]) < $limite) :
    $i + 1 => $i
ENDREPEAT
```

## Casos de prueba obligatorios

El archivo `test.txt` deberá incluir, como mínimo:

- Una llamada por **cada una de las cinco operaciones** de agregación.
- Una lista que contenga expresiones aritméticas, no sólo constantes y variables.
- Una lista con elementos **enteros y flotantes mezclados**, demostrando que el tipo del resultado es flotante.
- Una lista de un solo elemento.
- Un **AVG** cuyo resultado tenga parte decimal y otro cuya división sea exacta, verificando que ambos devuelven flotante.
- Un uso del resultado dentro de una expresión aritmética mayor.
- Un uso del resultado como parte de la condición de un IF y de un WHILE.
- Una llamada anidada dentro de la lista de otra llamada.
- Comentados, los casos de error: selector inexistente, lista vacía, variable no declarada dentro de la lista, elemento de tipo string y asignación del resultado de **AVG** a una variable entera.

## Alcance por entrega

- **Entrega 1 (AL y AS)**: reconocimiento léxico del identificador de la función, de los cinco selectores y de los delimitadores de la lista, con reglas gramaticales que admitan una cantidad indefinida de elementos mediante recursión.
- **Entrega 2 (GCI)**: generación del código intermedio con las variables auxiliares necesarias para acumular el resultado parcial y para almacenar el valor de cada expresión evaluada. Cada selector produce un patrón distinto: acumulación para **SUM**, comparación y reemplazo para **MIN** y **MAX**, acumulación más división final para **AVG**, y una constante conocida en tiempo de compilación para **COUNT**. Se suman aquí las validaciones de tipo y la determinación del tipo del resultado.
- **Entrega 3 (Assembler)**: traducción a assembler y ejecución correcta del programa de prueba.
