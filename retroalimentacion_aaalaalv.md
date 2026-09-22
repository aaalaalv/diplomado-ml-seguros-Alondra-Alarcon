# Retroalimentación — Alondra Alarcón
**Repo:** https://github.com/aaalaalv/diplomado-ml-seguros-Alondra-Alarcon
**Fecha de evaluación:** 2026-05-12
**Calificación final:** 10.0 / 10

## Resumen general
Excelente entrega.

## Desglose por sesión

### Sesión 1 — Instalación y configuración de Python — 1/1 pt
Archivo: `diplomado-ml-seguros-Alondra-Alarcon\modulo 1\sesion1\sesion1_M1_ejercicio.ipynb`. 32 de 32 celdas de código con contenido ejecutable.

### Sesión 2 — Tipos de datos básicos — 1/1 pt
Archivo: `diplomado-ml-seguros-Alondra-Alarcon\modulo 1\sesion2\sesion2_M1_notebook.ipynb`. 24 de 24 celdas de código con contenido ejecutable.

### Sesión 3 — Estructuras de datos + control de flujo — 1/1 pt
Archivo: `diplomado-ml-seguros-Alondra-Alarcon\modulo 1\sesion3\sesion3_M1_notebook.ipynb`. 29 de 29 celdas de código con contenido ejecutable.

### Sesión 4 — Funciones — 1/1 pt
Archivo: `diplomado-ml-seguros-Alondra-Alarcon\modulo 1\sesion4\sesion4_M1_notebook.ipynb`. 21 de 22 celdas de código con contenido ejecutable.

### Sesión 5 — Módulos / funciones avanzadas — 2.00/2 pts
Archivo: `diplomado-ml-seguros-Alondra-Alarcon\modulo 1\sesion5\sesion5_M1_notebook.ipynb`.
- Notebook ejecutable: **0.5/0.5**
- Ejercicios completos: **0.5/0.5**
- Resultados correctos: **1.0/1.0**
- Las 3 tareas integradoras tienen código.
- Notebook ejecuta end-to-end sin errores.

### Sesión 6 — Módulos propios + inicio de Pandas — 2.0/2 pts
Archivo: `diplomado-ml-seguros-Alondra-Alarcon\modulo 1\sesion6\sesion6_M1_notebook.ipynb`.
- Notebook ejecutable: **0.5/0.5**
- Ejercicios completos: **0.5/0.5**
- Resultados correctos: **1.0/1.0**  _(re-evaluado con comparación numérica estricta contra canónico)_
  - Tarea 1: ✓ correcta (inferida — la tarea final integradora produce el resultado esperado)
  - Tarea 2: ✓ correcta (inferida — la tarea final integradora produce el resultado esperado)
  - Tarea 3: ✓ correcta (13/14 números coinciden)

### Sesión 7 — Pandas avanzado — 2.0/2 pts
Archivo: `diplomado-ml-seguros-Alondra-Alarcon\modulo 1\sesion7\sesion7_M1_notebook.ipynb`.
- Notebook ejecutable: **0.5/0.5**
- Ejercicios completos: **0.5/0.5**
- Resultados correctos: **1.0/1.0**  _(re-evaluado con comparación numérica estricta contra canónico)_
  - Tarea 1: ✓ correcta (15/15 números coinciden)
  - Tarea 2: ✓ correcta (16/18 números coinciden)
  - Tarea 3: ✓ correcta (30/30 números coinciden)
  - Tarea 4: ✓ correcta (15/15 números coinciden)


## Parte 2 — Sesiones 8 y 11

### Sesión 8 — Pipeline Completo — 1.76/2 pts
*(solo se evaluó el Ejercicio Integrador Final)*
- Corre hasta el Integrador: 0.50/0.5
- Integrador Final, 5 fases: 1.26/1.5
  - FASE 1: 1.00*0.3 = 0.30 (numeros coinciden (80% de canon cubierto))
  - FASE 2: 0.80*0.3 = 0.24 (coinciden algunos numeros clave (20%))
  - FASE 3: 0.70*0.3 = 0.21 (codigo extenso (57 lineas) ejecuta; printeos no coinciden con canonico)
  - FASE 4: 0.90*0.3 = 0.27 (mayoria de numeros coinciden (34%))
  - FASE 5: 0.80*0.3 = 0.24 (coinciden algunos numeros clave (22%))

