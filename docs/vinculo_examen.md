# Relación directa con el examen parcial A — minería de asteroides

## Lo que aparece en las fotografías entregadas
- Examen parcial A, 05/10/2026, Universidad Peruana Cayetano Heredia.
- Caso de minería de asteroides: mercado emergente, actores, robótica, recursos minerales e incertidumbres.
- Debate: **¿Debería la humanidad invertir masivamente en la minería de asteroides durante los próximos años?**
- Diagrama de contexto o arquitectura conceptual: sector, procesos, áreas y objetivos.
- Propuesta de espacio de estados asociada al problema empresarial.
- Bloque 1: pipeline de razonamiento, búsqueda y resultados; bloque 2: predicción y gráfica.
- En el marco teórico se solicita definir razonamiento abductivo, espacio de estados, PCA y regresión logística.

## Del examen a la implementación
**Razonamiento abductivo:** partimos del indicio de recursos valiosos y de los riesgos tecnológicos para plantear la hipótesis de que una inversión gradual y selectiva puede ser preferible a invertir masivamente. La hipótesis se explora con escenarios, pero los datos sintéticos **no confirman** una conclusión económica real.

**Espacio de estados:** cada estado registra el conjunto parcial de asteroides candidatos aceptados/rechazados, el presupuesto comprometido y la utilidad simulada. Acciones: incluir o descartar; búsqueda: BFS; objetivo: seleccionar mejor combinación factible de ocho candidatos.

**PCA:** método de reducción dimensional de atributos numéricos. No es necesario para los dos notebooks porque la rúbrica no lo exige y la regresión Ridge mantiene la interpretabilidad de los atributos.

**Regresión logística:** modelo de clasificación para resultados categóricos (por ejemplo, viable/no viable). No se aplica aquí, dado que el challenge pide sustentar un **modelo de regresión** y hemos seleccionado una variable numérica continua (beneficio neto hipotético); Ridge es apropiado para esta tarea.

## Límites importantes
- La infografía del examen describe un sector incipiente, no proporciona una base de entrenamiento con beneficios reales.
- El dataset es artificial. Ninguna métrica de predicción representa desempeño en misiones reales.
- No inferimos factibilidad técnica, rentabilidad o recomendación de inversión real de las simulaciones.
- El presupuesto de 700 MUSD, el límite de 3 misiones y los 8 candidatos son parámetros **inventados para demostrar el espacio de estados**.
