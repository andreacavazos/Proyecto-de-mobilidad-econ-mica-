
# 🚦 Movilidad Urbana y Productividad Económica en Latinoamérica

### Análisis exploratorio de datos | Python | Pandas | Visualización de datos

## 📌 Descripción del proyecto

Este proyecto analiza la relación entre la congestión vehicular y los indicadores económicos de 15 ciudades de Latinoamérica durante 2024.

A partir de información de movilidad urbana de **TomTom Traffic Index** e indicadores económicos de **OECD Cities**, se desarrolla un proceso de exploración, limpieza, transformación, integración y visualización de datos.

El análisis se plantea como un caso de negocio orientado a apoyar la identificación de ciudades prioritarias para inversiones en infraestructura de transporte urbano.

## 🎯 Objetivo del proyecto

**Evaluar cómo se relacionan los niveles de congestión vehicular con la productividad económica de las principales ciudades latinoamericanas**, utilizando indicadores como el PIB per cápita y los retrasos asociados al tráfico.

Los objetivos específicos son:

- Preparar y estandarizar datos provenientes de diferentes fuentes.
- Integrar indicadores económicos y de movilidad en un único dataset.
- Identificar patrones de congestión y valores atípicos.
- Explorar posibles relaciones entre el tráfico y el PIB per cápita.
- Generar hallazgos y recomendaciones que apoyen decisiones estratégicas de inversión en infraestructura.

## 🛠️ Herramientas y tecnologías

| Herramienta | Aplicación |
|---|---|
| Python | Procesamiento y análisis de datos |
| Pandas | Limpieza, transformación, agrupación y unión de datasets |
| NumPy | Librería numérica importada como apoyo al entorno de análisis |
| Matplotlib | Creación y personalización de gráficos |
| Seaborn | Visualización estadística y exploración de distribuciones |
| Jupyter Notebook | Desarrollo y documentación del análisis |
| CSV | Lectura de fuentes de datos y exportación de resultados |

## 📂 Fuentes de datos

El proyecto utiliza dos conjuntos de datos:

**1. TomTom Traffic Index — Movilidad urbana**

Contiene métricas de congestión vehicular, incluyendo:

- `jams_delay`: indicador de retrasos por congestión.
- `traffic_index_live`: índice de tráfico.
- `jams_count`: cantidad de congestionamientos.
- `jams_length_in_kms`: longitud de los congestionamientos.
- `mins_delay`: retrasos en minutos.
- Indicadores de tiempo de viaje por cada 10 kilómetros.

**2. OECD Cities — Indicadores económicos**

Incluye variables como:

- `city_gdp_capita`: PIB per cápita.
- `unemployment_pct`: tasa de desempleo.
- `population`: población total.
- `pm25_ug_m3`: concentración de partículas contaminantes PM2.5.

**Alcance:** El análisis integrado se concentra en una muestra de 15 ciudades latinoamericanas para el año 2024.

## 🔎 Metodología del análisis

El proyecto se desarrolló mediante siete etapas:

### 1. Carga y exploración inicial

- Importación de datasets mediante `pd.read_csv()`.
- Inspección de columnas, tipos de datos y estructura.
- Revisión de valores faltantes.
- Identificación de inconsistencias en formatos numéricos y temporales.

### 2. Limpieza y preparación de datos

- Estandarización de nombres de columnas mediante `rename()` y convención `snake_case`.
- Conversión de fechas utilizando `pd.to_datetime()`.
- Limpieza de caracteres y símbolos en variables numéricas.
- Conversión de variables a tipos adecuados.
- Creación de una columna de población total.

### 3. Filtrado temporal

- Extracción del año a partir de las fechas.
- Selección de registros correspondientes a 2024.
- Creación de subconjuntos independientes utilizando `.copy()`.

### 4. Agregación de indicadores de movilidad

- Agrupación por ciudad, país y año mediante `groupby()`.
- Cálculo de promedios de indicadores de tráfico con `.agg('mean')`.
- Consolidación de múltiples registros de tráfico en una observación por ciudad y año.

### 5. Integración de datasets

- Selección de variables relevantes para el análisis.
- Unión de las fuentes económicas y de movilidad mediante `pd.merge()`.
- Aplicación de un `INNER JOIN` utilizando `city` y `year` como claves.
- Construcción del dataset analítico consolidado.

### 6. Análisis exploratorio y visualización

Se desarrollaron tres visualizaciones principales:

- **Boxplot:** distribución de los retrasos por congestión e identificación de valores atípicos.
- **Histograma:** distribución del PIB per cápita entre las ciudades estudiadas.
- **Gráfico de barras:** comparación de indicadores de congestión y PIB per cápita por ciudad.

### 7. Exportación y documentación

