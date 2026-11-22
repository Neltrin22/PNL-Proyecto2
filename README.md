```markdown
# Proyecto de Procesamiento del Lenguaje Natural (PLN)

Este repositorio/notebook contiene el desarrollo y entrenamiento de modelos avanzados de lenguaje de transferencia (Transformers) utilizando la librería `transformers` de Hugging Face para resolver tres tareas fundamentales en el área del Procesamiento del Lenguaje Natural.

---

## 🛠️ Estructura del Proyecto y Tareas

### 1. 🏷️ Clasificación de Intenciones (Problema de Clasificación)
* **Dataset:** `PolyAI/banking77` (Consultas bancarias reales de atención al cliente).
* **Modelo Utilizado:** `distilbert-base-uncased` (DistilBERT).
* **Objetivo:** Clasificar consultas breves en lenguaje natural en una de las **77 intenciones** posibles del dominio de banca digital.
* **Resultados destacados:** Optimizado tras una búsqueda sistemática de hiperparámetros (Grid Search rápido) variando épocas y Learning Rate, alcanzando una alta confianza en la demo de inferencia.

### 2. 📍 Reconocimiento de Entidades Nombradas — NER (Problema de Etiquetado)
* **Dataset:** `unimelb-nlp/wikiann` (Subconjunto en Español).
* **Modelo Utilizado:** `dccuchile/bert-base-spanish-wwm-cased` (BETO - BERT en español).
* **Objetivo:** Clasificar cada palabra (token classification) según el formato BIO para identificar entidades de tipo **Localización (LOC)**, **Persona (PER)** y **Organización (ORG)**.
* **Metodología:** Alineación robusta de subtokens con sus etiquetas originales asignando `-100` a tokens especiales y subpalabras del tokenizador. Evaluación optimizada utilizando la métrica `seqeval` (F1-score global).

### 3. ✍️ Resumen de Diálogos (Problema Seq2Seq)
* **Dataset:** `knkarthick/dialogsum` (Transcripciones de diálogos informales).
* **Modelo Utilizado:** `t5-small` (Seq2Seq Transformer).
* **Objetivo:** Generar resúmenes abstractivos coherentes, concisos y estructurados a partir de conversaciones de soporte al cliente.
* **Evaluación:** Uso de la métrica estándar de la industria `ROUGE` (ROUGE-1, ROUGE-2, ROUGE-L) para medir el solapamiento con los resúmenes humanos de referencia.

---

## 📁 Estructura de Almacenamiento e Inferencia

Todos los modelos ganadores han sido entrenados utilizando técnicas de optimización como precisión mixta (`fp16`), decaimiento de peso (`weight_decay`) y guardado del mejor checkpoint (`load_best_model_at_end`).

* **Persistencia:** Los modelos finales y sus respectivos tokenizadores se guardan de forma permanente en Google Drive bajo la ruta `/content/drive/MyDrive/PLN/Proyecto2/` para permitir su posterior despliegue o inferencia inmediata mediante pipelines de Hugging Face.
```
