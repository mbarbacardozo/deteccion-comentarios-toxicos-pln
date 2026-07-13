# Detección de Comentarios Tóxicos en Español

**Proyecto Final del Módulo · Maestría en Inteligencia Artificial**
Universidad Católica Boliviana "San Pablo"

![Python](https://img.shields.io/badge/Python-3.x-blue)
![NLP](https://img.shields.io/badge/NLP-Español-orange)
![Gradio](https://img.shields.io/badge/Interfaz-Gradio-red)
![Status](https://img.shields.io/badge/Estado-Completo-brightgreen)

**Autora:** Montserrat Barba Cardozo
**Docente:** M.Sc. Kenji Kawaida
**Fecha de entrega:** 13/07/2026

---

## Enlaces

- **Demo en vivo (permanente):** https://huggingface.co/spaces/MontserratBARBC/detector-toxicidad-es
- **Página del proyecto:** https://mbarbacardozo.github.io/deteccion-comentarios-toxicos-pln/

## Descripción

Sistema de Procesamiento de Lenguaje Natural de punta a punta que detecta comentarios tóxicos en español (insultos, ataques personales, discurso de odio), pensado como herramienta de apoyo para moderación de contenido en medios digitales.

El sistema no reemplaza la decisión humana: prioriza contenido para revisión.

## Dataset

**SocialTOX** (Hugging Face) — 4,011 comentarios reales de 16 medios de noticias en español, anotados por nivel de toxicidad. Licencia CC-BY-4.0.

## Pipeline

| Etapa | Técnica |
|---|---|
| Preprocesamiento | Limpieza + lematización (spaCy) |
| Representación numérica | TF-IDF + Embeddings multilingües |
| Modelado de temas | LDA (5 tópicos) |
| Análisis de sentimiento | RoBERTuito (preentrenado) |
| Clasificación clásica | Naive Bayes (ComplementNB) |
| Clasificación neuronal | BiLSTM |
| Interfaz | Gradio (modo individual + modo lote CSV) |

## Resultados

| Modelo | Accuracy | Precision | Recall | F1 |
|---|---|---|---|---|
| **Naive Bayes** (TF-IDF) | 0.760 | 0.268 | 0.324 | **0.294** |
| BiLSTM | 0.727 | 0.168 | 0.196 | 0.181 |

Naive Bayes superó a la red neuronal — hallazgo consistente con la literatura: con un set de entrenamiento moderado (3,016 comentarios, 748 tóxicos), un modelo clásico generaliza mejor que uno neuronal.

## Contenido del repositorio

```
├── ProyectoNLP_ComentariosToxicos_FINAL.ipynb   # Notebook completo (código + informe)
├── index.html                                    # Página del proyecto (GitHub Pages)
├── matriz_nb.png                                 # Matriz de confusión - Naive Bayes
├── matriz_bilstm.png                             # Matriz de confusión - BiLSTM
├── dist_clases.png                               # Distribución de clases
├── curva_umbral.png                              # F1 según umbral de decisión
└── README.md
```

## Cómo correrlo

1. Abrir el notebook en Google Colab
2. Activar GPU: Entorno de ejecución -> Cambiar tipo de entorno de ejecución -> GPU (T4)
3. Ejecutar todas las celdas en orden
4. La interfaz Gradio se genera al final del notebook (enlace temporal), o usar directamente el Space permanente enlazado arriba

## Limitaciones

- Corpus proveniente de España/Latinoamérica; puede generalizar peor ante contextos muy locales (ej. Bolivia)
- Dificultad esperable con sarcasmo e ironía
- Precisión moderada en la clase "Tóxico" (0.27)

---

*Proyecto académico — Módulo de Procesamiento de Lenguaje Natural, 2026*

