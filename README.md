# Riesgo y disrupción en cadenas de suministro — prototipo de portafolio

Prototipo de análisis de datos de punta a punta sobre un dataset sintético de envíos internacionales. Su objetivo es demostrar el flujo completo de trabajo: carga, limpieza, exploración, pruebas estadísticas, índice compuesto, matriz de riesgo, validación temporal interna y dashboard.

**No está validado para decisiones operativas.** Las conclusiones son ilustrativas del método.

## Fuente de datos

- Dataset: `global_supply_chain_risk_2026.csv`, publicado por *nudratabbas* en Kaggle, "Global Supply Chain Risk and Logistics 2024-2026".
- Licencia: CC0 (dominio público).
- La ficha del dataset indica que fue **generado sintéticamente** y que puede no reflejar datos del mundo real.
- Período real del archivo: del 1 de enero de 2024 al 31 de diciembre de 2025 (5.000 envíos). La ficha dice "2024-2026", pero el archivo no contiene datos de 2026.

## Estructura del notebook

| Etapa | Contenido |
|---|---|
| 0. Portada | Alcance, fuente, limitaciones |
| 1. Carga | Lectura y comprensión inicial |
| 2. Limpieza | Nulos, duplicados, tipos, normalización de texto, categorías, atípicos |
| 3. Consistencia | Validación de rangos y tipos |
| 4. EDA | Normalización min-máx, índice de impacto, relaciones entre variables |
| 5. Rutas | Tasas por ruta con intervalos de confianza, sensibilidad de pesos, pruebas chi-cuadrado |
| 6. Matriz ISO 31000 | Probabilidad e impacto por ruta, niveles de riesgo, hipótesis de acción |
| 7. Dashboard | Mapa y tabla con las 10 rutas del ranking |
| 8. Validación temporal | Partición 2024 (referencia) y 2025 (prueba), sin reajustar criterios |
| 9. Registro | Cambios aplicados con fecha y pendientes |

La lista de revisión metodológica (`Checklist_revision_metodologica.docx`) documenta cada decisión, su justificación, su referencia y su estado.

## Resultados principales

- **Tasa global de disrupción:** 61,3% (3.063 de 5.000 envíos).
- **Clima:** es la única variable con asociación fuerte con la disrupción (chi-cuadrado p < 0,0001). Tasas: despejado 37%, lluvia 42%, niebla 48%, tormenta 80%, huracán 100%.
- **Modo de transporte, origen y destino:** no muestran asociación con la disrupción (p = 0,98, 0,97 y 0,92).
- **Rutas:** de 64 rutas, 2 superan de forma significativa la media global, 2 quedan por debajo y 60 no se distinguen de ella (intervalos de confianza al 95%, unos 70 envíos por ruta).
- **Causa identificada:** las tres causas definidas explican 1.025 de 3.063 disrupciones (33%).
- **Sensibilidad de pesos:** con cuatro escenarios de pesos, la correlación de Spearman frente al caso base va de 0,93 a 0,97, y las 10 rutas principales coinciden entre 7 y 10.
- **Validación temporal (2024 vs. 2025):** el patrón por clima se repite en ambos años. Las rutas no persisten (Spearman = −0,12).

## Decisiones provisionales

- **Pesos del índice de impacto:** 0,4 lead time, 0,3 geopolítico, 0,2 transportista, 0,1 clima. Son juicios de valor del autor, con análisis de sensibilidad.
- **Orden de severidad del clima:** despejado < lluvia < niebla < tormenta < huracán, ajustado a las tasas observadas. Existe circularidad: el mismo resultado sirve para ordenar y para evaluar.
- **Criterios de la matriz:** probabilidad alta si la tasa supera la global; impacto alto si supera la media global. Son provisionales, pendientes de validación.
- **Umbrales de causa:** percentiles P90 para geopolítico y lead time, P10 para confiabilidad del transportista.

## Limitaciones

- Dataset sintético: los patrones pueden reflejar cómo se generó y no el mundo real.
- No hay validación externa. La validación temporal es interna, con el mismo dataset.
- Clima y disrupción pueden estar ligados por construcción del dataset.
- Pocos envíos por ruta: las diferencias entre rutas solo se detectan si superan unos 15 puntos porcentuales.
- El tablero de Power BI se construye a partir de las tablas de la carpeta `powerbi/`, exportadas desde el notebook.

## Tablero Power BI

La carpeta `powerbi/` contiene las tablas que alimentan el tablero:

- `1_kpis.csv`: indicadores generales (envíos, tasa global, rutas).
- `2_clima.csv`: tasas por clima con intervalos de confianza y por año.
- `3_rutas_ic.csv`: tasas por ruta con intervalo de confianza y ranking.
- `4_matriz_riesgo.csv`: probabilidad, impacto y nivel de riesgo por ruta (criterios provisionales).
- `5_sensibilidad_pesos.csv`: comparación de escenarios de pesos.
- `6_validacion_temporal.csv`: tasa global por año.

## Cómo reproducir

1. Coloca `global_supply_chain_risk_2026.csv` en la ruta que indica la celda de carga, o ajústala.
2. Instala las dependencias: `pandas`, `numpy`, `scipy`, `matplotlib`, `seaborn`, `plotly`, `nbformat`, `nbconvert`.
3. Ejecuta `Proyecto_logistica_corregido.ipynb` de principio a fin. No debe haber errores.

## Referencias

- ISO 31000:2018, cláusulas 6.4.2 a 6.4.4 y 6.5.2 (identificación, análisis, evaluación y tratamiento de riesgos).
- OECD (2008), *Handbook on Constructing Composite Indicators*, pp. 19–35 (normalización, ponderación y sensibilidad).
- scikit-learn, guía de buenas prácticas, §12.2 (fuga de datos).
- WMO: definición de niebla (visibilidad menor de 1 km).
- NHC: escala Saffir-Simpson de huracanes (viento sostenido).
- Ficha del dataset *nudratabbas* en Kaggle (origen sintético).

**Pendiente de verificar:** el capítulo de Tukey (1977) citado para atípicos y el número de sección de la OECD en la versión original del notebook.

## Estado

Prototipo para portafolio. Versión del 11 de octubre de 2026.
