# 💼 Pilotage des Charges Externes & Achats MP

Cas réel – PME industrielle (Sage 100 → Power BI)

# 🎯 Objectif du projet

Concevoir un modèle Power BI fiable permettant :

Le suivi des charges externes (6xx)

L’analyse détaillée des achats MP / approvisionnements (601 / 602 / 607)

La restitution cohérente avec les données comptables Sage 100

Le pilotage N vs N-1 / N-2, à date ou en année complète

L’objectif n’était pas uniquement de produire des visualisations, mais de :

🔎 Fiabiliser la donnée comptable avant toute analyse.

🧠 Contexte & enjeux métier

Projet mené dans le cadre de la modernisation du pilotage financier d’une PME industrielle.

Problématiques initiales

Difficulté à analyser les charges par fournisseur

Incohérences entre exports Excel et états Sage

Écritures comptables complexes mal interprétées

Rattachements fournisseurs instables

Confusion entre montants “à date” et montants “système complet”

🧩 Évolution majeure du modèle (Version 2)
🔹 1️⃣ Nouvelle logique de propagation fournisseur par pièce

Ancienne logique :

FillDown dépendant de l’ordre des lignes

Risque d’erreur de rattachement fournisseur

Nouvelle logique validée :

Groupement par EC_Piece

Identification explicite du compte 401

Extraction du fournisseur de référence par pièce

Propagation contrôlée via Nom_du_Tiers_Final

👉 Le fournisseur d’une pièce est désormais :

Unique

Traçable

Indépendant de l’ordre des lignes

Conforme à la logique Sage

🔹 2️⃣ Sécurisation des typages critiques

Un point bloquant majeur a été identifié :

Date_Analyse était passée en type texte

Rupture complète du contexte temporel

Toutes les mesures dépendantes de DIM_DATE retournaient BLANK

Correctifs :

Réapplication stricte des types en Power Query

Validation des relations Date

Contrôle du contexte fiscal

👉 Le modèle est désormais stable face aux évolutions.

🔹 3️⃣ Amélioration du Calculation Group (N / N-1 / N-2)

Nouvelle logique pour l’année fiscale en cours (N) :

Si slicer Mois filtré → calcul à la date sélectionnée

Si slicer Mois défiltré → prise en compte de la dernière date réellement présente dans les écritures

Suppression du simple cutoff basé sur TODAY()

Résultat :

Distinction claire entre :

Montant système complet

Montant YTD piloté

Cohérence parfaite entre :

Carte accueil

Courbe d’évolution

Matrice SIG

🧱 Architecture du modèle

Modèle en étoile structuré autour de :

FACT_F_ECRITUREC (écritures comptables)

DIM_DATE (année fiscale Avril → Mars)

DIM_COMPTES / PCG

Dimensions fournisseurs

Table technique SLICER_MOIS (pilotage temporel via TREATAS)

📊 Fonctionnalités clés

Analyse des charges externes par :

Fournisseur

Catégorie

Compte

Période fiscale

SIG dynamique multi-années fiscales

Comparaison N / N-1 / N-2

Pilotage YTD vs Année complète

Concordance comptable au centime près

Détection des pièces atypiques

🔎 Contrôles & gouvernance

Le modèle intègre :

Vérification de cohérence fournisseur par pièce

Audit des écritures 401

Tables de contrôle non calculatoires

Séparation claire entre :

Données de calcul

Données d’audit

Objectif :
👉 Garantir un outil exploitable par la DAF.

⚙️ Stack technique

Power BI

Power Query (M)

Regroupement par pièce

Propagation fournisseur robuste

Typage sécurisé

DAX

Calculation Groups

TREATAS

Logique fiscale dynamique

ODBC / SQL

Connexion directe à Sage 100

🚀 Résultats obtenus

✔ Concordance parfaite avec Sage (au centime)

✔ Rattachement fournisseur stabilisé

✔ Distinction claire système vs YTD

✔ SIG fiscal cohérent

✔ Modèle maintenable et explicable

✔ Suppression des dépendances à l’ordre des lignes

📁 Confidentialité

Les données sources et le modèle complet ne peuvent être publiés pour des raisons de confidentialité (RGPD & propriété entreprise).

Ce projet est présenté comme :

Cas réel de fiabilisation comptable et pilotage BI en environnement PME.

🧠 Ce que démontre ce projet

Compréhension approfondie des systèmes comptables Sage

Diagnostic et stabilisation d’un modèle instable

Maîtrise avancée Power Query & DAX

Implémentation de Calculation Groups complexes

Gestion des problématiques de contexte fiscal

Capacité à dialoguer avec une DAF

✅ En résumé

Un projet orienté :

Fiabilité comptable → Gouvernance des données → Pilotage financier réel

Au-delà d’un dashboard, il s’agit d’un modèle décisionnel robuste, aligné sur la réalité du système comptable.
Un cas concret démontrant :
- compréhension des systèmes comptables
- maîtrise de Power BI / Power Query
- capacité à dialoguer avec une DAF
- approche rigoureuse de la donnée financière
