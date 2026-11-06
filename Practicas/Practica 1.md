# Práctica 1 · Conceptos fundamentales

## A. Ejercicios de ProsKell

1. **1.3** `promedio`: recibe dos números y devuelve su promedio.
2. **1.4** `decenas`: recibe un número y devuelve cuántas decenas completas tiene.
3. **1.6** `esCero`: `True` solo si el número es igual a 0.
4. **1.7** `esDigito`: `True` solo si el número está entre 0 y 9.
5. **1.9** `esVocalA :: Char -> Bool`.
6. **1.11** `vocales`, la lista de las cinco vocales, con su tipo.
7. **1.12** `resto`, con `mod` escrito como operador.
8. **1.13** `segundo :: a -> b -> b`.

## B. Ejercicios sobre las diapositivas

**P1.1 · Reducciones.** Con el contexto `doble x = 2 * x`, `cuadrado x = x * x` y `primero (x, y) = x`, reducir paso a paso con lazy y con eager:

- `cuadrado (doble (1 + 1))`
- `primero (doble 2, div 1 0)`
- `doble (primero (3, 4))`

¿En cuál solo lazy llega al resultado?

**P1.2 · Tipos.** Escribir el tipo de `('a', 3.5)`, `(True, ("hola", 'x'))`, `[[True], []]`, `["a", "b"]` y `[('a', 1), ('b', 2)]`, usando `Int` y `Float` para los números.

**P1.3 · Función y operador.** Definir `menos x y = x - y` y escribir la resta de 9 menos 4 de cuatro formas: `menos` como función, `menos` como operador, `-` como operador y `(-)` como función.

**P1.4** `celsiusAFahrenheit :: Float -> Float`, con la fórmula `c * 9 / 5 + 32`. Probar 0, 100 y -40.

**P1.5 · Polimórfica.** `intercambiar :: a -> b -> (b, a)`, que recibe dos valores y devuelve el par en orden inverso.

**P1.6 · Alto orden.** `tresVeces :: (a -> a) -> a -> a`, que aplica una función tres veces. Probar `tresVeces doble 1`.
