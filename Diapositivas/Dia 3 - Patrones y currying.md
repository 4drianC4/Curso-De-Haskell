# Día 3
## Patrones, lambda y currying

Lecciones **2.8 a 2.11, 2.13, 2.14 y 3.1 a 3.5**

---

# ¿Qué es un patrón?

La **forma** que sigue el argumento

```haskell
primero (x, y) = x
```

---

# Tipos de patrones

- Constantes
- Comodín
- Estructurales
- @

---

# Patrón constante

```haskell
no :: Bool -> Bool
no True = False
no False = True
```

---

# Patrón constante: dos argumentos

```haskell
y :: Bool -> Bool -> Bool
y True True = True
y True False = False
y False True = False
y False False = False
```

---

# Emparejamiento de patrones

`y False True`

Toma la definición cuyo **parámetro formal** empareja con el **parámetro actual**

---

# Patrón comodín

`_` empareja con **todo**

```haskell
no :: Bool -> Bool
no True = False
no _ = True

y :: Bool -> Bool -> Bool
y True True = True
y _ _ = False
```

---

# Patrón estructural

Fecha mayor de dos

```haskell
fecMay (d1, m1, a1) (d2, m2, a2)
  | a1 > a2   = (d1, m1, a1)
  | a2 > a1   = (d2, m2, a2)
  | m2 > m1   = (d2, m2, a2)
  | m1 > m2   = (d1, m1, a1)
  | d2 > d1   = (d2, m2, a2)
  | otherwise = (d1, m1, a1)
```

---

# Patrón @

Un **alias** para el argumento

```haskell
fecMay f1@(d1,m1,a1) f2@(d2,m2,a2)
  | a1 > a2   = f1
  | a2 > a1   = f2
  | m2 > m1   = f2
  | m1 > m2   = f1
  | d2 > d1   = f2
  | otherwise = f1
```

---

# Expresiones lambda

Funciones **anónimas**

```text
f = \a1 -> \a2 -> … \an -> expr
```

Sin distinción de casos ni `where`

---

# Lambda: ejemplos

```haskell
doble :: Int -> Int
doble = \x -> 2 * x

suma :: Int -> Int -> Int
suma = \x -> \y -> x + y
```

```text
λ (\x -> \y -> x * 2 + y) 3 4
10
```

---

# Lambda con let

```haskell
may3 :: Int -> Int -> Int -> Int
may3 = \x -> \y -> \z ->
  let m = if x > y then x else y
  in if z > m then z else m
```

---

# Principio de currying

Toda función tiene **un solo argumento**

```haskell
doble :: Int -> Int
doble x = 2 * x
```

---

# Currying: cómo se lee

```haskell
suma :: Int -> Int -> Int
suma x y = x + y
```

se lee

```haskell
suma :: Int -> (Int -> Int)
(suma x) y = x + y
```

---

# Parametrización parcial

```haskell
suma x y z = x + y + z

incDos = suma 2
incDosTres = suma 2 3
```

```text
incDos 3 5     10
incDosTres 5   10
```

---

# Simplificación de funciones

| Definición | Simplificada |
| --- | --- |
| `suma x y = (+) x y` | `suma = (+)` |
| `f2 x y z = g y x z` | `f2 x y = g y x` |
| `f3 x y z = g z x y z` | `f3 x y z = g z x y z` |

---

# ¿Qué ganamos al simplificar?

| Expresión | `f1 x y = x y` | `f2 x = x` |
| --- | --- | --- |
| `(*2) 4` | `8` | `8` |
| `4` | error | `4` |

Más compacta = **más general**

---

# curry y uncurry

```haskell
curry f x y = f (x, y)

uncurry f (x, y) = f x y
```

En ProsKell: `currificar` y `descurrificar`

---

# Ventajas del currying

- Parametrización parcial
- Simplificación de funciones

---

# Pizarra: emparejamiento

¿Qué ecuación usa?

`y True False`

---

# Pizarra: parametrización parcial

¿Qué es?

`suma 2 5`

---

# ProsKell

<div class="qr-proskell"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 33 37" width="200" height="224" shape-rendering="crispEdges"><path fill="#fff" d="M0 0h33v37h-33z"/><path stroke="#1b2a4e" d="M2 2.5h7m3 0h3m2 0h2m1 0h1m1 0h1m1 0h7m-29 1h1m5 0h1m2 0h3m2 0h1m2 0h2m3 0h1m5 0h1m-29 1h1m1 0h3m1 0h1m2 0h2m4 0h3m1 0h2m1 0h1m1 0h3m1 0h1m-29 1h1m1 0h3m1 0h1m1 0h1m1 0h1m1 0h1m4 0h2m3 0h1m1 0h3m1 0h1m-29 1h1m1 0h3m1 0h1m3 0h1m2 0h3m6 0h1m1 0h3m1 0h1m-29 1h1m5 0h1m1 0h1m7 0h3m3 0h1m5 0h1m-29 1h7m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h7m-21 1h2m5 0h2m1 0h2m-19 1h2m3 0h1m2 0h1m2 0h1m3 0h4m2 0h2m1 0h1m-23 1h3m3 0h2m4 0h2m2 0h2m1 0h2m1 0h1m1 0h2m-28 1h2m2 0h3m1 0h1m1 0h2m2 0h1m2 0h4m2 0h2m2 0h1m-29 1h2m2 0h1m2 0h4m2 0h1m4 0h1m3 0h2m1 0h1m-26 1h1m3 0h5m1 0h2m1 0h3m3 0h1m1 0h2m2 0h1m1 0h1m-28 1h5m3 0h2m1 0h2m1 0h2m3 0h2m1 0h1m2 0h1m1 0h2m-28 1h2m3 0h3m1 0h2m1 0h3m1 0h4m4 0h2m1 0h1m-29 1h1m6 0h1m4 0h1m1 0h2m9 0h1m2 0h1m-29 1h3m1 0h4m1 0h1m2 0h1m3 0h4m1 0h3m-23 1h3m3 0h4m2 0h2m1 0h2m1 0h2m1 0h2m1 0h1m2 0h1m-29 1h3m2 0h2m2 0h3m4 0h1m1 0h2m6 0h1m1 0h1m-27 1h1m2 0h1m4 0h1m1 0h1m1 0h3m1 0h1m2 0h2m2 0h1m-26 1h2m4 0h1m2 0h2m1 0h1m3 0h1m2 0h6m-17 1h1m2 0h1m1 0h1m1 0h3m1 0h2m3 0h2m2 0h1m-29 1h7m4 0h1m3 0h2m3 0h1m1 0h1m1 0h5m-29 1h1m5 0h1m2 0h2m1 0h1m3 0h2m1 0h2m3 0h2m-26 1h1m1 0h3m1 0h1m3 0h2m5 0h1m1 0h6m-25 1h1m1 0h3m1 0h1m2 0h3m1 0h2m4 0h2m2 0h2m2 0h1m-28 1h1m1 0h3m1 0h1m1 0h2m2 0h1m1 0h2m1 0h1m3 0h1m2 0h2m1 0h2m-29 1h1m5 0h1m1 0h3m3 0h1m3 0h1m1 0h3m2 0h1m-26 1h7m2 0h3m1 0h4m3 0h2m1 0h3m2 0h1"/><text x="16.5" y="35" text-anchor="middle" font-size="2.7" font-family="sans-serif" fill="#1b2a4e">proskell.vercel.app</text></svg></div>

Lecciones **2.8 a 2.11, 2.13, 2.14 y 3.1 a 3.5**

Predecir → **Explicar** → **Prosa** → `λ`
