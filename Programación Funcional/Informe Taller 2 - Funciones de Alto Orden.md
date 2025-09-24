**Autores:** Juan Pablo Escamilla (2420580), Paul Weis (202513207)

---

## 1. Informe de Funciones de Alto Orden

Las funciones de alto orden pueden utilizarse de tres formas principales: como parámetro, de forma anónima, o como respuesta de una función. A continuación se presenta el análisis para cada función implementada:

| Función                   | Como Parámetro            | De Forma Anónima       | Como Respuesta            |
| ------------------------- | ------------------------- | ---------------------- | ------------------------- |
| `insert`                  | (comp: Comparador[T])     | x                      | x                         |
| `insertionSort`           | (comp: Comparador[T])     | (función inner/sorter) | (retorna algoritmoOrd[T]) |
| `menoresQue_noMenoresQue` | (comp: Comparador[T])     | x                      | x                         |
| `quickSort`               | (comp: Comparador[T])     | (función inner)        | (retorna algoritmoOrd[T]) |
| `comparar`                | (a1, a2: algoritmoOrd[T]) | x                      | x                         |

- `insertionSort` y `quickSort` son las funciones que más aprovechan las características de las funciones de alto orden, ya que utilizan las tres formas.

- Ambas reciben un comparador como parámetro, definen funciones anónimas internas para el procesamiento recursivo, y retornan una función como resultado.

- `comparar` recibe dos algoritmos de ordenamiento (funciones) como parámetros, demostrando el uso de funciones como datos de primera clase.

---

## 2. Informe de Corrección

### 2.1 Argumentación sobre la Corrección
#### 2.1.1 Función `insert`

Sea $f : T × List[T] × Comparador[T] → (List[T], Int)$ la función que inserta un elemento e en una lista ordenada $l$ manteniendo el orden según el comparador $comp$.

Sea $P_f$ el programa recursivo implementado para calcular $f$.

**Teorema:** $\forall(e, l, comp) \in  T × List[T] × Comparador[T] : P_f(e, l, comp) = f(e, l, comp)$

**Demostración por inducción estructural sobre la lista l:**

**Caso base:** $l = \emptyset$ (lista vacía)

$P_f(e, \emptyset, comp) → (e::\emptyset, 0) = ([e], 0)$

Por otro lado, $f(e, \emptyset, comp) = ([e], 0)$ pues insertar $e$ en una lista vacía produce la lista [e] con 0 comparaciones.

Por tanto: $P_f(e, \emptyset, comp) = f(e, \emptyset, comp)$

**Caso de inducción:** $l = h::t$, donde $h \in  T y t \in  List[T]$

**Hipótesis de inducción:** $P_f(e, t, comp) = f(e, t, comp)$

Debemos demostrar: $P_f(e, h::t, comp) = f(e, h::t, comp)$

Calculemos $P_f(e, h::t, comp)$:

Si $comp(e, h) = true: P_f(e, h::t, comp) → (e::(h::t), 1) = (e::h::t, 1)$

Si $comp(e, h) = false: P_f(e, h::t, comp) →$ sea $(l', c) = P_f(e, t, comp)$ entonces $(h::l', c+1)$

Por hipótesis de inducción: $P_f(e, t, comp) = f(e, t, comp)$

Por tanto: $P_f(e, h::t, comp) = (h::l', c+1)$ donde $(l', c) = f(e, t, comp)$

Esto corresponde exactamente a $f(e, h::t, comp).$

**Conclusión:** $\forall(e, l, comp) : P_f(e, l, comp) = f(e, l, comp)$

#### 2.1.2 Función `insertionSort`

Sea $f : List[T] × Comparador[T] → (List[T], Int)$ la función que ordena una lista usando insertion sort.

Sea $P_f$ el programa recursivo que implementa $f$.

**Teorema:** $\forall(l, comp) \in  List[T] × Comparador[T] : P_f(l, comp) = f(l, comp)$

**Demostración por inducción estructural sobre la lista l:**

**Caso base:** $l = \emptyset$

