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


## Demo interactiva para la defensa

El notebook principal incluye al final una interfaz basada en **ipywidgets** que utiliza el mismo
objeto `nlp` y el mismo modelo `es_core_news_sm`. La interfaz no reemplaza el código del
experimento: únicamente presenta las salidas de forma más visual para la demostración en vivo.

La demo permite:

- seleccionar O1, O11, O12 y O13;
- escribir y analizar una oración nueva;
- comparar la prueba adicional *Los estudiantes resuelven los ejercicios*;
- visualizar token, lema, POS, morfología, dependencia y núcleo;
- generar el árbol de dependencias con displaCy.

Secuencia sugerida durante la defensa:

1. O1: explicar `ROOT`, `nsubj` y `obj`;
2. cambiar singular a plural y observar los rasgos morfológicos;
3. comparar O11 y O12 con la palabra `banco`;
4. finalizar con O13 y su ambigüedad sintáctica.

> La prueba singular → plural se utiliza únicamente como demostración en vivo y no modifica
> las 13 oraciones ni los resultados descriptivos del corpus original.

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
