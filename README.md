# APD-Simulator (tambien ATD)
## Instrucciones de Programa
- Por cada línea se escribe UNA instrucción para UN estado.
- El nombre de los estados puede ser cualquiera. Ej: "1]", "S1]", "W]", etc.
- Las instrucciones pueden ser scan, write y read.
- El formato de una instruccion es: <estado>] <tipo_instruccion> (<símbolo>,<estado_sucesor>) (<símbolo>,<estado_sucesor>) ...
- Si un símbolo enviado esta conformado por más de un caracter, por ejemplo "perro", para que el programa lo tome como símbolo único, debe ir entre comillas dobles en la instrucción. Ej: "q1] write ("perro",q2)" y la Pila quedará: (base_pila) | perro. En el caso contrario, si no se agregan las comillas dobles, "perro" será interpretado como 'p', 'e', 'r', 'r', 'o'. Ej: "q1] write (perro,q2)" y la Pila quedará: (base_pila) | p | e | r | r | o. Esto es importante para tener en cuenta al momento de diseñar un aceptor top-down (ATD).
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
- Construye el diagrama y prepara el programa. Es importante construir el diagrama si o si antes de realizar la ejecución.

## Modo de Simulación
- Si el diseño es no determinístico, seleccionar "No Determinístico". Dejarlo en "Determinístico" es posible pero no tiene sentido y no funcionará correctamente.

## Cadena de entrada
- es la cadena w a evaluar para verificar si es aceptada o rechazada.
- no cargar indica al programa que la cadena w = λ (símbolo de vacío).

## Botón Ejecutar
- Realiza la verificación completa saltándose el paso a paso.

## Botón Paso Atrás
- Realiza un retroceso de un paso (transición)

## Botón Paso Adelante
- Realiza un paso (transición)

## Botón Reiniciar
- Reinicia el programa hasta antes de la ejecución

## Configuración Actual
- Indica el (q,ω,σ) actual, es decir, en qué estado q se encuentra (dirá q1,q2,... que son los estados 1, 2, ... que fueron cargados en las instrucciones), qué acción se realiza, la entrada y el símbolo apuntado, la cantidad de símbolos faltantes a escanear.

## Pila σ
- Pila en donde se guardan los símbolos que se requieren para realizar la comparación.

## Historial de Pasos
- Lista de pasos que se realizan para realizar la verificación de w.
- Cada linea representa un paso y contiene: <acción>(<símbolo>) -> <estado> | <string_sin_escanear> | <string_pila>
- Dirá q1,q2,... que son los estados 1, 2, ... que fueron cargados en las instrucciones.
- Ejemplo:
- Linea 1: inicio -> q1 | φ=aacaa | σ=[λ] (la configucación de inicio. Formalmente (q1,λ,λ))
- Linea 2: scan(a) -> q2 | φ=acaa | σ=[λ] (en el string w se apunta al primer símbolo y se realiza transición a q2. Formalmente (q2,a,λ))
- Linea 3: write(a) -> q1 | φ=acaa | σ=[a] (el símbolo escaneado de w se agrega al tope de la pila y se realiza transición a q1. Formalmente (q1,a,a))
- ...
