# Espacio de Estados

El espacio de estados es una representación matemática de los sistemas dinámicos que no solamente considera las entradas y salidas sino también otras variables que pueden ayudar a representar de mejor manera la dinámica del sistema.
![](https://github.com/andres14guevara/apuntes/blob/main/cohete.jpg)
## Conceptos Principales

### Representación Interna
- También se conoce como **representación interna**.
- La función de transferencia también es conocida como una forma de describir el **espacio de estados**.

### Variables de Estado
- Las **variables de estado** son las variables que determinan el comportamiento de un sistema.
- Estas variables no necesariamente deben ser medibles. Sin embargo, varios de los métodos de control en espacio de estados exigen que estas variables sean medibles.

### Ecuaciones de Estado
- Al combinar las variables de estado mediante operadores matemáticos, se generan varias ecuaciones.
- La combinación de dichas ecuaciones constituye un espacio geométrico denominado **espacio de estados**.

## Representación Matemática
![](https://github.com/andres14guevara/apuntes/blob/main/ecuaciones.png)

El análisis en frecuencia y los diagramas de Bode son herramientas poderosas para entender el comportamiento de sistemas dinámicos. A través de la separación de las componentes de magnitud y fase, podemos observar cómo las señales se modifican en términos de la frecuencia de entrada.

- **Métodos de Euler**: Ofrecen aproximaciones simples para discretizar sistemas, pero deben ser usados con cuidado, especialmente en sistemas donde la estabilidad es crítica.

- **Teorema de Nyquist**: Es fundamental en la discretización de señales, asegurando que la frecuencia de muestreo sea suficientemente alta para capturar toda la información relevante de la señal original sin aliasing.

Estos conceptos y métodos son fundamentales en el diseño y análisis de sistemas de control digital, permitiendo una transición efectiva entre sistemas continuos y discretos.

# Construcción del Espacio de Estados a partir de una Ecuación en Diferencias

Este documento explica la metodología para construir un espacio de estados desde una ecuación en diferencias y su representación en matrices. Además, se proporcionan las ecuaciones clave y los pasos necesarios para la implementación.

## Ecuación Diferencial
\[
u(t) - F_k - F_B = m \cdot a
\]

## Imagen Relacionada
_Aquí puedes subir una imagen que explique o detalle la ecuación en diferencias._

![]([ruta/imagen.png](https://github.com/andres14guevara/apuntes/blob/main/2%20parte%20primera%20imagen.png))

---

## Discretización de la Ecuación Diferencial

\[
M Y(k+2) - 2M Y(k+1) + M Y(k) + B T Y(k+1) - B T Y(k) + T^2 K Y(k) = U(k) T^2
\]

Simplificando:
\[
M Y(k+2) + (B T - 2M) Y(k+1) + (M - B T + T^2 K) Y(k) = U(k) T^2
\]

---

## Metodología

1. **Despejar el máximo adelanto de la ecuación en diferencias.**
2. **Igualar la salida a la variable de estado.**
3. **Aplicar adelantos sucesivamente para obtener las derivadas de las variables de estado.**
4. **Organizar los términos en las matrices \( A \), \( B \), \( C \), y \( D \).**

---

## Aplicación

### Procedimiento

1. Despejar el máximo adelanto:
   \[
   M Y(k+2) + (B T - 2M) Y(k+1) + (M - B T + T^2 K) Y(k) = U(k) T^2
   \]

2. Igualar la salida a la variable de estado:
   \[
   M Y(k) = x_1(k)
   \]
   \[
   M Y(k+1) = x_1(k+1) = x_2(k)
   \]

3. Ecuaciones de estado:
   - **Ecuación de estado 1**:
     \[
     x_1(k+1) = x_2(k)
     \]
   - **Ecuación de estado 2**:
     \[
     x_2(k+1) = M Y(k+2)
     \]

---

## Construcción de las Matrices de Estado

_Aquí puedes subir una imagen que muestre las matrices A, B, C y D._

![Espacio para imagen](ruta/matrices.png)

### Representación Matemática

La representación en espacio de estados se organiza en las siguientes matrices:

- Matriz \( A \): Describe las dinámicas internas del sistema.
- Matriz \( B \): Representa las entradas al sistema.
- Matriz \( C \): Relaciona las salidas del sistema con el vector de estado.
- Matriz \( D \): Representa la relación directa entre entrada y salida.


