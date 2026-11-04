# Día 1
## Conceptos fundamentales

Lecciones **1.1 a 1.14**

---

# ¿Por qué programación funcional?

- Código comprensible y conciso
- Funciones puras, **sin efectos colaterales**
- Programar **qué**, no **cómo**
- Más fácil detectar errores

---

# Paradigmas de programación

| Imperativo | Declarativo |
| --- | --- |
| **cómo** | **qué** |

Programación funcional = declarativa

---

# Programación funcional

**Programar** = modelar un problema con funciones

**Ejecutar** = evaluar expresiones

---

# Evaluar una expresión

```haskell
doble x = 2 * x
```

| Expresión | Reducción | Valor |
| --- | --- | --- |
| `doble (2 + 3)` | `2 * (2 + 3)` | `10` |

---

# Ventajas de la programación funcional

- Funciones = **valores de primer orden**
- Polimorfismo: `id x = x`
- Memoria: no es tarea del programador
- Evaluación **lazy**

**Desventaja:** entrada y salida

---

# Estrategias de evaluación

| Lazy | Eager |
| --- | --- |
| de afuera hacia adentro | de adentro hacia afuera |
| evalúa solo si lo necesita | primero los argumentos |

---

```haskell
doble x = 2 * x
cuadrado x = x * x
```

```text
Lazy:  cuadrado (doble 3)
     = (doble 3) * (doble 3)
     = 6 * 6
     = 36
```

```text
Eager: cuadrado (doble 3)
     = cuadrado 6
     = 36
```

---

# Lazy evalúa solo lo necesario
```haskell
primero (x, y) = x
```
```text
Lazy:  primero (2, 1+2*3*4)
     = 2
```

```text
Eager: primero (2, 1+2*3*4)
     = primero (2, 25)
     = 2
```

---

# Lazy llega al resultado

```text
Lazy:  primero (2, div 5 0)
     = 2
```

```text
Eager: primero (2, div 5 0)
     = error
```

Si existe un resultado, lazy lo calcula.

---

# Tipos básicos

| Tipo | Valor |
| --- | --- |
| `Int` | `5` |
| `Float` | `5.0` |
| `Char` | `'a'` |
| `String` | `"hola"` |
| `Bool` | `True` |

---

# Tipos compuestos

| Tipo | Valor |
| --- | --- |
| `(Int, Char)` | `(5, 'e')` |
| `(Int, Bool, (Char, Int))` | `(5, True, ('a', 7))` |
| `[Char]` | `"hola"` |
| `[[Int]]` | `[[1, 2, 3], [5, 6], []]` |

---

# ¿Qué es una función?

A cada `x` del **dominio**, un **único** `y` del **rango**

```haskell
doble :: Int -> Int
doble x = 2 * x
```

---

# Función = operador

```haskell
mas x y = x + y
```

| Función | Operador |
| --- | --- |
| `mas 2 4` | ``2 `mas` 4`` |
| `(+) 2 4` | `2 + 4` |

---

# Tipos de funciones

- Polimórficas
- De alto orden
- Sobrecargadas

---

# Funciones polimórficas

Trabajan con **cualquier tipo**

```haskell
primero :: (a, b) -> a
primero (x, y) = x
```

```text
primero (3, 8)          3
primero ("hola", True)  "hola"
```

---

# Funciones de alto orden

Reciben o devuelven **funciones**

```haskell
aplicar :: (a -> b) -> a -> b
aplicar f x = f x
```

---

# Funciones sobrecargadas

Trabajan con un **conjunto de tipos**

```haskell
maximo :: Ord a => a -> a -> a
maximo x y = if x > y then x else y
```

---

# Ejercicio: Lazy, Eager

¡GÁNATE STICKERS PARA TU LAPTOP!

Reducir con **lazy** y con **eager**         

`primero (2, 1 + 2 * 3 * 4)`

---

# Ejercicio: tipos

¡GÁNATE STICKERS PARA TU LAPTOP!

