# 🚀 ASTEROID ML | Minería de asteroides

![Portada del proyecto](images/portada.png)

**Challenge 1 (Individual) · Pipeline de Machine Learning · UPCH · 2026-II**  
**Tema:** Tipo A — Minería de asteroides  
**Estudiante:** [TU NOMBRE Y APELLIDOS]  
**Docente:** Yannick Patrick Carrasco Merma

> **Importante:** propuesta académica adaptable al enunciado de Minería de Asteroides del examen parcial. Datos completamente sintéticos. Las cifras no representan predicciones económicas reales.

## 🎯 1. Caso, problema y objetivos (5 puntos)
La minería de asteroides es una actividad propuesta para extraer recursos de cuerpos menores del sistema solar. Las misiones son costosas y existen múltiples candidatos con diferentes distancias, masas y concentraciones de materiales. Decidir cuáles explorar o explotar puede representarse como un problema de predicción y optimización bajo restricciones.

**Pregunta del problema:** ¿Cómo estimar el beneficio neto potencial de cada asteroide a partir de atributos numéricos y seleccionar una cartera de hasta tres misiones que maximice el beneficio esperado ajustado por riesgo sin exceder un presupuesto disponible?

**Objetivo general:** construir un pipeline académico de Machine Learning y búsqueda que permita predecir beneficios potenciales y seleccionar misiones de minería de asteroides dentro de restricciones explícitas.

**Objetivos específicos:** (1) estructurar un espacio de estados; (2) explorar opciones con búsqueda en anchura y poda; (3) entrenar y evaluar un modelo de regresión Ridge; (4) interpretar resultados con visualizaciones.

**Justificación:** Machine Learning permite identificar relaciones predictivas en datos numéricos, mientras que la búsqueda permite comparar decisiones combinatorias. La combinación contribuye al apoyo a decisiones, aunque el ejercicio requiere validación con datos físicos y financieros reales antes de cualquier aplicación práctica.

## 🧭 2. Espacio de estados (5 puntos)

![Representación visual del espacio de estados](images/espacio_estados.png)

| Elemento | Definición |
|---|---|
| Estado | `s=(i, S, C, U)` donde `i` = candidatos evaluados, `S` = índices seleccionados, `C` = costo acumulado, `U` = utilidad acumulada |
| Estado inicial | `s₀=(0, ∅, 0, 0)` |
| Operadores | `incluir` el siguiente candidato / `descartar` el siguiente candidato |
| Restricción 1 | Presupuesto total ≤ **700 MUSD** |
| Restricción 2 | Máximo **3 misiones** |
| Restricción 3 | Asteroides sin repetición |
| Estado terminal | Los **8 candidatos** han sido evaluados |
| Optimización | Elegir el estado terminal factible con mayor `Σ beneficio × (1 − riesgo)` |

La cifra de presupuesto y el máximo de misiones son **suposiciones del ejercicio**, no hechos reales.

## 🔎 3. Pipeline de razonamiento, búsqueda y resultados (5 puntos)

`Problema → Datos sintéticos → Espacio de estados → Acciones → Búsqueda BFS con poda → Solución óptima entre 8 candidatos → Gráficos`

📓 **Notebook:** [01 — Razonamiento y búsqueda](notebooks/01_razonamiento_busqueda.ipynb)

El algoritmo explora decisiones de inclusión/exclusión de cada candidato, descarta ramas inviables y conserva el mejor resultado factible. La búsqueda exhaustiva es óptima **solo para este conjunto discreto de ocho candidatos**, no para todos los asteroides existentes. En este cuaderno se usan valores sintéticos conocidos como referencia didáctica; el cuaderno predictivo muestra cómo estimarlos cuando son desconocidos.

## 📈 4. Pipeline predictivo y visualización (5 puntos)

`CSV → selección de X/y → división 80/20 → escalado → Ridge → predicción → MAE/RMSE/R² → gráficos`

📓 **Notebook:** [02 — Predicción y visualización](notebooks/02_prediccion_visualizacion.ipynb)

**Tarea:** regresión supervisada. **Objetivo:** estimar `beneficio_neto_musd` (millones de USD) a partir de `distancia_millones_km`, `masa_millones_ton`, `concentracion_metal_pct`, `costo_mision_musd` y `riesgo_operacional`.

**Modelo:** Ridge Regression con penalización L2 y estandarización. Se elige como línea base por su interpretabilidad y por controlar el tamaño de los coeficientes. Se evalúa con un conjunto de prueba separado y validación cruzada dentro del conjunto de entrenamiento.

**Generación de datos:** 220 casos sintéticos con semilla 42; la variable respuesta se construye con una fórmula lineal educativa más ruido aleatorio. Por ello, que Ridge obtenga buenos resultados **no demuestra** su calidad predictiva en minería espacial real.

## 🗂️ Estructura del repositorio
```text
ml-mineria-asteroides/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── asteroides_sinteticos.csv
├── docs/
│   ├── metodologia.md
│   └── instrucciones_colab.md
├── images/
│   ├── portada.png
│   └── espacio_estados.png
└── notebooks/
    ├── 01_razonamiento_busqueda.ipynb
    └── 02_prediccion_visualizacion.ipynb
```

## ▶️ Cómo ejecutar en Google Colab
1. Crear un repositorio **público o privado según las instrucciones del docente** llamado `ml-mineria-asteroides` y subir los archivos **conservando carpetas**.
2. Abrir [Google Colab](https://colab.research.google.com/), elegir **GitHub** y pegar la URL del repositorio para abrir cada notebook, o descargar los `.ipynb` y abrirlos desde tu equipo.
3. **Recomendado:** ejecutar `!git clone https://github.com/TU_USUARIO/ml-mineria-asteroides.git` en una celda de Colab y ` %cd ml-mineria-asteroides` (sustituir usuario) para que ambos notebooks encuentren `data/` de forma local; alternativamente cambia `GITHUB_USUARIO` en los notebooks para que lean el CSV desde GitHub (requiere repositorio público).
4. Ejecutar todas las celdas **en orden** y verificar las métricas y las gráficas.
5. Guardar en GitHub los notebooks ejecutados si el docente solicita evidencias de salidas; no incluir credenciales.

## 📚 Alcance y limitaciones
- Las variables y costos son hipótesis ilustrativas; **no** se ha validado ningún yacimiento, misión o estimación financiera.
- El primer notebook optimiza beneficios sintéticos conocidos, no predicciones del segundo cuaderno; esta separación evita presentar un rendimiento ficticio como validación operacional.
- Para integrar ambos notebooks en un proyecto futuro, las estimaciones del modelo deben construirse con datos independientes y evaluar incertidumbre fuera de muestra.

## ✅ Rúbrica cubierta
- [x] Caso, problema y justificación de IA/ML.
- [x] Estados, operadores, restricciones y visualización.
- [x] Problema → espacio de estados → exploración → búsqueda → resultado.
- [x] Dataset sintético → modelo de regresión → métricas → gráficos.

## 📖 Fuentes orientativas
- [NASA — Asteroids](https://science.nasa.gov/solar-system/asteroids/)
- [Scikit-learn — Ridge](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Ridge.html)
- [Scikit-learn — Pipeline](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html)

*El enunciado individual del examen parcial no está incluido en los archivos recibidos; ajustar el problema si ese caso fija otras condiciones.*
