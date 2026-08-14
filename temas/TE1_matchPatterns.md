# TE1 - matchPatterns

**Selección por patrones con rangos y guardas**

> Inspirado en la expresión `when` de **Kotlin** y en `match` con guardas de **Rust**.

## Descripción

Se deberá implementar una **sentencia de selección por patrones**: una estructura que evalúa una expresión de control **una sola vez** y ejecuta el bloque de la primera rama cuyo patrón la satisfaga.

A diferencia de una selección múltiple clásica, donde cada rama compara contra un valor exacto, aquí cada rama puede expresar **tres formas distintas de patrón**, lo que la vuelve mucho más expresiva que una cadena de IF / ELSE.

## Componentes

La sentencia se compone de:

1. Una **apertura** con la expresión de control entre paréntesis. Puede ser una constante, una variable o una operación aritmética.
2. Una o más **ramas**, cada una con un patrón y un bloque de una o más sentencias. El patrón puede ser de tres tipos:

   | Patrón | Significado | Ejemplo conceptual |
   |---|---|---|
   | **Valor exacto** | La expresión de control es igual a una constante | `is 10` |
   | **Rango** | La expresión de control está comprendida entre dos constantes, ambas inclusive | `in 1 .. 9` |
   | **Guarda** | La expresión de control cumple una condición relacional contra una constante | `is > 100` |

3. Una **rama por defecto opcional**, sin patrón, que se ejecuta cuando ninguna de las anteriores se satisface.
4. Un **cierre** de la estructura.

## Reglas de funcionamiento

- La expresión de control se evalúa **una sola vez**, al inicio de la sentencia.
- Las ramas se evalúan **en orden de aparición**. Al encontrar la primera que se satisface se ejecuta su bloque y se sale de la estructura: no se evalúan las ramas siguientes.
- Como los patrones pueden solaparse (por ejemplo, un rango `1 .. 9` y una guarda `> 5`), el orden de las ramas es significativo y forma parte de la semántica.
- En un patrón de rango, el límite inferior debe ser menor o igual al superior, y ambos extremos están **incluidos**.
- En un patrón de guarda, el operador relacional puede ser cualquiera de los definidos en los temas comunes.
- Si ninguna rama se satisface y existe rama por defecto, se ejecuta su bloque. Si no existe, la sentencia no produce ningún efecto.
- La estructura debe poder anidarse: dentro de una rama puede haber un IF, un WHILE u otra selección por patrones.

## Validaciones

| Validación | Momento |
|---|---|
| La estructura debe tener al menos una rama | Sintáctico |
| Los valores de los patrones deben ser constantes, no variables ni expresiones | Sintáctico |
| La rama por defecto no puede repetirse ni aparecer antes de otra rama | Sintáctico |
| El tipo de los patrones debe coincidir con el tipo de la expresión de control | Semántico |
| En un patrón de rango, el límite inferior debe ser menor o igual al superior | Semántico |
| No puede haber dos ramas con el mismo patrón de valor exacto | Semántico |

## Adaptación al lenguaje asignado

El tema es **independiente de la sintaxis concreta**. Cada grupo debe expresarlo con los delimitadores, palabras reservadas y estilo de bloques que corresponden a su lenguaje, tal como están definidos en [Temas Comunes](../Temas%20Comunes.md) y en los ejemplos de [lenguajes/](../lenguajes/). A modo orientativo:

| Lenguaje | Apertura | Valor exacto | Rango | Guarda | Por defecto | Cierre |
|---|---|---|---|---|---|---|
| [L1_aho](../lenguajes/L1_aho) | `when (expr)` | `is 10` | `in 1..9` | `is > 100` | `else` | `}` |
| [L2_lam](../lenguajes/L2_lam) | `WHEN (expr) OF` | `IS 10 THEN` | `IN 1 TO 9 THEN` | `IS > 100 THEN` | `OTHERWISE` | `END` |
| [L3_sethi](../lenguajes/L3_sethi) | `WHEN (expr) ->` | `IS 10 ->` | `IN 1 .. 9 ->` | `IS > 100 ->` | `ELSE ->` | `NEHW` |
| [L4_ullman](../lenguajes/L4_ullman) | `MATCH ($expr) :` | `IS 10 :` | `IN 1 .. 9 :` | `IS > 100 :` | `OTHERWISE :` | `ENDMATCH` |

Estas formas son sugerencias: lo que se evalúa es que la estructura respete la semántica descrita y sea coherente con el estilo del lenguaje asignado.

## Ejemplos por lenguaje

### L1_aho

**Ejemplo 1 — Los tres tipos de patrón en una misma estructura**

```
#+ Cada rama usa una forma distinta de patron +#
when (nota)
{
    is 10 { write("Perfecto") }
    in 4..9 { write("Aprobado") }
    is < 4 { write("Desaprobado") }
    else { write("Nota invalida") }
}
```

**Ejemplo 2 — Patrones solapados: gana la primera rama en orden**

```
#+ Con edad = 16 se ejecuta la primera rama, aunque la segunda tambien se cumpla +#
when (edad)
{
    in 0..17 { write("Menor de edad") }
    is > 15 { write("Mayor de 15") }
    else { write("Adulto") }
}
```

**Ejemplo 3 — Selección anidada dentro de un ciclo, con un IF dentro de una rama**

```
#+ La seleccion vive dentro de un while y contiene un if en una de sus ramas +#
while (i < limite)
{
    when (i * 2)
    {
        in 0..5 { write("bajo") }
        is >= 6
        {
            if (i == 4)
            {
                write("caso especial")
            }
            else
            {
                write("alto")
            }
        }
        else { write("otro") }
    }
    i := i + 1
}
```

