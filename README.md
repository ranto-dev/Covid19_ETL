# Projet ETL - Analyse des infections COVID-19

## Description

Ce projet met en œuvre un pipeline ETL (Extract, Transform, Load) afin d’analyser l’évolution des infections liées au COVID-19 durant le mois de mars 2020.

L’objectif principal est de :

- [x] Collecter des données fiables
- [x] Les transformer pour les rendre exploitables
- [x] Les stocker dans une base de données relationnelle
- [x] Effectuer des analyses à l’aide de requêtes SQL

## Stack technique

- **Python** — traitement et orchestration ETL
- **NumPy** — manipulation numérique
- **Pandas** — transformation et nettoyage des données
- **Matplotlib** — visualisation
- **SQLAlchemy** — interaction avec la base de données
- **PostgreSQL** — stockage des données

## Source des données

Les données proviennent de la plateforme officielle :

- 🔗 [https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases](https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases)

Elles sont compilées par le **Centre for Systems Science and Engineering (JHU CSSE)** de l’Université Johns Hopkins, à partir de plusieurs sources fiables :

- Organisation mondiale de la santé (OMS)
- Centres de contrôle sanitaire internationaux
- Autorités de santé locales

⚠️ Les données étant continuellement mises à jour, cette étude est volontairement limitée au **mois de mars 2020** pour garantir la cohérence de l’analyse.

## Processus ETL

### 1. Extraction

- Récupération des datasets COVID-19 depuis la source
- Chargement des fichiers dans l’environnement Python (Pandas DataFrames)

### 2. Transformation

Les données brutes ont subi plusieurs étapes de transformation :

- **Filtrage temporel**: Sélection des données correspondant uniquement à **mars 2020**

- **Normalisation des données** : Transformation des colonnes de dates en lignes avec `pd.melt()`

- **Calcul des indicateurs**
  - Calcul de l’augmentation quotidienne des cas
  - Conversion des valeurs en entiers pour améliorer la lisibilité

- **Nettoyage des données**
  - Suppression des valeurs inutiles ou incohérentes
  - Harmonisation des formats

### 3. Chargement

- Connexion à une base de données **PostgreSQL locale** via SQLAlchemy
- Création d’un schéma relationnel adapté
- Vérification des tables avec `engine.table_names()`

- Insertion des données transformées depuis Pandas vers PostgreSQL

## Modélisation des données

Les données sont organisées sous forme de tables représentant :

- Cas confirmés
- Décès
- Guérisons

Chaque table contient :

- Pays
- Date
- Nombre de cas
- Augmentation quotidienne

## Analyse des données

Les analyses ont été réalisées à l’aide de requêtes SQL afin de répondre aux questions suivantes :

### Par pays

- Top 5 des pays avec le plus de cas confirmés
- Top 5 des pays avec le moins de cas confirmés
- Top 5 des pays avec le plus de décès
- Top 5 des pays avec le moins de décès
- Top 5 des pays avec le plus de guérisons
- Top 5 des pays avec le moins de guérisons

### Par date

- Jour avec le plus de cas confirmés
- Jour avec le plus de décès
- Jour avec le plus de guérisons

## Résultats attendus

- [x] Base de données propre et structurée
- [x] Données exploitables via SQL
- [x] Indicateurs clairs sur l’évolution du COVID-19 en mars 2020
