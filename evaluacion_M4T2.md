# Evaluación — Módulo 4 · Tema 2: GLM con Python

**Alumno:** Alondra Abril
**Variable asignada:** `uso`  (uso)
**Fecha de entrega:** ________________

> **Instrucciones.** Este archivo evalúa las tres sesiones del tema. Las tablas ya vienen
> calculadas; tu trabajo es **responder las preguntas de interpretación** en el espacio
> "**Tu respuesta:**". Se evalúa la interpretación, no el código. Máx. 4–6 líneas por respuesta.
> Todas tus preguntas usan **tu variable asignada** (`uso`). Guarda y sube este archivo a tu repositorio.

---

## Parte 1 · Sesión 1 — Modelo de Frecuencia

**Diagnóstico del supuesto de Poisson (modelo completo):**

| métrica | valor |
| --- | --- |
| φ de Pearson | 1.1664 |
| Cameron-Trivedi α | 0.0744 |
| z | 15.80 |
| p-value | 3.7e-56 |

**Rating factors de frecuencia para `uso`** (base × RF reproduce la tasa empírica; diferencia máx = 1.7e-05):

| nivel | RF_frec | IC_inf | IC_sup | p | tasa_emp |
| --- | --- | --- | --- | --- | --- |
| Particular (ref) | 1 | 1 | 1 | 0 | 0.1393 |
| Trabajo | 0.9887 | 0.9272 | 1.0542 | 0.7281 | 0.1377 |

**P1.** ¿Se cumple la equidispersión? Justifica con φ **y** con Cameron-Trivedi, y di qué familia usarías.
**Tu respuesta: No, no se cumple la equidispersión: φ=1.1664>1 dado a que indica una varianza mayor que la media, es decir, sobredispersión. Por otro lado, Cameron-Trivedi también nos indica sobredispersión con α=0.0744 y p=3.7×10⁻⁵⁶, por lo que no se cumple la equidispersión. Sin embargo, es una sobredispersión muy pequeña (φ<1.5), por lo que yo usaría sería Quasi-Poisson, que conserva los coeficientes y ajusta los errores estándar.**

**P2.** Interpreta los rating factors de tu variable: nivel más alto y más bajo, traducidos a % de
recargo/descuento. ¿Algún IC cruza 1 o tiene p > 0.05? ¿Qué harías con ese nivel?
**Tu respuesta: El nivel con mayor frecuencia es "particular", que es la referencia RF=1 y el menor es trabajo con RF=0.9887, equivalente a un descuento de 1.13% en frecuencia respecto a particular. Sin embargo, el IC de trabajo [0.9272, 1.0542] cruza 1 y p=0.7281 > 0.05, por lo que no hay evidencia de diferencia. Por lo anterior, agruparía trabajo con particular y mantendría la referencia para la tarifa.**

**P3.** ¿Por qué el GLM one-way reproduce exactamente la tasa empírica, y qué aporta el GLM que una
tabla empírica no puede dar?
**Tu respuesta: En una poisson con liga log y offset de exposición, las ecuaciones de estimación hacen que la suma de siniestros predichos coincida con la observada por nivel, por lo que exp(η)=Σsiniestros/Σexposición, es decir, la tasa empírica. El GLM permite combinar múltiples variables de riesgo de forma multiplicativa y estimar factores de riesgo, intervalos de confianza y significancia estadística**, algo que una tabla empírica simple no proporciona.**

---

## Parte 2 · Sesión 2 — Severidad y Selección de Modelos

**Comparación de modelos de frecuencia:**

| modelo | AIC | BIC | pseudoR2_McF |
| --- | --- | --- | --- |
| Poisson | 125,081.7 | 125,261.7 | 0.0198 |
| Binomial Negativa | 124,925.7 | 125,105.8 | 0.021 |

**Rating factors de severidad (Gamma) para `uso`:**

| nivel | RF_sev | severidad_emp |
| --- | --- | --- |
| Particular (ref) | 1 | 1,310 |
| Trabajo | 0.9868 | 1,293 |

**P4.** ¿Por qué se usa **Gamma** para severidad y no una regresión lineal sobre log(Y)? (menciona la
propiedad del CV y por qué Lognormal no es GLM).
**Tu respuesta: La severidad presenta un coeficiente de variación relativamente estable entre los niveles de `uso`, compatible con una distribución Gamma. La Gamma con liga log modela directamente la severidad media (E[Y|X]), importante para tarificación. La Lognormal no pertenece a la familia exponencial utilizada por los GLM estándar, por lo que no se modela mediante un GLM. Además, una regresión sobre (\log(Y)) modela (E[\log(Y)|X]) y requiere una corrección para regresar a la escala monetaria.**

