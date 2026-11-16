# Resumen — Laboratorio 2 (Semana 14)

**Estudiante:** Sergio David Vargas Garzón  
**ID Estudiante:** 28 | **Semilla:** 1028 | **Huella de muestra:** `5ba650737e6f`

\---

## 1\. Reducción de Dimensionalidad (PCA)

* **Variables numéricas iniciales:** 24
* **Componentes principales retenidas ($\\ge 90%$ varianza):** 15 componentes (90.54% de varianza exacta explicada).
* **Análisis:** PCA comprime la colinealidad entre variables numéricas (como peso, volumen, precios y fletes) manteniendo el 90% de la dispersión geométrica. Sin embargo, maximizar varianza no garantiza conservar toda la señal discriminante de la clase minoritaria (`is\\\_late`), pudiendo descartar información sutil contenida en direcciones de baja varianza.

\---

## 2\. Comparación de Experimentos y Costo Empresarial

Todos los modelos se evaluaron sobre la partición de validación (`n = 5250`) con `class\\\_weight='balanced'` y umbral de `0.50`:

|Experimento|PCA|C|Accuracy|Precision|Recall|F1|AP|FP|FN|Costo\_BRL|
|-|-|-|-|-|-|-|-|-|-|-|
|A. Referencia (Sin PCA, C=1.0)|No|1.0|0.6644|0.1212|0.6338|0.2034|0.1387|1632|130|17606|
|B. PCA 90% (C=1.0)|Sí (90%)|1.0|0.6541|0.1112|0.5887|0.1871|0.1252|1670|146|18470|
|C. PCA 90% + Mayor reg (C=0.1)|Sí (90%)|0.1|0.655|0.1132|0.6|0.1904|0.1234|1669|142|18322|
|D. PCA 90% + Menor reg (C=10.0)|Sí (90%)|10.0|0.6535|0.1123|0.5972|0.189|0.1246|1676|143|18413|

* **Efecto de PCA (B vs. A):** El modelo sin PCA obtuvo un F1 de **0.2034** y costo de **R$ 17,606**, frente al modelo con PCA (C=1.0) con F1 de **0.1871** y costo de **R$ 18,470**.
* **Elección empresarial:** Se selecciona el experimento **A. Referencia (Sin PCA, C=1.0)**, ya que minimiza el impacto financiero en validación con un costo total de **R$ 17,606** (FP: 1632, FN: 130), priorizando la reducción de falsos negativos (R$ 35 c/u) frente a falsas alarmas (R$ 8 c/u).

\---

## 3\. Validación Estadística (Prueba Kolmogorov-Smirnov)

* **Variable evaluada:** `valor\\\_flete` entre entrenamiento (`n = 24500`) y validación (`n = 5250`).
* **Hipótesis:** $H\_0$: ambas muestras provienen de la misma distribución; $H\_1$: las distribuciones difieren ($
* lpha = 0.05$).
* **Resultados:** Estadístico $D = 0.01822$, valor $p = 0.11199$ $
ightarrow$ **No rechazar H0**.
* **Interpretación y limitación:** Con un nivel de significancia del 5%, no se dispone de evidencia estadística suficiente para afirmar que las distribuciones de `valor\\\_flete` difieran entre particiones (lo cual no demuestra equivalencia exacta). Como limitación metodológica, la prueba KS asume distribuciones continuas sin empates (mientras que los montos monetarios presentan valores repetidos por redondeo) y evalúa únicamente la similitud marginal de una variable, sin medir la capacidad predictiva de los clasificadores.

