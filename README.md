Выполнил `Дьяконов Олег`
Группа `БВТ2506`
---

### Установка зависимостей
```
pip install sentence-transformers numpy pandas matplotlib scikit-learn
```
> Устанавливаем библиотеки для работы с эмбеддингами, вычислений и визуализации
---

### Импорт библиотек
```
import json
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sentence_transformers import SentenceTransformer
from sklearn.manifold import TSNE
from sklearn.metrics.pairwise import cosine_similarity
import warnings
warnings.filterwarnings('ignore')
```
> `entence-transformers` - генерация эмбеддингов
> `sklearn.manifold.TSNE` - визуализация в 2D
> `sklearn.metrics.pairwise.cosine_similarity` - сравнение векторов
---

### Загрузка данных

```
with open('code_corpus.json', 'r', encoding='utf-8') as f:
    code_corpus = json.load(f)

with open('eval_questions.json', 'r', encoding='utf-8') as f:
    eval_questions = json.load(f)
```
> `code_corpus.json` - 200 фрагментов кода (Python + Java)
> `eval_questions.json` — 25 вопросов с правильными ответами
---

### Подготовка тестов для эмбеддингов

```
corpus_texts = [f"{item['code']} {item['description']}" for item in code_corpus]
queries = [q['query'] for q in eval_questions]
correct_ids = [q['correct_chunk_id'] for q in eval_questions]
```
> Склеиваем код и описание в один текст
> Так модель видит синтаксис и смысловое описание
---

### Загрузка моделей
```
models = {}
for name in ["paraphrase-multilingual-MiniLM-L12-v2", 
             "paraphrase-multilingual-mpnet-base-v2"]:
    models[name] = SentenceTransformer(name)
```
> `MiniLM-L12` — 384 размерность, 80MB, быстрая
> `mpnet-base` — 768 размерность, 420MB, точнее
