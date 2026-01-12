# Retail-Performance-Dashboard

![Aperçu du Dashboard](https://github.com/ton-pseudo/ton-repo/blob/main/Screenshots/Home_Store.png) 
Figure 1 : Page *Vue Globale* présentant la synthèse des ventes et l'impact des facteurs environnementaux.
***

## 📜 Contexte
Dans le cadre d'une analyse pour une enseigne de grande distribution, l'enjeu est de piloter la performance commerciale de *45 magasins*. Ce projet transforme des données brutes de ventes, de météo et de contexte économique en insights stratégiques pour optimiser la prise de décision.
***

## 🎯 Objectifs du Projet
L'objectif principal est de fournir une vision claire au PCA sur les leviers de croissance :

* *Analyse de la Saisonnalité* : Identifier l'impact réel des semaines de congés (*IsHoliday*) sur le chiffre d'affaires.
* *Évaluation de l'Élasticité* : Mesurer la sensibilité des clients face à la variation du *Prix du Carburant*.
* *Segmentation Climatique* : Corréler les performances selon les *Tranches de Température* (Froid, Tempéré, Chaud).
* *Ranking Dynamique* : Identifier les *Top Performers* du réseau grâce à un système de classement automatisé.

***

## 📂 Données
Le projet utilise le dataset historique de Walmart, croisant plusieurs dimensions :

* *Sales* : Données de ventes hebdomadaires par magasin.
* *Features* : Facteurs externes (Météo, Fuel Price, CPI, Unemployment).
* *Stores* : Métadonnées sur la taille et le type des magasins (A, B, C).
* *Période* : Analyse couvrant les années 2010 à 2012.

***

## 🛠️ Stack Technique
* *Microsoft Power BI* : Outil principal de visualisation et de reporting.
* *Power Query* : Nettoyage (ETL) et création de clés composites pour lier les facteurs externes aux ventes.
* *DAX (Data Analysis Expressions)* : Création de mesures complexes pour le ranking et la segmentation.

***
## ⚙️ Méthodologie & Formules DAX Clés
Le projet a nécessité une modélisation précise pour isoler les variables influentes :

### 1. Classement Dynamique des Magasins
```dax
top des magasinis = 
RANKX(
    ALL(Sales[Store]), 
    [Chiffre d'affaire Hebdo], 
    , 
    DESC, 
    Dense
)

