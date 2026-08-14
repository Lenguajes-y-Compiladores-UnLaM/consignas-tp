# TE2 - labeledBreak

**Salida anticipada de ciclos con etiquetas**

> Inspirado en el `break`/`continue` **etiquetado** de **Java**, **Kotlin** y **Rust** (`'outer: loop { break 'outer }`).

## Descripción

Se deberán implementar dos sentencias que alteran el flujo normal de un ciclo desde su interior:

- **Corte**: termina inmediatamente la ejecución del ciclo y continúa con la sentencia posterior al mismo.
- **Salto**: abandona la iteración actual y vuelve a evaluar la condición del ciclo para comenzar la siguiente.

La particularidad del tema es que ambas sentencias admiten, de forma **opcional**, una **etiqueta** que indica **sobre qué ciclo actúan**. Esto permite, desde el interior de un ciclo anidado, cortar o saltar el ciclo externo directamente, algo imposible de expresar con las sentencias de los temas comunes.

## Componentes

1. Una **etiqueta de ciclo**: un identificador que precede a la apertura de un WHILE y lo nombra. Es opcional; un ciclo sin etiqueta funciona igual que hasta ahora.
2. La sentencia de **corte**, seguida opcionalmente del nombre de una etiqueta.
3. La sentencia de **salto**, seguida opcionalmente del nombre de una etiqueta.

## Reglas de funcionamiento

- Sin etiqueta, ambas sentencias actúan sobre el **ciclo más interno** que las contiene.
- Con etiqueta, actúan sobre el ciclo nombrado por esa etiqueta, sin importar cuántos niveles de anidamiento haya entre medio.
- El **corte** transfiere el control a la primera sentencia posterior al ciclo afectado. Si el ciclo afectado es externo, se abandonan también todos los ciclos internos.
- El **salto** transfiere el control a la evaluación de la condición del ciclo afectado.
- Ambas sentencias pueden aparecer dentro de un IF o de una selección que esté dentro del ciclo.
- Las etiquetas viven en un espacio de nombres propio: una etiqueta puede llamarse igual que una variable sin generar conflicto.

**Ejemplo conceptual** de por qué la etiqueta importa:

```
externo: mientras (i < 10)
    mientras (j < 10)
        si (a > b)  ->  corte externo     # termina AMBOS ciclos
        si (c > d)  ->  corte             # termina solo el ciclo interno
```

## Validaciones

| Validación | Momento |
|---|---|
| Las sentencias de corte y salto sólo pueden aparecer dentro de un ciclo | Semántico |
| La etiqueta referenciada debe existir y corresponder a un ciclo que contenga a la sentencia | Semántico |
| No puede haber dos ciclos anidados entre sí con la misma etiqueta | Semántico |
| Una etiqueta sólo puede preceder a un ciclo, no a otra sentencia | Sintáctico |
| Debe advertirse el código inalcanzable ubicado inmediatamente después de un corte | Semántico |

## Adaptación al lenguaje asignado

El tema es **independiente de la sintaxis concreta**. Cada grupo debe elegir las palabras reservadas y el marcador de etiqueta de forma coherente con el estilo de su lenguaje, definido en [Temas Comunes](../Temas%20Comunes.md) y en los ejemplos de [lenguajes/](../lenguajes/). A modo orientativo:

| Lenguaje | Etiqueta | Corte | Salto |
|---|---|---|---|
| [L1_aho](../lenguajes/L1_aho) | `externo: while (...)` | `break externo` | `continue externo` |
| [L2_lam](../lenguajes/L2_lam) | `externo : WHILE (...) DO` | `EXIT externo ;` | `SKIP externo ;` |
| [L3_sethi](../lenguajes/L3_sethi) | `externo :: DO (...) ->` | `BREAK externo` | `NEXT externo` |
| [L4_ullman](../lenguajes/L4_ullman) | `#externo REPEAT (...) :` | `LEAVE #externo` | `RESUME #externo` |

Estas formas son sugerencias: lo que se evalúa es que las sentencias respeten la semántica descrita y sean coherentes con el estilo del lenguaje asignado.

## Ejemplos por lenguaje

### L1_aho

**Ejemplo 1 — Corte sin etiqueta: actúa sobre el ciclo más interno**

```
#+ El ciclo termina apenas i llega a 5 +#
i := 0
while (i < 10)
{
    if (i == 5)
    {
        break
    }
    write(i)
    i := i + 1
}
```

**Ejemplo 2 — Corte con etiqueta: termina el ciclo externo desde el interno**

```
#+ Al cumplirse la condicion se abandonan los dos ciclos a la vez +#
i := 0
externo: while (i < 5)
{
    j := 0
    while (j < 5)
    {
        if (i * j > 6)
        {
            break externo
        }
        j := j + 1
    }
    i := i + 1
}
```

**Ejemplo 3 — Salto con etiqueta: continúa el ciclo externo desde el interno**

```
#+ Al saltar con etiqueta se vuelve a evaluar la condicion del ciclo externo +#
i := 0
externo: while (i < 5)
{
    j := 0
    while (j < 5)
    {
        i := i + 1
        if (j == 2)
        {
            continue externo
        }
        write(j)
        j := j + 1
    }
}
```

### L2_lam

**Ejemplo 1 — Corte sin etiqueta: actúa sobre el ciclo más interno**

