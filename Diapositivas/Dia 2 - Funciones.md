# Día 2
## Definición de funciones

Lecciones **2.1 a 2.7 y 2.12**

---

# Cómo definir funciones

- Combinación
- Distinción de casos
- `if`
- `case`
- Definiciones locales

---

# Definición por combinación

```haskell
cuad :: Int -> Int
cuad x = x * x

pote4 :: Int -> Int
pote4 x = cuad (cuad x)
```

---

# Expresión if

```text
if exprLogica
  then expr1
  else expr2
```

`expr1` y `expr2`: **mismo tipo**

---

# Ejemplo: mayor de dos

```haskell
mayor :: Int -> Int -> Int
mayor x y = if x > y then x else y
```

---

# if anidados

```haskell
may3 :: Int -> Int -> Int -> Int
may3 x y z =
  if x > y
    then (if x > z then x else z)
    else (if y > z then y else z)
```

---

# Distinción de casos

```text
f a1 .. ak
  | exprLog1  = expr1
  | exprLog2  = expr2
  | otherwise = exprn
```

Mutuamente **excluyentes** y **exhaustivas**

---

# ¿Es exhaustiva?

```haskell
mayor :: Int -> Int -> Int
mayor x y
  | x > y = x
  | x < y = y
```

`mayor 5 5` ⇒ ?

---

# El caso otherwise

```haskell
sgteVocal :: Char -> Char
sgteVocal v
  | v == 'a'  = 'e'
  | v == 'e'  = 'i'
  | v == 'i'  = 'o'
  | v == 'o'  = 'u'
  | v == 'u'  = 'a'
  | otherwise = '?'
```

---

# Expresión case

```text
case expresion of
  expr1 -> exprRes1
  expr2 -> exprRes2
  _     -> exprResn
```

---

# case sobre un valor

```haskell
num2bool :: Int -> Bool
num2bool x = case x of
  0 -> False
  _ -> True
```

---

# case sobre una condición

```haskell
menor :: Int -> Int -> Int
menor x y = case x < y of
  True -> x
  _    -> y
```

---

# Definiciones locales: where y let

```text
f a1 .. ak = expr
  where defLocal
```

```text
f a1 .. ak =
  let defLocal
  in expr
```

---

# Mayor de tres

```haskell
m3 :: Int -> Int -> Int -> Int
m3 x y z = if z > m then z else m
  where m = if x > y then x else y
```

```haskell
m3 x y z =
  let m = if x > y then x else y
  in if z > m then z else m
```

---

# Problema: evaluar 4 notas

Promedio de 4 notas

```text
90 a 100    Excelente
80 a 89     Muy Bien
70 a 79     Bien
51 a 69     Regular
0 a 50      Mal
otro        notas invalidas
```

---

# Sin definiciones locales

El promedio, **diez** veces

```haskell
evalua n1 n2 n3 n4
  | div (n1+n2+n3+n4) 4 >= 90
    && div (n1+n2+n3+n4) 4 <= 100
    = "Excelente"
  | div (n1+n2+n3+n4) 4 >= 80
    && div (n1+n2+n3+n4) 4 <= 89
    = "Muy Bien"
  ...
```

---

# Con definiciones locales

```haskell
evalua_v3 n1 n2 n3 n4
  | promEn 90 100 = "Excelente"
  | promEn 80 89  = "Muy Bien"
  | promEn 70 79  = "Bien"
  | promEn 51 69  = "Regular"
  | promEn 0 50   = "Mal"
  | otherwise = "notas invalidas"
  where
    prom = div (n1+n2+n3+n4) 4
    promEn li ls =
      prom >= li && prom <= ls
```

---

# Pizarra: prueba de escritorio

Prueba de escritorio

`may3 4 9 2`

---

# Pizarra: ¿qué falla?

¿Qué falla?

`if n >= 51 then "Aprobado" else False`

---

# ProsKell

<div class="qr-proskell"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 33 37" width="200" height="224" shape-rendering="crispEdges"><path fill="#fff" d="M0 0h33v37h-33z"/><path stroke="#1b2a4e" d="M2 2.5h7m3 0h3m2 0h2m1 0h1m1 0h1m1 0h7m-29 1h1m5 0h1m2 0h3m2 0h1m2 0h2m3 0h1m5 0h1m-29 1h1m1 0h3m1 0h1m2 0h2m4 0h3m1 0h2m1 0h1m1 0h3m1 0h1m-29 1h1m1 0h3m1 0h1m1 0h1m1 0h1m1 0h1m4 0h2m3 0h1m1 0h3m1 0h1m-29 1h1m1 0h3m1 0h1m3 0h1m2 0h3m6 0h1m1 0h3m1 0h1m-29 1h1m5 0h1m1 0h1m7 0h3m3 0h1m5 0h1m-29 1h7m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h1m1 0h7m-21 1h2m5 0h2m1 0h2m-19 1h2m3 0h1m2 0h1m2 0h1m3 0h4m2 0h2m1 0h1m-23 1h3m3 0h2m4 0h2m2 0h2m1 0h2m1 0h1m1 0h2m-28 1h2m2 0h3m1 0h1m1 0h2m2 0h1m2 0h4m2 0h2m2 0h1m-29 1h2m2 0h1m2 0h4m2 0h1m4 0h1m3 0h2m1 0h1m-26 1h1m3 0h5m1 0h2m1 0h3m3 0h1m1 0h2m2 0h1m1 0h1m-28 1h5m3 0h2m1 0h2m1 0h2m3 0h2m1 0h1m2 0h1m1 0h2m-28 1h2m3 0h3m1 0h2m1 0h3m1 0h4m4 0h2m1 0h1m-29 1h1m6 0h1m4 0h1m1 0h2m9 0h1m2 0h1m-29 1h3m1 0h4m1 0h1m2 0h1m3 0h4m1 0h3m-23 1h3m3 0h4m2 0h2m1 0h2m1 0h2m1 0h2m1 0h1m2 0h1m-29 1h3m2 0h2m2 0h3m4 0h1m1 0h2m6 0h1m1 0h1m-27 1h1m2 0h1m4 0h1m1 0h1m1 0h3m1 0h1m2 0h2m2 0h1m-26 1h2m4 0h1m2 0h2m1 0h1m3 0h1m2 0h6m-17 1h1m2 0h1m1 0h1m1 0h3m1 0h2m3 0h2m2 0h1m-29 1h7m4 0h1m3 0h2m3 0h1m1 0h1m1 0h5m-29 1h1m5 0h1m2 0h2m1 0h1m3 0h2m1 0h2m3 0h2m-26 1h1m1 0h3m1 0h1m3 0h2m5 0h1m1 0h6m-25 1h1m1 0h3m1 0h1m2 0h3m1 0h2m4 0h2m2 0h2m2 0h1m-28 1h1m1 0h3m1 0h1m1 0h2m2 0h1m1 0h2m1 0h1m3 0h1m2 0h2m1 0h2m-29 1h1m5 0h1m1 0h3m3 0h1m3 0h1m1 0h3m2 0h1m-26 1h7m2 0h3m1 0h4m3 0h2m1 0h3m2 0h1"/><text x="16.5" y="35" text-anchor="middle" font-size="2.7" font-family="sans-serif" fill="#1b2a4e">proskell.vercel.app</text></svg></div>

Lecciones **2.1 a 2.7 y 2.12**

Predecir → **Explicar** → **Prosa** → `λ`
