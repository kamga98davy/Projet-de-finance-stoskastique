## **PARTIE 1 : Construction de la courbe des taux**

### **Objectif**

Évaluer la **meilleure estimation (best estimate)** de la valeur actuelle d’un portefeuille de contrats d’assurance vie, en utilisant comme taux d’actualisation les **taux zéro-coupon (zero-coupon yields)** des obligations d’État belges (OLOs), au 10/02/2025.

---

## **Étapes de la première partie**

---

### 🔹 1. **Calcul des intérêts courus et du dirty price**

* Utilisation de la **convention "jour réel/jour réel"** (*actual/actual*) pour le calcul des intérêts courus.
* Objectif : obtenir le **prix "sale"** (*dirty price*) de chaque obligation, c’est-à-dire :

  $$
  \text{Dirty Price} = \text{Clean Price} + \text{Intérêts courus}
  $$

📌 **Rappel :**

* Le *clean price* est le prix coté (sans les coupons courus).
* Le *dirty price* reflète la vraie valeur de marché que paierait un acheteur.

---

### 🔹 2. **Calcul des taux actuariels (yield) et courbe des taux**

* Calcul du **yield to maturity** (taux de rendement actuariel) pour chaque obligation.
* Construction de la **courbe des taux actuariels**.
* Interprétation des résultats et **analyse des anomalies/irrégularités observées** (liées à l’illiquidité, coupons faibles, etc.).

---

### 🔹 3. **Lissage de la courbe des taux avec le modèle de Svensson**

* Ajustement d’une **courbe de Svensson** (modèle paramétrique à 6 paramètres) à la courbe des taux observés.
* Objectif : **minimiser l’erreur quadratique moyenne** entre les taux observés et ceux du modèle.
* Utilisation d’**Excel Solver** pour ajuster les paramètres $(b_0, b_1, b_2, b_3, c_1, c_2)$.
* Comparaison entre courbe observée et courbe lissée.

---

## 📦 **Outils utilisés**

* **Excel** exclusivement pour les calculs de la partie 1 (intérêts courus, taux actuariels, ajustement Svensson).

## **PARTIE 2**

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
