#  Análisis de Riesgo en la Cadena de Suministro Global
### Proyecto Final de Análisis de Datos · IT Academy, Barcelona Activa (2025-2026)

---

## Descripción

Análisis descriptivo y exploratorio de los principales factores de riesgo que afectan las rutas logísticas marítimas internacionales. Se construye un **índice de impacto compuesto bajo metodología ISO 31000** para identificar, cuantificar y priorizar disrupciones operativas, geopolíticas y de transportista.

El proyecto culmina con una **matriz de riesgo interactiva** y un **mapa global de rutas logísticas** que permite visualizar qué corredores requieren acción inmediata y cuáles pueden operar bajo monitoreo rutinario.

---

## Preguntas de negocio respondidas

| # | Pregunta |
|---|----------|
| P1 | ¿Dónde están los problemas? — Identificación de rutas críticas |
| P2 | ¿Qué tan impactante es el riesgo? — Cuantificación del impacto |
| P3 | ¿Dónde priorizar la inversión en mitigación? |
| P4 | ¿Qué variables explican el fenómeno? — Drivers del riesgo |
| P5 | ¿Qué acciones reducen el riesgo de forma inmediata? |

---

## 🗂️ Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `Proyecto_logistica_definitivo.ipynb` | Notebook principal con el análisis completo |
| `riesgo_cadena_de_suministro_global_2026.csv` | Dataset de envíos internacionales con variables operativas, climáticas y geopolíticas |
| `proyecto_documento.pdf` | Informe técnico del proyecto |
| `Presentación_proyecto.pptx` | Presentación ejecutiva de resultados |

---

## Herramientas y tecnologías

- **Python 3**
- **pandas** — carga, limpieza y transformación de datos
- **matplotlib / seaborn** — visualización estadística
- **plotly** — visualizaciones interactivas y mapa global de rutas
- **numpy** — cálculos numéricos y normalización
- **Jupyter Notebook** — entorno de desarrollo

---

## 🔍 Metodología

### 1. Carga y comprensión de datos
Dataset con registros de envíos internacionales que incluye variables operativas (`lead_time_days`, `distance_km`, `weight_mt`), climáticas (`weather_condition`) y geopolíticas (`geopolitical_risk_score`, `carrier_reliability_score`).

### 2. Limpieza de datos
- Revisión y tratamiento de valores nulos y duplicados
- Corrección de tipos de datos (conversión a datetime, categorización)
- Normalización de columnas categóricas (strip + lowercase)
- Auditoría y validación de variables categóricas

### 3. Tratamiento de outliers
Los valores extremos en `lead_time_days` se mantuvieron como señal operativa real — en logística los retrasos severos no son errores de medición sino exactamente los eventos que se quieren modelar.
> Referencia: Tukey, J.W. (1977). *Exploratory Data Analysis*, cap. 2.

### 4. Construcción del índice de impacto (Risk Scoring Model)
Normalización min-max de variables clave y construcción de un índice compuesto con pesos basados en impacto operativo:

```
impact = lead_time_norm × 0.4 + geo_norm × 0.3 + carrier_norm × 0.2 + weather_norm × 0.1
```

> Referencia: OECD (2008). *Handbook on Constructing Composite Indicators*, §3. ISO 31000:2018.

### 5. Segmentación del riesgo
Clasificación de cada ruta en 4 categorías de disrupción (geopolítica, fallo de carrier, retraso operativo, sin disrupción) mediante algoritmo basado en percentiles extremos (P90/P10).

### 6. Análisis exploratorio (EDA)
- Distribución de variables clave mediante boxplots
- Correlación de Pearson y Spearman entre drivers de riesgo
- Pairplot segmentado por ocurrencia de disrupción
- Análisis de rutas más disruptivas mediante heatmap

### 7. Matriz de riesgo ISO 31000
Clasificación de rutas en 4 niveles (Critical / High / Medium / Low) combinando probabilidad de disrupción e impacto normalizado, con decisiones ejecutivas específicas por nivel y tipo.

### 8. Mapa global interactivo
Visualización geográfica de las rutas logísticas coloreadas por nivel de riesgo (rojo / naranja / verde) con tooltips interactivos.

