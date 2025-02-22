# Introducción a la Cimática y Simulación de Figuras de Chladni

## ¿Qué es la Cimática?
La **cimática** es el estudio de los patrones visibles que se forman cuando un medio (como arena, sal o agua) es sometido a vibraciones sonoras. Fue popularizado por Hans Jenny en el siglo XX, pero sus raíces se remontan a los experimentos de Ernst Chladni en el siglo XVIII. Chladni usó placas metálicas cubiertas de arena y las hizo vibrar con un arco de violín, observando cómo las partículas se acumulaban en líneas donde la vibración era mínima (**nodos**), formando figuras geométricas conocidas como **figuras de Chladni**.

Estas figuras dependen de la frecuencia de vibración y de las propiedades de la placa (como su forma, tamaño y material). En este documento, simulamos estas figuras para una placa cuadrada de acero usando Python.

---

## Descripción del Código
El código simula figuras de Chladni en una placa cuadrada de acero de 20 cm de lado. Genera partículas que representan arena y las coloca en los nodos de vibración, mostrando cómo cambian los patrones al variar los modos de vibración ($m$, $n$). Además, calcula y muestra la frecuencia en hercios (Hz) para cada modo.

### Parámetros de la Placa
- Longitud del lado: $a = 0.2 \, \text{m}$ (20 cm)
- Espesor: $h = 0.001 \, \text{m}$ (1 mm)
- Módulo de Young (acero): $E = 200 \times 10^9 \, \text{Pa}$
- Coeficiente de Poisson: $\nu = 0.3$
- Densidad: $\rho = 7850 \, \text{kg/m}^3$
- Número de partículas: 5000

---

## Fórmulas Principales

1. **Rigidez a la Flexión ($D$)**  
   La rigidez de la placa se calcula como:
   $$
   D = \frac{E h^3}{12 (1 - \nu^2)}
   $$
   Donde $D$ mide la resistencia de la placa a la flexión y depende del material y el espesor.

2. **Velocidad Efectiva ($c_{\text{effective}}$)**  
   Esta constante relaciona las propiedades del material con la propagación de las ondas:
   $$
   c_{\text{effective}} = \sqrt{\frac{D}{\rho h}}
   $$

3. **Frecuencia de Vibración ($f_{mn}$)**  
   La frecuencia en Hz para cada modo $(m, n)$ en una placa cuadrada con bordes simplemente apoyados es:
   $$
   f_{mn} = \frac{\pi}{2} c_{\text{effective}} \left( \left( \frac{m}{a} \right)^2 + \left( \frac{n}{a} \right)^2 \right)
   $$
   Aquí, $m$ y $n$ son números enteros positivos que indican el número de nodos en las direcciones $x$ e $y$.

4. **Amplitud de Vibración ($U(x, y)$)**  
   La forma de las figuras de Chladni está dada por:
   $$
   U(x, y) = \sin\left( \frac{m \pi x}{a} \right) \sin\left( \frac{n \pi y}{a} \right)
   $$
   Las partículas se acumulan en los **nodos**, donde $U(x, y) \approx 0$.

---

## ¿Cómo Funciona el Código?
1. **Cálculo de Frecuencias**: Genera una lista de modos $(m, n)$ (de 1 a 5) y calcula sus frecuencias usando la fórmula de $f_{mn}$.
2. **Simulación de Partículas**: Coloca 5000 partículas aleatoriamente en la placa y muestra solo las que están cerca de los nodos (donde $|U| < 0.05$).
3. **Interactividad**: Usa un deslizador para cambiar entre modos y ver cómo varían los patrones y las frecuencias.

Por ejemplo, para el modo fundamental ($m = 1$, $n = 1$):
- $f_{11} \approx 120 \, \text{Hz}$ (verificado con los parámetros dados).

Ejecuta el código en este notebook para explorar los patrones de Chladni de forma interactiva.
