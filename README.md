# 💼 Suivi des Charges Externes (CE) & Lecture SIG – Cas réel (Power BI)
## 🎯 Objectif du projet

Mettre à disposition de la direction une vision fiable, catégorisée et actionnable des charges externes (compta SAGE) et une lecture SIG simplifiée pour piloter les coûts, suivre les écarts et éclairer les décisions (budget, renégociation fournisseurs, priorisation des postes).

## 🧠 Contexte métier

Les écritures comptables issues de l’ERP/Compta sont hétérogènes (journaux, libellés, lettrage, sens débit/crédit) et peu comparables en l’état. L’enjeu a été de :

Nettoyer et structurer les données SAGE,

Catégoriser les charges externes de façon homogène (ASSURANCE, CARBURANT, HONORAIRE, etc.),

Construire une lecture SIG pragmatique et progressive, exploitable dans Power BI.

## ⚙️ Outils & Architecture

Power BI Desktop (modèle, visuels, DAX)

Power Query (M) : normalisation, enrichissements, catégorisation CE, clés techniques

ODBC vers SAGE Compta (tables F_ECRITUREC, référentiels)

Tables de référence : PCG_ERVENT, DIM_DATE, DIM_NUMERO_COMPTE_COMPTABLE, listes d’exclusion/clients/fournisseurs

## 🧩 Modèle de données (simplifié)

FACT_F_ECRITUREC (écritures comptables normalisées)

DIM_DATE (civil/fiscal, FY start/end, clés Annee_Fiscale_*, Annee_Mois_Fiscale_Key)

DIM_NUMERO_COMPTE_COMPTABLE (clé technique et mapping CE)

Référentiels métiers : clients/fournisseurs, tiers à exclure, PCG (nature de compte), etc.

## 🔧 Étapes clés Power Query (extrait de la logique)

Normalisation comptable

Mapping des journaux → Description_Journal (ACHAT, VENTE, BANQUE, etc.)

Sens débit/crédit transformé en Montant_Facture (débits négativés)

Détermination Compte Client/Fournisseur (préfixes 411* / 401*)

Statut de lettrage EC Lettrée / Non Lettrée

Calendrier fiscal & clés techniques

Date_Analyse (période comptable sinon date EC)

Libellés/numéros fiscaux : Annee_Fiscale_Libelle, Annee_Fiscale_Num, Mois_Fiscal, Annee_Mois_Fiscale_Key

PieceKey = EC_Piece_Clean | Annee_Fiscale_Debut_Num (agrégation multi-lignes d’une même pièce)

Catégorisation business

Secteurs (ATELIER / NEGOCE / POSE / TRANSPORT) via mapping précis des comptes 701/707/706/708

Charges externes = repérage par préfixes (606*, 61*, 62*)

Catégories CE robustes (ASSURANCE, CARBURANT, DÉPLACEMENT, DIVERS, ÉNERGIE, ENTRETIEN, FOURNITURE, HONORAIRE, INTÉRIM, LOC IMMOBILIÈRES, LOC MOBILIÈRES, MAINTENANCE, TÉLÉCOM & IT, TRANSPORT…) à partir d’une liste de comptes finement curée

Jointure PCG pour Nature_Compte (CHARGE, PRODUIT, BANQUE, etc.)

Clients/Fournisseurs & Lettrage

Jointures aux dimensions clients et fournisseurs

Date d’échéance calculée (enrichie depuis les conditions de règlement)

Jours de retard pour les 411 non lettrés (vue créances)

Ces étapes rendent les CE comparables et exploitables en analyse (par période fiscale, par catégorie, par fournisseur, par secteur, par pièce…).

## 📊 Lecture SIG (version opérationnelle & évolutive)

But : offrir une lecture analytique des comptes pour expliquer la performance, avec les briques disponibles aujourd’hui.
Cette première version se concentre sur Chiffre d’Affaires / Charges externes et SIG simplifié, et peut être enrichie (personnel 64*, impôts 63*, dotations 68*…) selon la portée souhaitée.

Niveaux retenus (exemples adaptés à tes mappings) :

Chiffre d’affaires

Produits d’exploitation issus des comptes 701 / 706 / 707 / 708 (via ton mapping Secteurs & Description_Compte_Produit).

Achats consommés / Sous-traitance (si disponibles dans la source)

À isoler/affiner via comptes matières & sous-traitance.

Charges externes

Somme des catégories CE mappées (606*, 61*, 62*) → ventilées par categorie_CE.

Marge commerciale / Marge brute (selon disponibilité des achats)

Marge = CA – Achats consommés (si Achats bien isolés), sinon Marge brute = CA – CE* (version pédagogique).

Valeur Ajoutée (VA)

VA = Marge – Charges externes (ou VA = CA – Achats – CE si Achats isolés).

EBE (version simplifiée)

EBE ≈ VA – Charges de personnel – Impôts & taxes (à enrichir quand 64*/63* seront intégrés).

Remarques :

Le niveau de granularité (par catégorie CE, fournisseur, secteur, mois fiscal) explique où part la valeur.

La version finale du SIG dépendra du périmètre de comptes intégré. Ici, on part d’un socle CE robuste et on ouvre la voie aux autres classes du PCG.

## 📈 KPIs & Questions métier adressées

Montant des CE par catégorie, fournisseur, secteur, période fiscale

Poids des 5 principales catégories (effet Pareto des coûts)

Top fournisseurs (montant, tendance, FY vs FY-1)

Évolution mensuelle des CE (lissage, saisonnalité)

Créances (via jours de retard / 411 non lettrés) — en bonus si affichées

## 🧩 Fonctionnalités du dashboard

Slicer fiscal : Année fiscale, Mois fiscal, Trimestre fiscal

Vue “Catégories CE” : treemap / bar chart + table détaillée

Vue “Fournisseurs” : ranking, delta FY, drill-through pièce

Vue “Secteurs” (ATELIER / NÉGOCE / POSE / TRANSPORT)

Section SIG : paliers en cartes KPI + graphiques (CA, CE, VA, EBE simplifié)

Contrôles qualité : EC lettrées/non lettrées, exclusions de tiers, cohérence des montants

## 🚀 Résultats & impact

Fiabilisation de l’analyse des CE via un cadre commun (catégories stables)

Visibilité immédiate sur les postes coûteux et leviers d’optimisation

Dialogue facilité avec les fournisseurs (volumes, tendances, renégociation)

Base SIG prête pour monter en puissance (personnel, taxes, dotations…)

## 🔒 Confidentialité

Projet réalisé sur données réelles – publications RGPD-friendly : le PBIX et les fichiers sources ne sont pas partagés.
Le README documente la méthode et les résultats attendus sans exposer d’informations sensibles.