---

## Principales hallazgos

- **Todas las rutas analizadas superan el 65% de probabilidad de disrupción**, indicando una red logística con exposición generalizada al riesgo operativo.
- **Los retrasos operativos son el tipo de disrupción con mayor impacto promedio (0.52)**, seguidos de eventos geopolíticos (0.44) y fallos de carrier (0.39).
- **El corredor Asia–Europa concentra las rutas más críticas**, especialmente aquellas con disrupciones de tipo Carrier y Geopolítico.
- **Shanghai – Singapore** se posiciona como la ruta de mayor criticidad, con el mayor impacto normalizado del conjunto.
- **El transporte marítimo** presenta la mayor cantidad de retrasos extremos; el transporte aéreo no registra outliers en tiempo de entrega.
- La severidad climática actúa como **amplificador del riesgo**, incrementando tanto el impacto como la volatilidad operativa.

---

## Rutas críticas — Acción inmediata recomendada
# Análisis de Riesgo en la Cadena de Suministro Global
### Proyecto Final de Análisis de Datos · IT Academy, Barcelona Activa (2025)

---

## Descripción

Análisis descriptivo y exploratorio de los principales factores de riesgo que afectan las rutas logísticas marítimas internacionales. Se construye un **índice de impacto compuesto bajo metodología ISO 31000** para identificar, cuantificar y priorizar disrupciones operativas, geopolíticas y de transportista.

El proyecto culmina con una **matriz de riesgo interactiva** y un **mapa global de rutas logísticas** que permite visualizar qué corredores requieren acción inmediata y cuáles pueden operar bajo monitoreo rutinario.

---

##  Preguntas de negocio respondidas

| # | Pregunta |
|---|----------|
| P1 | ¿Dónde están los problemas? — Identificación de rutas críticas |
| P2 | ¿Qué tan impactante es el riesgo? — Cuantificación del impacto |
| P3 | ¿Dónde priorizar la inversión en mitigación? |
| P4 | ¿Qué variables explican el fenómeno? — Drivers del riesgo |
| P5 | ¿Qué acciones reducen el riesgo de forma inmediata? |

---

##  Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `Proyecto_logistica_definitivo.ipynb` | Notebook principal con el análisis completo |
| `riesgo_cadena_de_suministro_global_2026.csv` | Dataset de envíos internacionales con variables operativas, climáticas y geopolíticas |
| `proyecto_documento.pdf` | Informe técnico del proyecto |
| `Presentación_proyecto.pptx` | Presentación ejecutiva de resultados |

---

##  Herramientas y tecnologías

- **Python 3**
- **pandas** — carga, limpieza y transformación de datos
- **matplotlib / seaborn** — visualización estadística
- **plotly** — visualizaciones interactivas y mapa global de rutas
- **numpy** — cálculos numéricos y normalización
- **Jupyter Notebook** — entorno de desarrollo

---

##  Metodología

### 1. Carga y comprensión de datos
Dataset con registros de envíos internacionales que incluye variables operativas (`lead_time_days`, `distance_km`, `weight_mt`), climáticas (`weather_condition`) y geopolíticas (`geopolitical_risk_score`, `carrier_reliability_score`).

### 2. Limpieza de datos
- Revisión y tratamiento de valores nulos y duplicados
- Corrección de tipos de datos (conversión a datetime, categorización)
- Normalización de columnas categóricas (strip + lowercase)
- Auditoría y validación de variables categóricas

### 3. Tratamiento de outliers
Los valores extremos en `lead_time_days` se mantuvieron como señal operativa real — en logística los retrasos severos no son errores de medición sino exactamente los eventos que se quieren modelar.
> Referencia: Tukey, J.W. (1977). *Exploratory Data Analysis*, cap. 2.

### 4. Construcción del índice de impacto (Risk Scoring Model)
Normalización min-max de variables clave y construcción de un índice compuesto con pesos basados en impacto operativo:

```
impact = lead_time_norm × 0.4 + geo_norm × 0.3 + carrier_norm × 0.2 + weather_norm × 0.1
```

