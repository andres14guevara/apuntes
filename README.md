# Análisis en Frecuencia y Diagramas de Bode

## Introducción

El análisis en frecuencia es una técnica fundamental para estudiar sistemas dinámicos. Consiste en verificar el comportamiento de un sistema en la salida a partir de cambios en la frecuencia de la señal de entrada. Esto es comúnmente realizado aplicando señales sinusoidales a la entrada.

La señal sinusoidal se puede expresar como:

`R = A * sin(ω * kT + θ)`

Donde:
- `A` es la amplitud,
- `ω` es la frecuencia angular,
- `kT` es el tiempo discreto,
- `θ` es la fase.

Al variar la frecuencia de la señal de entrada, se observan cambios en la amplitud y fase de la señal de salida.

---

## Análisis en Fasores

Las señales sinusoidales también se pueden representar como **fasores**, lo cual simplifica el análisis de sistemas lineales. Los fasores representan una señal en términos de su amplitud y fase, asumiendo una frecuencia constante.

### Sistema en Fasores

Consideremos un sistema donde la entrada y salida son representadas como fasores:

`G(s) = (A2 ∠ φ2) / (A1 ∠ φ1) = M ∠ φ`

Donde:
- `M = A2 / A1` es la magnitud relativa entre la entrada y la salida,
- `φ = φ2 - φ1` es la diferencia de fase entre la entrada y salida.

---

## Expresar Función de Transferencia en Términos de la Frecuencia

Para analizar un sistema continuo en términos de la frecuencia, utilizamos la transformada de Laplace `s = jω`, y el mapeo de polos y ceros se expresa como:

`z = e^(sT)`

Por lo tanto, en términos de la frecuencia, la variable `z` es:

`z = e^(jωT)`

---

## Ejemplo de Función de Transferencia

Consideremos una función de transferencia con un tiempo de muestreo de 0.1 segundos:

`H(z) = 1 / [(z - 0.1)(z - 5)]`

Expresada en el dominio de la frecuencia:

`H(e^(jωT)) = 1 / [(e^(jωT) - 0.1)(e^(jωT) - 5)]`

---

## Efecto de Parámetros Dinámicos

No es posible hacer análisis en frecuencia directamente en tiempo discreto, por lo que se aprovecha la transformación bilineal (Tustin) para aproximar el sistema continuo en tiempo discreto.

Reemplazando `z = e^(jωT)`, se obtiene:

`w = 2 * (z - 1) / [T * (z + 1)]`

Sustituyendo `w = jv`, resulta:

`w = j * (2 / T) * tan(ωT / 2)`

Y:

`v = (2 / T) * tan(ωT / 2)`

Si se tiene un sistema en tiempo continuo, por ejemplo:

`G(s) = 1 / (s + 10)`

Se puede obtener la aproximación discreta (ZOH) con `T = 0.1` segundos, y aplicar la transformada `w`:

`G(z) = 0.06321 / (z - 0.3679)`

Y transformando en `w`:

`G(w) = 0.924(-0.05w + 1) / (w + 9.242)`

---

## Diagramas de Bode

Los **diagramas de Bode** son gráficos que muestran cómo la magnitud de la ganancia y el ángulo de desfase de un sistema varían con respecto a la frecuencia de la señal de entrada. Estos diagramas son útiles para el análisis de estabilidad y el diseño de compensadores en sistemas de control.

### Características:
- Usualmente se presentan en **escala logarítmica**.
- En sistemas discretos, es importante considerar que los compensadores pierden eficacia en frecuencias altas debido a la transformada `w`.
- La aproximación de la transformada `w` es válida entre 0 y la **frecuencia de Nyquist**.

### Cálculo de Ganancia:

Los **decibelios** (dB) se utilizan para representar la ganancia o potencia. Para la ganancia, se utiliza la siguiente fórmula:

`AdB = 20 * log10(A)`

### Ejemplo de Diagrama de Bode:

![Diagrama de Bode]([ruta/a/tu/imagen.png](https://github.com/andres14guevara/apuntes/blob/main/Captura%20de%20pantalla%202024-10-05%20191749.png)

---

## Conclusiones

El análisis en frecuencia y los diagramas de Bode son herramientas poderosas para entender el comportamiento de sistemas dinámicos. A través de la separación de las componentes de magnitud y fase, podemos observar cómo las señales se modifican en términos de la frecuencia de entrada.

- **Métodos de Euler**: Ofrecen aproximaciones simples para discretizar sistemas, pero deben ser usados con cuidado, especialmente en sistemas donde la estabilidad es crítica.

- **Teorema de Nyquist**: Es fundamental en la discretización de señales, asegurando que la frecuencia de muestreo sea suficientemente alta para capturar toda la información relevante de la señal original sin aliasing.

Estos conceptos y métodos son fundamentales en el diseño y análisis de sistemas de control digital, permitiendo una transición efectiva entre sistemas continuos y discretos.
