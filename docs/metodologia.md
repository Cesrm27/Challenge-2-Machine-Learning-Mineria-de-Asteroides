# Metodología y supuestos

Se consideran 220 observaciones sintéticas generadas con una semilla fija. La variable beneficio neto (MUSD) sigue la expresión didáctica aproximada:

`24 × masa + 4.2 × concentración − 2.1 × distancia − 1.15 × costo − 140 × riesgo − 200 + ruido`

El ruido es normal de media 0 y desviación estándar 34 MUSD. Las unidades y rangos se eligieron arbitrariamente con fines didácticos; **no** tienen calibración empírica.

Búsqueda: decisiones binarias incluir/descartar sobre 8 asteroides, exploración BFS, poda si el presupuesto supera 700 MUSD o si ya se seleccionaron 3 misiones. La utilidad se calcula como beneficio sintético × (1 − riesgo); es una heurística didáctica, no un valor financiero de riesgo validado. La solución maximiza la utilidad entre los estados terminales factibles explorados.

Predicción: Ridge sobre StandardScaler, división aleatoria 80/20 y validación cruzada R² sobre el conjunto de entrenamiento. Interpretar MAE, RMSE y R² como métricas únicamente de un experimento simulado.

**Limitación:** el notebook de búsqueda usa la columna sintética objetivo a modo de oráculo ilustrativo. No se pretende demostrar un planificador completo de misiones con resultados predichos fuera de muestra. Para convertirlo en un sistema integrado, separar una base histórica y usar predicciones para asteroides candidatos independientes.
