# Definición 
Decimos que una función $f$(x) es continua en un punto $x=a$ si y sólo si se cumplen estas tres condiciones:
- $f(x)$ está definida en $a$
- $\lim{x \to a⁻} f(x)= \lim{x \to a⁺} f(x)= \lim{x \to a}f(x)$ (El límite cuando $x$ tiende a $a$ existe)
- $f(a) = \lim{x \to a}f(x)$ (El límite cuando $x$ tiende a $a$ es igual a la función evaluada en $a$)

# Continuidad de Funciones a Trozos
Supongamos que tenemos la siguiente función:

$$
f(x) =
\begin{cases}
  1 & \text{si } x \leq{}  1, \\
  x & \text{si } 1 < x \leq{} 3, \\
  3 & \text{si } x > 3
\end{cases} 
$$

Podemos decir que $f$ está definida en 1 en el intervalo $(-\infty{}, 1]$, en x en el intervalo $(1,3]$, y en 3 en el intervalo $(3, \infty{})$

# Continuidad en Intervalos
Para este caso, tomaremos a $f$ como una función continua en el intervalo cerrado $[a,b]$ si:

- $f(x)$ es continua para todo $x$ en el intervalo $[a,b]$.
- $f(x)$ es continua en a por la derecha. Es decir: $f(a)= \lim{x \to{} a⁺} f(x)$
- - $f(x)$ es continua en b por la izquierda. Es decir: $f(a)= \lim{x \to{} b⁻} f(x)$

