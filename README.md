# Projet ETL sur les infections COVID-19

## Proposition de projet

Basé sur les données compilées par l’Université Johns Hopkins, je souhaite explorer ''' Insérer les raisons ici '''.
Cela sera réalisé en extrayant les données CSV et en les migrant vers une base de données PostgreSQL.

## Description du projet

J’ai trouvé des données provenant de `data.data.org` qui ont été compilées par l’Université Johns Hopkins. J’ai filtré les données pour le mois de mars 2020 et évalué le nombre de cas en fonction des décès, des guérisons et des cas confirmés.

## Recherche des données

Toutes les données utilisées proviennent de
`https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases`,
où elles sont compilées par le Centre pour la science et l’ingénierie des systèmes de l’Université Johns Hopkins (JHU CSSE) à partir de diverses sources, notamment l’Organisation mondiale de la santé, le Département de la santé de Hong Kong, le Centre européen de prévention et de contrôle des maladies, etc.
Ces données sont constamment mises à jour, c’est pourquoi nous limitons notre étude au mois de mars.

## Nettoyage et analyse des données

### *Étapes de transformation*

Les étapes de transformation nécessaires pour rendre les données lisibles, présentables et faciles à interroger par la suite ont été les suivantes :

* Développement d’une fonction de nettoyage en Python permettant de sélectionner les données du mois de mars 2020. Cette fonction a été appliquée à tous les ensembles de données.
* Toutes les dates présentes dans les ensembles de données ont été traitées comme des valeurs à l’aide de la fonction `pd.melt` de Pandas.
* Mise en place d’une méthode pour calculer l’augmentation quotidienne pour chaque table. Cette valeur a été convertie de float en entier.

### *Étapes de chargement*

* Établissement d’une connexion à un serveur PostgreSQL local sur notre ordinateur afin de stocker les données.
* Création d’un schéma permettant de générer les tables, vérifié via `engine.table_names()`.
* Insertion des DataFrames Pandas dans le serveur PostgreSQL local afin de pouvoir récupérer et interroger les données dans notre notebook Jupyter.

### *Analyse / Requêtes SQL*

Dans cette partie, je souhaite déterminer :

* Les 5 pays avec le plus / le moins de cas confirmés
* Les 5 pays avec le plus / le moins de décès
* Les 5 pays avec le plus / le moins de guérisons
* La date du mois de mars avec le plus de cas confirmés / décès / guérisons

