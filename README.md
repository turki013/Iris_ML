# 🌸 Iris Flower Classification — KNN vs Logistic Regression

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-green?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

> مشروع تصنيف زهور الأيريس باستخدام خوارزميتي **KNN** و**Logistic Regression**، مع تحسين قيمة K للوصول إلى أفضل دقة ممكنة.

---

## 📌 نظرة عامة

يستخدم هذا المشروع مجموعة بيانات **Iris** الشهيرة لتصنيف أنواع زهور الأيريس الثلاثة بناءً على أبعادها. يتضمن الـ notebook مقارنةً بين نموذجين، ثم إيجاد أفضل قيمة لـ K في خوارزمية KNN.

الأنواع المستهدفة:
- 🌺 *Iris Setosa*
- 🌷 *Iris Versicolor*
- 🌼 *Iris Virginica*

---

## 📊 البيانات (Iris Dataset)

| الميزة | الوصف |
|---|---|
| `sepal_length` | طول السبلة (سم) |
| `sepal_width` | عرض السبلة (سم) |
| `petal_length` | طول البتلة (سم) |
| `petal_width` | عرض البتلة (سم) |
| `species` | النوع المستهدف (Setosa / Versicolor / Virginica) |

- **عدد العينات:** 150 (50 لكل نوع)
- **المصدر:** `sklearn.datasets.load_iris()`
- **تقسيم البيانات:** 80% تدريب — 20% اختبار (`random_state=98`)

---

## 🗂️ هيكل المشروع

```
Iris_ML/
│
├── main.ipynb        # الـ Notebook الرئيسي
└── README.md         # توثيق المشروع
```

---

## 🔬 خطوات العمل

### 1️⃣ استدعاء المكتبات وتحميل البيانات
```python
from sklearn.neighbors import KNeighborsClassifier
from sklearn.datasets import load_iris

iris = load_iris()
x = iris.data
y = iris.target
```

### 2️⃣ تدريب نموذج KNN (K=1)
```python
knn = KNeighborsClassifier(n_neighbors=1)
knn.fit(x_train, y_train)
```
- **دقة النموذج:** `93.33%`

### 3️⃣ مقارنة مع Logistic Regression
```python
logreg = LogisticRegression(max_iter=1000)
logreg.fit(x_train, y_train)
```
- **دقة النموذج:** `93.33%`

> كلا النموذجين حققا نفس الدقة، مما دفع إلى البحث عن أفضل قيمة K.

### 4️⃣ إيجاد أفضل قيمة K

تم اختبار قيم K من 1 إلى 27 ورسم النتائج:

```python
k_range = range(1, 28)
scores = []
for k in k_range:
    knn = KNeighborsClassifier(n_neighbors=k)
    knn.fit(x_train, y_train)
    y_pred = knn.predict(x_test)
    scores.append(accuracy_score(y_test, y_pred))
```

![K vs Accuracy Plot](https://i.imgur.com/placeholder.png)

### 5️⃣ النموذج النهائي (K=14)
```python
knn = KNeighborsClassifier(n_neighbors=14)
knn.fit(x, y)
knn_pred = knn.predict([[6.1, 2.8, 4.7, 1.4]])
# Output: ['versicolor']
```

---

## 📈 مقارنة النماذج

| النموذج | دقة الاختبار | ملاحظات |
|---|---|---|
| KNN (K=1) | 93.33% | بسيط لكن قد يكون حساساً للضوضاء |
| Logistic Regression | 93.33% | خطي، أداء مستقر |
| KNN (K=14) ✅ | أفضل دقة | النموذج النهائي بعد ضبط K |

---

## 🛠️ المكتبات المستخدمة

| المكتبة | الغرض |
|---|---|
| `scikit-learn` | تحميل البيانات، النماذج، التقييم |
| `matplotlib` | رسم منحنى K مقابل الدقة |

---

## 🚀 تشغيل المشروع

### المتطلبات
```bash
pip install scikit-learn matplotlib jupyter
```

### تشغيل الـ Notebook
```bash
git clone https://github.com/turki013/Iris_ML.git
cd Iris_ML
jupyter notebook main.ipynb
```

---

## 👤 المطور

**Turki**  
GitHub: [@turki013](https://github.com/turki013)

---

<p align="center">
  Built with Python 🐍 & scikit-learn
</p>