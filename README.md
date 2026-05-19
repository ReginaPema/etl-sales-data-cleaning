# etl-sales-data-cleaning

# <img src="https://img.icons8.com/?size=50&id=80660&format=png&color=000000" align="center"/> Extract, Transform, Load (ETL) for Sales Data Cleaning & Integration
### Limpieza e Integración de Datos de Ventas

> **EN** · Data pipeline project for cleaning and integrating multi-source 
> retail sales data into a unified, analysis-ready dataset.  
> **ES** · Proyecto de pipeline de datos para limpiar e integrar múltiples 
> fuentes de datos de ventas retail en un dataset unificado listo para análisis.

---

## <img src="https://img.icons8.com/?size=40&id=Ihw7rsNxtanQ&format=png&color=000000" align="center"/> Overview / Descripción

**EN** · This project processes raw retail sales data from 5 different sources 
(products, categories, segments, calendar, and sales facts), applying 
systematic cleaning and 6 structured transformations to produce a 
consolidated dataset ready for exploratory analysis.

**ES** · Este proyecto procesa datos crudos de ventas retail provenientes 
de múltiples fuentes, aplicando limpieza sistemática y transformaciones 
estructuradas para producir un dataset consolidado listo para análisis exploratorio.

---

## <img src="https://img.icons8.com/?size=40&id=80431&format=png&color=000000" align="center"/> Tools / Herramientas

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-b48cba?style=flat&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-d19999?style=flat&logo=numpy&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-C4A882?style=flat&logo=jupyter&logoColor=white)

---

## <img src="https://img.icons8.com/?size=40&id=81350&format=png&color=000000" align="center"/> Pipeline ETL

### <img src="https://img.icons8.com/?size=25&id=TyCKx8nVDY0n&format=png&color=000000" align="center"/> Extract / Extracción
- Loaded data from CSV and Excel files using Pandas
- Carga de datos desde archivos CSV y Excel con Pandas

### <img src="https://img.icons8.com/?size=25&id=v0qkjNOz5TXt&format=png&color=000000" align="center"/> Transform / Transformación
Applied 6 structured transformations · Se aplicaron 6 transformaciones:

| # | Transformation / Transformación |
|---|---|
| 1 | Remove duplicate columns / Eliminación de columnas duplicadas |
| 2 | Column renaming & standardization / Renombramiento y estandarización |
| 3 | Date & time feature engineering / Columnas temporales (año, mes, trimestre) |
| 4 | Sales metrics calculation / Métricas de ventas calculadas |
| 5 | Sales range categorization / Categorización de rangos de ventas |
| 6 | Product attribute extraction / Extracción de atributos de producto |

### <img src="https://img.icons8.com/?size=25&id=eYYTdLLHOr9O&format=png&color=000000" align="center"/> Load / Carga
- Unified dataset exported for downstream analysis
- Dataset consolidado exportado para análisis posterior

---

## <img src="https://img.icons8.com/?size=40&id=80351&format=png&color=000000" align="center"/> Key Learnings / Aprendizajes

- **EN** · How to handle multiple data sources with different schemas; 
  strategies for cleaning real-world (messy) data; importance of 
  documenting each transformation step for reproducibility.
- **ES** · Cómo manejar múltiples fuentes con esquemas distintos; 
  estrategias de limpieza para datos reales; importancia de documentar 
  cada paso para reproducibilidad.

---

## <img src="https://img.icons8.com/?size=40&id=PhymLYNNjf3I&format=png&color=000000" align="center"/> Repository Structure / Estructura

    etl-sales-data-cleaning/
    ├── notebook/
    │   └── etl_sales_cleaning.ipynb
    ├── README.md
    └── requirements.txt       # Python libraries

---

*Project developed as part of the Data Scientist Certificate · 
Proyecto desarrollado como parte del certificado Científico de Datos — EBAC (2025)* <img src="https://img.icons8.com/?size=35&id=FgMs84V9yrMV&format=png&color=000000" align="center"/>
