# Apuntes sistemas de control 1 
### Rincon Benavides Juan Esteban 
### Avila Rojas Nestor Alexander 
## Sistemas de Primer Orden
>🔑​Un sistema de primer orden es aquel cuya dinámica puede ser descrita por una ecuación diferencial de primer orden. En el dominio de Laplace, su función de transferencia tiene un único polo.
>La forma general de la función de transferencia de un sistema de primer orden es:
>$$\frac{K}{ts + 1}$$
>
**Donde:**
- K es la ganancia del sistema.
- τ es la constante de tiempo del sistema, que determina la rapidez con la que el sistema responde a un cambio en su entrada.
## Sistemas de Segundo orden 
>🔑Un sistema de segundo orden es aquel cuya dinámica puede ser descrita por una ecuación diferencial de segundo orden. En el dominio de Laplace, su función de transferencia tiene dos polos.
>La forma general de la función de transferencia de un sistema de segundo orden es:  $$\frac{w^2n}{s^2 + 2ζw_n s + w^2n}$$
>
Donde:

- **ω_n** es la frecuencia natural no amortiguada del sistema, que indica la frecuencia de oscilación del sistema sin amortiguamiento.
- **ζ** es el coeficiente de amortiguamiento (damping ratio), que determina el tipo de respuesta del sistema.

## Tipos de respuesta de un sistema de segundo orden según el valor de ζ:

- Sobreamortiguado (ζ>1): La respuesta es lenta y no presenta oscilaciones. El sistema regresa al equilibrio lentamente.
  
![image](https://github.com/user-attachments/assets/520d119c-1e07-44fa-b7e2-784fd66d07b8)

- Críticamente amortiguado (ζ=1): El sistema regresa al equilibrio lo más rápido posible sin oscilaciones.

  ![image](https://github.com/user-attachments/assets/17316017-8fa6-46f4-b280-a2939cd1881e)

- Subamortiguado (0<ζ<1): La respuesta oscila alrededor del valor final antes de establecerse. La amplitud de las oscilaciones disminuye con el tiempo.
  
![image](https://github.com/user-attachments/assets/8e641c60-d5cd-4f4b-8419-48229a744476)

## EJEMPLOS:

💡 1. Cual es la respuesta esperada para el siguiente sistema:
$$\frac{25}{s^2 + 10s + 25}$$

**Identifica $w^2n$ y calcula $w_n$:**
- comparando con la formula general se tiene que w^2n = 25 por lo tanto.
  $$wn =\sqrt{25} = 5$$
**Identifica $2ζw_n$ y calcula ζ:**
- Tenemos que $2ζw_n = 10$. sustituyendo el valor de $w_n$:
  $$2ζ(5)=10$$
  $$10ζ=10$$
  $$ζ=\frac{10}{10} = 1$$
**Determinar el tipo de respuesta:**
  Como ζ=1, la respuesta del sistema es críticamente amortiguada.
  
💡 2. Cual es la respuesta esperada para el siguiente sistema:
$$\frac{9}{s^2 + 3s + 9}$$

**Identifica $w^2n$ y calcula $w_n$:**
- comparando con la formula general se tiene que w^2n = 9 por lo tanto.
  $$wn =\sqrt{9} = 3$$
**Identifica $2ζw_n$ y calcula ζ:**
- Tenemos que $2ζw_n = 3$. sustituyendo el valor de $w_n$:
  $$2ζ(3)=3$$
  $$6ζ=3$$
  $$ζ=\frac{3}{6} = 0.5$$
**Determinar el tipo de respuesta:**
  Como ζ=0.5, la respuesta del sistema es sub-amortiguada.
## Ejercicios 
📚1. Ejercicio: Dada la siguiente función de transferencia:

$$\frac{4}{s^2 + 5s + 4}$$

**Identifica $w^2n$ y calcula $w_n$:**
- comparando con la formula general se tiene que w^2n = 4 por lo tanto.
  $$wn =\sqrt{4} = 2$$
**Identifica $2ζw_n$ y calcula ζ:**
- Tenemos que $2ζw_n = 5$. sustituyendo el valor de $w_n$:
  $$2ζ(2)=5$$
  $$4ζ=5$$
  $$ζ=\frac{5}{4} = 1.25$$
**Determinar el tipo de respuesta:**
  Como ζ=1.25, la respuesta del sistema es **sobreamortiguada.**
  
  ![image](https://github.com/user-attachments/assets/d68b92f0-97bc-46a6-98b7-58ef9adf588d)

**codigo MatLab:**
```
% Definir numerador y denominador
num = 4;
den = [1 5 4];

% Crear función de transferencia
G = tf(num, den);

% Graficar respuesta al escalón
step(G)
title('Respuesta al escalón de G(s) = 4 / (s^2 + 5s + 4)')
xlabel('Tiempo [s]')
ylabel('Amplitud')
grid on

```

📚2. Ejercicio: Dada la siguiente función de transferencia:

$$\frac{16}{s^2 + 16}$$

**Identifica $w^2n$ y calcula $w_n$:**
- comparando con la formula general se tiene que w^2n = 16 por lo tanto.
  $$wn =\sqrt{16} = 4$$
**Identifica $2ζw_n$ y calcula ζ:**
- Tenemos que $2ζw_n = 0 $. sustituyendo el valor de $w_n$:
  $$2ζ(4)=0$$
  $$8ζ=0$$
  $$ζ=\frac{0}{8} = 0 $$
**Determinar el tipo de respuesta:**
  Como ζ=0, la respuesta del sistema es **no amortiguada.** Se espera una oscilación continua a la frecuencia natural (ωn=4 rad/s) ante una entrada escalón.
  
![image](https://github.com/user-attachments/assets/46087e70-6641-46aa-84c0-9982aeacd276)

Imagen 1. grafica respuesta del sistema con escalon unitario

La salida y(t) oscila como 1−cos(4t), con una frecuencia natural de 4 rad/s, sin amortiguamiento

## Sistemas de orden superior
Los sistemas de orden superior son aquellos cuya dinámica está descrita por ecuaciones diferenciales de orden tres o superior, o equivalentemente, cuya función 
de transferencia tiene tres o más polos. Aunque los sistemas de primer y segundo orden son bloques de construcción fundamentales y proporcionan mucha intuición 
sobre el comportamiento de los sistemas dinámicos, muchos sistemas reales son inherentemente de orden superior debido a la presencia de múltiples componentes de 
almacenamiento de energía o subsistemas interconectados.
