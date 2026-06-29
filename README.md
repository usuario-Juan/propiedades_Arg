# 🏠 Análisis de Ventas Inmobiliarias - Argentina

## 📋 Descripción

Análisis exploratorio del mercado inmobiliario argentino basado en datos de **Properati**, una de las principales plataformas de publicación de avisos inmobiliarios de la región. El estudio se enfoca exclusivamente en **operaciones de venta** dentro de **Argentina**, analizando patrones geográficos, precios y oportunidades de mercado.

## 🎯 Objetivos

- Identificar patrones geográficos de precios y volumen de ventas
- Analizar la relación entre ubicación y valor por m²
- Detectar oportunidades de inversión por zona
- Comparar el mercado de Capital Federal vs. Provincias
- Crear dashboard interactivo en Power BI para visualización ejecutiva

## 📊 Dataset

| Característica | Detalle |
|----------------|---------|
| **Fuente** | Properati |
| **Período** | 2019-2020 |
| **Región** | Argentina (exclusivamente) |
| **Tipo de operación** | Ventas (se excluyeron alquileres) |
| **Registros finales** | ~536,000 propiedades |
| **Variables principales** | Provincia, Ciudad, Barrio, Tipo Propiedad, Precio, Superficie, Coordenadas |

### ⚠️ Nota Metodológica

El dataset proviene de una plataforma de publicación de avisos. La variable `end_date` representa la fecha de baja del anuncio, no necesariamente la fecha de escrituración. Por lo tanto, `days_on_market` es un **proxy de rotación de avisos** y permite comparaciones relativas entre zonas, pero no representa el tiempo real de venta (que en Argentina típicamente es 90-180 días).

## 📁 Estructura del Proyecto

```text
Propiedades_Arg/
│
├── data/
│   ├── raw/                     # Dataset original (no subido a GitHub)
│   │   └── entrenamiento.csv
│   │
│   ├── processed/              # Datasets procesados
│   │   └── PROPERATI_VENTAS_ARG_FINAL.csv
│   │
│   └── archive/                # Archivos intermedios
│
├── notebooks/
│   ├── 03_eda_geografico_FINAL.ipynb
│
│
├── figures/                    # Visualizaciones generadas
│   ├── 01_volumen_vs_precio_provincia.png
│   ├── 02_caba_top10_barrios.png
│   └── dashboard_powerbi_final.png
│
├── .gitignore                  # Archivos excluidos de Git
├── requirements.txt            # Dependencias de Python
└── README.md                   # Este archivo
```
## 🚀 Instalación y Uso

### Requisitos previos

- Python 3.8+
- Jupyter Notebook
- Power BI Desktop (para el dashboard)

### Instalación
```bash
# Clonar repositorio
git clone https://github.com/tu_usuario/properati_argentina.git
cd Propiedades_Arg

# Crear entorno virtual (recomendado)
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

# Instalar dependencias
pip install -r requirements.txt
```
### Ejecutar el análisis
```bash 
# Iniciar Jupyter Notebook
jupyter notebook

# Abrir el notebook de análisis
notebooks/03_eda_geografico_FINAL.ipynb
```  
### Abrir el Dashboard
- Abre Power BI Desktop
- Importa el archivo *data/processed/base.pbix*
- El dashboard cargará automáticamente los datos desde el CSV

## 📈 Hallazgos Principales
### KPIs del Mercado Argentino
| Métrica | Valor |
| :--- | :--- |
| Total propiedades en venta | ~536,000 |
| Precio mediano | $125,000 USD |
| Precio/m² promedio | $1,750 USD |
| Superficie mediana | 103 m² |
| Días en mercado (mediana) | 65 días |

### Análisis Geográfico por Provincia

### Hallazgos clave:
- **Capital Federal** lidera en volumen (~88,000 ventas) y tiene el segundo mayor precio/m² ($2,491)
- **Bs.As. G.B.A. Zona Norte** muestra alto volumen (~46,000) con precio/m² más accesible ($1,300)
- **Bs.As. Costa Atlántica** tiene menor volumen pero precio/m² relativamente alto ($1,419), indicando mercado de segunda vivienda/turismo
- **Provincias del interior** (Córdoba, Santa Fe) muestran precios/m² significativamente menores ($500-800)
Análisis de Barrios en Capital Federal

