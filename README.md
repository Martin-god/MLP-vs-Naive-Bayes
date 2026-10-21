# MLP vs Naive Bayes para detección de intrusiones de redes

---
## 1. Descripción breve

Este trabajo compara dos modelos de aprendizaje supervisado al momento de detectar intrusiones de redes: *Naive Bayes* como modelo de aprendizaje probabilístico y *Multilayer Perceptron (MLP)* como modelo de aprendizaje profundo.

Ambos modelos se aplican utilizando el dataset *CICIDS-2017*, que contiene trafico de red normal y diferentes tipos de ataques. Esto con el fin de analizar y comparar su desempeño utilizando distintas metricas, para luego, contrastar los resultados obtenidos con los reportados en el trabajo de Ali et al. (2025).

---
## 2. Motivacion

Como consecuencia de la digitalización hubo un incremento en la vulnerabilidad de las redes informáticas ante amenazas, por ello, la detección de intrusiones en redes se convirtió en un problema de gran relevancia.

La comparación entre MLP y Naive Bayes resulta interesante pues ambos modelos representan filosofías de aprendizaje automático distintas. Además, pone sobre la mesa la discusión de "más complejo no siempre es mejor", pues, al Naive Bayes ser utilizado generalmente como baseline, si un MLP no supera significativamente la precisión de NB en un conjunto de datos, no se justifica el gasto computacional que el mismo tiene.

Este trabajo toma como referencia el artículo **Deep Learning vs. Machine Learning for Intrusion Detection in Computer Networks: A Comparative Study** (Ali et al., 2025), que compara modelos clásicos de aprendizaje automático vs modelos de aprendizaje profundo sobre el dataset CICIDS-2017.

---
## 3. Datos

Se utilizara el dataset *CICIDS-2017 (Canadian Institute for Cybersecurity Intrusion Detection Evaluation Dataset 2017).

Este dataset contiene trafico de red capturado a lo largo de 5 dias, contiene trafico normal y distintos tipos de ataques. Originalmente, el dataset cuenta con aproximadamente 2.830.743 observaciones y 79 columnas, entre las cuales se tiene a la variable objetivo '' 'label' ''.
