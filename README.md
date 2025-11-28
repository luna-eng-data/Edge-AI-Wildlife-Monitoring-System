#  Eco-Sentinel : Filtrage Intelligent pour la Surveillance Faunique

![Python](https://img.shields.io/badge/Python-3.10-blue) ![TensorFlow](https://img.shields.io/badge/Framework-TensorFlow-orange) ![GreenAI](https://img.shields.io/badge/Focus-Green_AI-green)

> **Projet DIA6 - Green AI & Computer Vision**
> Système de filtrage embarqué (Edge AI) pour optimiser la surveillance des parcs naturels et réduire l'empreinte carbone numérique.

##  Contexte et Problématique
Les parcs naturels africains utilisent des caméras pièges connectées par satellite pour lutter contre le braconnage et les conflits homme-faune. Cependant, cette technologie fait face à un mur technologique et écologique :
1.  **Coût Écologique & Financier :** Transmettre des milliers d'images par satellite (souvent "vides" ou sans intérêt) consomme énormément d'énergie et de bande passante coûteuse.
2.  **Latence :** Les rangers sont noyés sous les données brutes, retardant l'intervention en cas d'intrusion humaine.

##  Notre Solution : Le Filtrage "Edge AI"
Au lieu de déporter l'analyse dans le cloud (approche classique), nous proposons un modèle d'Intelligence Artificielle léger capable de tourner directement sur la caméra (**Edge Computing**).

Le système agit comme un filtre intelligent :
-   **Faune (Animaux) :** L'image est stockée localement pour les statistiques (0 transmission = 0g CO2).
-   **Humain (Danger) :** L'image déclenche une **alerte prioritaire** et est transmise immédiatement.

##  Architecture Technique & Choix Green AI

### Pourquoi avons-nous abandonné YOLO ?
Initialement partis sur une solution de détection d'objets (YOLO), nous avons pivoté vers une architecture de **Classification (MobileNetV2)** pour maximiser l'impact Green AI :
*   **Complexité réduite :** MobileNetV2 est spécifiquement conçu pour les processeurs mobiles.
*   **Consommation énergétique :** L'inférence est plus rapide et demande moins de calculs que la génération de bounding boxes.
*   **Pertinence :** Pour une alerte de sécurité, savoir *où* est l'humain au pixel près est moins crucial que de savoir *s'il y a* un humain.

### Stack Technique
*   **Modèle :** MobileNetV2 (Transfer Learning sur ImageNet).
*   **Framework :** TensorFlow / Keras.
*   **Input :** Images redimensionnées en 224x224 (Standardisation low-res).

##  Structure du Dataset
Nous avons agrégé et nettoyé plusieurs sources de données (Kaggle African Wildlife & Human Detection) pour constituer un dataset équilibré pour la classification binaire :

```text
dataset_classification/
├──  animaux/  (1500+ images : Buffles, Éléphants, Rhinos, Zèbres)
└──  humains/  (500+ images : Détection de personnes en milieu varié)