> Referencia: OECD (2008). *Handbook on Constructing Composite Indicators*, §3. ISO 31000:2018.

### 5. Segmentación del riesgo
Clasificación de cada ruta en 4 categorías de disrupción (geopolítica, fallo de carrier, retraso operativo, sin disrupción) mediante algoritmo basado en percentiles extremos (P90/P10).

### 6. Análisis exploratorio (EDA)
- Distribución de variables clave mediante boxplots
- Correlación de Pearson y Spearman entre drivers de riesgo
- Pairplot segmentado por ocurrencia de disrupción
- Análisis de rutas más disruptivas mediante heatmap

### 7. Matriz de riesgo ISO 31000
Clasificación de rutas en 4 niveles (Critical / High / Medium / Low) combinando probabilidad de disrupción e impacto normalizado, con decisiones ejecutivas específicas por nivel y tipo.

### 8. Mapa global interactivo
Visualización geográfica de las rutas logísticas coloreadas por nivel de riesgo (rojo / naranja / verde) con tooltips interactivos.

---

##  Principales hallazgos

- **Todas las rutas analizadas superan el 65% de probabilidad de disrupción**, indicando una red logística con exposición generalizada al riesgo operativo.
- **Los retrasos operativos son el tipo de disrupción con mayor impacto promedio (0.52)**, seguidos de eventos geopolíticos (0.44) y fallos de carrier (0.39).
- **El corredor Asia–Europa concentra las rutas más críticas**, especialmente aquellas con disrupciones de tipo Carrier y Geopolítico.
- **Shanghai – Singapore** se posiciona como la ruta de mayor criticidad, con el mayor impacto normalizado del conjunto.
- **El transporte marítimo** presenta la mayor cantidad de retrasos extremos; el transporte aéreo no registra outliers en tiempo de entrega.
- La severidad climática actúa como **amplificador del riesgo**, incrementando tanto el impacto como la volatilidad operativa.

---

## 🔴Rutas críticas — Acción inmediata recomendada

| Ruta | Tipo disrupción | Decisión |
|------|----------------|----------|
| Rotterdam – Busan | Carrier | Reevaluar SLA del carrier, sustituir si es necesario |
| Rotterdam – Marseille | Operativo | Aumentar buffer stock +15% y ajustar plan |
| Hamburg – Rotterdam | Geopolítico | Diversificar rutas alternativas |
| Los Ángeles – Singapore | Geopolítico | Aumentar buffer +15% y ajustar plan |
| Shanghai – Singapore | Crítico | Plan de contingencia inmediato |

---

##  Autora

**Ana Cristina Urdaneta Flores**
Analista de Datos | Ingeniería de Petróleo | IT Academy Barcelona Activa
 Barcelona, España
🔗 [LinkedIn](https://www.linkedin.com/in/urdanetaac)

---

*Nota: El dashboard de visualización interactivo fue desarrollado con asistencia de IA (Claude, Anthropic) para la implementación del código. El diseño, los requisitos técnicos, las preguntas de negocio, la metodología y las especificaciones analíticas fueron definidos por la autora.*
| Ruta | Tipo disrupción | Decisión |
|------|----------------|----------|
| Rotterdam – Busan | Carrier | Reevaluar SLA del carrier, sustituir si es necesario |
| Rotterdam – Marseille | Operativo | Aumentar buffer stock +15% y ajustar plan |
| Hamburg – Rotterdam | Geopolítico | Diversificar rutas alternativas |
| Los Ángeles – Singapore | Geopolítico | Aumentar buffer +15% y ajustar plan |
| Shanghai – Singapore | Crítico | Plan de contingencia inmediato |

---

##  Autora

**Ana Cristina Urdaneta Flores**
Analista de Datos | Ingeniería de Petróleo | IT Academy Barcelona Activa
 Barcelona, España
🔗 [LinkedIn](https://www.linkedin.com/in/urdanetaac)

---

*Nota: El dashboard de visualización interactivo fue desarrollado con asistencia de IA (Claude, Anthropic) para la implementación del código. El diseño, los requisitos técnicos, las preguntas de negocio, la metodología y las especificaciones analíticas fueron definidos por la autora.*
