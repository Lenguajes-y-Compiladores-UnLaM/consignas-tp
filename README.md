# Trabajo Práctico Integrador de Lenguajes y Compiladores

<p align="center">
  <img src="images/unlam-logo.jpg" alt="Logo UNLaM" width="300">
</p>

## Índice

- [📋 Consideraciones Generales](#-consideraciones-generales)
  - [Lineamientos para la formación de grupos](#lineamientos-para-la-formación-de-grupos)
  - [Asignación profesor, lenguaje, temas especiales y notación intermedia](#asignación-profesor-lenguaje-temas-especiales-y-notación-intermedia)
- [📧 Entregas](#-entregas)
  - [1️⃣ Primera Entrega - AL y AS (auto-corrección)](#1️⃣-primera-entrega---al-y-as-auto-corrección)
  - [2️⃣ Segunda Entrega - GCI](#2️⃣-segunda-entrega---gci)
  - [3️⃣ Entrega Final - Assembler y binario](#3️⃣-entrega-final---assembler-y-binario)
  - [👥 Coloquio Grupal](#-coloquio-grupal)
- [📚 Temas comunes](#-temas-comunes)
- [⭐ Temas especiales](#-temas-especiales)
- [🛠️ ¿Qué templates puedo usar para llevar a cabo el Trabajo Práctico?](#️-qué-templates-puedo-usar-para-llevar-a-cabo-el-trabajo-práctico)
  - [📊 Comparación de herramientas de parsing](#-comparación-de-herramientas-de-parsing)
  - [🧠 Notas rápidas (importantes)](#-notas-rápidas-importantes)

## 📋 Consideraciones Generales

### Lineamientos para la formación de grupos:
* Hasta un máximo de 5 integrantes, sin excepciones.
* Los integrantes deben pertenecer a una misma comisión.
* La cátedra creará un repositorio privado por cada grupo, permitiendoles acceder al mismo con el rol de administrador para que puedan desarrollar, subir nuevos archivos o hacer modificaciones.

**Nota**: Deberán anotarse en [hoja de grupos de la planilla de grupos 2C 2026](https://docs.google.com/spreadsheets/d/14Mvx8ekXms5qHZvtEQEENNJSpEQ_4V9X2OVyU8zDltg/edit?gid=0#gid=0) con un mail válido de github para cada integrante.

### Asignación profesor, lenguaje, temas especiales y notación intermedia

En cada repositorio se creara un archivo YAML llamado `configuracion_lyc.yml` donde tendrán la siguiente información:
```yaml
grupo: N
lenguaje: LX_nombre
integrantes:
  - Ap_Nom
  - Ap_Nom
  - Ap_Nom
temas_especiales:
  - TEX
  - TEX
notacion: NOTX
profesor: PROFX
```

## 📧 Entregas:

### 1️⃣ Primera Entrega - AL y AS (auto-corrección):

**Objetivo**: Realizar un analizador léxico y sintáctico con las herramientas provistas. 

El programa ejecutable deberá mostrar por pantalla las reglas sintácticas que va analizando el parser en base a un archivo de entrada (test.txt). 

Las impresiones deben ser claras. Las reglas que no realizan ninguna acción no deben generar salida.

La entrega 1.0.0 incluirá:
- El archivo lexer con la definición de todos los componentes léxicos.
- El archivo parser con la definición de la gramática del lenguaje y la lógica de generación de la tabla de símbolos.
- El archivo `symbol-table.txt` deberá contener la lista de variables y constantes con sus respectivos atributos. El archivo `symbol-table.txt` debe ser autogenerado cada vez que se ejecute el compilador.
- El archivo de pruebas `test.txt` que contendrá ejemplos de todos los temas comunes y especiales (selecciones, ciclos anidados, temas especiales, verificación de cotas para las constantes, chequeo de longitud de los nombres de los identificadores, comentarios, etc).
- Dicho archivo debe ser único, general y abarcativo (no enviar diferentes escenarios de prueba en diferentes archivos).
- Las líneas de código que ejemplifican casos de error en tiempo de compilación deberán presentarse en el documento de manera comentadas y acompañadas de un mensaje descriptivo.
- Cree el tag 1.0.0 en su repositorio dónde se generará un zip con los archivos necesarios.

✅ **Criterio de aprobación:**
- Todos los casos de prueba presentes en el archivo `correccion\E1_autocorreccion.md` deben estar contemplados.
- La tabla de símbolos debe generarse respetando la estructura descrita en la consigna.

En la raíz de su repositorio encontrará un archivo dentro de la carpeta corrección `correccion\E1_autocorreccion.md` dónde el mismo equipo podrá corroborar si la entrega está aprobada o no.

📅 **Fecha de entrega**: auto-corrección por el equipo. 

_Recomendamos que esta primer entrega la tengan realizada una semana antes del primer parcial para evacuar todas las dudas que puedan surgir en la auto-corrección. De necesitar una validación docente se puede notificar enviando un mail a lenguajesycompiladores@gmail.com asunto NombredelDocente_GrupoXX (Ej Daniel_Grupo03, Eleazar_Grupo02, Etc) pero no es obligatorio._

### 2️⃣ Segunda Entrega - GCI:

**Objetivo:** Realizar un generador de código intermedio utilizando el archivo parser generado en la primera entrega. El programa ejecutable deberá procesar el archivo de entrada (test.txt) y devolver el código intermedio del mismo junto con la tabla de símbolos.

La entrega 2.0.0 incluirá:
- Todo lo realizado en la primer entrega.
- Actualización del archivo `symbol-table.txt` con sus atributos.
- El archivo `intermediate-code.txt` que contiene el código intermedio generado. El archivo intermediate-code.txt debe ser autogenerado cada vez que se ejecute el compilador.
- Se puede usar todas las primitivas y estructuras que se crean necesarias para el desarrollo del código intermedio junto con las validaciones semánticas correspondientes.
- Cree el tag 2.0.0 en su repositorio dónde se generará un zip con los archivos necesarios.

✅ **Criterio de aprobación:**
- El código intermedio debe generarse correctamente.
- Todos los casos de prueba presentes en el archivo `correccion\E2_correccion.md` deben estar contemplados.

Envíe el enlace del tag generado enviado a: lenguajesycompiladores@gmail.com

Asunto: NombredelDocente_GrupoXX (Ej: Daniel_Grupo03, Eleazar_Grupo02)

📅 **Fecha de entrega**: semana del 19/10/2026. 

### 3️⃣ Entrega Final - Assembler y binario

**Objetivo**: Realizar un compilador utilizando el archivo generado en la segunda entrega. 
El programa ejecutable deberá procesar el archivo de entrada (test.txt), compilarlo y ejecutarlo.

La entrega 3.0.0 incluirá:
- Todo lo realizado en la primer y segunda entrega.
- El archivo assembler que se llamará `final.asm`
- El archivo por lotes `run.bat` (o equivalente según el sistema operativo que desee utilizar) que incluirá las sentencias necesarias para compilar con TASM y TLINK el archivo `final.asm` generado por el compilador
- Cree el tag 3.0.0 en su repositorio dónde se generará un zip con los archivos necesarios.

✅ **Criterio de aprobación:**
- El código assembler debe generarse correctamente y generar el binario final.
- El programa de prueba debe ejecutarse sin problemas en DOSBox o en GUI Turbo Assembler.

📅 **Fecha de entrega**: el día del coloquio, lunes 9/11/2026 o martes 10/11/2026.

### 👥 Coloquio Grupal

Lunes 9/11/2026 y Martes 10/11/2026 de forma virtual.

## 📚 Temas comunes

Los temas comunes se describen [aquí](Temas%20Comunes.md)

## ⭐ Temas especiales

En la rama `main` se añadirá una carpeta llamada temas con dos archivos markdown.

```
proyecto/
├── ...
└── temas/
    ├── TE1_nombre.md
    └── TE2_nombre.md
```

## 🛠️ ¿Qué templates puedo usar para llevar a cabo el Trabajo Práctico?

La cátedra provee diversas plantillas para desarrollar el compilador. Estas plantillas son completas: proveen casos de prueba, gestión de dependencias y uso de herramientas modernas. Sin embargo, estamos abierto al uso de otras tecnologías. El uso de otras herramientas requerirá un trabajo de investigación adicional al grupo/equipo que así lo decida, y mayor autonomía en las particularidades de implementación. De igual forma, el esfuerzo de investigación de otras herramientas será tenido en cuenta positivamente en la evaluación definitiva.

Dejamos a continuación, las plantillas disponibles:

[Plantilla para TP Integrador usando JFlex y JCup - Java](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-java)

[Plantilla para TP Integrador usando JFlex y JCup - Kotlin](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-kotlin)

[Plantilla para TP Integrador usando Flex y Bison - C](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-c)

[Plantilla para TP Integrador usando PLY - Python](https://github.com/Lenguajes-y-Compiladores-UnLaM/compilador-python)

[Plantilla para TP Integrador usando Rflex y Rustemo - Rust](https://github.com/Lenguajes-y-Compiladores-UnLaM/compiler-rust)

### 📊 Comparación de herramientas de parsing

| Herramienta | Lenguaje | Tipo de Parsing | Documentación |
|------------|---------|----------------|--------------|
| GNU Bison | C / C++ | LALR(1), GLR | https://www.gnu.org/software/bison/ |
| Java CUP | Java | LALR(1) | http://www2.cs.tum.edu/projects/cup/ |
| PLY (Python Lex-Yacc) | Python | LALR(1) | https://www.dabeaz.com/ply/ |
| Rustemo | Rust | LR (LALR(1), GLR opcional) | https://github.com/igordejanovic/rustemo |
