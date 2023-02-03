# Trabajo Práctico Integrador de Lenguajes y Compiladores

## Consideraciones Generales

Es necesario cumplir con las siguientes consideraciones para evaluar el TP:

1. Cada grupo deberá desarrollar el compilador teniendo en cuenta:
   - Todos los temas comunes.
   - Los temas especiales asignados.
   - El método de generación intermedia asignado.
   - El profesor que le ha sido asignado.

Nota: Los grupos y sus respectivas asignaciones están listados en esta [planilla](https://docs.google.com/spreadsheets/d/1b51HqEtF7h6dG8lfSI5Ww22tkSWS7fM88WEWhBb_QRA/edit?usp=sharing).

2. Cada grupo deberá designar un integrante para el envío de los correos durante todo el cuatrimestre.
3. El TP deberá respetar la estructura provista en esta planilla y ser entregado a través de un enlace al repositorio de GitHub generado.
4. Para generar su propio repositorio GitHub seleccione la opción "Use this template".
5. Se fijan a continuación puntos de control con fechas y requerimientos determinados.


### Primera Entrega:

**Objetivo**: Realizar un analizador léxico y sintáctico con las herramientas provistas. 
El programa ejecutable deberá mostrar por pantalla las reglas sintácticas que va analizando el parser en base a un archivo de entrada (test.txt). 
Las impresiones deben ser claras. Las reglas que no realizan ninguna acción no deben generar salida.

La entrega 1.0.0 incluirá:

- El archivo lexer con la definición de todos los componentes léxicos.
- El archivo parser con la definición de la gramática del lenguaje y la lógica de generación de la tabla de símbolos.
- El archivo symbol-table.txt deberá contener la lista de variables y constantes con sus respectivos atributos.
- El archivo ejecutable lyc-compiler-1.0.0.
- El archivo de pruebas test.txt que contendrá ejemplos de todos los temas comunes y especiales (selecciones, ciclos anidados, temas especiales, verificación de cotas para las constantes, chequeo de longitud de los nombres de los identificadores, comentarios, etc).
  - Dicho archivo debe ser único (no enviar diferentes escenarios de prueba en diferentes archivos).
  - Las líneas de código que ejemplifican casos de error en tiempo de compilación deberán presentarse en el documento de manera comentadas y acompañadas de un mensaje descriptivo.

Nota: Los archivos requeridos ya son provistos/generados por la plantilla, lo que debe agregarse es la implementación de la funcionalidad en ellos.

##### Criterio de aprobación:
- Todos los casos de prueba presentes en la plantilla elegida deberán pasar.
- La tabla de símbolos debe generarse respetando la estructura descrita en la consigna.

Cree el tag 1.0.0 en su repositorio.

Envíe el enlace del tag generado del repositorio generado enviado a: lenguajesycompiladores@gmail.com

Asunto: NombredelDocente_GrupoXX (Ej Daniel_Grupo03, Eleazar_Grupo02, Facundo_Grupo15)

Fecha de entrega: 14/02/2023


### Segunda Entrega:

**Objetivo:** Realizar un generador de código intermedio utilizando el archivo parser generado en la primera entrega. El programa ejecutable deberá procesar el archivo de entrada (prueba.txt) y devolver el código intermedio del mismo junto con la tabla de símbolos.

La entrega 2.0.0 incluirá:

- El archivo lexer con la definición de todos los componentes léxicos.
- El archivo parser con la definición de la gramática del lenguaje y la lógica de generación de la tabla de símbolos.
- El archivo symbol-table.txt deberá contener la lista de variables y constantes con sus respectivos atributos.
- El archivo intermediate-code.txt y que contiene el código intermedio generado.
- El archivo ejecutable lyc-compiler-2.0.0.jar.
- El archivo de pruebas test.txt que contendrá ejemplos de todos los temas comunes y especiales (selecciones, ciclos anidados, temas especiales, verificación de cotas para las constantes, chequeo de longitud de los nombres de los identificadores, comentarios, etc).
    - Dicho archivo debe ser único (no enviar diferentes escenarios de prueba en diferentes archivos).
    - Las líneas de código que ejemplifican casos de error en tiempo de compilación deberán presentarse en el documento de manera comentadas y acompañadas de un mensaje descriptivo.

Nota: Los archivos requeridos ya son provistos/generados por la plantilla, lo que debe agregarse es la implementación de la funcionalidad en ellos.

##### Criterio de aprobación:
- El código intermedio debe generarse correctamente.
- Deben agregarse validaciones semánticas (Por ej: validación de tipos en asignación, variable ya declarada, etc.)

Cree el tag 2.0.0 en su repositorio.

Envíe el enlace del tag generado enviado a: lenguajesycompiladores@gmail.com

Asunto: NombredelDocente_GrupoXX    (Ej Daniel_Grupo03, Eleazar_Grupo02)

Fecha de entrega: 24/02/2023

### Entrega final

***Objetivo***: Realizar un compilador utilizando el archivo generado en la segunda entrega. 
El programa ejecutable deberá procesar el archivo de entrada (test.txt), compilarlo y ejecutarlo.

La entrega 3.0.0 incluirá:

- El archivo lexer con la definición de todos los componentes léxicos.
- El archivo parser con la definición de la gramática del lenguaje y la lógica de generación de la tabla de símbolos.
- El archivo symbol-table.txt deberá contener la lista de variables y constantes con sus respectivos atributos.
- El archivo intermediate-code.txt y que contiene el código intermedio generado.
- El archivo ejecutable lyc-compiler-3.0.0.
- El archivo de pruebas test.txt que contendrá ejemplos de todos los temas comunes y especiales (selecciones, ciclos anidados, temas especiales, verificación de cotas para las constantes, chequeo de longitud de los nombres de los identificadores, comentarios, etc).
    - Dicho archivo debe ser único (no enviar diferentes escenarios de prueba en diferentes archivos).
    - Las líneas de código que ejemplifican casos de error en tiempo de compilación deberán presentarse en el documento de manera comentadas y acompañadas de un mensaje descriptivo.
- El archivo assembler que se llamará final.asm
- El archivo por lotes run.bat que incluirá las sentencias necesarias para compilar con TASM y TLINK el archivo final.asm generado por el compilador

Nota: Los archivos requeridos ya son provistos/generados por la plantilla, lo que debe agregarse es la implementación de la funcionalidad en ellos.

##### Criterio de aprobación:
- El código assembler debe generarse correctamente.
- El programa de prueba debe ejecutarse sin problemas en DOSBox.

Cree el tag 3.0.0 en su repositorio.

Envíe el enlace del tag generado enviado a: lenguajesycompiladores@gmail.com

Asunto: NombredelDocente_GrupoXX    (Ej Daniel_Grupo03, Eleazar_Grupo02)

Fecha de entrega: 02/03/2023


## Temas comunes

Los temas comunes se describen [aquí](Temas%20Comunes.md)

## Temas especiales

Los temas especiales se describen [aquí](Temas%20Especiales.md)


## ¿Qué herramientas puedo usar para el Trabajo Práctico?

La cátedra provee plantillas para desarrollar el TP principalmente en Java o Kotlin.
Estas plantillas son completas: proveen casos de prueba, gestión de dependencias y uso de herramientas modernas.
Sin embargo, estamos abierto al uso de otras tecnologías.
El uso de otras herramientas requerirá un trabajo de investigación adicional al grupo/equipo que así lo decida, y mayor
autonomía en las particularidades de implementación (dado que los docentes no conocemos todas las herramientas y no podremos dar soporte
a cada una de ellas).

De igual forma, el esfuerzo de investigación de otras herramientas será tenido en cuenta positivamente en la evaluación definitiva.

Dejamos a continuación, las plantillas disponibles:


[Plantilla para TP Integrador usando JFlex y JCup - Java](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-java)

[Plantilla para TP Integrador usando JFlex y JCup - Kotlin](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-kotlin)

[Plantilla para TP Integrador usando Flex y Bison - C](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-c)



