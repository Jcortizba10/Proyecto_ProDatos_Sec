# 📚 Conjunto de Datos de Clasificación de Temas de AG News

### 👥 Realizado por:
- **Diego Alexander Parra**  
- **Juan Camilo Ortiz**  

---

## 🚀 Introducción

El **conjunto de datos AG News** es una colección de más de 1 millón de artículos de noticias, recopilados de más de 2000 fuentes por *ComeToMyHead* durante un año. *ComeToMyHead* es un motor de búsqueda de noticias académicas en funcionamiento desde julio de 2004.

Este conjunto de datos se proporciona a la comunidad académica para fines de investigación en áreas como:
- **Minería de datos:** clustering, clasificación
- **Recuperación de información:** ranking, búsqueda
- **Otras aplicaciones:** XML, compresión y transmisión de datos

[**Más información aquí**](http://www.di.unipi.it/~gulli/AG_corpus_of_news_articles.html).

El **conjunto de datos de Clasificación de Temas de AG News** fue curado por **Xiang Zhang** (*xiang.zhang@nyu.edu*) a partir del corpus original. Este conjunto se utilizó como referente en el artículo:

- *Xiang Zhang, Junbo Zhao, Yann LeCun. Redes Neuronales Convolucionales a Nivel de Caracteres para la Clasificación de Textos. Avances en Sistemas de Procesamiento de Información Neural 28 (NIPS 2015).*  

---

## 📊 Descripción del Conjunto de Datos

El conjunto de datos se centra en las **cuatro categorías más grandes** del corpus original:

- 🌍 **Mundo**  
- 🏅 **Deportes**  
- 💼 **Negocios**  
- 🔬 **Ciencia/Tecnología**  

### 📦 Estructura del Conjunto de Datos
- **Conjunto de Entrenamiento:** 120,000 muestras (30,000 por clase)
- **Conjunto de Prueba:** 7,600 muestras (1,900 por clase)

### 📂 Detalles de los Archivos
- **`classes.txt`**: Lista de clases correspondientes a cada etiqueta.
- **`train.csv` y `test.csv`**: Muestras de entrenamiento y prueba en formato CSV.

Cada archivo CSV incluye:
1. **🔢 Índice de Clase (1 a 4)**
2. **📄 Título del Artículo**
3. **💰 Descripción del Artículo**

> *Nota:* Los títulos y descripciones están entrecomillados (`" "`). Las comillas internas se escapan con comillas dobles (`""`). Los saltos de línea se representan como `\n`.

---

## ⚙️ Metodología

### 1️⃣ Preprocesamiento de Datos
- **Tokenización y Relleno:** Estandarización de la longitud de las secuencias de entrada.
- **Codificación One-Hot:** Transformación de variables categóricas.

### 2️⃣ Arquitectura del Modelo
- **LSTM (Long Short-Term Memory):** Capaz de manejar dependencias a largo plazo.
- **GRU (Gated Recurrent Unit):** Alternativa eficiente al LSTM.
- **Transformer (Atención de Cabeza Única):** Captura relaciones contextuales.
- **Transformer (Atención Multi-Cabezal - 4 Cabezas):** Mejora el procesamiento paralelo de la atención.

---

## 📈 Resultados

El rendimiento de cada modelo se evaluó usando **Precisión**, **Recall** y **F1-Score**.

### 🔍 Comparación General
- **LSTM y GRU:** Alcanzaron una **precisión del 91%** y puntuaciones F1 de **0.91**, mostrando alto rendimiento.
- **Transformers (1 y 4 Cabezas):** Precisión del **90%** con F1 de **0.90**, ligeramente inferior a LSTM y GRU.

### 🏆 Rendimiento por Categoría
- **Deportes:** Mejor rendimiento, F1 de **0.97** (GRU) y **0.96** (otros modelos).
- **Negocios:** Rendimiento más bajo, especialmente en el Transformer de 4 cabezas (F1: **0.86**).
- **Ciencia/Tecnología:** Rendimiento estable, F1 entre **0.87** y **0.88**.

### ⚡ Impacto de Cabezas de Atención en Transformers
- Aumentar de **1 a 4 cabezas** **no mejoró significativamente el rendimiento**. En algunos casos, hubo ligeras disminuciones, como en la categoría de Negocios (de **0.86** a **0.84**).

---

## ✅ Conclusiones

- **LSTM y GRU** demostraron ser altamente efectivos, con GRU destacando por su eficiencia computacional.
- Aunque los **Transformers** son potentes en tareas complejas, **no superaron** a los modelos basados en RNN en este escenario.
- El **número de cabezas de atención** en Transformers **no garantizó mejoras** significativas.

---

## 💡 Recomendaciones

1. **Ajuste de Hiperparámetros:** Explorar configuraciones para optimizar el rendimiento de los Transformers.
2. **Embeddings Preentrenados:** Utilizar modelos de embeddings para mejorar la comprensión semántica.
3. **Aumento de Datos:** Implementar técnicas de aumento para mejorar el rendimiento, especialmente en categorías más desafiantes como *Negocios*.



