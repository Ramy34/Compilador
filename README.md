# Compilador (nqcc)

Este proyecto fue desarrollado para la materia de Compiladores de la Facultad de Ingeniería durante el semestre 2019-1. Su objetivo es implementar un compilador básico utilizando [ReasonML](https://reasonml.github.io/) y compilándolo a JavaScript mediante BuckleScript.

## Características

El compilador implementa fases de análisis léxico y sintáctico para un subconjunto de un lenguaje estilo C. A través de un analizador de descenso recursivo, el compilador es capaz de interpretar:

- **Declaración de Funciones:** Estructuras básicas que retornan enteros (ej. `int main() { ... }`).
- **Sentencias:** Manejo y validación de la palabra reservada `return`.
- **Expresiones Matemáticas y Lógicas:**
  - **Operadores Binarios:** Suma, Multiplicación, División.
  - **Operadores Unarios:** Negación matemática (`-`), Negación de bits (`~`) y Negación lógica (`!`).
  - Respeto de la precedencia de operadores dividiendo la gramática en *Expresiones*, *Términos* y *Factores*.
- **Manejo de Errores:** Incluye detección de errores de sintaxis (falta de punto y coma, paréntesis o llaves sin cerrar, identificadores inválidos, etc.).

## Estructura del Proyecto

- `bsconfig.json`: Archivo de configuración de BuckleScript, define las reglas de construcción y la compilación del código hacia CommonJS.
- `src/`: Carpeta con el código fuente y los archivos generados.
  - `Ast`: Define la estructura del Árbol de Sintaxis Abstracta (AST) y funciones para validar y extraer partes estructurales del código como `prog`, `fun_decl`, `statement`, `exp`, `termino`, y `factor`.
  - `Parser`: Contiene el analizador sintáctico. Toma una lista de tokens generada previamente y la convierte en la estructura del AST o reporta errores sintácticos.
  - `Token`: Maneja la definición y las extracciones de los tokens identificados (referenciado internamente por el parser).

## Tecnologías Utilizadas

- **ReasonML** (Lenguaje principal)
- **BuckleScript / bs-platform** (Herramienta de compilación hacia JavaScript)

> *Nota:* Los archivos `.bs.js` son el resultado de la compilación de BuckleScript sobre los archivos fuente originales escritos en ReasonML.