$P_f(\emptyset, comp) → (\emptyset, 0)$

Por definición, $f(\emptyset, comp) = (\emptyset, 0)$ pues una lista vacía ya está ordenada con 0 comparaciones.

Por tanto: $P_f(\emptyset, comp) = f(\emptyset, comp)$

**Caso de inducción:** $l = h::t$

**Hipótesis de inducción:** $P_f(t, comp) = f(t, comp)$

Sea $(l_{sorted}, c₁) = P_f(t, comp)$. Por hipótesis de inducción, $l_{sorted}$ es la versión ordenada de $t$.

Sea $(l_{final}, c₂) = insert(h, l_{sorted}, comp)$. Por demostración anterior, $l_{final}$ es $l_{sorted}$ con $h$ insertado en orden.

Entonces: $P_f(h::t, comp) = (l_{final}, c₁ + c₂)$

Esto corresponde exactamente a $f(h::t, comp)$, que debe ordenar todos los elementos de $h::t$.

**Conclusión:** $\forall(l, comp) : P_f(l, comp) = f(l, comp)$

#### 2.1.3 Función `menoresQue_noMenoresQue`

Sea $f : List[T] × T × Comparador[T] → (List[T], List[T], Int)$ la función que particiona una lista $l$ según un pivote $v$.

**Teorema:** $\forall(l, v, comp) : P_f(l, v, comp) = f(l, v, comp)$

**Demostración por inducción estructural sobre la lista l:**

**Caso base:** $l = \emptyset$

$P_f(\emptyset, v, comp) → (\emptyset, \emptyset, 0)$

Por definición, $f(\emptyset, v, comp) = (\emptyset, \emptyset, 0).$

Por tanto: $P_f(\emptyset, v, comp) = f(\emptyset, v, comp)$

**Caso de inducción:** $l = h::t$

**Hipótesis de inducción:** $P_f(t, v, comp) = f(t, v, comp)$

Sea $(l₁, l₂, c) = P_f(t, v, comp)$. Por hipótesis de inducción, $l₁$ contiene elementos de $t$ que no satisfacen $comp(v, x)$ y $l₂$ contiene elementos que sí satisfacen $comp(v, x)$.

Si $comp(v, h) = true: P_f(h::t, v, comp) = (l₁, l₂ ++ [h], c + 1)$

Si $comp(v, h) = false: P_f(h::t, v, comp) = (l₁ ++ [h], l₂, c + 1)$

En ambos casos se mantiene el invariante de partición y se cuenta la comparación realizada.

**Conclusión:** $\forall(l, v, comp) : P_f(l, v, comp) = f(l, v, comp)$
#### 2.1.4 Función `quickSort`

Sea $f : List[T] × Comparador[T] → (List[T], Int)$ la función que ordepna una lista usando quicksort.

**Teorema:** $\forall(l, comp) : P_f(l, comp) = f(l, comp)$

**Demostración por inducción estructural sobre la lista l:**

**Caso base:** $l = \emptyset$

$P_f(\emptyset, comp) → (\emptyset, 0)$

Por definición, $f(\emptyset, comp) = (\emptyset, 0).$

Por tanto: $P_f(\emptyset, comp) = f(\emptyset, comp)$

**Caso de inducción:** $l = h::t$

**Hipótesis de inducción:** Para toda lista $l'$ con $|l'| < |l|, P_f(l', comp) = f(l', comp)$

Sea $(l₁, l₂, c₁) = menoresQue_noMenoresQue(t, h, comp)$.

Por demostración anterior: $l₁ ∪ l₂ = t$ y $\forall x \in  l₁ : ¬comp(h, x) ∧ \forall x \in  l₂ : comp(h, x)$

Sea $(sorted_l₁, c₂) = P_f(l₁, comp) y (sorted_l₂, c₃) = P_f(l₂, comp).$

Por hipótesis de inducción: $sorted_l₁ y sorted_l₂$ están correctamente ordenadas.

Entonces: $P_f(h::t, comp) = (sorted_l₁ ++ [h] ++ sorted_l₂, c₁ + c₂ + c₃)$

