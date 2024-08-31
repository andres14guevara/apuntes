# Discretización de Controladores

En la discretización de controladores, buscamos una equivalencia entre el espacio de Laplace y el espacio Z.

## 1. Método de Invarianza al Impulso
- Se utiliza la respuesta al impulso de \( C(s) \) para obtener \( C(z) \).
- La transformada de Laplace del impulso \( e(t) = \delta(t) \) es \( e(s) = 1 \).
- Si \( C(s) \) es estrictamente propia y se asume un tiempo de muestreo \( T \) suficientemente pequeño:

  \[
  C(z) = T \cdot Z \left\{ \mathcal{L}^{-1} \{ C(s) \} \bigg|_{t=kT} \right\}
  \]

## 2. Método de Invarianza al Paso
- Sabiendo que la transformada Z de una función escalón es:

  \[
  Z \{ e(t) \} = \frac{z}{z-1}
  \]

- Se pueden igualar las transformadas inversas:

  \[
  Z^{-1} \left\{ C(z) \cdot \frac{z}{z-1} \right\} = \mathcal{L}^{-1} \left\{ C(s) \cdot \frac{1}{s} \right\}
  \]

- Resolviendo para \( C(z) \):

  \[
  C(z) = \frac{z-1}{z} Z \left\{ \mathcal{L}^{-1} \left\{ C(s) \cdot \frac{1}{s} \right\} \right\}
  \]

## 3. Método de Euler Adelante
- La aproximación discreta de la derivada es:

  \[
  \frac{d}{d(kT)}x(kT) \approx \frac{x(k+1) - x(k)}{T}
  \]

- Aplicando la transformada Z:

  \[
  sX(s) \approx \frac{z-1}{T} X(z)
  \]

  Por lo tanto:

  \[
  s \approx \frac{z-1}{T}
  \]

## 4. Método de Euler Atrás
- La aproximación discreta de la derivada es:

  \[
  \frac{d}{d(kT)}x(kT) \approx \frac{x(k) - x(k-1)}{T}
  \]

- Aplicando la transformada Z:

  \[
  sX(s) \approx \frac{1 - z^{-1}}{T} X(z)
  \]

  Por lo tanto:

  \[
  s \approx \frac{1 - z^{-1}}{T}
  \]

## 5. Teorema de Muestreo de Nyquist
- El teorema de muestreo relaciona la velocidad de muestreo \( f_s \) con la frecuencia de la señal medida.
- La velocidad de muestreo \( f_s \) debe ser mayor que el doble de la componente de frecuencia más alta en la señal.
  
  \[
  f_s > 2f_{\text{máx}}
  \]

- Esta frecuencia se conoce como la frecuencia de Nyquist.

# Ejemplos

## Ejemplo 1: Método de Euler Adelante

Dado un sistema continuo descrito por:

\[
H(s) = \frac{1}{s+1}
\]

Discretizar usando el método de Euler Adelante con un tiempo de muestreo \( T = 0.1 \).

### Solución:

1. Usamos la aproximación \( s \approx \frac{z-1}{T} \):

   \[
   H(z) = \frac{1}{\frac{z-1}{T} + 1} = \frac{T}{z-1 + T}
   \]

2. Con \( T = 0.1 \):

   \[
   H(z) = \frac{0.1}{z - 0.9}
   \]

   Este es el sistema discretizado.

## Ejemplo 2: Teorema de Muestreo de Nyquist

Supongamos que tenemos una señal de frecuencia máxima \( f_{\text{máx}} = 500 \text{ Hz} \). Determina la frecuencia mínima de muestreo requerida.

### Solución:

1. Según el teorema de muestreo de Nyquist:

   \[
   f_s > 2 \times 500 = 1000 \text{ Hz}
   \]

2. La frecuencia mínima de muestreo requerida es \( f_s > 1000 \text{ Hz} \).

# Conclusiones

- **Discretización**: La discretización de controladores es crucial para implementar sistemas de control en tiempo real. La elección del método de discretización (invarianza al impulso, invarianza al paso, métodos de Euler) afecta la precisión y estabilidad del sistema discretizado.
  
- **Método de Invarianza al Impulso**: Este método asegura que la respuesta al impulso del sistema discretizado sea idéntica a la del sistema continuo, bajo ciertas condiciones.

- **Método de Invarianza al Paso**: Ideal para sistemas donde la respuesta al escalón es de mayor interés, pero puede no preservar la estabilidad en todos los casos.

- **Métodos de Euler**: Ofrecen aproximaciones simples para discretizar sistemas, pero deben ser usados con cuidado, especialmente en sistemas donde la estabilidad es crítica.

- **Teorema de Nyquist**: Es fundamental en la discretización de señales, asegurando que la frecuencia de muestreo sea suficientemente alta para capturar toda la información relevante de la señal original sin aliasing.

Estos conceptos y métodos son fundamentales en el diseño y análisis de sistemas de control digital, permitiendo una transición efectiva entre sistemas continuos y discretos.