- Exportación del dataset consolidado mediante `.to_csv()`.
- Documentación de hallazgos y conclusiones.
- Elaboración de recomendaciones orientadas a decisiones de inversión.

## 📊 Principales hallazgos

El análisis exploratorio permitió identificar los siguientes patrones:

**1. Ciudad de México destaca por sus niveles de congestión.**

Ciudad de México presenta los mayores retrasos por congestión dentro de la muestra, con un valor promedio de `jams_delay` cercano a 2,800, destacándose como un valor atípico.

**2. Las grandes concentraciones urbanas muestran importantes desafíos de movilidad.**

Ciudades como Ciudad de México, São Paulo y Bogotá registran niveles elevados de congestión vehicular, lo que sugiere la necesidad de estudiar la capacidad de sus infraestructuras de transporte frente a la actividad urbana.

**3. Existen ciudades con menores niveles de congestión.**

Montevideo y Porto Alegre presentan indicadores comparativamente bajos de retrasos vehiculares dentro de la muestra analizada.

**4. La relación entre economía y movilidad requiere mayor investigación.**

Las visualizaciones permiten observar diferencias relevantes entre ciudades, pero no son suficientes para demostrar una correlación estadísticamente significativa ni establecer relaciones causales entre el PIB per cápita y la congestión.

## 💡 Recomendaciones de negocio

A partir de los hallazgos exploratorios, se proponen las siguientes líneas de acción:

- **Priorizar estudios de infraestructura:** considerar a Ciudad de México, São Paulo y Bogotá como candidatas para evaluaciones más profundas de necesidades de transporte urbano.
- **Evaluar alternativas de movilidad sostenible:** estudiar oportunidades de inversión en transporte público de alta capacidad, como sistemas de metro y BRT.
- **Ampliar el análisis económico:** incorporar variables como densidad poblacional, crecimiento urbano y empleo para mejorar la interpretación de los patrones.
- **Fortalecer la evidencia estadística:** realizar análisis de correlación y otros métodos cuantitativos antes de establecer prioridades definitivas de inversión.

## ⚠️ Limitaciones del análisis

- El estudio se limita al año 2024 y a una muestra de 15 ciudades.
- Los resultados son exploratorios y no permiten demostrar causalidad.
- No se realizaron pruebas estadísticas de significancia para determinar la intensidad de las relaciones entre las variables.
- Los indicadores de congestión y PIB per cápita tienen escalas diferentes, por lo que su comparación visual directa requiere precaución.
- Se necesitan datos adicionales para evaluar la viabilidad económica y social de proyectos específicos de infraestructura.

## 📦 Entregables del proyecto

- **Notebook de Jupyter:** contiene el código, las transformaciones, visualizaciones e interpretaciones.
- **Dataset consolidado:** `ladb_mobility_economy_2024_clean.csv`, generado mediante el proceso de limpieza e integración.
- **Resumen ejecutivo:** presenta el contexto, metodología, hallazgos y recomendaciones del análisis.

### Ejecución del proyecto

Para reproducir el análisis se requiere un entorno de Python con las siguientes librerías:

```bash
pip install pandas numpy matplotlib seaborn notebook
```

Los archivos de entrada utilizados en el notebook son:

- `tomtom_traffic.csv`
- `oecd_city_economy.csv`

Las rutas de lectura deberán ajustarse a la ubicación local de los archivos antes de ejecutar el notebook.

## 🧠 Competencias desarrolladas

Este proyecto permitió poner en práctica habilidades fundamentales de análisis de datos:

- Exploración y validación de datasets.
- Limpieza y transformación de datos.
- Manipulación de fechas y variables numéricas.
- Agregación de registros mediante `groupby()`.
- Integración de datos mediante `merge()`.
- Análisis exploratorio de datos (EDA).
- Identificación de valores atípicos.
- Visualización e interpretación de indicadores.
- Traducción de hallazgos analíticos en recomendaciones de negocio.
- Documentación y comunicación de resultados.

## ✅ Conclusión

El proyecto demuestra la aplicación de un flujo de trabajo de análisis de datos, desde la preparación de información procedente de distintas fuentes hasta la elaboración de conclusiones orientadas a un problema de negocio.

Los resultados muestran diferencias importantes en los niveles de congestión urbana de las ciudades estudiadas y permiten identificar oportunidades para profundizar en la evaluación de inversiones en movilidad.

Más allá de los resultados específicos, el proyecto evidencia la importancia de **transformar datos en información comprensible, detectar patrones y comunicar hallazgos que contribuyan a la toma de decisiones fundamentadas**.

---

**Proyecto académico:** TripleTen — Data Analyst Bootcamp  
**Módulo:** Sprint 5 — Proyecto final  
**Área de aplicación:** Movilidad urbana, economía y análisis de datos  
**Periodo analizado:** 2024
