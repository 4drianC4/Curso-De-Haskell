# Práctica 3 · Patrones, lambda y currying
## A. Ejercicios de ProsKell que no se hicieron en clase

1. **2.10** `segundo :: (a, b) -> b`.
2. **2.11** `masLejano`: recibe dos pares de enteros y, con @, devuelve el par cuya primera componente es mayor.
3. **3.3** `doble` y `diezMenos` con secciones.
4. **3.5** `sumaPar :: (Int, Int) -> Int` y `sumaPar2 = uncurry (+)`. Comparar su prosa.

## B. Ejercicios sobre las diapositivas

**P3.1 · Patrón @.** Copiar `fecMay` con @ y definir `fecMay4`, la mayor de cuatro fechas, como `fecMay4v1` de la diapositiva. Explicar por qué no hace falta @ en `fecMay4`.

**P3.2 · Emparejamiento** (en papel). Con `y True True = True` y `y _ _ = False`, ¿qué ecuación se usa en `y True False`? ¿Qué pasa con `y True True` si se intercambian las ecuaciones?

**P3.3 · Lambda y currying.** Definir `suma3L = \x -> \y -> \z -> x + y + z` con su tipo, y `incDiez = suma3L 4 6`. ¿Qué tipo tiene `incDiez`?

**P3.4 · Simplificación** (en papel). Simplificar cuando se pueda; si no se puede, decir por qué.

```text
resta x y = (-) x y
f1 x y z = g x y z
f2 x y z = g z y x
f3 x y = g x y y
f4 (x, y) = g x y
```

**P3.5 · Generalidad.** Escribir `f1 x y = x y` y `f2 x = x` en ProsKell. Predecir y luego comprobar después de `λ`: `f1 (*2) 4`, `f2 (*2) 4`, `f1 4`, `f2 4`.

**P3.6 · curry y uncurry.** Copiar `currificar` y `descurrificar` de la lección 3.5. Con `mas x y = x + y`, evaluar `descurrificar mas (3, 4)` y `currificar sumaPar 3 4`.
