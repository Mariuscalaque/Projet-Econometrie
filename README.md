# 📊 Projet d'Économétrie — Cours de l'Or & Taux US 10Y

**Auteurs :** Pierre Loison & Marius Calaque

---

## 📖 Introduction

Ce projet d'économétrie étudie les **corrélations entre le cours de l'or et les taux d'intérêt obligataires américains à 10 ans (Taux US 10Y)** sur la période janvier 1990 – mai 2024.

L'or est un métal précieux qualifié de **valeur refuge** : il tend à se stabiliser, voire à s'apprécier, en périodes d'incertitude économique ou de forte volatilité des marchés. Les **taux US 10Y** représentent le rendement des obligations du Trésor américain sur dix ans et servent d'indicateur de référence pour de nombreux autres taux d'intérêt.

**Hypothèse principale :** En période d'incertitude, le cours de l'or augmente tandis que les taux US 10Y diminuent (les investisseurs se réfugient dans les obligations, faisant monter leur cours et baisser leur rendement). On s'attend donc à une **corrélation négative** entre les deux séries.

---

## 📁 Structure du projet

```
Projet-Econometrie/
├── Projet_Econometrie.ipynb   # Notebook principal (R via Google Colab)
└── README.md                  # Documentation du projet
```

> **Note :** Les fichiers de données (`Gold.xlsx`, `Rate10Y.xlsx`, `Spx.xlsx`) doivent être téléchargés manuellement dans l'environnement Google Colab avant d'exécuter le notebook.

---

## 📊 Données

| Série | Source | Période | Fréquence | N |
|-------|--------|---------|-----------|---|
| Cours de l'or ($/once) | Yahoo Finance | Jan. 1990 – Mai 2024 | Mensuelle | 413 |
| Taux US 10Y (%) | Yahoo Finance | Jan. 1990 – Mai 2024 | Mensuelle | 413 |

---

## 🔍 Contenu de l'analyse

### Partie 1 — Modélisation univariée

#### I. Analyse graphique des séries
- Évolution du cours de l'or : stable jusqu'en 2000, forte hausse après la crise financière de 2008, nouveaux records post-COVID (>2000 $/once)
- Évolution des taux US 10Y : tendance baissière de 1990 à 2020, forte remontée récente

#### II. Autocorrélogrammes (ACF & PACF)
- Les deux séries présentent une décroissance très lente des lags → **non-stationnarité**
- Chute brutale dès le 2ème lag sur les PACF → structure AR(1) probable

#### III. Tests de racine unitaire

**Série de l'Or :**
- **Test ADF** (avec tendance et constante) : τ = -1.543 < seuils critiques → non-rejet de H₀ → série **non stationnaire** (processus TS)
- **Test KPSS** : statistique = 6.05 (niveau) et 0.73 (tendance), p-value < 0.01 → rejet de H₀ → **non stationnaire**
- **Détrending + différenciation** : ADF → τ = -7.507, KPSS → p-value = 0.078 → série **stationnaire** après transformation

**Série des Taux US 10Y :**
- **Test ADF** (avec tendance et constante) : τ = -2.317 < seuils critiques → non-rejet de H₀ → série **non stationnaire**
- Tests complémentaires et stationnarisation similaires à la série de l'or

### Partie 2 — Modélisation bivariée

- Analyse de la **cointégration** entre les deux séries
- Modèle à **Correction d'Erreur (ECM)**
- Tests de **causalité de Granger**
- Estimation et interprétation économique des résultats

---

## 🛠️ Technologies utilisées

| Outil | Usage |
|-------|-------|
| **R** | Langage de programmation principal |
| **Google Colab** | Environnement d'exécution du notebook |
| `readxl` | Lecture des fichiers Excel |
| `ggplot2` | Visualisation des séries temporelles |
| `forecast` | Calcul des ACF/PACF |
| `tseries` | Tests ADF et KPSS |
| `urca` | Tests de racine unitaire avancés |

---

## 🚀 Lancer le projet

1. **Cloner le dépôt :**
   ```bash
   git clone https://github.com/Mariuscalaque/Projet-Econometrie.git
   ```

2. **Ouvrir le notebook** `Projet_Econometrie.ipynb` dans [Google Colab](https://colab.research.google.com/)

3. **Télécharger les données** dans l'onglet "Fichiers" de Colab :
   - `Gold.xlsx`
   - `Rate10Y.xlsx`
   - `Spx.xlsx`

4. **Exécuter les cellules** dans l'ordre

---

## 👥 Auteurs

| Nom | GitHub |
|-----|--------|
| Marius Calaque | [@Mariuscalaque](https://github.com/Mariuscalaque) |
| Pierre Loison | — |

---

## 📄 Licence

Projet réalisé dans le cadre d'un cours d'économétrie. Usage académique uniquement.