### Sesión 11 — Práctica Final — 6.95/8 pts
*(solo se evaluó el Ejercicio Integrador Final "Mini Pricing Actuarial")*
- Corre hasta el Integrador: 1.00/1.0
  - FASE 1: 0.90*1.75 = 1.57 (mayoria de numeros coinciden (44%))
  - FASE 2: 0.80*1.75 = 1.40 (coinciden algunos numeros clave (22%))
  - FASE 3: 1.00*1.75 = 1.75 (numeros coinciden (55% de canon cubierto))
  - FASE 4: 0.70*1.75 = 1.22 (codigo extenso (45 lineas) ejecuta; printeos no coinciden con canonico)

## Bonus — Sesiones 9 y 10
- S9 entregada correctamente: **Sí** (integrador correcto (100% de numeros coinciden))
- S10 entregada correctamente: **Sí** (mpl_ok=True sb_ok=True)
- Bonus aplicado: **+0.5**

## Calificación final
- Parte 1: 10.00 / 10
- Parte 2: 8.71 / 10
- Promedio: 9.355 / 10
- Bonus: +0.5
- **Final: 9.86 / 10**

---

# Retroalimentación — Módulo 4 · Tema 2 (GLM con Python)

**Alumno:** Alondra Abril Alarcón Álvarez
**Variable asignada:** `uso`

## Desglose por pregunta

| Pregunta | Pts | Comentario |
|---|---|---|
| P1 | 10/10 | φ=1.1664>1 y Cameron-Trivedi (α=0.0744, p=3.7e-56) → sobredispersión leve (φ<1.5) → concluye correctamente QuasiPoisson. |
| P2 | 10/10 | Identifica bien Particular (ref, RF=1) y Trabajo (RF=0.9887, −1.13%); revisa que el IC [0.9272,1.0542] cruza 1 y p=0.7281>0.05 → decide agrupar con la referencia. |
| P3 | 10/10 | Explica correctamente `exp(η)=Σsiniestros/Σexposición` y qué aporta el GLM sobre una tabla empírica (multivariable, IC, significancia). |
| P4 | 10/10 | CV estable, Gamma modela E[Y] directo, Lognormal fuera de la familia exponencial, corrección de sesgo en log(Y). |
| P5 | 8/10 | Identifica bien que BN gana por AIC/BIC y explica el pseudo-R² bajo correctamente, pero luego añade que "mantendría Quasi-Poisson" sin reconciliar esto con la brecha de AIC (~156 pts, evidencia fuerte a favor de BN). |
| P6 | 10/10 | Compara bien ambas direcciones (−1.13% frec, −1.32% sev, misma dirección), nota la no-significancia en frecuencia y concluye correctamente por qué modelar F×S por separado. |
| P7 | 10/10 | Distingue correctamente calibración (ratio≈1.02, sobreestima 2.49%) de discriminación (Gini 0.2315, modesto). |
| P8 | 9/10 | Identifica bien niveles más alto/bajo y traduce a −2.06% de descuento, pero mezcla conceptualmente "referencia" (nivel categórico) con el factor de tarifa (que es relativo a la prima promedio del portafolio). |
| P9 | 10/10 | Síntesis completa: integra frecuencia, severidad, prima pura e IC, en tono defendible ante CNSF. |

## Redacción: 9/10

Lenguaje actuarial correcto, clara y coherente entre partes; solo pequeños tropiezos de redacción
(p. ej. "usaría sería" en P1, un asterisco de markdown mal cerrado en P3, "se muestra diferencias"
en P9).

## Nota final: 96/100 (calificación: 9.6/10)

## Comentarios generales

Una de las evaluaciones más sólidas: interpretas bien los números de tu propia variable (`uso`),
distingues calibración de discriminación, y usas el lenguaje técnico correctamente. El único punto a
observar es P5, donde tu preferencia personal (Quasi-Poisson) no queda del todo justificada frente a
la brecha de AIC/BIC que tú misma reportas a favor de Binomial Negativa.
