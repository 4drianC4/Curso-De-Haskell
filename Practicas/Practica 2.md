# Práctica 2 · Definición de funciones

## A. Ejercicios de ProsKell

1. **2.3** `signo` con `if` anidados: -1 si es negativo, 0 si es cero y 1 si es positivo.
2. **2.7** `areaAnillo` con `let … in` en lugar de `where`.

## B. Ejercicios sobre las diapositivas

**P2.1 · Exhaustividad.** La diapositiva define `mayor x y | x > y = x | x < y = y`. Escribirla en ProsKell, encontrar una llamada que dé error y corregirla de dos formas.

**P2.2 · Distinción de casos.** `tipoTriangulo :: Int -> Int -> Int -> String`: recibe los tres lados y devuelve `"equilátero"`, `"isósceles"` o `"escaleno"`. ¿Importa el orden de los casos?

**P2.3 · case anidado.** Definir la función `o :: Bool -> Bool -> Bool` con `case`, como `y` en la lección 2.12.

**P2.4 · Combinación y where.** Definir `m4`, el mayor de 4 números, usando `m3` de la lección 2.6 dentro de un `where`.

**P2.5 · let.** `notaFinal :: Int -> Int -> Int -> Int`: recibe dos notas parciales y la nota del examen; con `let`, calcula el promedio entero de los parciales y devuelve el promedio entero entre ese valor y el examen. Probar `notaFinal 60 80 50`.

**P2.6 · Leer y corregir** (en papel): encontrar el error de cada definición de la diapositiva.

```text
suma :: Int -> Int -> Int
suma x y z = x + y + z

menor x y = case x < y of
  True = x
  _    = y
```