La lista resultante está ordenada porque:

- $sorted_l₁$ está ordenada y $\forall x \in  sorted_l₁ : x ≤ h$ (por la partición)
- $sorted_l₂$ está ordenada y $\forall x \in  sorted_l₂ : h < x$ (por la partición)
- Por tanto: $sorted_l₁ ++ [h] ++ sorted_l₂$ está totalmente ordenada

**Conclusión:** $\forall(l, comp) : P_f(l, comp) = f(l, comp)$

#### 2.1.5 Función `comparar`

Sea $f : algoritmoOrd[T] × algoritmoOrd[T] × List[T] → (Int, Int)$ la función que compara dos algoritmos de ordenamiento.

**Especificación:** $f(a₁, a₂, l)$ devuelve $(c₁, c₂)$ donde $cᵢ$ es el número de comparaciones del algoritmo $aᵢ$, si ambos producen el mismo resultado ordenado; $(-1, -1)$ en caso contrario.

Sea $P_f$ el programa que implementa $f$.

**Demostración directa:**

Para cualquier entrada $(a₁, a₂, l)$:

Sea $(l₁, c₁) = a₁(l) y (l₂, c₂) = a₂(l)$
$$ P_f(a_1, a_2, l) =
\begin{cases}
  (c_1, c_2) & \text{si } l_1 = l_2 \\
  (-1, -1) & \text{si } l_1 \neq l_2
\end{cases} $$

Esto corresponde exactamente a la especificación de $f$.

**Conclusión:** $\forall(a₁, a₂, l) : P_f(a₁, a₂, l) = f(a₁, a₂, l)$
### 2.2 Casos de Prueba

#### 2.2.1 Función `insert`

| Caso | Entrada                            | Resultado Esperado   | Resultado Obtenido   |
| ---- | ---------------------------------- | -------------------- | -------------------- |
| 1    | `insert(5, List(), menorQue)`      | `(List(5), 0)`       | `(List(5), 0)`       |
| 2    | `insert(1, List(3,5,7), menorQue)` | `(List(1,3,5,7), 1)` | `(List(1,3,5,7), 1)` |
| 3    | `insert(9, List(1,3,5), menorQue)` | `(List(1,3,5,9), 3)` | `(List(1,3,5,9), 3)` |
| 4    | `insert(4, List(1,5,7), menorQue)` | `(List(1,4,5,7), 2)` | `(List(1,4,5,7), 2)` |
| 5    | `insert(3, List(1,3,5), menorQue)` | `(List(1,3,3,5), 2)` | `(List(1,3,3,5), 2)` |

#### 2.2.2 Función `menoresQue_noMenoresQue`

| Caso | Entrada                                                   | Resultado Esperado              | Resultado Obtenido              |
| ---- | --------------------------------------------------------- | ------------------------------- | ------------------------------- |
| 1    | `menoresQue_noMenoresQue(List(), 5, menorQue)`            | `(List(), List(), 0)`           | `(List(), List(), 0)`           |
| 2    | `menoresQue_noMenoresQue(List(1,2,3), 5, menorQue)`       | `(List(1,2,3), List(), 3)`      | `(List(1,2,3), List(), 3)`      |
| 3    | `menoresQue_noMenoresQue(List(5,6,7), 5, menorQue)`       | `(List(), List(5,6,7), 3)`      | `(List(), List(5,6,7), 3)`      |
| 4    | `menoresQue_noMenoresQue(List(2,5,1,8,3,6), 4, menorQue)` | `(List(2,1,3), List(5,8,6), 6)` | `(List(2,1,3), List(5,8,6), 6)` |
| 5    | `menoresQue_noMenoresQue(List(3,5,3,5,5), 4, menorQue)`   | `(List(3,3), List(5,5,5), 5)`   | `(List(3,3), List(5,5,5), 5)`   |

#### 2.2.3 Función `insertionSort`

