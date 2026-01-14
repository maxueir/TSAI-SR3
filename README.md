# TSAI-SR3 : Super-Résolution d'Images via Raffinement Itératif

Ce dépôt contient le pipeline d'inférence pour le projet **TSAI-SR3**. Il s'appuie sur l'architecture **SR3 (Super-Resolution via Repeated Refinement)** pour effectuer une super-résolution d'images (Upscaling 8x) passant de **64x64** à **512x512** pixels.

Le projet est structuré autour d'un **Notebook Jupyter (Colab)** qui automatise l'installation de l'environnement, la récupération des poids pré-entraînés et la génération d'images haute fidélité.

## Description du Pipeline

Le fichier principal .ipynb orchestre les étapes suivantes :
1.  **Clonage de l'implémentation de référence** : Utilisation du dépôt GitHub de *Janspiry* (basé sur le papier de Google Research).
2.  **Configuration de l'environnement** : Installation des dépendances Python.
3.  **Téléchargement des modèles** : Récupération automatique des poids pré-entraînés via Google Drive.
4.  **Patch de Configuration** : Configuration automatique des fichiers .json pour charger correctement les checkpoints téléchargés.
5.  **Préparation des Données** : Conversion des images utilisateur au format LMDB requis par le modèle.
6.  **Inférence & Visualisation** : Génération des images haute résolution et comparaison visuelle (Originale vs Low-Res vs SR3).

## Prérequis

* **Environnement** : Google Colab ou machine locale avec GPU NVIDIA.
* **Accélération Matérielle** : GPU requis pour l'inférence (utilisation de cuda).
* **Python** : 3.x

## Guide d'Utilisation Rapide

### 1. Lancement du Notebook
Ouvrez le fichier SR3.ipynb dans Google Colab ou en local.

### 2. Initialisation
Exécutez les premières cellules pour :
* Cloner le dépôt.
* Installer les librairies.
* Télécharger la configuration du modèle.

### 3. Importation de vos Images
Lors de l'exécution de la cellule "Prepair Data", cliquez sur le bouton **"Browse"** qui devrait apparaître.
* **Format recommandé** : PNG ou JPG.
* **Résolution idéale** : 64x64 pixels (le modèle est optimisé pour cette entrée).

### 4. Lancement de la Super-Résolution
Le script va automatiquement :
* Convertir vos images.
* Lancer infer.py.
* Le processus peut prendre quelques minutes selon le GPU alloué.

### 5. Résultats
Les résultats sont sauvegardés en local.

Une cellule de visualisation à la fin du notebook permet d'afficher directement le comparatif :
* *Original High Res* (si disponible)
* *Resized Low Res* (l'entrée du modèle)
* *Infered* (le résultat SR3 généré)
