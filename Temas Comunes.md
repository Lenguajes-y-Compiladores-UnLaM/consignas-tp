## Temas comunes a todos los lenguajes

### Declaración de variables
Todas las variables deberán ser declaradas dentro de un bloque especial para ese fin. El bloque puede estar contenido de diversas formas (palabra reservada o caracter) y siempre se ubica en la cabecera del programa. Existe un solo bloque único de declaración de variables

Pueden existir varias líneas de declaración, incluso utilizando más de una línea para el mismo tipo.

### Tipos de datos

| Tipo | Tamaño | Rango / Detalle |
|---|---|---|
| Float | 32 bits | Separador decimal: punto “.”. Rango aprox.: -3.4028235 × 10³⁸ a 3.4028235 × 10³⁸ |
| Int | 16 bits | Mínimo: -32.768  Máximo: 32.767 |
| String | — | Constantes de hasta 50 caracteres alfanuméricos, limitadas por comillas (“ “), de la forma “XXXX” |

### Asignaciones

Las asignaciones deben ser permitidas, solo en los casos en los que los tipos son compatibles, caso contrario deberá desplegarse un error.

### Operadores

Suma (+), resta (-), multiplicación (*) y división (/).

### Sentencias de control

Selección: IF / IF - ELSE

Iteración: WHILE

### Lectura y escritura

Las salidas y entradas por teclado (en la práctica real pueden venir de distintas fuentes conocidas o desconocidas; ejemplo endpoints, señales, entrada por usuario, etc) se implementarán mediante los comandos `read` y `write`.

### Condiciones

Las condiciones para un constructor de ciclos o de selección pueden ser simples ( a < b ) o múltiples. Las condiciones múltiples pueden ser hasta dos condiciones simples ligadas a través del operador lógico (AND, OR) o una condición simple con el operador lógico NOT.

Comparadores: ==, <, >, <=, >=, !=.

Conectores lógicos: AND, OR, NOT

### Comentarios

Deberán estar delimitados por los caracteres que correspondan al lenguaje y podrán estar anidados en un solo nivel.

Nota: Los comentarios se ignoran, de manera que no generan un componente léxico o token

### Tabla de Símbolos

La tabla de símbolos tiene la capacidad de guardar las variables y constantes con sus atributos.
Los atributos portan información necesaria para operar con constantes, variables, etc.

| NOMBRE | TIPODATO | VALOR | LONGITUD |
|---|---|---|---|
| a1 | Float | — | |
| b1 | Int | — | |
| _variable1 | Cte_String | variable1 | 9 |
| _30.5 | Cte_Float | 30.5 | |
| _0b111 | Cte_Binaria | 7 | |
| _0xF3A1 | Cte_Hexadecimal | 62369 | |

### Equivalencias entre Lenguajes

Todos los lenguajes implementan los mismos temas comunes, pero cada uno define su propia sintaxis concreta. La siguiente tabla resume las diferencias:

| Elemento | L1_aho | L2_lam | L3_sethi | L4_ullman |
|---|---|---|---|---|
| Programa principal | — | `void main () { }` | — | — |
| Comentarios | `#+ ... +#` | `<* ... *>` | `(: ... :)` | `/% ... %/` |
| Bloque de declaración | `init { }` (palabra reservada) | `%{ %}` (caracteres) | `DEF ... FED` (palabra reservada) | `<< >>` (caracteres) |
| Línea de declaración | `a, b : Float` | `Float : a, b ;` (tipo primero) | `a <- 10.5` (sin tipo, se deduce de la constante) | `$a, $b AS Float` (tipo al final) |
| Nombre de variable | `a` | `a` | `a` | `$a` (prefijo obligatorio) |
| Asignación | `a := 10.5` | `a =: 10.5` | `a <- 10.5` | `10.5 => $a` (destino a la derecha) |
| Bloques de sentencias | `{ }` | `BEGIN ... END` | `-> ... FI` / `-> ... OD` | `: ... ENDWHEN` / `: ... ENDREPEAT` |
| Selección | `if (...) { } else { }` | `IF (...) THEN ... ELSE ...` | `IF (...) -> ... ELSE -> ... FI` | `WHEN (...) : ... OTHERWISE : ... ENDWHEN` |
| Iteración | `while (...) { }` | `WHILE (...) DO ...` | `DO (...) -> ... OD` | `REPEAT (...) : ... ENDREPEAT` |
| Fin de sentencia | — | `;` | — | — |

Se mantienen sin cambios en todos los lenguajes: los comandos `read` y `write`, los conectores lógicos `AND`, `OR`, `NOT`, los comparadores (`==`, `<`, `>`, `<=`, `>=`, `!=`), los operadores aritméticos (`+`, `-`, `*`, `/`) y las comillas para las constantes string.

[Ejemplo L1_aho](lenguajes/L1_aho) — [Ejemplo L2_lam](lenguajes/L2_lam) — [Ejemplo L3_sethi](lenguajes/L3_sethi) — [Ejemplo L4_ullman](lenguajes/L4_ullman)
