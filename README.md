# Resumen: Función en términos de muestras, Representación matemática de los sistemas, y Transformada Z

## 1. Función en términos de muestras

En la semana dos se inició con el tema de "Función en términos de muestras", donde se explicó que si se tiene una función continua 𝑓(𝑡) y se quiere expresar matemáticamente su equivalente discreto, esto se debe hacer mediante la toma de muestras a intervalos regulares (tiempo de muestreo). Por ejemplo, si se tiene una función seno, para expresarla como una función discreta, se debe tomar el valor de la función en determinados intervalos de tiempo.

Como se muestra en las imágenes, a partir de la función \( y(t) = 5\sin(1.04t) \) se toma una muestra cada 0.5 segundos. Este intervalo de tiempo puede variar; al ser más pequeño, se obtiene una muestra más precisa de la función, mientras que con un intervalo más grande, la discretización será menos exacta.

## 2. Representación matemática de los sistemas

Para llegar al punto anterior y poder realizar una discretización de una función, dependemos de una función de transferencia, la cual a su vez depende de representaciones matemáticas.

### 2.1 Ecuaciones en Diferencia

Al analizar estas ecuaciones, notamos que tienen términos como 'u' (entrada) y 'y' (salida). La dinámica del sistema se representa a través de una combinación lineal de estos términos, reflejando el comportamiento dinámico del sistema.

Las ecuaciones en diferencia pueden ser homogéneas, lineales, o invariantes en el tiempo. Para solucionarlas, se suele emplear un método interactivo, que consiste en tomar muestras anteriores o adelantadas y reemplazar los términos correspondientes.

## 3. Transformada Z

La transformada Z permite obtener una expresión matemática para solucionar ecuaciones de sistemas discretos. A diferencia de la transformada de Laplace, la transformada Z opera en un espacio diferente.

### Pasos para la solución de ecuaciones en diferencias utilizando la transformada Z:
  - Aplicar la transformada Z a la ecuación.
  - Despejar la variable desconocida o salida del sistema.
  - Aplicar la transformada Z inversa.

En las ecuaciones en diferencia, tenemos términos como \( f(k+n) \) o \( f(k-n) \). 
- La función \( f(k-n) \) se denomina atraso.
- La función \( f(k+n) \) se denomina adelanto.

# Conclusiones

1. **Importancia de la Discretización**: La discretización de funciones continuas, como las senoidales, es esencial para analizar y controlar sistemas en el dominio digital. A través del muestreo, se puede obtener una representación discreta que permite el procesamiento digital de señales. Es fundamental elegir un tiempo de muestreo adecuado para garantizar la precisión de la representación discreta.

2. **Transformada Z como Herramienta Clave**: La transformada Z es una herramienta indispensable para analizar sistemas discretos. Permite convertir ecuaciones en diferencia, que describen el comportamiento dinámico de sistemas discretos, en expresiones algebraicas más manejables. Esto facilita la solución de dichas ecuaciones y, por ende, el análisis de la estabilidad y respuesta de sistemas digitales.

3. **Representación Matemática de Sistemas**: La representación matemática de sistemas a través de ecuaciones en diferencia es crucial para el modelado y análisis de sistemas dinámicos. La correcta formulación de estas ecuaciones permite predecir el comportamiento del sistema bajo diversas condiciones de entrada y ayuda a diseñar controladores eficaces.

# Ejemplo 1: Discretización de una Función Senoidal

Supongamos que tenemos la función continua \( y(t) = 3\sin(2t) \). Queremos discretizar esta función tomando muestras cada 0.25 segundos.

1. **Función Continua**: \( y(t) = 3\sin(2t) \)
2. **Tiempo de Muestreo**: \( T_s = 0.25 \) s
3. **Función Discreta**: \( y[k] = 3\sin(2 \times 0.25k) = 3\sin(0.5k) \)

Por lo tanto, la función discreta sería \( y[k] = 3\sin(0.5k) \). A medida que se incrementa \( k \), se obtienen los valores de la señal en momentos discretos.

# Ejemplo 2: Solución de una Ecuación en Diferencias usando la Transformada Z

Consideremos la siguiente ecuación en diferencias:

\[
y(k) - \frac{1}{2}y(k-1) = u(k)
\]

donde \( u(k) \) es la entrada al sistema y \( y(k) \) es la salida.

**Paso 1: Aplicar la Transformada Z**

Aplicamos la transformada Z a ambos lados de la ecuación:

\[
Y(z) - \frac{1}{2}z^{-1}Y(z) = U(z)
\]

**Paso 2: Despejar la variable desconocida \( Y(z) \)**

\[
Y(z)\left(1 - \frac{1}{2}z^{-1}\right) = U(z)
\]

\[
Y(z) = \frac{U(z)}{1 - \frac{1}{2}z^{-1}}
\]

**Paso 3: Aplicar la Transformada Z Inversa**

La transformada Z inversa nos da la solución en el dominio del tiempo discreto:

\[
y(k) = \frac{1}{2}^k u(k)
\]

Esta solución describe cómo la salida \( y(k) \) evoluciona en función de la entrada \( u(k) \) y el número de muestras \( k \).
