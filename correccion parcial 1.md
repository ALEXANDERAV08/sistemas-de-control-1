# Apuntes sistemas de control 1 
### Rincon Benavides Juan Esteban 
### Avila Rojas Nestor Alexander 
# Corrección parcial 1 
## Punto 1
La figura representa un Sistema para variar la posición de un émbolo. La bomba de presión es controlada por tensión v(t) que genera una presión p(t); la tensión de entrada de la bomba es suministrada por un amplificador que a 0 V entrega a la bomba 0 V y tiene una salida de 10 V con una entrada de 1 V. El émbolo de M = 5 Kg y área de contacto con el fluido de 0.25 m², se mueve dentro de la carcasa con un rozamiento viscoso de 2.5 N/m/s. El émbolo está en contacto con un cuerpo elástico con constante de elasticidad de 1 N/m. El fabricante de la bomba indica en su datasheet que puede ser modelada a través de una ecuación diferencial, donde la suma de la presión y la tasa de cambio de la presión es equivalente a aplicar 1.2 veces la entrada.

[![image.png](https://i.postimg.cc/cCp5bkt4/image.png)](https://postimg.cc/LgVTqTVr)

Para la solución del siguiente ejercicio deberemos analizar el sistema en 2 grupos uno en el cual se vea el sistema neumático y el segundo el sistema de la caja en movimiento por el mismo teniendo que para el sistema en general del modelo neumático tendremos lo siguiente.

$$p(t) + p'(t) = 1.2 \, v(t)$$

$$\frac{v(t)}{c(t)} = \frac{0 - 10}{0 - 1} = 10$$

$$p(t) + p'(t) = 12 \, c(t)$$

$$p + s p = 12 \, e$$
Teniendo esto damos por finalizado a la primera parte del ejercicio la segunda es analizar la parte de la masa para ver y sacar sus segundas ecuaciones teniendo que el diagrama de cuerpo libre correspondiente para la masa es el siguiente.

[![image.png](https://i.postimg.cc/15KjHB5P/image.png)](https://postimg.cc/xcc5jKzF)

Su representación matemática es la siguiente.

$$F_k + F_x - F = M \ddot{y}$$

$$y + 2.5 \dot{y} - p(t) A = 5 \ddot{y}$$

## Punto 2
Se tiene un sistema intercambiador de calor que tiene una electroválvula que permite cambiar el paso de vapor para cambiar la temperatura del horno. Se está realizando el modelamiento de la parte driver-electroválvula y se obtiene la función de transferencia de la figura. Grafique la respuesta de dicho conjunto para una entrada de 4.2 V, sabiendo que el flujo q está en cm³/s y la base de tiempo está en segundos. Señale toda la información relevante (vista en clase) en la gráfica.

[![image.png](https://i.postimg.cc/gjsHvMyT/image.png)](https://postimg.cc/MfcBwmF7)

A continuación nos piden graficar la respuesta de dicho conjunto para una entrada de 4.2 voltios hoy sabiendo que tenemos un flujo k específico y el tiempo estará en segundos para ello lo que resultará más fácil es analizar lo siguiente sabiendo que Q es el flujo y V es el voltaje, aremos las siguientes operaciones matemáticas
La función de transferencia del sistema es:

$$\frac{Q}{V} = \frac{2805.56}{s + 100}$$

Reescribiendo:

$$\frac{2805.56}{100} \cdot \frac{1}{\frac{s}{100} + 1} = \frac{28.05}{\frac{s}{100} + 1}$$

Respuesta final para una entrada de 4.2 V:

$$V_{\text{final}} = 28.05 \cdot 4.2 \, \text{V} = 117.81 \approx 119.7$$

Constantes del sistema:

$$\tau = \frac{1}{100} = 0.01$$

$$T_s = 0.04$$

Con estos resultados hoy podemos identificar mejor las partes de la gráfica y dar una respuesta al ejercicio teniendo que la gráfica correspondiente al en la transferencia de la figura es la siguiente

[![image.png](https://i.postimg.cc/2j0W7BRM/image.png)](https://postimg.cc/LhZhH5s3)

# Sistemas de segundo orden 
La estructura general del sistema de ecuaciones de segundo grado es la siguiente hoy estás ecuaciones nos ayudan aclarar un poco más los sistemas que queremos modelar o qué queremos tener en cuenta hoy también nos describe una diferencia entre los sistemas de primer orden en este caso trataremos con sistemas con una gráfica un poco más diferente, Su estructura es de la siguiente forma.

$$\ddot{y}(t) + a_1 \dot{y}(t) + a_0 y(t) = b_0 u(t)$$

Y allende la función de transferencia de dicho sistema de segundo orden tenemos que también aplicando la transformada de laplace nos queda.

$$s^2 Y(s) + a_1 s Y(s) + a_0 Y(s) = b_0 U(s)$$

Y despejando la salida/entrada

$$\frac{Y(s)}{U(s)} = \frac{b_0}{s^2 + a_1 s + a_0}$$

## Forma canónica de sistemas de segundo orden 

$$G(s) = \frac{Y(s)}{U(s)} = \frac{b_0}{s^2 + a_1 s + a_0}$$

Esta forma no permite identificar directamente los parámetros temporales del sistema por ello se utiliza la forma canónica mostrada anteriormente ya que nos ayuda a visualizar mejor ciertos parámetros que necesitamos a la hora del análisis de un sistema ya sea mecánico, hidráulico, térmico etc. La forma canónica considera lo siguiente.

$$a_1 = 2\zeta \omega_n, \quad a_0 = \omega_n^2, \quad b_0 = K \cdot \omega_n^2$$

Por lo tanto, la función de transferencia queda:

$$G(s) = \frac{Y(s)}{U(s)} = \frac{K \cdot \omega_n^2}{s^2 + 2\zeta \omega_n s + \omega_n^2}$$

Donde 

[![image.png](https://i.postimg.cc/c4mdnfpt/image.png)](https://postimg.cc/vc4RRxHG)

## Respuesta de un sistema de segundo orden con una entrada escalón
Esto se hace con el fin de ver como un sistema de segundo orden en su forma canónica es representado mediante distintas entradas como en este caso la más común un escalón esto para ver su respuesta a través del tiempo, la función de transferencia es:

$$G(s) = \frac{K \cdot \omega_n^2}{s^2 + 2\zeta \omega_n s + \omega_n^2}$$

Factorizando:

$$G(s) = \frac{K \cdot \omega_n^2}{(s + \zeta \omega_n + \omega_n \sqrt{\zeta^2 - 1})(s + \zeta \omega_n - \omega_n \sqrt{\zeta^2 - 1})}$$

Aplicando escalón:

$$Y(s) = \frac{K \cdot \omega_n^2 \cdot A}{(s + \zeta \omega_n + \omega_n \sqrt{\zeta^2 - 1})(s + \zeta \omega_n - \omega_n \sqrt{\zeta^2 - 1})s}$$

## Factor de amortiguamiento 
Es un parámetro clave en los sistemas de segundo orden que describe cómo responde el sistema ante una perturbación o entrada (por ejemplo, un escalón), comúnmente representado como ζ(zeta), para enlazarlo y verlo más explícitamente lo analizaremos con el sistema que hayamos anteriormente el cual tiene una entrada a escalón, veremos cómo nos dan 3 casos
### Si ζ=1: sistema críticamente amortiguado (se estabiliza lo más rápido posible sin oscilar).

[![image.png](https://i.postimg.cc/mkkyyYdZ/image.png)](https://postimg.cc/m1x9bHfK)

Su ecuación correspondiente es la siguiente.

$$\mathcal{L}^{-1}\{Y(s)\} = K \cdot A \cdot \left(1 - e^{-\omega_n t} (1 + \omega_n t)\right)$$

### Si ζ<1: sistema subamortiguado (oscila pero se estabiliza con el tiempo)

[![image.png](https://i.postimg.cc/FF6yQJWc/image.png)](https://postimg.cc/z3nbC31X)

Su ecuación correspondiente según la entrada escalón es la siguiente.

$$\mathcal{L}^{-1}\{Y(s)\} = K \cdot A \cdot \left( 1 - e^{-\zeta \omega_n t} \left( \cos\left(t \omega_n \sqrt{\zeta^2 - 1}\right) + \frac{\zeta}{\sqrt{\zeta^2 - 1}} sen\left(t \omega_n \sqrt{\zeta^2 - 1}\right) \right) \right)$$

### Si ζ>1: sistema sobreamortiguado (no oscila, pero tarda más en estabilizarse que uno críticamente amortiguado)

[![image.png](https://i.postimg.cc/cCt8JX93/image.png)](https://postimg.cc/y3BNQXz6)

La ecuación que describe el siguiente sistema ciento zeta mayor a uno es la siguiente.

$$\mathcal{L}^{-1}\{Y(s)\} = K \cdot A \cdot \left(1 - e^{-\left(\zeta - \sqrt{\zeta^2 - 1} \right) \omega_n t}\right)$$