### Insights Accionables
💎 Zonas Premium (Alto valor + Liquidez):
- Puerto Madero, Palermo Chico, Recoleta
- Recomendación: Enfocar captación de propiedades de lujo

### 🚀 Zonas Oportunidad (Alta liquidez + Precio accesible):
- Almagro, Caballito, Villa Crespo
- Recomendación: Campañas para compradores primerizos e inversores

### ⚠️ Zonas con Rotación Lenta:
- Barrios con DOM > 100 días

### Características del dashboard:
- Mapa interactivo: Distribución geográfica de propiedades con coordenadas reales
- KPIs en tiempo real: Total propiedades, precio/m², precio mediano, días en mercado
- Filtros dinámicos: Por provincia y tipo de propiedad
Gráfico de barras: Top 10 provincias por volumen de ventas
- Drill-down: De provincia a barrio para análisis detallado

### 🛠️ Tecnologías Utilizadas
- Recomendación: Revisar pricing o mejorar marketing de propiedades

### 📊 Dashboard Interactivo (Power BI)

| Tecnología | Uso |
| :--- | :--- |
| Python | Análisis de datos y visualización |
| Pandas | Manipulación de DataFrames |
| NumPy | Cálculos numéricos |
| Matplotlib | Gráficos estáticos |
| Seaborn | Visualizaciones estadísticas |
| Jupyter Notebook | Documentación interactiva del análisis |
| Power BI | Dashboard interactivo |
| Git/GitHub | Control de versiones y portafolio |

### 📚 Proceso de Análisis
### Fase 1: Exploración y Limpieza
- Carga del dataset original (~900MB)
- Identificación de valores nulos y duplicados
- Limpieza de coordenadas geográficas
- Filtrado de solo operaciones de venta en Argentina

### Fase 2: Feature Engineering
- Creación de columna *barrio_real* (unificación de l3 y l4)
- Cálculo de *rice_per_m2* (precio por metro cuadrado)
- Cálculo de *days_on_market* (días en mercado)
- Aplicación de jitter a coordenadas para visualización

### Fase 3: Análisis Exploratorio (EDA)
- Análisis geográfico por provincia
- Análisis granular por barrio (CABA)
- Identificación de oportunidades comerciales
- Generación de insights accionables

### Fase 4: Visualización
- Creación de gráficos estáticos con Matplotlib/Seaborn
- Desarrollo de dashboard interactivo en Power BI
- Documentación de hallazgos en README

### 🎓 Aprendizajes Clave
- **Validación de datos:** Detectar que *end_date* no representa fecha de venta real fue crucial para interpretar correctamente *days_on_market*
- **Filtrado geográfico:** Identificar y eliminar propiedades fuera de Argentina mejoró la precisión del análisis
- **Manejo de coordenadas:** Aplicar jitter para evitar superposición visual en mapas
- **Comunicación de insights:** Traducir datos en recomendaciones accionables para el negocio

## 📚 Fuente de Datos

Este proyecto utiliza el dataset **Properati - Argentina**, disponible en Kaggle.

**Detalles de la fuente:**
- **Plataforma**: [Kaggle](https://www.kaggle.com)
- **Autor original**: Properati (plataforma inmobiliaria)
- **Licencia**: Desconocida (Unknown)
- **Tamaño**: 904.38 MB (archivo entrenamiento.csv)
- **Contenido**: ~1 millón de propiedades

**Descripción del dataset:**
> "Este conjunto de datos contiene casi un millón de anuncios inmobiliarios de Properati, que abarcan propiedades en toda Argentina. Incluye información como ubicación (provincia, ciudad, barrio, coordenadas), precio, tipo de propiedad, tipo de operación (venta o alquiler), superficie, número de habitaciones y más."

**Nota sobre la licencia:**
La licencia del dataset no está especificada en Kaggle. Este proyecto se realiza con fines **educativos y de portfolio**, sin intención comercial. 