**P5.** Según la tabla de comparación, ¿qué modelo elegirías? Justifica con AIC/BIC. ¿Por qué el pseudo R²
es tan bajo y eso NO significa que el modelo sea malo?
**Tu respuesta: Según la tabla, la binomial negativa es el mejor modelo, ya que presenta menores AIC 124,925.7 y BIC 125,105.8 que Poisson. Sin embargo, en mi opinión mantendría Quasi-Poisson, porque la sobredispersión observada es leve y no justifica una binomial negativa. El pseudo-R² es cercano a 0.02, pero no implica un mal modelo, ya que la frecuencia de siniestros presenta alta variabilidad aleatoria.**

**P6.** Compara tus rating factors de frecuencia (Parte 1) con los de severidad para `uso`. ¿Apuntan en
la misma dirección? ¿Qué implica eso para separar Frecuencia × Severidad?
**Tu respuesta: Para uso, el nivel Trabajo tiene una frecuencia de 1.13% menor y una severidad de 1.32% menor que Particular, por lo que ambos efectos apuntan en la misma dirección. Sin embargo, la diferencia en frecuencia no es estadísticamente significativa IC incluye 1 y p=0.7281. Esto demuestra que una variable puede tener efectos diferentes en frecuencia y severidad, dicho lo anterior, concluyo en que ambos componentes deben modelarse por separado para calcular la prima pura.**

---

## Parte 3 · Sesión 3 — Validación y Tarifa

**Validación out-of-sample del modelo de frecuencia:**

| metrica | valor | ideal |
| --- | --- | --- |
| Gini (test) | 0.2315 | > 0.30 aceptable |
| Ratio pred/obs (test) | 1.0249 | ≈ 1.00 |

**Prima pura por nivel de `uso`** (Frecuencia × Severidad, con su factor de tarifa):

| nivel | prima_pura_modelo | factor_tarifa |
| --- | --- | --- |
| Particular (ref) | 182.53 | 1.0011 |
| Trabajo | 178.57 | 0.9794 |

**P7.** Interpreta las métricas de validación: ¿el modelo está bien calibrado (ratio pred/obs)? ¿discrimina
bien el riesgo (Gini)? ¿Qué mide cada una?
**Tu respuesta: El modelo presenta una calibración adecuada en términos globales, debido a que el ratio predicción/observación es 1.0249 lo cual es cercano a uno, aunque sobreestima ligeramente los siniestros en 2.49%. Por otro lado, el Gini es de 0.2315 lo cual indica una discriminación menor al 0.30 orientativo. En conjunto, el modelo es razonablemente el volumen esperado, pero tiene capacidad limitada para diferenciar entre riesgos de distinta frecuencia.**

**P8.** Lee la tabla de tarifa: ¿qué nivel de tu variable paga la prima pura más alta y cuál la más baja?
Traduce el factor de tarifa a un recargo/descuento sobre la prima promedio.
**Tu respuesta: Particular es el nivel de referencia y presenta un factor tarifario de 1.0011, trabajo tiene un factor de 0.9794, lo que representa un descuento aproximado de 2.06% respecto a la referencia. Esto es consistente con su menor prima pura: $178.57 frente a $182.53 en particular. Por lo que, el uso trabajo genera una prima de tarifa ligeramente menor.**

**P9. (Conclusión de nota técnica).** En 3–4 líneas, redacta cómo `uso` afecta la tarifa, integrando
frecuencia, severidad y prima pura, en estilo defendible ante la CNSF.
**Tu respuesta: La variable uso se muestra diferencias pequeñas entre particular y trabajo. Trabajo presenta una frecuencia menor de  1.13% y una severidad menor de 1.32% que particular, sin embargo, la diferencia en frecuencia no es estadísticamente significativa pues IC 95%: 0.9272–1.0542. En consecuencia, su prima pura resulta 2.17% menor ($178.57 vs. $182.53), por lo que el factor tarifario de trabajo puede mantenerse ligeramente por debajo de uno, sujeto a monitoreo de experiencia.**

---
*Evaluación generada automáticamente · Diplomado ML en Seguros · FC UNAM · Módulo 4 · Tema 2*
