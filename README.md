# 🏥 Análisis de Salud Pública en Chile

[![R](https://img.shields.io/badge/R-4.3%2B-276DC3?style=flat&logo=r&logoColor=white)](https://www.r-project.org/)
[![Data Source](https://img.shields.io/badge/Fuente-DEIS%20MINSAL-blue?style=flat)](https://deis.minsal.cl)
[![License](https://img.shields.io/badge/Licencia-MIT-green?style=flat)](LICENSE)
[![Status](https://img.shields.io/badge/Estado-Activo-brightgreen?style=flat)]()
[![Last Update](https://img.shields.io/badge/Actualización-Marzo%202026-orange?style=flat)]()

> Portafolio de análisis de datos de salud pública chilena aplicando R y técnicas de data science a problemas de equidad sanitaria. Incluye análisis exploratorio de la red asistencial y análisis avanzado de disparidades territoriales con indicadores ajustados por población y superficie.

---

## 📋 Tabla de Contenidos

- [Resumen Ejecutivo](#resumen-ejecutivo)
- [Análisis Disponibles](#análisis-disponibles)
  - [1. Análisis Exploratorio de Establecimientos](#1-análisis-exploratorio-de-establecimientos)
  - [2. Disparidades Territoriales en Salud](#2-disparidades-territoriales-en-salud-nuevo)
- [Hallazgos Clave](#hallazgos-clave)
- [Fuentes de Datos](#fuentes-de-datos)
- [Estructura del Repositorio](#estructura-del-repositorio)
- [Requisitos y Reproducibilidad](#requisitos-y-reproducibilidad)
- [Autor](#autor)

---

## 🎯 Resumen Ejecutivo

Este repositorio demuestra cómo el conteo bruto de establecimientos de salud puede ser engañoso para la planificación sanitaria. A través de dos análisis complementarios, se evidencia que:

| Métrica | Región Metropolitana | Interpretación |
|---------|---------------------|----------------|
| Conteo bruto | 1° posición nacional | Aparente líder en cobertura |
| Estab. por 100k hab. | 12° última posición | Menor cobertura relativa |
| Hab. por establecimiento | 8,000 (máxima carga) | Mayor presión asistencial del país |

> **Conclusión**: Las métricas absolutas favorecen políticamente a las regiones pobladas, pero ocultan las verdaderas brechas de acceso y equidad del sistema de salud.

---

## 📊 Análisis Disponibles

### 1. Análisis Exploratorio de Establecimientos

**Archivo:** `analisis_establecimientos.Rmd`

Análisis descriptivo de la red de establecimientos de salud pública y privada en Chile, con foco en:
- Distribución geográfica por región
- Composición por dependencia administrativa (pública vs. privada)
- Tipos de establecimientos predominantes
- Cobertura de servicios de urgencia

#### Preguntas de Investigación

1. ¿Cómo se distribuyen los establecimientos de salud por región?
2. ¿Qué tipos de establecimientos predominan en la red asistencial pública vs. privada?
3. ¿Cómo se distribuye la cobertura de urgencia a nivel regional?
4. ¿Cuál es la composición de dependencia administrativa del sistema de salud?

#### Visualizaciones

| | |
|---|---|
| Distribución por Región | Dependencia Administrativa |
| Tipos de Establecimiento | Urgencia por Región |

---

### 2. Disparidades Territoriales en Salud ✨ NUEVO

**Archivo:** `salud_chile_disparidades.Rmd`

Análisis avanzado que cruza múltiples fuentes de datos para construir indicadores de equidad en salud que revelan las verdaderas disparidades del sistema sanitario chileno.

#### Indicadores Construidos

| Indicador | Fórmula | Interpretación |
|-----------|---------|----------------|
| Estab. / 100k hab. | `n_estab / población × 100,000` | Acceso poblacional relativo |
| Hab. / establecimiento | `población / n_estab` | Carga asistencial / presión sobre el sistema |
| Estab. / 1,000 km² | `n_estab / superficie × 1,000` | Densidad territorial de la red |
| Urgencias / 100k hab. | `n_urgencias / población × 100,000` | Cobertura crítica per cápita |
| Densidad poblacional | `población / superficie` | Contexto territorial |

#### Fuentes Integradas

- **DEIS MINSAL** → establecimientos
- **INE** → población 2024
- **BCN-SIIT** → superficie

#### Hallazgos del Análisis de Disparidades

1. **Correlación negativa densidad-cobertura**: A mayor densidad poblacional, menor dotación de establecimientos por persona. El sistema tiene mayor presión donde vive más gente.
2. **Regiones australes: alta cobertura, baja accesibilidad**: Aysén y Magallanes tienen la mejor cobertura per cápita, pero 1 estab/1,000 km² implica distancias críticas.
3. **Doble vulnerabilidad rural**: O'Higgins y Maule combinan carga asistencial media-alta con baja densidad territorial.
4. **Urgencias concentradas estratégicamente**: Las regiones extremas concentran urgencias per cápita porque deben cubrir emergencias para poblaciones dispersas.

#### Visualización Principal: Scatter Multidimensional

El análisis incluye un scatter plot que codifica 4 variables simultáneamente:
- **Eje X** (log): Densidad poblacional (hab/km²)
- **Eje Y**: Establecimientos por 100k habitantes
- **Tamaño**: Población total de la región
- **Color**: Urgencias por 100k habitantes

---

## 🔍 Hallazgos Clave Consolidado

**Distribución Regional**
La Región Metropolitana concentra ~20% de los establecimientos del país, pero tiene la menor cobertura relativa (12 estab/100k hab.) y la mayor carga asistencial (8,000 hab/establecimiento).

**Dependencia Administrativa**
Predominio de la red pública (SNSS), con presencia relevante del sector municipal a través de la APS.

**Tipos de Establecimiento**
Las Postas de Salud Rural y CESFAM constituyen los tipos más frecuentes, evidenciando la fortaleza de la estrategia de APS.

**Cobertura de Urgencia**
Mayor proporción de urgencia per cápita en regiones extremas (Magallanes, Aysén), reflejando concentración de capacidad resolutiva donde las distancias son críticas.

**Implicancia para Políticas**
Una planificación sanitaria equitativa debe incorporar indicadores ajustados como estándar, evitando la ilusión del conteo bruto.

---

## 📁 Fuentes de Datos

| Fuente | Dataset | Uso | URL |
|--------|---------|-----|-----|
| DEIS MINSAL | Registro Nacional de Prestadores (marzo 2026) | Establecimientos, tipos, urgencia | deis.minsal.cl |
| INE Chile | Proyecciones población 2024 (base Censo 2017) | Población regional | ine.gob.cl |
| BCN-SIIT | Superficie regional | Territorio km² | bcn.cl/siit |

---

## 🗂️ Estructura del Repositorio

```
salud-chile-analytics/
├── README.md                          # Este archivo
├── analisis_establecimientos.Rmd      # Análisis exploratorio
├── salud_chile_disparidades.Rmd       # Análisis de disparidades ✨ NUEVO
├── establecimientos_20260303.csv      # Dataset DEIS MINSAL
├── 01_establecimientos_region.png     # Distribución por región
├── 02_dependencia_region.png          # Dependencia administrativa
├── 03_tipos_establecimiento.png       # Tipos de establecimiento
├── 04_urgencia_region.png             # Cobertura de urgencia
└── output/
    ├── analisis_establecimientos.html # Reporte exploratorio renderizado
    └── salud_chile_disparidades.html  # Reporte disparidades renderizado
```

---

## ⚙️ Requisitos y Reproducibilidad

### Software

- R 4.3.0+
- RStudio 2023.x (recomendado)

### Instalación de dependencias

```r
install.packages(c("tidyverse", "scales", "forcats", "knitr", "kableExtra", "ggrepel"))
```

### Reproducir los análisis

```r
# Análisis exploratorio
rmarkdown::render("analisis_establecimientos.Rmd")

# Análisis de disparidades
rmarkdown::render("salud_chile_disparidades.Rmd")
```

### Metodología — Pipeline de Análisis

```
DEIS MINSAL          INE Chile        BCN-SIIT
establecimientos  →  población    +   superficie
    ↓                    ↓
 Carga y limpieza    Análisis
 Filtro vigentes     población /
 Estandarizacin     superficie
         ↓
  Dataset integrado con indicadores de equidad
         ↓
    Análisis de          Visualizaciones
    disparidades  →      descriptivas
```

### Código Destacado — Construcción del Dataset Integrado (Disparidades)

```r
# Consolidar datos demográficos y territoriales
poblacion_region <- tibble(
  region_csv = c("Región de Arica y Parinacota", ...),
  region_label = c("Arica y Parinacota", ...),
  poblacion_2024 = c(261779, 406287, ...),
  superficie_km2 = c(16873, 42226, ...)
)

# Calcular indicadores de equidad
df_integrado <- establecimientos_region |>
  left_join(poblacion_region, by = "region_csv") |>
  mutate(
    estab_x100k     = n_total / poblacion_2024 * 100000,
    hab_x_estab     = poblacion_2024 / n_total,
    estab_x1000km2  = n_total / superficie_km2 * 1000,
    urgencia_x100k  = n_urgencia / poblacion_2024 * 100000,
    densidad_pob    = poblacion_2024 / superficie_km2
  )
```

### Código Destacado — Scatter Plot Multidimensional

```r
df_integrado |>
  ggplot(aes(
    x      = densidad_pob,
    y      = estab_x100k,
    size   = poblacion_2024,
    colour = urgencia_x100k,
    label  = region_label
  )) +
  geom_point(alpha = 0.8) +
  geom_text_repel(size = 3.2, colour = "grey25") +
  scale_x_log10(labels = comma) +
  scale_colour_gradient(low = "#aab7b8", high = "#c0392b") +
  scale_size_continuous(range = c(3, 14), labels = comma) +
  labs(
    title = "Relación entre Densidad Poblacional y Cobertura de Salud",
    x     = "Densidad de población (hab/km², escala log)",
    y     = "Establecimientos por 100.000 hab."
  )
```

---

## 👤 Autor

**Ignacio Coo Aravena**  
Enfermero Universitario | Study Nurse en Investigación Clínica Fase I | Data Science

---

> Este proyecto está bajo la licencia MIT. Los datos utilizados son de dominio público y provienen de fuentes oficiales del Estado de Chile (MINSAL/DEIS, INE, BCN).

---
*Última actualización: Marzo 2026 | Fuentes: DEIS/MINSAL, INE Chile, BCN-SIIT*
