# 🌩️ Classification des Nuages avec le Deep Learning

Ce projet vise à développer un système automatique de classification des nuages à partir d’images capturées depuis le sol, en utilisant des techniques avancées de deep learning telles que les CNN (MobileNetV2) et les Vision Transformers (ViT).

## 🎯 Objectif du projet

Concevoir un outil capable de :

- Reconnaître automatiquement les genres et motifs de nuages à partir d’images.
- Optimiser les prévisions météorologiques et l’analyse du climat local.
- Exploiter des architectures récentes de deep learning malgré un corpus limité.

## 🗂️ Structure du projet

- `data/` : contient les jeux de données CCSN et SWIMCAT.
- `models/` : implémentations de MobileNetV2 et Vision Transformer.
- `notebooks/` : notebooks Jupyter pour l'entraînement, la validation, l'évaluation.
- `results/` : courbes d’apprentissage, matrices de confusion, scores.
- `utils/` : fonctions de prétraitement, d’augmentation et de visualisation.

## 🧠 Méthodologies

- **CNN (MobileNetV2)** : utilisé avec et sans augmentation de données.
- **Vision Transformer (ViT-B/16)** : avec Shifted Patch Tokenization et Locality Self-Attention.
- **Triplet Loss** : pour simuler davantage de combinaisons dans des corpus réduits.

## 📊 Jeux de données utilisés

### 1. CCSN (Cirrus, Cumulus, Stratus, Nimbus)

- 2543 images 256×256
- 11 classes originales, réduites à 9 pour éviter les déséquilibres extrêmes.

### 2. SWIMCAT

- 784 images 125×125
- 5 classes : Clear Sky, Patterned Clouds, Thick Dark Clouds, Thick White Clouds, Veil Clouds.

## ⚙️ Entraînement

| Modèle             | Accuracy (CCSN) | F1 (CCSN) | Accuracy (SWIMCAT) | F1 (SWIMCAT) |
| ------------------ | --------------- | --------- | ------------------ | ------------ |
| MobileNetV2 + Aug. | 78.4%           | 0.77      | 92.6%              | 0.91         |
| ViT                | 70.1%           | 0.68      | 88.3%              | 0.87         |

- Optimiseur : SGD ou AdamW
- Batch size : 8/16
- Early stopping avec patience = 20
- Techniques : horizontal flip, zoom, variation de luminosité

## 🔍 Analyse critique

- Les CNN sont plus robustes avec peu de données.
- ViT nécessite des corpus plus vastes malgré des ajustements locaux.
- L’augmentation améliore surtout la classification fine (CCSN).

## 🔮 Perspectives

- Intégrer l’auto-supervision pour réduire l’effort d’annotation.
- Collecter plus de données via des applications mobiles.
- Combiner CNN + ViT pour une meilleure robustesse.
- Déploiement sur des stations météo basse consommation.
