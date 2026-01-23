# 💼 Suivi des Charges Externes & Achats MP – PME Industrielle

## 🎯 Objectif du projet

Mettre en place un outil de pilotage financier fiable sous **Power BI** permettant :
- le suivi des **charges externes** (comptes 6xx)
- l’analyse détaillée des **achats de matières premières, approvisionnements et marchandises** (601 / 602 / 607)
- une restitution cohérente avec les **données comptables Sage 100**

L’objectif principal est de garantir une **lecture fidèle des montants comptables**, tout en apportant une capacité d’analyse avancée par catégorie, fournisseur et période.

---

## 🧠 Contexte & enjeux métier

Ce projet a été réalisé dans le cadre de la modernisation du pilotage financier d’une **PME industrielle**.

### Problématiques initiales :
- Difficulté à analyser les charges par fournisseur de façon fiable
- Écarts inexpliqués entre les exports Excel et les états Sage
- Manque de traçabilité sur certaines écritures comptables complexes
- Besoin de distinguer les **pièces comptables fiables** des cas atypiques

Le projet ne se limite pas à la visualisation :
👉 il vise avant tout la **fiabilisation de la donnée comptable**.

---

## 🧩 Approche retenue

### 🔹 Respect strict de la logique Sage

Le modèle repose sur la logique suivante, propre à Sage :
EC PIECE → comptes de charges (6xx) → compte fournisseur (401)

Le rattachement fournisseur est effectué **exclusivement via les écritures 401**, considérées comme la source de vérité.

---

### 🔹 Construction d’une dimension EC PIECE centralisée

Une **dimension EC PIECE** a été créée afin de :
- regrouper toutes les écritures d’une même pièce comptable
- identifier le fournisseur de référence
- calculer une catégorie d’achat dominante par pièce
- assurer la cohérence entre charges et fournisseur

---

### 🔹 Mise en place de contrôles de fiabilité

Des tables de contrôle dédiées ont été intégrées au modèle afin de :
- détecter les pièces multi-fournisseurs
- identifier les pièces instables ou atypiques
- expliquer les exclusions éventuelles des analyses

Ces tables ne servent **pas au calcul**, mais à :
- auditer les données
- sécuriser les analyses
- dialoguer avec la DAF / la comptabilité

---

## 📊 Fonctionnalités clés

- Suivi des **charges externes** par période, catégorie et compte
- Analyse détaillée des **achats MP (601 / 602 / 607)** par fournisseur
- Comparaison N vs N-1 (montants et variations)
- Fiabilité des montants **au centime près** vs Sage et fichiers sources
- Identification explicite des pièces comptables non fiables
- Séparation claire entre calculs et contrôles

---

## ⚙️ Stack technique

- **Power BI**
- **Power Query (M)**  
  - structuration comptable
  - logique EC PIECE
  - contrôles de stabilité
- **DAX**  
  - calculs de variations
  - agrégations multi-niveaux
- **ODBC / SQL**  
  - connexion directe à Sage 100

---

## 🚀 Résultats obtenus

- ✔ Concordance parfaite avec les données Sage (au centime)
- ✔ Fiabilité renforcée du suivi des achats MP
- ✔ Meilleure compréhension des écarts historiques
- ✔ Outil exploitable pour le pilotage financier réel
- ✔ Modèle robuste, explicable et maintenable

---

## 📁 Confidentialité

Les données sources, fichiers Power BI et structures internes ne peuvent être publiés pour des raisons de confidentialité (RGPD & propriété de l’entreprise).

👉 Ce projet est présenté comme **cas réel de mise en œuvre BI en environnement PME**, avec une forte exigence métier et comptable.

---

## ✅ En résumé

Un projet Power BI orienté **fiabilité comptable et pilotage financier**, allant au-delà de la visualisation pour adresser des enjeux réels de gouvernance de la donnée.

Un cas concret démontrant :
- compréhension des systèmes comptables
- maîtrise de Power BI / Power Query
- capacité à dialoguer avec une DAF
- approche rigoureuse de la donnée financière