```
<* El ciclo termina apenas i llega a 5 *>
i =: 0 ;
WHILE (i < 10) DO
BEGIN
    IF (i == 5) THEN
    BEGIN
        EXIT ;
    END
    write(i) ;
    i =: i + 1 ;
END
```

**Ejemplo 2 — Corte con etiqueta: termina el ciclo externo desde el interno**

```
<* Al cumplirse la condicion se abandonan los dos ciclos a la vez *>
i =: 0 ;
externo : WHILE (i < 5) DO
BEGIN
    j =: 0 ;
    WHILE (j < 5) DO
    BEGIN
        IF (i * j > 6) THEN
        BEGIN
            EXIT externo ;
        END
        j =: j + 1 ;
    END
    i =: i + 1 ;
END
```

**Ejemplo 3 — Salto con etiqueta: continúa el ciclo externo desde el interno**

```
<* Al saltar con etiqueta se vuelve a evaluar la condicion del ciclo externo *>
i =: 0 ;
externo : WHILE (i < 5) DO
BEGIN
    j =: 0 ;
    WHILE (j < 5) DO
    BEGIN
        i =: i + 1 ;
        IF (j == 2) THEN
        BEGIN
            SKIP externo ;
        END
        write(j) ;
        j =: j + 1 ;
    END
END
```

### L3_sethi

**Ejemplo 1 — Corte sin etiqueta: actúa sobre el ciclo más interno**

```
(: El ciclo termina apenas i llega a 5 :)
i <- 0
DO (i < 10) ->
    IF (i == 5) ->
        BREAK
    FI
    write(i)
    i <- i + 1
OD
```

**Ejemplo 2 — Corte con etiqueta: termina el ciclo externo desde el interno**

```
(: Al cumplirse la condicion se abandonan los dos ciclos a la vez :)
i <- 0
externo :: DO (i < 5) ->
    j <- 0
    DO (j < 5) ->
        IF (i * j > 6) ->
            BREAK externo
        FI
        j <- j + 1
    OD
    i <- i + 1
OD
```

**Ejemplo 3 — Salto con etiqueta: continúa el ciclo externo desde el interno**

```
(: Al saltar con etiqueta se vuelve a evaluar la condicion del ciclo externo :)
i <- 0
externo :: DO (i < 5) ->
    j <- 0
    DO (j < 5) ->
        i <- i + 1
        IF (j == 2) ->
            NEXT externo
        FI
        write(j)
        j <- j + 1
    OD
OD
```

### L4_ullman

**Ejemplo 1 — Corte sin etiqueta: actúa sobre el ciclo más interno**

```
/% El ciclo termina apenas i llega a 5 %/
0 => $i
REPEAT ($i < 10) :
    WHEN ($i == 5) :
        LEAVE
    ENDWHEN
    write($i)
    $i + 1 => $i
ENDREPEAT
```

**Ejemplo 2 — Corte con etiqueta: termina el ciclo externo desde el interno**

```
/% Al cumplirse la condicion se abandonan los dos ciclos a la vez %/
0 => $i
#externo REPEAT ($i < 5) :
    0 => $j
    REPEAT ($j < 5) :
        WHEN ($i * $j > 6) :
            LEAVE #externo
        ENDWHEN
        $j + 1 => $j
    ENDREPEAT
    $i + 1 => $i
ENDREPEAT
```

**Ejemplo 3 — Salto con etiqueta: continúa el ciclo externo desde el interno**

```
/% Al saltar con etiqueta se vuelve a evaluar la condicion del ciclo externo %/
0 => $i
#externo REPEAT ($i < 5) :
    0 => $j
    REPEAT ($j < 5) :
        $i + 1 => $i
        WHEN ($j == 2) :
            RESUME #externo
        ENDWHEN
        write($j)
        $j + 1 => $j
    ENDREPEAT
ENDREPEAT
```

## Casos de prueba obligatorios

El archivo `test.txt` deberá incluir, como mínimo:

- Un corte **sin** etiqueta dentro de un ciclo simple.
- Un salto **sin** etiqueta dentro de un ciclo simple, demostrando que las sentencias posteriores de esa iteración no se ejecutan.
- Dos ciclos anidados donde un corte **con** etiqueta termine el ciclo externo desde el interno.
- Dos ciclos anidados donde un salto **con** etiqueta continúe el ciclo externo desde el interno.
- Tres niveles de anidamiento, con un corte que actúe sobre el nivel intermedio.
- Un corte ubicado dentro de un IF que está dentro del ciclo.
- Comentados, los casos de error: corte fuera de todo ciclo, etiqueta inexistente, etiqueta de un ciclo que no contiene a la sentencia y dos ciclos anidados con la misma etiqueta.

## Alcance por entrega

- **Entrega 1 (AL y AS)**: reconocimiento léxico de las nuevas palabras reservadas y del marcador de etiqueta, y reglas gramaticales que admitan la etiqueta opcional tanto en la declaración del ciclo como en las sentencias de corte y salto.
- **Entrega 2 (GCI)**: es el núcleo del tema. Requiere mantener una **pila de ciclos abiertos** con la etiqueta y las direcciones de inicio y fin de cada uno, para resolver el destino de cada salto. Los saltos hacia el final del ciclo quedan pendientes de completar hasta conocer esa dirección.
- **Entrega 3 (Assembler)**: traducción a assembler de los saltos generados y ejecución correcta del programa de prueba.
