> [!NOTE] Nota
> Taller 3 será sobre Reconocimiento de Patrones (hasta el tema anterior)
# Secuencias
## Listas
Secuencias lineales (esto significa que el acceso al primer elemento es mucho más rápido que al del medio o a los últimos)
## Vectores
A diferencia de las listas, proveen un acceso más balanceado a los elementos de la secuencia (son una manera de acceso inmediato, por así decirlo)
### Creación de Vectores
En Scala, se crean mediante el siguiente comando:
```
Vector(1,2,3,4)
```
Por ejemplo:
```
val nums = Vector (10,12,6,8)
val personas = Vector ("Juan", "Jose", "Pedro")
```
### Manipulación de Vectores
**Ejemplo**: Queremos acceder al elemento en la posición 3 del vector. Entonces usaremos:
```
Vector(1,2,3,4)(3)              
```
### Operaciones Binarias
Los vectores soportan las mismas operaciones que las listas, salvo `::`. Para eso, se usan los operadores binarios `+:` y `:+`.
- `x :+ xs`: Crea un nuevo vector que tiene de primer elemento a `x`, seguido por los elementos del vector `xs`
- `xs +: x`: Crea un nuevo vector con `x` como último elemento, antecedido de los elementos de `xs`.
## Rangos
 Representan una secuencia de enteros espaciados uniformemente. Se representan por:
```
x until y by z
```
- `x` es el número inicial
- `y` es el número al que se va a llegar
- `z` es el incremento que se va a usar (Por ejemplo: de 1 en 1, de 2 en 2, etc).
# Operaciones Sobre Secuencias
- `xs exists p`: Si hay un elemento `x` de `xs` tal que `p(x)`, retorna `true`. De lo contrario, retorna `false` 
- `xs forall p`: Si todo elemento `x` de `xs` cumple `p(x)`, retorna `true`. De lo contrario, retorna `false`.
- `xs zip ys`: Devuelve una secuencia de parejas de elementos `xs` con elementos de `ys` en la misma posición 
- `xs unzip ys`: Recibe una pareja de elementos, y devuelve una pareja con las listas de los primeros y segundos elementos de la pareja.
- ![[Pasted image 20250925103507.png]]
- `xs.flatMap f`: Devuelve la secuencia resultante de aplicar f a cada fragmento de `xs`. 
-  ![[Pasted image 20250925103943.png]]
## Ejercicio
Crear una función que permita determinar si un número es primo. 
![[Pasted image 20250925104949.png]]
Lo que quiere decir esta linea es: `n` es primo si desde `2` hasta `n` no haya un número que al realizar el módulo el residuo sea cero
# Expresiones For
Son expresiones de la forma `for (s) yield e`, que se lee "para `s` recoger `e`". Todos los for que usemos deben ser de esta manera. 
En esta expresión, `s` es una secuencia de generadores y filtros
- Un **generador** es una expresion de la forma `p <- e` ("para los p de la coleccion e hacer:")
- Un **filtro** es una expresion de la forma `if f` (`if` no es un condicional, sino que es un ), donde `f` es   una   expresión booleana.
# Conjuntos
Son abstracciones básicas de las colecciones de Scala. Su sintaxis es similar a la de las secuencias
```
val conjunto=Set(1,2,3,4)
```
Sobre los conjuntos se pueden aplicar la mayoría de operaciones que se aplican sobre las secuencias. 
Una característica de los conjuntos es que no tienen orden ni elementos duplicados.
Los conjuntos implementan una nueva operación: `contains`. Esta sirve para revisar si un elemento está dentro del conjunto
# Consultas For
Son útiles para realizar consultas típicas en bases de datos. 