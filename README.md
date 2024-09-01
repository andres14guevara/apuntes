# Estabilidad en Sistemas Discretos

## 1. Estabilidad Absoluta
Un sistema es estable cuando su salida es limitada ante una entrada limitada. En otras palabras, si se aplica una entrada escalón, la respuesta del sistema debe tener las mismas características de la entrada.

## 2. Espacio de LaPlace vs Espacio Z
- Aunque el concepto de estabilidad es el mismo, la ubicación de polos y ceros se comporta de manera diferente en los espacios de LaPlace y Z.
- **Espacio de LaPlace**: La frontera de estabilidad es el eje vertical.
- **Espacio Z**: La frontera de estabilidad es un círculo de radio uno centrado en el origen del plano complejo.

## 3. Estabilidad Asintótica
Un sistema es asintóticamente estable si su respuesta a cualquier conjunto de condiciones iniciales decae a cero asintóticamente en estado estable.

\[
\lim_{k \to \infty} y[k] = 0
\]

## 4. Estabilidad BIBO (Bounded Input - Bounded Output)
Un sistema tiene estabilidad BIBO si su respuesta a una entrada acotada permanece acotada. Es decir, para cualquier entrada acotada, la salida satisface:

\[
|y[k]| \leq b_y \quad \text{para } k = 0, 1, 2, \dots
\]

Donde \( b_y \) es un número real o complejo que actúa como cota para \( y[k] \).

## 5. Test de Jury
Para determinar la estabilidad de un sistema, se utiliza el Test de Jury, que evalúa el polinomio característico de la función de transferencia en Z:

\[
D(z) = a_0 z^n + a_1 z^{n-1} + \dots + a_{n-1} z + a_n
\]

El sistema es estable si se cumplen todas las siguientes condiciones:
- \( a_0 > 0 \)
- \( a_n < a_0 \)
- \( P(z) |_{z=1} > 0 \)
- \( P(z) |_{z=-1} > 0 \) (si \( n \) es par) o \( P(z) |_{z=-1} < 0 \) (si \( n \) es impar)
- Construir y verificar el arreglo de Jury.

# Ejemplos

## Ejemplo 1: Estabilidad Asintótica

Considera un sistema discreto con la siguiente ecuación de diferencia:

\[
y[k+1] = 0.5y[k]
\]

### Solución:

1. Para verificar la estabilidad asintótica, observamos que:

   \[
   \lim_{k \to \infty} y[k] = \lim_{k \to \infty} 0.5^k y[0] = 0
   \]

   Como la salida decae a cero, el sistema es asintóticamente estable.

## Ejemplo 2: Test de Jury

Dado un polinomio característico:

\[
D(z) = z^2 - 0.5z + 0.25
\]

### Solución:

1. Comprobamos las condiciones del Test de Jury:
   - \( a_0 = 1 > 0 \)
   - \( a_2 = 0.25 < a_0 \)
   - \( P(z) |_{z=1} = 1 - 0.5 + 0.25 = 0.75 > 0 \)
   - \( P(z) |_{z=-1} = 1 + 0.5 + 0.25 = 1.75 > 0 \)

   Cumpliendo todas las condiciones, el sistema es estable.

# Conclusiones

- **Estabilidad Absoluta**: Garantiza que el sistema responda de manera controlada ante entradas limitadas, esencial para sistemas de control en tiempo real.
  
- **Espacios de LaPlace vs Z**: La representación en el espacio Z es más adecuada para sistemas discretos, con la estabilidad determinada por la ubicación de los polos dentro del círculo unitario.

- **Estabilidad Asintótica**: Es una propiedad deseable en muchos sistemas, asegurando que la salida decaiga a cero con el tiempo.

- **Estabilidad BIBO**: Importante en aplicaciones donde es crucial que las salidas permanezcan dentro de límites aceptables para entradas acotadas.

- **Test de Jury**: Es una herramienta efectiva para evaluar la estabilidad de sistemas discretos mediante la evaluación de su polinomio característico.

Estos conceptos son fundamentales en el análisis y diseño de sistemas discretos, asegurando que se comporten de manera estable y predecible bajo diversas condiciones.

