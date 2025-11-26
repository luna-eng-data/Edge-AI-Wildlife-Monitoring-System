# Wildlife Human Conflict Detection using YOLO

Projet de Machine Learning - DIA6 - Detection automatique des conflits homme-faune

## Contexte

Ce projet vise a automatiser la detection de zones a risque de conflit entre humains et animaux sauvages en Afrique, en utilisant le deep learning sur des images de cameras pieges.

## Objectifs

- Detecter automatiquement animaux (buffalo, elephant, rhino, zebra) et humains
- Identifier les zones geographiques de chevauchement
- Fournir des cartes de densite pour optimiser les patrouilles

## Dataset

- **Total** : 2063 images annotees
- **Classes** : 5 (buffalo, elephant, rhinocéros, zebra, person)
- **Format** : YOLO
- **Split** : 
  - Train : 1650 images (80%)
  - Validation : 205 images (10%)
  - Test : 208 images (10%)
- **Validation reelle** : 40 images mixtes (animaux + humains)

## Methodologie

- **Modele** : YOLOv8 nano
- **Approche** : Transfer learning
- **Framework** : Ultralytics (PyTorch)
- **Infrastructure** : Google Colab (GPU T4)

## Structure du projet
```
wildlife-conflict-detection/
├── README.md
├── LICENSE
├── .gitignore
├── requirements.txt
├── notebooks/
│   └── 02_train_model.ipynb
├── data/
│   └── data.yaml
└── results/
    ├── model/
    ├── plots/
    └── maps/
```

## Installation
```bash
pip install -r requirements.txt
```

## Usage

### Sur Google Colab

1. Ouvrir le notebook `notebooks/02_train_model.ipynb`
2. Executer les cellules sequentiellement
3. Les resultats sont sauvegardes automatiquement

## Resultats

Les resultats seront ajouter après l'entrainement du modèle.

## Articles de reference

1. Multi-perspective monitoring of wildlife and human activities from camera traps and drones with deep learning models (arXiv:2508.15629)
2. A completer

## Equipe

Projet realisé par l'equipe DIA6 - Novembre 2025

## Licence

MIT License
