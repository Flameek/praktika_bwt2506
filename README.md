# praktika_bwt2506
Выполнил `Дьяконов Олег`
---

### Установка зависимостей
"""pip install sentence-transformers numpy pandas matplotlib scikit-learn"""
>>> Устанавливаем библиотеки для работы с эмбеддингами, вычислений и визуализации.

---

### Импорт библиотек
"""import json
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sentence_transformers import SentenceTransformer
from sklearn.manifold import TSNE
from sklearn.metrics.pairwise import cosine_similarity
import warnings
warnings.filterwarnings('ignore')"""
>>> `entence-transformers` - генерация эмбеддингов
>>> `sklearn.manifold.TSNE` - визуализация в 2D
>>> `sklearn.metrics.pairwise.cosine_similarity` - сравнение векторов

# Загрузка данных 
""" with open('code_corpus.json', 'r', encoding='utf-8') as f:
    code_corpus = json.load(f)

with open('eval_questions.json', 'r', encoding='utf-8') as f:
    eval_questions = json.load(f)"""
>>> `code_corpus.json` - 200 фрагментов кода (Python + Java)
    `eval_questions.json` — 25 вопросов с правильными ответами
