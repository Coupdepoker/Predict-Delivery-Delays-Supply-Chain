# 📦 Prédiction des Retards de Livraison — Supply Chain

> Modèle de Machine Learning pour anticiper les retards de livraison dans la chaîne d'approvisionnement de DataCo Global.

---

## 📌 Project Overview

DataCo Global fait face à un problème de retards de livraison qui nuit à la satisfaction client et à la réputation de l'entreprise. Ce projet utilise le Machine Learning pour **prédire à l'avance les commandes à risque de retard**, permettant une intervention proactive.

**Problème :** Classification binaire — une livraison sera-t-elle en retard ou non ?

---

## 🗂️ Project Structure

```
├── Predict_Delivery_Delays_Supply_Chain.ipynb  ← Pipeline complet
└── data/
    └── DataCoSupplyChainDataset.csv
```

---

## 🔬 Méthodologie

### 1. Data Preprocessing
- Suppression des colonnes non pertinentes
- Gestion des valeurs nulles
- Feature engineering : création de nouvelles variables plus discriminantes (`Order_to_Shipment_Hours`)
- Encodage et standardisation des variables

### 2. Analyse Exploratoire
- Matrice de corrélation pour identifier les features les plus liées aux retards
- Variables les plus corrélées avec `Late_delivery_risk` :

| Feature | Corrélation |
|---|---|
| `Order_to_Shipment_Hours` | +0.39 |
| `Shipping Mode` | -0.40 |
| `Days for Shipment (scheduled)` | -0.37 |
| `Type` | -0.062 |

### 3. Modèle — K-Nearest Neighbors (KNN)
- Optimisation du hyperparamètre **k** via minimisation du RMSE
- k optimal sélectionné : **k = 14**
- Entraînement sur un jeu de données splitté (train / test)

---

## 📊 Résultats

| Métrique | Train | Test |
|---|---|---|
| **Accuracy** | 95.17% | **95.31%** |
| **RMSE** | 0.2199 | 0.2166 |

- Le modèle généralise bien : le score sur le test est légèrement supérieur à celui du train
- Pas de surapprentissage (overfitting) détecté

---

## 🛠️ Tech Stack

| Catégorie | Outils |
|---|---|
| Langage | Python |
| ML | scikit-learn (KNeighborsClassifier) |
| Data | pandas, NumPy |
| Visualisation | Matplotlib, Seaborn |
| Environnement | Jupyter Notebook |

---

## 🚀 Getting Started

```bash
# Cloner le repo
git clone https://github.com/Coupdepoker/Predict-Delivery-Delays-Supply-Chain.git
cd Predict-Delivery-Delays-Supply-Chain

# Lancer le notebook
jupyter notebook Predict_Delivery_Delays_Supply_Chain.ipynb
```

---

## 💡 Key Takeaways

- Le **mode de livraison** et le **délai de traitement de la commande** sont les facteurs les plus prédictifs des retards
- L'algorithme KNN avec k=14 offre le meilleur compromis biais/variance
- Un modèle à **95% de précision** permettrait à DataCo Global d'identifier proactivement les commandes à risque et d'agir avant la livraison

---
