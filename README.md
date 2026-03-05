# 🏥 Análisis de Establecimientos de Salud en Chile

![R](https://img.shields.io/badge/R-4.3%2B-276DC3?style=flat&logo=r&logoColor=white)
![Data Source](https://img.shields.io/badge/Fuente-DEIS%20MINSAL-blue?style=flat)
![License](https://img.shields.io/badge/Licencia-MIT-green?style=flat)
![Status](https://img.shields.io/badge/Estado-Activo-brightgreen?style=flat)
![Last Update](https://img.shields.io/badge/Actualización-Marzo%202026-orange?style=flat)

> Análisis exploratorio y descriptivo de la red de establecimientos de salud pública y privada en Chile, utilizando datos oficiales del Registro Nacional de Prestadores del Ministerio de Salud (MINSAL).

---

## 📋 Tabla de Contenidos

- [Descripción](#descripción)
- [Preguntas de Investigación](#preguntas-de-investigación)
- [Fuente de Datos](#fuente-de-datos)
- [Estructura del Repositorio](#estructura-del-repositorio)
- [Metodología](#metodología)
- [Hallazgos Principales](#hallazgos-principales)
- [Visualizaciones](#visualizaciones)
- [Requisitos](#requisitos)
- [Reproducibilidad](#reproducibilidad)
- [Autor](#autor)

---

## 📌 Descripción

Este proyecto explora la **distribución geográfica y características institucionales** de los establecimientos de salud en Chile, con foco en:

- La cobertura territorial de la red asistencial por región
- La composición según tipo de dependencia administrativa (pública vs. privada)
- Los tipos de establecimientos presentes en el sistema nacional
- La disponibilidad de servicios de urgencia a nivel regional

El análisis fue desarrollado íntegramente en **R** mediante un documento R Markdown reproducible, aplicando principios de ciencia de datos abierta y transparencia metodológica.

---

## ❓ Preguntas de Investigación

1. ¿Cómo se distribuyen los establecimientos de salud por región?
2. ¿Qué tipos de establecimientos predominan en la red asistencial pública vs. privada?
3. ¿Cómo se distribuye la cobertura de urgencia a nivel regional?
4. ¿Cuál es la composición de dependencia administrativa del sistema de salud?

---

## 📊 Fuente de Datos

| Campo | Detalle |
|---|---|
| **Institución** | Departamento de Estadísticas e Información de Salud (DEIS) – MINSAL |
| **Registro** | Registro Nacional de Prestadores Individuales e Institucionales |
| **Archivo** | `establecimientos_20260303.csv` |
| **Formato** | CSV delimitado por punto y coma (UTF-8) |
| **Actualización** | Marzo 2026 |
| **URL** | [https://deis.minsal.cl/](https://deis.minsal.cl/) |

---

## 🗂️ Estructura del Repositorio

```
salud-chile-analytics/
│
├── analisis_establecimientos.Rmd    # Documento R Markdown principal
├── establecimientos_20260303.csv    # Dataset fuente (DEIS - MINSAL)
│
├── 01_establecimientos_region.png   # Gráfico: Distribución por región
├── 02_dependencia_region.png        # Gráfico: Dependencia administrativa por región
├── 03_tipos_establecimiento.png     # Gráfico: Tipos de establecimiento
├── 04_urgencia_region.png           # Gráfico: Cobertura de urgencia por región
│
└── README.md                        # Este archivo
```

---

## 🔬 Metodología

### Pipeline de Análisis

```
Datos crudos (CSV)
      │
      ▼
Carga y exploración inicial
      │
      ▼
Limpieza y estandarización
 • Normalización de TieneServicioUrgencia → {Con Urgencia, Sin Urgencia, NA}
 • Estandarización de EstadoFuncionamiento (str_to_title)
 • Abreviación de nombres de regiones para visualización
      │
      ▼
Filtrado de establecimientos vigentes
      │
      ▼
Análisis exploratorio (4 dimensiones)
      │
      ▼
Visualizaciones con ggplot2
```

### Paquetes Utilizados

| Paquete | Versión | Uso |
|---|---|---|
| `tidyverse` | ≥ 2.0 | Manipulación y visualización de datos |
| `scales` | ≥ 1.3 | Formateo de ejes y etiquetas |
| `forcats` | ≥ 1.0 | Manejo de factores (`fct_reorder`, `fct_lump`) |
| `knitr` | ≥ 1.45 | Generación de tablas en el documento |
| `kableExtra` | ≥ 1.3 | Estilo profesional de tablas HTML |

### Parámetros del Documento

```yaml
output: html_document
  theme: flatly
  highlight: tango
  toc: true (flotante, profundidad 3)
  code_folding: show
  fig.width: 10 | fig.height: 6 | dpi: 150
```

---

## 🔎 Hallazgos Principales

> 📍 **Distribución Regional:** La Región Metropolitana concentra aproximadamente el **20% de todos los establecimientos del país**, seguida por regiones con alta ruralidad como Maule, Araucanía y Los Lagos, lo que refleja la red de Postas de Salud Rural distribuidas en territorio.

> 🏛️ **Dependencia Administrativa:** El sistema de salud chileno muestra una clara predominancia de la red **pública (SNSS)**, con presencia relevante del sector municipal a través de la Atención Primaria de Salud (APS).

> 🏨 **Tipos de Establecimiento:** Las **Postas de Salud Rural** y los **Centros de Salud Familiar (CESFAM)** constituyen los tipos más frecuentes, evidenciando la fortaleza de la estrategia de APS.

> 🚨 **Cobertura de Urgencia:** La distribución de servicios de urgencia presenta asimetrías regionales importantes, con **mayor proporción de urgencia por establecimiento en regiones extremas** (Magallanes, Aysén, Arica y Parinacota), lo que refleja una red de atención más concentrada en establecimientos con capacidad resolutiva.

---

## 📈 Visualizaciones

### 1. Establecimientos de Salud Vigentes por Región
![Distribución por Región](01_establecimientos_region.png)

### 2. Dependencia Administrativa por Región
![Dependencia Administrativa](02_dependencia_region.png)

### 3. Tipos de Establecimiento
![Tipos de Establecimiento](03_tipos_establecimiento.png)

### 4. Cobertura de Urgencia por Región
![Urgencia por Región](04_urgencia_region.png)

---

## ⚙️ Requisitos

### Software
- **R** ≥ 4.3.0
- **RStudio** ≥ 2023.x (recomendado) o VS Code con extensión R

### Instalación de dependencias

```r
install.packages(c(
  "tidyverse",
  "scales",
  "forcats",
  "knitr",
  "kableExtra"
))
```

---

## 🔄 Reproducibilidad

Para reproducir el análisis completo:

1. **Clonar** el repositorio:
   ```bash
   git clone https://github.com/ignaciocooaravena-sys/-salud-chile-analytics.git
   cd salud-chile-analytics
   ```

2. **Descargar** el dataset desde [DEIS MINSAL](https://deis.minsal.cl/) y guardarlo como `establecimientos_20260303.csv` en la raíz del proyecto.

3. **Renderizar** el documento R Markdown:
   ```r
   rmarkdown::render("analisis_establecimientos.Rmd")
   ```

4. El reporte HTML generado incluye todas las tablas, gráficos e interpretaciones con código plegable.

---

---

## 💻 Análisis en R

A continuación se presentan los bloques de código R utilizados en el análisis, organizados por etapa del pipeline.

### 1. Carga de Librerías y Datos

```r
library(tidyverse)   # manipulación y visualización de datos
library(scales)      # formateo de ejes y etiquetas
library(forcats)     # manejo de factores (fct_reorder, fct_lump)
library(knitr)       # tablas en el documento
library(kableExtra)  # estilo de tablas

# Carga del dataset
df_raw <- read_delim(
  "establecimientos_20260303.csv",
  delim = ";",
  locale = locale(encoding = "UTF-8"),
  show_col_types = FALSE
)
cat("Dimensiones del dataset:", nrow(df_raw), "filas ×", ncol(df_raw), "columnas")
```

### 2. Limpieza y Estandarización

```r
df <- df_raw |>
  # Estandarizar TieneServicioUrgencia
  mutate(
    urgencia = case_when(
      TieneServicioUrgencia == "SI"  ~ "Con Urgencia",
      TieneServicioUrgencia == "NO"  ~ "Sin Urgencia",
      TRUE                           ~ NA_character_   # SIN DATO / No Aplica / No
    ),
    # Estandarizar EstadoFuncionamiento (mayúsculas inconsistentes)
    estado = str_to_title(EstadoFuncionamiento),
    # Abreviar nombres de regiones largas para gráficos
    region_abrev = RegionGlosa |>
      str_remove("Región D?d?el? ?") |>
      str_remove("Región ") |>
      str_trunc(35)
  )

# Filtrar solo establecimientos vigentes
df_vigente <- df |> filter(str_detect(estado, "Vigente"))
cat("Establecimientos vigentes:", nrow(df_vigente), "de", nrow(df), "totales")
```

### 3. Distribución por Región

```r
df_vigente |>
  count(region_abrev, name = "n") |>
  mutate(region_abrev = fct_reorder(region_abrev, n)) |>
  ggplot(aes(x = n, y = region_abrev, fill = n)) +
  geom_col(show.legend = FALSE) +
  geom_text(
    aes(label = comma(n)),
    hjust = -0.1, size = 3.2, colour = "grey30"
  ) +
  scale_fill_gradient(low = "#a8d8ea", high = "#1a5276") +
  scale_x_continuous(
    expand = expansion(mult = c(0, 0.12)),
    labels = comma
  ) +
  labs(
    title    = "Establecimientos de Salud Vigentes por Región",
    subtitle = "Fuente: DEIS – MINSAL · Marzo 2026",
    x = "N° de establecimientos", y = NULL
  ) +
  theme_minimal(base_size = 11) +
  theme(
    plot.title          = element_text(face = "bold", size = 13),
    plot.subtitle       = element_text(colour = "grey50"),
    panel.grid.major.y  = element_blank()
  )
```

### 4. Dependencia Administrativa por Región

```r
df_dep <- df_vigente |>
  mutate(
    dependencia = fct_other(
      DependenciaAdministrativa,
      keep = c("Municipal", "Privado", "Servicio de Salud",
               "Fuerzas Armadas y de Orden (FFAA)"),
      other_level = "Otras"
    )
  ) |>
  count(region_abrev, dependencia) |>
  group_by(region_abrev) |>
  mutate(pct = n / sum(n)) |>
  ungroup() |>
  mutate(region_abrev = fct_reorder(region_abrev, n, sum))

paleta_dep <- c(
  "Municipal"                       = "#2471a3",
  "Privado"                         = "#e74c3c",
  "Servicio de Salud"               = "#27ae60",
  "Fuerzas Armadas y de Orden (FFAA)" = "#8e44ad",
  "Otras"                           = "#95a5a6"
)

df_dep |>
  ggplot(aes(x = n, y = region_abrev, fill = dependencia)) +
  geom_col(position = "stack") +
  scale_fill_manual(values = paleta_dep, name = "Dependencia") +
  scale_x_continuous(labels = comma, expand = expansion(mult = c(0, 0.05))) +
  labs(
    title    = "Dependencia Administrativa por Región (establecimientos vigentes)",
    subtitle = "Fuente: DEIS – MINSAL · Marzo 2026",
    x = "N° de establecimientos", y = NULL
  ) +
  theme_minimal(base_size = 11) +
  theme(
    plot.title         = element_text(face = "bold", size = 13),
    plot.subtitle      = element_text(colour = "grey50"),
    panel.grid.major.y = element_blank(),
    legend.position    = "bottom"
  )
```

### 5. Top 15 Tipos de Establecimiento

```r
df_vigente |>
  count(TipoEstablecimientoGlosa, name = "n") |>
  slice_max(n, n = 15) |>
  mutate(TipoEstablecimientoGlosa = fct_reorder(TipoEstablecimientoGlosa, n)) |>
  ggplot(aes(x = n, y = TipoEstablecimientoGlosa, fill = n)) +
  geom_col(show.legend = FALSE) +
  geom_text(
    aes(label = comma(n)),
    hjust = -0.1, size = 3.2, colour = "grey30"
  ) +
  scale_fill_gradient(low = "#a9dfbf", high = "#1e8449") +
  scale_x_continuous(
    expand = expansion(mult = c(0, 0.12)),
    labels = comma
  ) +
  labs(
    title    = "Top 15 Tipos de Establecimiento de Salud Vigentes",
    subtitle = "Fuente: DEIS – MINSAL · Marzo 2026",
    x = "N° de establecimientos", y = NULL
  ) +
  theme_minimal(base_size = 11) +
  theme(
    plot.title         = element_text(face = "bold", size = 13),
    plot.subtitle      = element_text(colour = "grey50"),
    panel.grid.major.y = element_blank()
  )
```

### 6. Cobertura de Urgencia por Región

```r
df_urg <- df_vigente |>
  filter(!is.na(urgencia)) |>
  count(region_abrev, urgencia) |>
  group_by(region_abrev) |>
  mutate(total = sum(n), pct = n / total) |>
  ungroup() |>
  mutate(
    region_abrev = fct_reorder(
      region_abrev,
      if_else(urgencia == "Con Urgencia", pct, 0),
      max
    )
  )

df_urg |>
  ggplot(aes(x = pct, y = region_abrev, fill = urgencia)) +
  geom_col(position = "fill") +
  geom_text(
    data = df_urg |> filter(urgencia == "Con Urgencia"),
    aes(label = percent(pct, accuracy = 0.1), x = 0.02),
    hjust = 0, size = 3, colour = "white", fontface = "bold"
  ) +
  scale_x_continuous(labels = percent, expand = c(0, 0)) +
  scale_fill_manual(
    values = c("Con Urgencia" = "#c0392b", "Sin Urgencia" = "#aab7b8"),
    name = NULL
  ) +
  labs(
    title    = "Proporción de Establecimientos con Servicio de Urgencia por Región",
    subtitle = "Fuente: DEIS – MINSAL · Marzo 2026",
    x = "Proporción de establecimientos", y = NULL
  ) +
  theme_minimal(base_size = 11) +
  theme(
    plot.title         = element_text(face = "bold", size = 13),
    plot.subtitle      = element_text(colour = "grey50"),
    panel.grid.major.y = element_blank(),
    legend.position    = "bottom"
  )
```

### 7. Tabla Resumen por Región

```r
df_vigente |>
  group_by(region_abrev) |>
  summarise(
    Total        = n(),
    Hospitales   = sum(TipoEstablecimientoGlosa == "Hospital"),
    CESFAM       = sum(TipoEstablecimientoGlosa == "Centro de Salud Familiar (CESFAM)"),
    PSR          = sum(TipoEstablecimientoGlosa == "Posta de Salud Rural (PSR)"),
    `Con Urgencia` = sum(urgencia == "Con Urgencia", na.rm = TRUE),
    `% Urgencia` = percent(
      mean(urgencia == "Con Urgencia", na.rm = TRUE),
      accuracy = 0.1
    )
  ) |>
  arrange(desc(Total)) |>
  rename(Región = region_abrev) |>
  kable(caption = "Tabla 2. Resumen por región – establecimientos vigentes") |>
  kable_styling(
    bootstrap_options = c("striped", "hover", "condensed"),
    font_size = 12
  )
```

## 👤 Autor

**Ignacio Coo Aravena**

Análisis desarrollado como parte del estudio de datos de salud pública chilena. Datos actualizados a **marzo de 2026**.

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Los datos utilizados son de dominio público y provienen de fuentes oficiales del Estado de Chile (MINSAL/DEIS).

---

*Última actualización: Marzo 2026 · Fuente: DEIS – Ministerio de Salud de Chile*