| Caso | Entrada                                      | Resultado Esperado         | Resultado Obtenido           |
| ---- | -------------------------------------------- | -------------------------- | ---------------------------- |
| 1    | `insertionSort(menorQue)(List())`            | `(List(), 0)`              | `(List(), 0)`                |
| 2    | `insertionSort(menorQue)(List(42))`          | `(List(42), 0)`            | `(List(42), 0)`              |
| 3    | `insertionSort(menorQue)(List(1,2,3,4))`     | `(List(1,2,3,4), ≤6)`      | Lista ordenada correctamente |
| 4    | `insertionSort(menorQue)(List(4,3,2,1))`     | `(List(1,2,3,4), ≤10)`     | Lista ordenada correctamente |
| 5    | `insertionSort(menorQue)(List(4,5,6,1,2,3))` | `(List(1,2,3,4,5,6), ≤15)` | Lista ordenada correctamente |

#### 2.2.4 Función `quickSort`

| Caso | Entrada                                  | Resultado Esperado         | Resultado Obtenido           |
| ---- | ---------------------------------------- | -------------------------- | ---------------------------- |
| 1    | `quickSort(menorQue)(List())`            | `(List(), 0)`              | `(List(), 0)`                |
| 2    | `quickSort(menorQue)(List(42))`          | `(List(42), 0)`            | `(List(42), 0)`              |
| 3    | `quickSort(menorQue)(List(1,2))`         | `(List(1,2), 1)`           | `(List(1,2), 1)`             |
| 4    | `quickSort(menorQue)(List(2,1))`         | `(List(1,2), 1)`           | `(List(1,2), 1)`             |
| 5    | `quickSort(menorQue)(List(4,5,6,1,2,3))` | `(List(1,2,3,4,5,6), ≤20)` | Lista ordenada correctamente |

#### 2.2.5 Función `comparar`

| Caso | Entrada                                              | Resultado Esperado         | Resultado Obtenido                            |
| ---- | ---------------------------------------------------- | -------------------------- | --------------------------------------------- |
| 1    | `comparar(iSort_Asc, iSort_Asc, List(4,5,6,1,2,3))`  | `(13, 13)`                 | Mismo algoritmo, mismas comparaciones         |
| 2    | `comparar(iSort_Asc, qSort_Asc, List(4,5,6,1,2,3))`  | `(c1, c2)` donde c1,c2 > 0 | Ambos ordenan igual, comparaciones diferentes |
| 3    | `comparar(iSort_Asc, qSort_Desc, List(4,5,6,1,2,3))` | `(-1, -1)`                 | Orden diferente                               |
| 4    | `comparar(iSort_Asc, qSort_Asc, List())`             | `(0, 0)`                   | Lista vacía                                   |
| 5    | `comparar(iSort_Asc, qSort_Asc, List(42))`           | `(0, 0)`                   | Un elemento                                   |

### 2.3 Suficiencia de los Casos de Prueba

Los casos de prueba diseñados cubren:

- **Casos límite:** Listas vacías, un elemento
- **Casos típicos:** Listas ordenadas, desordenadas, parcialmente ordenadas
- **Casos especiales:** Elementos duplicados, diferentes tamaños
- **Casos de error:** Algoritmos con diferentes criterios de ordenamiento

Consideramos que estos casos son **suficientes** para confiar en la corrección de las implementaciones porque:

1. Cubren todos los casos base de las recursiones
2. Incluyen casos representativos de los casos inductivos
3. Verifican el comportamiento con diferentes tipos de entrada
4. Validan tanto la funcionalidad como el conteo de comparaciones

---

## 3. Conclusiones

1. **Funciones de Alto Orden:** La implementación demuestra el poder expresivo de las funciones de alto orden en Scala, permitiendo crear algoritmos parametrizados y reutilizables.

2. **Corrección Algorítmica:** Todas las funciones implementadas son correctas según sus especificaciones, demostrado mediante inducción matemática.

3. **Eficiencia:** El sistema de conteo de comparaciones permite analizar objetivamente la eficiencia relativa de los algoritmos.

4. **Verificación:** Los casos de prueba proporcionan confianza en la corrección de las implementaciones y cubren los escenarios más importantes.

