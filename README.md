# 💼 Suivi des Charges Externes (CE) – Cas réel en PME industrielle

## 🎯 Objectif du projet
Ce projet Power BI a été conçu pour permettre à la direction financière de suivre et d’analyser les **charges externes** (CE) issues de la comptabilité SAGE 100, de façon dynamique et automatisée.  
L’objectif : disposer d’une **vision claire, fiable et catégorisée** des dépenses pour mieux piloter la rentabilité et identifier les postes à optimiser.

---

## 🧠 Contexte métier
L’entreprise faisait face à une difficulté classique : les charges externes étaient dispersées dans le plan comptable, rendant toute analyse manuelle fastidieuse.  
L’idée a été de créer un **système d’analyse automatisé** qui :
- Regroupe les comptes fournisseurs par **catégories métiers** (Énergie, Intérim, Fournitures, Maintenance, etc.)
- Met en lien les journaux comptables, la nature des comptes et les tiers
- Fournit à la DAF une lecture synthétique et exploitable en quelques clics

---

## 📊 Fonctionnalités du dashboard

- Classification automatique des écritures via des **règles métier sur les numéros de comptes**
- Regroupement des dépenses par **catégorie de charges**
- Visualisation des **évolutions temporelles** et comparaison entre exercices
- Identification des **principaux fournisseurs** par type de dépense
- Indicateurs clés : total CE, % par catégorie, top 5 fournisseurs, variation annuelle
- Filtrage dynamique (année fiscale, fournisseur, catégorie, journal, nature du compte)

---

## ⚙️ Outils & Technologies utilisés

- **Power BI** : visualisation et mesures DAX  
- **Power Query (M)** : transformation, fusion, catégorisation des écritures comptables  
- **SQL / ODBC (SAGE 100)** : extraction des données ERP  
- **DIM_DATE** : gestion temporelle sur base d’année fiscale  
- **Plan de comptes (PCG)** : intégration et enrichissement via jointures

---

## 🧩 Structure technique

- Modèle en étoile :  
  - **Fait central** → `FACT_F_ECRITUREC`  
  - **Dimensions** → `DIM_DATE`, `DIM_COMPTE_CLIENT`, `DIM_COMPTE_FOURNISSEUR`, `PCG_ERVENT`, `DIM_NUMERO_COMPTE_COMPTABLE`  
- Colonnes calculées pour :  
  - Identifier la nature du compte (charges / produits)  
  - Classifier automatiquement les CE  
  - Suivre la période fiscale et les retards de paiement fournisseurs  

---

## 🚀 Résultats & impact

💡 Lecture simplifiée et cohérente des dépenses de l’entreprise  
📈 Vision immédiate des postes de charges majeurs  
⚙️ Mise à jour automatisée à chaque import comptable  
🧮 Gain de temps significatif dans les reportings mensuels DAF  
🎯 Base solide pour de futures analyses financières (SIG, budgets prévisionnels…)

---

## 📁 Confidentialité
Les données issues de SAGE 100 étant confidentielles, le fichier Power BI n’est pas publié.  
Le modèle et les scripts Power Query peuvent néanmoins être présentés à titre d’exemple pour illustrer le travail technique et analytique réalisé.

---

## ✅ En résumé
Un projet de **Business Intelligence orienté finance**, combinant :
- Nettoyage et structuration des écritures comptables  
- Catégorisation automatique des charges externes  
- Visualisation claire et interactive dans Power BI  

Ce travail renforce la capacité de l’entreprise à **piloter ses dépenses et optimiser ses coûts** grâce à une approche data-driven.