¿Qué tipo tiene?                            

`(5, True, ('a', 7))`

---

# ProsKell

<div class="qr-proskell"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 33 37" width="200" height="224" shape-rendering="crispEdges"><path fill="#fff" d="M0 0h33v37h-33z"/><path stroke="#1b2a4e" d="M2 2.5h7m3 0h3m2 0h2m1 0h1m1 0h1m1 0h7m-29 1h1m5 0h1m2 0h3m2 0h1m2 0h2m3 0h1m5 0h1m-29 1h1m1 0h3m1 0h1m2 0h2m4 0h3m1 0h2m1 0h1m1 0h3m1 0h1m-29 1h1m1 0h3m1 0h1m1 0h1m1 0h1m1 0h1m4 0h2m3 0h1m1 0h3m1 0h1m-29 1h1m1 0h3m1 0h1m3 0h1m2 0h3m6 0h1m1 0h3m1 0h1m-29 1h1m5 0h1m1 0h1m7 0h3m3 0h1m5 0h1m-29 1h7m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h7m-21 1h2m5 0h2m1 0h2m-19 1h2m3 0h1m2 0h1m2 0h1m3 0h4m2 0h2m1 0h1m-23 1h3m3 0h2m4 0h2m2 0h2m1 0h2m1 0h1m1 0h2m-28 1h2m2 0h3m1 0h1m1 0h2m2 0h1m2 0h4m2 0h2m2 0h1m-29 1h2m2 0h1m2 0h4m2 0h1m4 0h1m3 0h2m1 0h1m-26 1h1m3 0h5m1 0h2m1 0h3m3 0h1m1 0h2m2 0h1m1 0h1m-28 1h5m3 0h2m1 0h2m1 0h2m3 0h2m1 0h1m2 0h1m1 0h2m-28 1h2m3 0h3m1 0h2m1 0h3m1 0h4m4 0h2m1 0h1m-29 1h1m6 0h1m4 0h1m1 0h2m9 0h1m2 0h1m-29 1h3m1 0h4m1 0h1m2 0h1m3 0h4m1 0h3m-23 1h3m3 0h4m2 0h2m1 0h2m1 0h2m1 0h2m1 0h1m2 0h1m-29 1h3m2 0h2m2 0h3m4 0h1m1 0h2m6 0h1m1 0h1m-27 1h1m2 0h1m4 0h1m1 0h1m1 0h3m1 0h1m2 0h2m2 0h1m-26 1h2m4 0h1m2 0h2m1 0h1m3 0h1m2 0h6m-17 1h1m2 0h1m1 0h1m1 0h3m1 0h2m3 0h2m2 0h1m-29 1h7m4 0h1m3 0h2m3 0h1m1 0h1m1 0h5m-29 1h1m5 0h1m2 0h2m1 0h1m3 0h2m1 0h2m3 0h2m-26 1h1m1 0h3m1 0h1m3 0h2m5 0h1m1 0h6m-25 1h1m1 0h3m1 0h1m2 0h3m1 0h2m4 0h2m2 0h2m2 0h1m-28 1h1m1 0h3m1 0h1m1 0h2m2 0h1m1 0h2m1 0h1m3 0h1m2 0h2m1 0h2m-29 1h1m5 0h1m1 0h3m3 0h1m3 0h1m1 0h3m2 0h1m-26 1h7m2 0h3m1 0h4m3 0h2m1 0h3m2 0h1"/><text x="16.5" y="35" text-anchor="middle" font-size="2.7" font-family="sans-serif" fill="#1b2a4e">proskell.vercel.app</text></svg></div>

1. Crear cuenta
2. **+** Unirse a una clase 
    **Introducción a la Programación Funcional  ** 
    CÓDIGO DE CLASES: **IP-BDFW**
3. Tema 1 · Lección **1.1**

---

# Cómo trabajar cada lección

Predecir → **Explicar** → **Prosa** → `λ` Compilador en el navegador
