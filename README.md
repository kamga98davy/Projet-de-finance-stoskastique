## **Titre du projet**

**Valuation with a tree – Évaluation d'un produit de rente variable avec garanties**

---

## 🎯 **Objectif global**

Le projet consiste à **évaluer la valeur actuarielle** d’un produit de rente variable souscrit par un assuré. Ce produit combine des éléments d’assurance vie (avec un taux de mortalité) et de finance (fonds investi dans un actif risqué avec un retrait annuel garanti).

L’évaluation se fera par **deux méthodes principales** :

1. **Arbre binomial (binomial tree)** pour approximer le processus stochastique.
2. **Simulation Monte-Carlo** pour vérifier et comparer les résultats.

---

## 🔎 **Contexte technique**

* Le **fonds $S_t$** suit une dynamique de type **mouvement brownien géométrique (GBM)** avec :

  * Volatilité : $\sigma = 19\%$
  * Taux sans risque : $r = 3\%$
* L’assuré retire chaque année une proportion $\gamma = 10\%$ de la valeur initiale du contrat.
* À l’échéance, le bénéficiaire reçoit le **maximum** entre la valeur restante du fonds et un capital minimum garanti $K_T$.
* Valeurs clés :

  * $F_0 = 250 \text{k€}$
  * $K_T = 100 \text{k€}$
  * Durée $T = 10$ ans
  * Taux de mortalité annuel : 0,08 %

---

## 🧮 **Travail à faire**

### **1) Formulation mathématique**

Fournir l’expression analytique de la valeur actuarielle du contrat en supposant un taux de mortalité constant.

### **2) Évaluation par arbre binomial**

* Implémenter un modèle à arbre binaire sous R ou Python.
* Représenter la convergence du prix (valeur du contrat) en fonction du nombre de pas de discrétisation.
* Expliquer clairement l’algorithme utilisé dans un rapport.

### **3) Simulation Monte-Carlo**

* Simuler la trajectoire de $S_t$, calculer les flux de trésorerie attendus.
* Ne pas simuler la mortalité, mais intégrer les probabilités de survie dans les flux.
* Comparer les résultats avec ceux obtenus par l’arbre binomial.

### **4) Stratégie alternative d’investissement**

* L’assuré investit dans un portefeuille mixte :

  $$\frac{dS_t}{S_t} = \theta \frac{dS_t^{(1)}}{S_t^{(1)}} + (1 - \theta) \frac{dS_t^{(2)}}{S_t^{(2)}}$$

  avec $\theta \in [0,1]$ représentant la part d’actions et $S_t^{(1)}$, $S_t^{(2)}$ les fonds d’actions et d’obligations.
* Les séries de données sont fournies dans le fichier `DATA.xlsx`.

**Tâches associées :**

* Estimer les rendements, écarts-types et corrélations log-retours des deux fonds.
* Simuler et évaluer le contrat pour différentes allocations en faisant varier $\theta$.
* Recommander une allocation optimale selon les résultats.

---
