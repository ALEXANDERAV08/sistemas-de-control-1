### Rincon Benavides Juan Esteban 
### Avila Rojas Nestor Alexander 
## Estabilidad
## ¿Que es estabilidad?
>🔑La estabilidad es una característica esencial de un sistema de control que indica su capacidad para mantenerse bajo control o responder
>de forma predecible cuando se le aplica una perturbación o se modifica la entrada. Un sistema se considera estable si, al recibir una entrada
>limitada, su salida también se mantiene dentro de ciertos límites y, si no hay más alteraciones, el sistema retorna a su estado de equilibrio.
>
Los tipos de estabilidad que podemos encontrar son:
- Estable: La respuesta del sistema no se desborda y con el tiempo se acerca a un valor constante.
- Inestable: Ante una pequeña alteración, la respuesta del sistema aumenta sin control.
- Marginalmente estable: La salida no se incrementa indefinidamente ni se reduce a cero, sino que permanece oscilando sin disiparse
  (como ocurre en sistemas sin amortiguamiento).
 ## 1 teorema del valor final
 >🔑 Es un método para encontrar el valor al que tiende una función f(t) cuando el tiempo se aproxima a infinito, usando su transformada de Laplace F(s). se
>expresa como:  $lim_{t \to \infty} f(t) = \lim_{s \to 0} sF(s)$
>
## 2 Condiciones para aplicar el teorema
- Estabilidad del sistema: Todos los polos de F(s) deben tener partes reales negativas, excepto, como máximo, un polo simple en el origen.
- Existencia del límite: El límite $lim_{t \to \infty} f(t)$ debe existir.

💡**Ejemplo 1: Sistema estable con entrada escalón**
**sistema**
- $G(s) = \frac{6}{s + 2}$
- $U(s) = \frac{1}{s}$ (escalón unitario)
**Cálculo:**

$$\lim_{t \to \infty} y(t) = \lim_{s \to 0} s \cdot G(s) \cdot U(s) = \lim_{s \to 0} s \cdot \frac{6}{s + 2} \cdot \frac{1}{s} = \lim_{s \to 0} \frac{6}{s + 2} = 3$$

**Interpretación:**  
El sistema es estable y la salida tiende a 3 en estado estacionario.

💡**Ejemplo 2: Sistema inestable**

**Sistema:**

- $G(s) = \frac{1}{s - 1}$
- $U(s) = \frac{1}{s}$

**Cálculo:**

$$\lim_{t \to \infty} y(t) = \lim_{s \to 0} s \cdot \frac{1}{s - 1} \cdot \frac{1}{s} = \lim_{s \to 0} \frac{1}{s - 1} \to \infty$$

**Interpretación:**  
El sistema es inestable (tiene un polo en $s = 1$), por lo tanto el teorema del valor final **no es aplicable**.

## 📚 EJERCICIO 1 (Sistema marginalmente estable (oscilatorio))
**Sistema:**

- $G(s) = \frac{9}{s^2 + 9}$
- $U(s) = \frac{1}{s}$

**Cálculo:**

$$\lim_{t \to \infty} y(t) = \lim_{s \to 0} s \cdot \frac{9}{s^2 + 9} \cdot \frac{1}{s} = \lim_{s \to 0} \frac{9}{s^2 + 9} = 1$$

**Interpretación:**  
Aunque el límite da 1, el sistema tiene polos imaginarios puros en $s = \pm 3i$, por lo tanto el sistema es marginalmente estable y el teorema del valor final **no es válido**.

