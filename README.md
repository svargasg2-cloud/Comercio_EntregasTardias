# Predicción de Entregas Tardías en Comercio Electrónico (Olist)
### Reto de Machine Learning & Analytics — Laboratorio 1 (Semana 12)

**Estudiante:** Sergio David Vargas Garzón  
**ID Estudiante:** 28  
**Semilla de Reproducibilidad:** 1028  
**Asignatura:** Data Analytics (2026-2)  
**Profesor:** Elias Buitrago Bolivar  
**Institución:** Universidad Central  

---

## Descripción del Proyecto

Este proyecto aborda un problema logístico operativo en el comercio electrónico brasileño utilizando el conjunto de datos público de **Olist**. El objetivo principal es construir modelos predictivos supervisados para **anticipar qué pedidos corren el riesgo de entregarse después de la fecha comprometida**, evaluando la decisión en términos de métricas estadísticas y costos de impacto empresarial.

El sistema utiliza exclusivamente **28 variables predictoras** que se encuentran razonablemente disponibles al momento de confirmarse la compra (plazos prometidos, calendario, dimensiones de los productos, ubicación del comprador/vendedor y medio de pago).

---

## Estructura del Repositorio

El repositorio sigue la arquitectura estándar de ingeniería analítica para garantizar la reproducibilidad y la modularidad a lo largo del curso:

```text
Comercio_EntregasTardias/
├── data/                  # Datos locales (no se suben los archivos CSV pesados a Git)
│   ├── raw/               # Archivos CSV descargados directamente desde la fuente
│   └── processed/         # Conjuntos de datos procesados/resumidos
├── docs/                  # Documentación técnica del laboratorio (Guia_Olist_S12.html)
├── notebooks/             # Cuadernos de experimentación en Jupyter / Google Colab
│   └── S12_ML_Challenge.ipynb  # Cuaderno de análisis resuelto (S12)
├── reports/               # Reportes y resultados ejecutivos
│   └── S12_resultados_ID_28.json  # Métricas y metadatos de la muestra individual ID 28
├── src/                   # Código modular reutilizable (para desarrollos de las S13-S15)
└── README.md              # Descripción general del proyecto e instrucciones de ejecución
