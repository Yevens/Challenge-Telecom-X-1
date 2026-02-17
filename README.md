# 📡 Telecom X — Análisis de Evasión de Clientes (Churn)

Análisis exploratorio de datos (EDA) sobre la evasión de clientes de Telecom X, orientado a identificar los factores que impulsan la cancelación del servicio y a sentar las bases para modelos predictivos de retención.

---

## 📋 Descripción del Proyecto

Telecom X enfrenta una tasa de evasión de aproximadamente el **26-27%** de su base de clientes. Este notebook realiza un proceso completo de ETL y EDA para entender el comportamiento de los clientes y detectar los segmentos de mayor riesgo.

Los resultados de este análisis están diseñados para apoyar al equipo de Data Science en la construcción de modelos predictivos y al equipo comercial en el diseño de estrategias de retención proactivas.

---

## 🗂️ Estructura del Repositorio

```
├── TelecomX_Churn_Analysis.ipynb   # Notebook principal con el análisis completo
├── TelecomX_Data.json               # Dataset fuente en formato JSON
└── README.md                        # Este archivo
```

---

## 🔄 Flujo del Análisis

### 1. 📥 Extracción de Datos
Carga del dataset desde un archivo JSON con estructura anidada, aplanado a un DataFrame tabular mediante `pd.json_normalize`.

### 2. 🔍 Exploración Inicial y Limpieza
- Revisión de tipos de datos y valores nulos
- Detección y eliminación de duplicados
- Corrección de `Charges_Total` (originalmente en formato string)
- Validación de valores únicos en columnas críticas como `Churn`

### 3. 🔧 Transformación y Estandarización
- Creación de columna `Cuentas_Diarias` (cargo diario aproximado)
- Codificación binaria de variables categóricas `Yes/No → 1/0`
- Renombrado de columnas al español para mayor claridad
- Creación de columna `Num_Servicios` (cantidad de servicios contratados)

### 4. 📊 Análisis Exploratorio (EDA)
- Distribución general de la variable objetivo `Evasion`
- Tasa de evasión por variables categóricas: tipo de contrato, método de pago, servicio de internet, factura digital
- Tasa de evasión por variables demográficas: género, adulto mayor, pareja, dependientes
- Distribución de variables numéricas por grupo (histogramas y boxplots)
- Matriz de correlación y análisis de dispersión

### 5. 📝 Conclusiones e Insights

---

## 🔑 Principales Hallazgos

| Factor | Observación |
|---|---|
| **Tipo de contrato** | Contratos mensuales tienen ~42-45% de evasión vs ~3% en contratos bianuales |
| **Antigüedad** | Clientes con menos meses de contrato evaden significativamente más |
| **Cargo mensual** | Clientes que evaden pagan más en promedio (percepción de bajo valor) |
| **Internet fibra óptica** | Mayor tasa de evasión que DSL o sin internet |
| **Método de pago** | El cheque electrónico está asociado a mayor evasión; el pago automático, a menor |
| **Servicios adicionales** | Seguridad online y soporte técnico reducen la evasión |
| **Número de servicios** | A más servicios contratados, menor tendencia a evadir |
| **Adultos mayores** | Tasa de evasión considerablemente más alta que el resto |

---

## 🛠️ Tecnologías Utilizadas

- **Python 3.10**
- **pandas** — manipulación y transformación de datos
- **numpy** — operaciones numéricas
- **matplotlib** — visualizaciones base
- **seaborn** — visualizaciones estadísticas

---

## ⚠️ Nota Técnica

Durante el proceso de limpieza, la columna `Churn` puede contener valores no reconocidos por el mapa de codificación binaria si el dataset tiene inconsistencias en los datos fuente. El notebook maneja esto eliminando las filas con valores inválidos antes de continuar con el análisis, garantizando que `Evasion` solo contenga los valores `0` (no evadió) y `1` (sí evadió).

---

## 👤 Autor

Proyecto desarrollado como parte del programa de formación en Data Science.
