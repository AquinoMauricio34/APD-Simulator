# APD-Simulator
## Instrucciones de Programa
- Por cada línea se escribe UNA intrucción para UN estado.
- El nombre de los estados es un numero si o si.
- Las instrucciones pueden ser scan, write y read.
- El formato de una instruccion es: <estado>] <tipo_instruccion> (<simbolo>,<estado_sucesor>) (<simbolo>,<estado_sucesor>) ...
- Ejemplo
-   1] scan (a,2) (b,3) (c,4)
-   2] write (a,1)
-   3] write (b,1)
-   4] scan (a,5) (b,6)
-   5] read (a,4)
-   6] read (b,4)
