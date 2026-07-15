# pneumonia-classification-deep-learning
# Clasificación de Neumonía en Radiografías de Tórax (Chest X-Ray)

Este proyecto está diseñado para la descarga, preprocesamiento, limpieza, análisis y visualización de un conjunto de datos de radiografías de tórax extraídas de Kaggle. El objetivo principal es preparar y balancear un pipeline de datos optimizado para el entrenamiento posterior de modelos de Inteligencia Artificial orientados al diagnóstico médico automatizado de Neumonía.

## Estructura del Proyecto

El flujo de trabajo implementado en el entorno de desarrollo se divide en cuatro etapas principales:

1. **Descarga Automatizada del Dataset**: Integración directa con la API de Kaggle para la obtención del dataset oficial de radiografías de tórax.
2. **Redireccionamiento y Redimensionamiento**: Procesamiento por lotes de las imágenes para estandarizar sus dimensiones y optimizar el almacenamiento.
3. **Limpieza e Inspección de Datos**: Validación estructural, conteo exhaustivo de muestras por clase (`NORMAL` vs. `PNEUMONIA`) y división del dataset (`train`, `test`, `val`).
4. **Análisis y Visualización**: Generación de métricas estadísticas y gráficos analíticos interactivos sobre la distribución y balance del dataset.

---

## Requisitos e Instalación

El proyecto está desarrollado en **Python 3** y requiere las siguientes dependencias clave:

```bash
pip install kagglehub pandas pillow matplotlib seaborn
```

> **Nota:** Si ejecutas el notebook en Google Colab, la mayoría de estas librerías ya se encuentran preinstaladas, requiriendo únicamente la inicialización y descarga a través de `kagglehub`.

---

## Guía de Ejecución Paso a Paso

### 1. Descarga del Dataset

El proyecto utiliza la herramienta oficial `kagglehub` para descargar de forma automática y asíncrona la versión más reciente del conjunto de datos **Chest X-Ray Images (Pneumonia)** de Paul Mooney:

```python
import kagglehub

path = kagglehub.dataset_download("paultimothymooney/chest-xray-pneumonia")
print("Ruta de los archivos del dataset:", path)
```

### 2. Preprocesamiento y Redimensionamiento de Imágenes

Para optimizar el uso de memoria RAM y acelerar los tiempos de cómputo durante la fase de Deep Learning, las imágenes originales se redimensionan a una resolución estandarizada y se guardan bajo una estructura optimizada en:

```text
./resized_chest_xray_balanced_limited
```

**Entrada:**

```text
chest_xray
```

(Muestras de imágenes médicas originales de alta resolución).

**Salida:**

```text
resized_chest_xray_balanced_limited
```

(Dataset optimizado estructurado por categorías).

### 3. Limpieza y Validación Estructural

Se realiza un escaneo completo de los directorios para garantizar la integridad de los archivos, mapeando las clases en un DataFrame de `pandas`. Esto permite registrar los conteos por carpeta (`train`, `test`, `val`) y por diagnóstico (`NORMAL`, `PNEUMONIA`).

### 4. Análisis y Visualización de Datos

Utilizando `matplotlib` y `seaborn`, el script genera un reporte agregando los totales absolutos y porcentuales de la distribución de clases. Esto resulta crucial para identificar posibles sesgos o desbalances severos de datos (*Class Imbalance*) que puedan afectar la precisión del modelo predictivo.

---

## Resultados Esperados en el Análisis

Al ejecutar la fase final, el entorno generará:

- Una tabla consolidada en consola con la distribución de clases.
- Gráficos estadísticos que muestran la proporción exacta de radiografías sanas vs. con presencia de neumonía.
- Métricas descriptivas para evaluar el balance del dataset antes del entrenamiento del modelo.
- Información útil para la toma de decisiones relacionadas con técnicas de balanceo o aumento de datos (*Data Augmentation*).

---

## Estructura General del Proyecto

```text
Proyecto/
│
├── chest_xray/
│   ├── train/
│   ├── test/
│   └── val/
│
├── resized_chest_xray_balanced_limited/
│   ├── train/
│   ├── test/
│   └── val/
│
├── notebooks/
│   └── pneumonia_analysis.ipynb
│
└── README.md
```

---

## Objetivo del Proyecto

Desarrollar un pipeline completo de procesamiento y análisis de imágenes médicas que permita:

- Descargar automáticamente datasets desde Kaggle.
- Estandarizar imágenes para modelos de Deep Learning.
- Validar la calidad e integridad de los datos.
- Analizar la distribución de clases.
- Preparar un conjunto de datos confiable para la clasificación automática de neumonía mediante Inteligencia Artificial.

---

## Licencia y Créditos

**Dataset Original:**  
Chest X-Ray Images (Pneumonia) por Paul Mooney — Licencia CC BY 4.0.

**Desarrollo:**  
Proyecto de Inteligencia Artificial implementado en Jupyter Notebook y Google Colab para fines académicos y de investigación.

### Tecnologías Utilizadas

- Python 3
- KaggleHub
- Pandas
- Pillow (PIL)
- Matplotlib
- Seaborn
- Jupyter Notebook
- Google Colab
