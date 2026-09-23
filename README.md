# <img src="https://img.icons8.com/?size=50&id=80660&format=png&color=000000" align="center"/> Extract, Transform, Load (ETL) for Sales Data Cleaning & Integration
## Limpieza e Integración de Datos de Ventas

> **EN** · Data pipeline project for cleaning and integrating multi-source retail sales data into a unified, analysis-ready dataset; including careful validation to catch data-quality issues that aggregated sales data can easily hide.
> 
> **ES** · Proyecto de pipeline de datos para limpiar e integrar múltiples fuentes de datos de ventas retail en un dataset unificado listo para análisis; incluyendo validación cuidadosa para detectar problemas de calidad que los datos agregados de venta pueden esconder fácilmente.
---

## <img src="https://img.icons8.com/?size=40&id=Ihw7rsNxtanQ&format=png&color=000000" align="center"/> Overview / Descripción

**EN** · This project consolidates raw retail sales data from 5 sources (products, categories, segments, calendar, and weekly sales facts with 122,002
records) into a single analytical dataset of 47 engineered columns, applying systematic cleaning, feature engineering, and explicit data-quality
validation at every step.

**ES** · Este proyecto consolida datos crudos de ventas retail provenientes de 5 fuentes (productos, categorías, segmentos, calendario y hechos de venta semanal con 122,002 registros) en un único dataset analítico de 47 columnas, aplicando limpieza sistemática, ingeniería de variables y validación
explícita de calidad de datos en cada paso.

---

## <img src="https://img.icons8.com/?size=40&id=81083&format=png&color=000000" align="center"/> Data Quality Highlights / Hallazgos de Calidad de Datos

**EN** · A few things worth calling out, since catching them is what actually makes a dataset trustworthy:

- **Regional totals validated against a national aggregate.** The source data includes a national total alongside the six regional areas. Before any regional analysis, an explicit `region_type` flag separates "regional area" from "national total"; summing regions and the national figure together would double-count revenue, so this distinction is enforced at the data level rather than left to whoever queries it later.
- **Text fields audited beyond the standard cleaning pass.** Standardizing case and whitespace isn't enough on its own, the product catalog was checked for capture artifacts (e.g., stray leading characters in descriptions), verifying each pattern was a genuine data error before correcting it.
- **Business thresholds computed at the right level of aggregation.** The "high turnover" indicator is benchmarked against the median rotation *per product* (not per row), so products with more historical records don't get overweighted in the comparison.
- **Self-documenting column names.** A derived column representing the average selling price per week is named `avg_weekly_price`, explicit about being a weekly average computed from aggregated totals, not a fixed list price, so it can't be misread downstream.

**ES** · Algunos puntos que vale la pena resaltar, porque detectarlos es lo que hace confiable a un dataset:

- **Totales regionales validados contra un agregado nacional.** Los datos de origen incluyen un total nacional junto a las seis áreas regionales. Antes de cualquier análisis regional, una bandera explícita `region_type` separa "área regional" de "total nacional"; sumar las regiones junto con la cifra nacional duplicaría los ingresos, así que esta distinción se refuerza a nivel de datos en vez de dejarla a criterio de quien consulte el dataset después.
- **Campos de texto auditados más allá de la limpieza estándar.** Estandarizar mayúsculas y espacios no es suficiente por sí solo, el catálogo de productos se revisó buscando artefactos de captura (p. ej. caracteres espurios al inicio de las descripciones), verificando que cada patrón fuera un error real antes de corregirlo.
- **Umbrales de negocio calculados al nivel de agregación correcto.** El indicador de "alta rotación" se compara contra la mediana de rotación *por producto* (no por fila), para que los productos con más historial registrado no pesen de más en la comparación.
- **Nombres de columna autodescriptivos.** Una columna derivada que representa el precio promedio de venta semanal se llama `avg_weekly_price`, deja explícito que es un promedio semanal calculado desde totales agregados, no un precio de lista fijo, para que no se malinterprete más adelante.

---

## <img src="https://img.icons8.com/?size=40&id=80431&format=png&color=000000" align="center"/> Tools / Herramientas

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-b48cba?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-d19999?style=flat&logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-C4A882?style=flat&logo=jupyter&logoColor=white)
![Parquet](https://img.shields.io/badge/Parquet-50ABF1?style=flat&logo=apacheparquet&logoColor=white)

---

## <img src="https://img.icons8.com/?size=40&id=81350&format=png&color=000000" align="center"/> Pipeline ETL

### <img src="https://img.icons8.com/?size=25&id=TyCKx8nVDY0n&format=png&color=000000" align="center"/> Extract / Extracción
- Loaded 5 sources (CSV + Excel) with Pandas: products, categories, segments, calendar, and weekly sales facts.
- Carga de 5 fuentes (CSV + Excel) con Pandas: productos, categorías, segmentos, calendario y hechos de venta semanal.

### <img src="https://img.icons8.com/?size=25&id=v0qkjNOz5TXt&format=png&color=000000" align="center"/> Transform / Transformación

| Step / Paso | Description / Descripción |
|---|---|
| Cleaning / Limpieza | Typo correction, text standardization, dependency-aware null handling, duplicate removal across all 5 sources |
| Integration / Integración | Sequential left joins into a single consolidated table, with automatic detection and removal of duplicate columns |
| Regional vs. national flag / Bandera regional vs. nacional | `region_type` explicitly separates the six regional areas from the national aggregate |
| Temporal features / Variables temporales | Day, week, month, quarter, year-month/quarter, part-of-month |
| Sales metrics / Métricas de venta | Average weekly selling price (ASP), weekly variance vs. historical average |
| Categorization / Categorización | Sales, unit, and price range buckets |
| Product attributes / Atributos de producto | Standardized size extraction (ml/l/g/kg) from free-text descriptions via regex |
| Business indicators / Indicadores de negocio | High-value, high-turnover, VIP-sale, and star-product flags, built on per-product benchmarks |
| Rankings / Rankings | Product-level and product-year rankings, regional percentiles |
| Validation / Validación | Null/duplicate checks, regional-vs-national cross-check, in-notebook column dictionary |

### <img src="https://img.icons8.com/?size=25&id=eYYTdLLHOr9O&format=png&color=000000" align="center"/> Load / Carga
- Final dataset (122,002 rows × 47 columns, 0 nulls, 0 duplicates) exported to CSV, Excel, and Parquet for downstream analysis.
- Dataset final (122,002 filas × 47 columnas, 0 nulos, 0 duplicados) exportado a CSV, Excel y Parquet para análisis posterior.

---

## <img src="https://img.icons8.com/?size=40&id=PhymLYNNjf3I&format=png&color=000000" align="center"/> Repository Structure / Estructura

    etl-sales-data-cleaning/
    ├── notebook/
    │   └── Pipeline_ETL_Retail.ipynb
    ├── data/
    │   └── data_dictionary.csv        # Column-level documentation / Documentación por columna
    ├── README.md
    └── requirements.txt               # Python libraries

---

*Project developed as part of the Data Scientist Certificate ·
Proyecto desarrollado como parte del certificado Científico de Datos — EBAC (2025)* <img src="https://img.icons8.com/?size=35&id=FgMs84V9yrMV&format=png&color=000000" align="center"/>
