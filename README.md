MLP vs Naive Bayes para detección de intrusiones de redes

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

Se utilizara el dataset *CICIDS-2017 (Canadian Institute for Cybersecurity Intrusion Detection Evaluation Dataset 2017)*.

Este dataset contiene trafico de red capturado a lo largo de 5 dias, contiene trafico normal y distintos tipos de ataques. Originalmente, el dataset cuenta con aproximadamente 2.830.743 observaciones y 79 columnas, entre las cuales se tiene a la variable objetivo `` `label` ``.

Para simplificar el problema de clasificación, se consolidaron las etiquetas originales en categorías comunes: BENIGN, DoS, DDoS, PortScan, Bot, Web Attack y Other.

---
## 4. Metodología

El análisis siguio un pipeline de procesamiento basado en el indicado por el paper de referencia.

1. **Eliminación de duplicados**

   Se identificaron 308.381 registros duplicados y posteriormente fueron eliminados, evitando así que interfieran con el entrenamiento.

2. **Tratamiento de valores faltantes**

   Fueron detectados 353 valores faltantes, estos, fueron imputados utilizando la media de la variable numerica correspondiente.

3. **Eliminación de valores infinitos**

    Se detectaron 2 registros que contenían valores infinitos, para deshacernos de ellos eliminamos dichos registros.

4. **Consolidación de etiquetas**

    Diferentes variantes de las etiquetas originales fueron agrupadas en categorías comunes para reducir la complejidad del problema.

5. **Separación train/test**

   Se realizo una partición estratificada de los datos con una proporción 80/20.

6. **Estandarización**

   Escalamos las variables numéricas utilizando `` `StandardScaler` ``, esto para evitar que variables con valores numéricos muy altos dominen en el modelado.

7. **Selección de variables**

   Calculamos la matriz de correlación entre las variables, una vez hecho eso, se la recorre de a pares buscando features altamente correlacionada de las cuales eliminamos una arbitrariamente. El criterio para considerar a dos features como altamente correlacionadas es: Su correlación absoluta es superior a 0.85

8. **Balanceo mediante SMOTE**

   El dataset presenta un fuerte desbalance entre clases, pues la clase `` `BENIGN` `` domina. Para solucionar esto utilizamos la técnica SMOTE, la cual genera muestras sintéticas de las clases minoritarias.

### Modelos

Se van a entrenar y comparar dos modelos:

- **Naive Bayes**: Es un algoritmo de aprendizaje automático supervisado que calcula la probabilidad de que un elemento pertenezca a una categoría determinada. Su principal característica es el supuesto de independencia condicional entre variables que utiliza, el cual lo hace bastante eficiente, sin embargo, este supuesto en general no se cumple.
- **MLP (Multilayer Perceptron)**: Es una red neuronal formada por una capa de entrada, capas ocultas interconectadas y una capa de salida. Las capas ocultas utilizan funciones de activación no lineales, lo que le permite al modelo aprender relaciones complejas. Durante el entrenamiento, los parámetros se ajustan mediante métodos de optimización por gradientes.

### Evaluación de desempeño

Una vez implementados ambos modelos, se los evalúa sobre el conjunto de prueba utilizando como métrica: Accuracy, F1-score macro y F1-score ponderado.

---
## 5. Resultados principales

Los resultados obtenidos en este trabajo son comparados con los reportados por el paper de referencia Ali et al.

Las diferencias en métricas respecto al paper pueden explicarse por distintos factores: Distintas versiones de el dataset, decisiones de preprocesamiento diferentes, hiperparámetros utilizados no concordantes y diferencias provocadas por seed aleatoria.

---
## 6. Cómo ejecutar

El repositorio se encuentra organizado de la siguiente forma:

MLP-vs-Naive-Bayes/
├── AI Usage/
│   └── tpfinal_mad1_naivebayes_mlp_chat.txt
├── Data/
│   └── README.md
├── Notebook/
│   └── tpfinal_mad1_naivebayes_mlp.ipynb
├── Reports/
│   ├── tpfinal_mad1_naivebayes_mlp.tex
│   └── tpfinal_mad1_naivebayes_mlp.pdf
└── README.md
