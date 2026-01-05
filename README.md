# Moteur de Solvabilité Bâle III & Stress Testing

## Vue d'ensemble
Ce projet est un moteur de simulation prudentielle conçu pour calculer le ratio de solvabilité CET1 (Common Equity Tier 1) conformément au règlement européen CRR (Capital Requirements Regulation) et aux normes de Bâle III.

Au-delà du simple calcul réglementaire, cet outil intègre un module de stress testing et une fonctionnalité d'analyse "Waterfall" pour décomposer les facteurs de variation de la solvabilité sous des scénarios économiques et climatiques adverses.

## Objectifs
* **Conformité Réglementaire :** Reconstitution d'un bilan prudentiel et calcul des RWA (Actifs Pondérés par les Risques) selon l'Approche Standard.
* **Sensibilité au Risque :** Modélisation de l'impact de la dégradation de la qualité de crédit et du risque opérationnel.
* **Stress Testing :** Évaluation de l'adéquation des fonds propres face à des chocs combinés (macroéconomiques + risque de transition climatique / actifs bruns).
* **Pilotage du Capital :** Visualisation de la mécanique de consommation des fonds propres via une analyse quantitative en cascade (Waterfall).

## Cadre Réglementaire & Méthodologie
Les calculs respectent les directives du règlement **CRR (Capital Requirements Regulation)** :

### 1. Fonds Propres (Numérateur)
* **Capital CET1 :** Capitaux propres comptables ajustés des déductions prudentielles.
* **Déductions :** Les actifs incorporels (Goodwill) sont déduits intégralement du CET1.

### 2. Actifs Pondérés (RWA - Dénominateur)
* **Risque de Crédit (Approche Standard) :**
    * Exposition Entreprises (Corporate) : Pondération à 100% (non noté).
    * Retail PME : Pondération à 75%.
    * Garanti par immobilier (Mortgage) : Pondération à 35%.
    * Souverain / Banque Centrale : Pondération à 0% (États membres de l'UE).
* **Risque Opérationnel :**
    * Calculé selon l'approche Indicateur de Base (**BIA - Basic Indicator Approach**) basé sur la moyenne du PNB des 3 dernières années.

### 3. Scénarios de Stress
Le modèle simule un scénario adverse combinant :
* **Choc Macroéconomique :** Hausse du coût du risque et dotations aux provisions supplémentaires.
* **Inflation des RWA :** Dégradation du portefeuille Corporate (proxy via augmentation des pondérations).
* **Risque Climatique :** Application d'un facteur pénalisant sur les "Actifs Bruns" (Risque de transition).

## Structure du Projet
Le dépôt est organisé comme suit :

* **1_Bilan_source :** Données comptables d'entrée (Actif/Passif).
* **2_Mapping :** Mapping des lignes comptables vers les classes d'exposition CRR.
* **3_RWA_Calculs :** Moteur de calcul pour les RWA Crédit et Opérationnel.
* **4_Ratio_CET1 :** Agrégation du ratio de solvabilité de base.
* **5_Stress_Test :** Définition des paramètres de choc et calcul post-stress.
* **6_Waterfall :** Analyse du pont expliquant le delta entre CET1 Initial et CET1 Post-Stress (Effet Capital vs Effet RWA).
* **7_Controles :** Contrôles de cohérence automatiques (intégrité, seuils).

## Résultats Clés (Simulation)
* **Ratio CET1 Initial :** 10.42%
* **Ratio CET1 Post-Stress :** 4.81%
* **Facteur Principal :** La dégradation est principalement pilotée par l'effet "Coût du Risque" (impact Numérateur) suivi par l'inflation des RWA Corporate (impact Dénominateur).

## Technologies
* **Excel :** Modélisation cœur, tables de sensibilité et visualisation Waterfall.
* **Python (Extension optionnelle) :** Utilisé pour le pré-traitement des données et la génération d'alertes automatiques pour les contrôles de conformité.

## Auteur
**Théo Paradis**
Master Analyse des Risques Bancaires | Université de Montpellier
Recherche
