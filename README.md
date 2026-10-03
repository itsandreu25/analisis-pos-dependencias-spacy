# Análisis de etiquetas POS y dependencias sintácticas con spaCy

Implementación práctica desarrollada para la asignatura **Base de Conocimiento** de la carrera de **Ingeniería en Software** de la **Escuela Superior Politécnica de Chimborazo (ESPOCH)**.

El proyecto realiza un análisis morfosintáctico de un corpus controlado de oraciones en español mediante la biblioteca **spaCy** y el modelo lingüístico `es_core_news_sm`.

## Objetivo

Analizar categorías gramaticales (POS) y relaciones de dependencia sintáctica en oraciones en español, incluyendo casos de ambigüedad léxica y sintáctica.

## Herramientas utilizadas

- Python 3.13.15
- spaCy 3.8.16
- `es_core_news_sm` 3.8.0
- pandas 2.2.3
- Matplotlib
- displaCy
- Google Colab / Jupyter Notebook

## Corpus

Se utilizó un corpus didáctico controlado compuesto por **13 oraciones en español**.

Las oraciones incluyen:

- estructuras sujeto-verbo-objeto;
- modificadores;
- coordinación;
- subordinación;
- complementos preposicionales;
- casos de ambigüedad léxica;
- un caso de ambigüedad sintáctica.

El corpus tiene fines demostrativos y **no constituye un gold standard anotado manualmente**.

## Información extraída

Para cada token se registran los siguientes atributos:

- texto original;
- lema;
- categoría gramatical POS;
- rasgos morfológicos;
- relación de dependencia;
- cabeza sintáctica.

## Casos analizados

### Ambigüedad léxica

Se compara la palabra `banco` en dos contextos diferentes:

- como institución financiera;
- como asiento.

El análisis permite observar cómo una misma forma léxica puede mantener su categoría gramatical y desempeñar funciones sintácticas diferentes según el contexto.

### Ambigüedad sintáctica

Se analiza la oración:

> María observó al profesor con los binoculares.

El objetivo es observar qué estructura de dependencias selecciona automáticamente spaCy ante una construcción que admite más de una interpretación.

## Estructura del repositorio

```text
analisis-pos-dependencias-spacy/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── notebook/
│   └── analisis_pos_dependencias_spacy.ipynb
│
├── datos/
│   ├── resultados_tokens.csv
│   ├── resumen_pos.csv
│   └── resumen_dependencias.csv
│
└── figuras/
    ├── distribucion_pos.png
    └── dependencias_O13.svg
```

## Ejecución

1. Instalar las dependencias del proyecto:

```bash
pip install -r requirements.txt
```

2. Instalar el modelo de español de spaCy:

```bash
python -m spacy download es_core_news_sm
```

3. Abrir y ejecutar el notebook:

```text
notebook/analisis_pos_dependencias_spacy.ipynb
```

El notebook también puede ejecutarse mediante **Google Colab**.

## Archivos generados

- `resultados_tokens.csv`: información lingüística detallada de cada token.
- `resumen_pos.csv`: frecuencia y porcentaje de las categorías POS.
- `resumen_dependencias.csv`: frecuencia y porcentaje de las relaciones sintácticas.
- `distribucion_pos.png`: gráfico de distribución de categorías POS.
- `dependencias_O13.svg`: representación del análisis de dependencias de la oración ambigua O13.

## Consideraciones sobre los resultados

El procesamiento de las 13 oraciones produjo:

- 114 tokens en total;
- 99 tokens al excluir signos de puntuación;
- 11 categorías POS diferentes;
- 17 tipos de relaciones de dependencia.

Estos valores corresponden a **estadísticas descriptivas del corpus** y no deben interpretarse como métricas de rendimiento del modelo.

No se calcularon `accuracy`, `precision`, `recall` ni `F1-Score`, debido a que el corpus utilizado no dispone de anotaciones manuales de referencia con las cuales comparar las predicciones.

## Reproducibilidad

El notebook documenta:

- la configuración del entorno;
- la carga del modelo lingüístico;
- el corpus utilizado;
- el procesamiento token por token;
- la generación de tablas;
- el análisis de casos ambiguos;
- las visualizaciones;
- la exportación de resultados.

Para reproducir el análisis, se recomienda ejecutar todas las celdas del notebook en orden desde un entorno limpio.

## Autores

Trabajo grupal desarrollado por:

- Anthony Fabricio Miranda Sinaluisa
- Carlos David Basantes Valdiviezo
- Juan Carlos López
- Anahí Micaela Quispillo Heredia
- Alejandro Salazar
- Andrea Gabriela Astudillo Dávalos

**Escuela Superior Politécnica de Chimborazo (ESPOCH)**  
**Facultad de Informática y Electrónica**  
**Carrera de Ingeniería en Software**  
**Asignatura: Base de Conocimiento**