### L2_lam

**Ejemplo 1 — Los tres tipos de patrón en una misma estructura**

```
<* Cada rama usa una forma distinta de patron *>
WHEN (nota) OF
BEGIN
    IS 10 THEN BEGIN write("Perfecto") ; END
    IN 4 TO 9 THEN BEGIN write("Aprobado") ; END
    IS < 4 THEN BEGIN write("Desaprobado") ; END
    OTHERWISE BEGIN write("Nota invalida") ; END
END
```

**Ejemplo 2 — Patrones solapados: gana la primera rama en orden**

```
<* Con edad = 16 se ejecuta la primera rama, aunque la segunda tambien se cumpla *>
WHEN (edad) OF
BEGIN
    IN 0 TO 17 THEN BEGIN write("Menor de edad") ; END
    IS > 15 THEN BEGIN write("Mayor de 15") ; END
    OTHERWISE BEGIN write("Adulto") ; END
END
```

**Ejemplo 3 — Selección anidada dentro de un ciclo, con un IF dentro de una rama**

```
<* La seleccion vive dentro de un while y contiene un if en una de sus ramas *>
WHILE (i < limite) DO
BEGIN
    WHEN (i * 2) OF
    BEGIN
        IN 0 TO 5 THEN BEGIN write("bajo") ; END
        IS >= 6 THEN
        BEGIN
            IF (i == 4) THEN
            BEGIN
                write("caso especial") ;
            END
            ELSE
            BEGIN
                write("alto") ;
            END
        END
        OTHERWISE BEGIN write("otro") ; END
    END
    i =: i + 1 ;
END
```

### L3_sethi

**Ejemplo 1 — Los tres tipos de patrón en una misma estructura**

```
(: Cada rama usa una forma distinta de patron :)
WHEN (nota) ->
    IS 10 ->
        write("Perfecto")
    IN 4 .. 9 ->
        write("Aprobado")
    IS < 4 ->
        write("Desaprobado")
    ELSE ->
        write("Nota invalida")
NEHW
```

**Ejemplo 2 — Patrones solapados: gana la primera rama en orden**

```
(: Con edad = 16 se ejecuta la primera rama, aunque la segunda tambien se cumpla :)
WHEN (edad) ->
    IN 0 .. 17 ->
        write("Menor de edad")
    IS > 15 ->
        write("Mayor de 15")
    ELSE ->
        write("Adulto")
NEHW
```

**Ejemplo 3 — Selección anidada dentro de un ciclo, con un IF dentro de una rama**

```
(: La seleccion vive dentro de un ciclo y contiene un if en una de sus ramas :)
DO (i < limite) ->
    WHEN (i * 2) ->
        IN 0 .. 5 ->
            write("bajo")
        IS >= 6 ->
            IF (i == 4) ->
                write("caso especial")
            ELSE ->
                write("alto")
            FI
        ELSE ->
            write("otro")
    NEHW
    i <- i + 1
OD
```

### L4_ullman

**Ejemplo 1 — Los tres tipos de patrón en una misma estructura**

```
/% Cada rama usa una forma distinta de patron %/
MATCH ($nota) :
    IS 10 :
        write("Perfecto")
    IN 4 .. 9 :
        write("Aprobado")
    IS < 4 :
        write("Desaprobado")
    OTHERWISE :
        write("Nota invalida")
ENDMATCH
```

**Ejemplo 2 — Patrones solapados: gana la primera rama en orden**

```
/% Con edad = 16 se ejecuta la primera rama, aunque la segunda tambien se cumpla %/
MATCH ($edad) :
    IN 0 .. 17 :
        write("Menor de edad")
    IS > 15 :
        write("Mayor de 15")
    OTHERWISE :
        write("Adulto")
ENDMATCH
```

**Ejemplo 3 — Selección anidada dentro de un ciclo, con un IF dentro de una rama**

```
/% La seleccion vive dentro de un ciclo y contiene un if en una de sus ramas %/
REPEAT ($i < $limite) :
    MATCH ($i * 2) :
        IN 0 .. 5 :
            write("bajo")
        IS >= 6 :
            WHEN ($i == 4) :
                write("caso especial")
            OTHERWISE :
                write("alto")
            ENDWHEN
        OTHERWISE :
            write("otro")
    ENDMATCH
    $i + 1 => $i
ENDREPEAT
```

## Casos de prueba obligatorios

El archivo `test.txt` deberá incluir, como mínimo:

- Una selección que use los **tres tipos de patrón** en la misma estructura.
- Una selección con expresión de control compuesta, por ejemplo `a + b * 2`.
- Un caso con **patrones solapados**, donde se demuestre que gana la primera rama en orden de aparición.
- Una selección **con** rama por defecto y otra **sin** rama por defecto.
- Un caso donde ninguna rama se satisface.
- Una selección anidada dentro de un WHILE, y un IF anidado dentro de una rama.
- Comentados, los casos de error: patrón con variable en lugar de constante, rango invertido, patrones de tipo distinto al de la expresión de control y rama por defecto ubicada antes de otra rama.

## Alcance por entrega

- **Entrega 1 (AL y AS)**: reconocimiento léxico de las nuevas palabras reservadas y del operador de rango, y reglas gramaticales que admitan los tres tipos de patrón dentro de una misma estructura.
- **Entrega 2 (GCI)**: la expresión de control se evalúa una sola vez en una variable auxiliar. Cada rama genera sus comparaciones (dos en el caso del rango) y su salto al final de la estructura, respetando el orden de evaluación.
- **Entrega 3 (Assembler)**: traducción a assembler y ejecución correcta del programa de prueba.
