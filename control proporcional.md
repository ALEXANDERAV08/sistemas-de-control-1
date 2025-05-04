### Rincon Benavides Juan Esteban 
### Avila Rojas Nestor Alexander 
# 1 Diseño de controladores proporcionales
>🔑 Un control proporcional (P) es un tipo de estrategia de control en sistemas de retroalimentación donde la acción de control generada por el controlador es 
directamente proporcional al error entre la señal de referencia deseada (el setpoint) y la variable controlada real (la salida del sistema).
>
**Matematicamente esto se expresa como:**
$$U(t) = K_p e(t)$$

**Donde:**
- U(t) es la señal de control (es la entrada al sistema)
- $K_p$ es la ganancia proporcional, una constante ajustable
- e(t) = r(t) - y(t) es la señal de error
en termonos de laplace, la funcion de transferencia de un controlador proporcional es:
$$G_c(s) = K_p$$


![image](https://github.com/user-attachments/assets/0df9f794-e6e6-40a0-bdbf-24b192ac711d)

Figura 1. Diagrama de un sistema en lazo cerrado
- Comparador: Compara la señal de referencia (setpoint) con la salida medida del sistema (señal real).
- Controlador: Recibe el error del comparador y calcula la señal de control basada en este error. En un controlador proporcional, la salida es directamente proporcional al error.
- Accionador: Recibe la señal de control del controlador y la convierte en una acción física que afecta al sistema. El actuador puede ser un motor, una válvula, una bomba
- planta o sistema: Es el sistema o proceso que se desea controlar. Es el objeto de control, como un motor, un horno, un sistema de transporte, etc.
- Sensor: Mide la salida del sistema (también conocida como variable controlada). Esta señal es enviada al comparador para ser comparada con la referencia.
- Retroalimentación: La retroalimentación es la señal que se envía de vuelta desde el sensor al comparador y controlador. Esto permite al sistema ajustar su comportamiento en función
  de la diferencia entre la salida real y la referencia.

## 1.1 controlador proporcional
>🔑El controlador proporcional es la forma más básica de control en tiempo continuo y se usa en sistemas de lazo cerrado. Su función principal es reducir la diferencia entre una señal de 
referencia (lo que se desea) y la señal real (lo que el sistema produce), aplicando una acción proporcional a ese error.

Este tipo de controlador genera una señal de salida que depende directamente del valor del error. Es decir, si hay una diferencia entre el valor deseado y el valor actual, el controlador 
actúa en proporción a esa diferencia para corregir el sistema. El error e(t) se calcula restando la salida actual del sistema al valor de referencia establecido.

![image](https://github.com/user-attachments/assets/d5e20f43-2eab-40dd-a918-0f57326fb2ab)

este controlador proporcional busca reducir el error de la manera mas rapida, pero no siempre tiene una respuesta satisfatoria ya que existe errores en las etapas estacionarias 
- Si el error es grande, el controlador aplica una acción de control fuerte.
- Si el error es pequeño, la acción de control es suave.
- Si no hay error, la acción de control también es cero (idealmente).


## 2. ¿Que es lazo cerrado?
>🔑 Un sistema de lazo cerrado o tambien conocido como sistema de control conretroalintacion,es un sistema donde la salida del proceso o sistema que se está controlando se mide y se utiliza 
para ajustar la entrada de control, con el objetivo de mantener la salida en un valor deseado (la referencia o setpoint).
>

La clave de un sistema de lazo cerrado es la retroalimentación (feedback). La información sobre la salida del sistema se "realimenta" al controlador, que la compara con la referencia y toma
decisiones para corregir cualquier desviación o error.

## 2.1 ventajas de un sistema de lazo cerrado
- **Reducción del Error:** La retroalimentación permite corregir las desviaciones entre la salida real y la referencia, minimizando el error en estado estacionario y durante la respuesta transitoria.
- **Menor Sensibilidad a Variaciones de Parámetros:** La retroalimentación puede hacer que el sistema sea menos sensible a los cambios en los parámetros de la planta debido al envejecimiento, cambios 
ambientales
- **Mejora del Rendimiento:** Se pueden lograr especificaciones de rendimiento más exigentes en términos de tiempo de respuesta, sobreimpulso

## EJEMPLOS
💡 **1. Lazo Abierto:**

Sea la función de transferencia de la planta:

$$G(s) = \frac{0.5}{s+4}$$

**Reescribiendo en la forma estándar de primer orden:**
$$G(s) = \frac{K}{ts+1} =  \frac{0.5}{s+4} = \frac{0.125}{0.25s+1}$$ 

la ganancia en lazo abierto K=0.125 y la constante de tiempo en lazo abierto τ=0.25 Seg.

💡 **2.  Lazo Cerrado con Control Proporcional Kp:**

La función de transferencia del sistema en lazo cerrado con retroalimentación unitaria es:(analizando el ejemeplo anterior como lazo cerrado)

$$G(s) = \frac{KpG(s)}{1+KpG(s)}$$ 

$$G(s) = \frac{0.5}{s+4}$$

sustituyendo:

$$G(s) = \frac{Kp\frac{0.5}{s+4}}{1+Kp\frac{0.5}{s+4}}$$ 

multiplicamos numerador y denominador por (s +4)

$$G(s) = \frac{0.5Kp}{s + 4 +0.5Kp}$$ 

## 3 Lugar geometrico de las raices

>🔑 El lugar geométrico de las raíces es una herramienta visual que se usa en el diseño y análisis de sistemas de control. Permite observar cómo se 
modifican las raíces de la ecuación característica del sistema (es decir, los polos del sistema en lazo cerrado) cuando se cambia un parámetro, que normalmente es la ganancia K.

## 3.1 para que sirve?
- Evaluar si el sistema será estable o inestable.
- Diseñar controladores (como P), modificando la ganancia o agregando polos y ceros.
- Ver cómo se desplazan los polos del sistema cuando se cambia la ganancia.
### Ejemplo
💡**1. Analiza como cambian los polos en lazo cerrado al modificar la ganancia K.**
![image](https://github.com/user-attachments/assets/de2f53e2-4ed5-4684-9573-1522b777dd3c)
```
% Definir numerador y denominador del sistema sin la ganancia
num = [1];               % Numerador sin K
den = [1 2 0];           % Denominador s(s+2)

% Crear la función de transferencia
G = tf(num, den);

% Dibujar el lugar geométrico de las raíces
rlocus(G)

% Título y etiquetas
title('Lugar Geométrico de las Raíces')
xlabel('Parte Real')
ylabel('Parte Imaginaria')
grid on
```
📚 **1. Ejercicio: analice el siguiente sistema.**

$$G(s) = \frac{3}{s+4}$$
$$G(s) = \frac{Kp\frac{3}{s+4}}{1+Kp\frac{3}{s+4}}$$ 
$$G(s) = \frac{Kp}{s+4+Kp}$$
como resultado se tiene:

$$G(s) = \frac{Kp}{s+4+Kp}$$
