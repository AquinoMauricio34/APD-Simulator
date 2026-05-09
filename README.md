# APD-Simulator
## Instrucciones de Programa
- Por cada línea se escribe UNA intrucción para UN estado.
- El nombre de los estados es un numero si o si.
- Las instrucciones pueden ser scan, write y read.
- El formato de una instruccion es: <estado>] <tipo_instruccion> (<simbolo>,<estado_sucesor>) (<simbolo>,<estado_sucesor>) ...
- Ejemplo: "1] scan (a,2) (b,3) (c,4)", "2] write (a,1)", "3] write (b,1)", "4] scan (a,5) (b,6)", "5] read (a,4)", "6] read (b,4)".

## Estado(s) inicial(es)
- ¿Qué inserta? -> el o los (mínimo un estado) estado(s) inicial(es) de la máquina.
- Formato: <estado>,<estado>,...

## Estado(s) final(es)
- ¿Qué inserta? -> el o los (mínimo un estado) estado(s) final(es) de la máquina.
- Formato: <estado>,<estado>,...

## Límite de pila (anti-loop infinito)
- Por defecto en 100 por si entra en loop infinito. Esta situación ocurre a veces en APD no determinísticos.
- Si se necesita más pasos incrementar.

## Botón Construir Diagrama
- Construye el diagrama y prepara el programa. Es importante contruir el diagrama si o si antes de realizar la ejecución.

## Modo de Simulación
- Si el diseño es no determinístico, seleccionar "No Determinístico", dejarlo en "Determinístico" es posible pero no tiene sentido.

## Cadena de entrada
- es la cadena w a evaluar para verificar si es aceptada o rechasada.
- no cargar indica al programa que la cadena w = λ (simbolo de vacío).

## Boton Ejecutar
- Realiza la verificación completa saltandose el paso a paso.

## Boton Paso Atrás
- Realiza un retroceso de un paso (transición)

## Boton Paso Adelante
- Realiza un paso (transición)

## Boton Reiniciar
- Reinicia el programa hasta antes de la ejecución

## Configuración Actual
- Indica el (q,ω,σ) actual, es decir, en qué estado q se encuentra, qué acción se realiza, la entrada y el simbolo apuntado, la cantidad de simbolos faltantes a escanear.

## Pila σ
- Pila en donde se guardan los simbolos que se requeren para realizar la comparación.

## Historial de Pasos
- Lista de pasos que se realizan para realizar la verificación de w.
- Cada linea representa un paso y contiene: <acción>(<simbolo>) -> <estado> | <string_sin_escanear> | <string_pila>
- Linea 1: inicio -> q1 | φ=aacaa | σ=[λ] (la configucación de inicio. Formalmente (q1,λ,λ))
- Linea 2: scan(a) -> q2 | φ=acaa | σ=[λ] (en el string w se apunta al primer simbolo y se realiza transición a q2. Formalmente (q2,a,λ))
- Linea 3: write(a) -> q1 | φ=acaa | σ=[a] (el simbolo escaneado de w se agrega al tope de la pila y se realiza transición a q1. Formalmente (q1,a,a))
