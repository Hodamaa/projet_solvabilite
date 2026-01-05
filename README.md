# Moteur de Solvabilité Bâle III & Stress Testing

## Vue d'ensemble
Ce projet est un moteur de simulation prudentielle conçu pour calculer le ratio de solvabilité CET1 (Common Equity Tier 1) conformément au règlement européen CRR (Capital Requirements Regulation).

Au-delà du simple calcul réglementaire, cet outil intègre un module de stress testing pour simuler des scénarios de crise.

## Objectifs
* **Conformité Réglementaire :** Reconstitution d'un bilan prudentiel et calcul des RWA (Actifs Pondérés par les Risques).
* **Sensibilité au Risque :** Modélisation de l'impact de la dégradation de la qualité de crédit.
* **Stress Testing :** **L'objectif central est de tester la résilience de la banque**, c'est-à-dire sa capacité à absorber des chocs majeurs (économiques ou climatiques) tout en conservant une solvabilité supérieure aux exigences réglementaires.
* **Pilotage du Capital :** Visualisation de la consommation des fonds propres via une analyse "Waterfall".

## Cadre Réglementaire & Méthodologie
Les calculs respectent les directives du règlement **CRR** :

### 1. Fonds Propres (Numérateur)
* **Capital CET1 :** Capitaux propres comptables ajustés.
* **Déductions :** Les actifs incorporels (Goodwill) sont déduits intégralement.

### 2. Actifs Pondérés (RWA - Dénominateur)
* **Risque de Crédit (Approche Standard) :**
    * Exposition Entreprises (Corporate) : Pondération à 100%.
    * Retail PME : Pondération à 75%.
    * Garanti par immobilier : Pondération à 35%.
    * Souverain / Banque Centrale : Pondération à 0% (États membres de l'UE).
* **Risque Opérationnel :**
    * Calcul fondé sur la moyenne du Produit Net Bancaire (PNB) des 3 dernières années, pondérée par un facteur réglementaire.

### 3. Scénarios de Stress
Le modèle simule un scénario adverse combinant :
* **Choc Macroéconomique :** Hausse du coût du risque et dotations aux provisions.
* **Inflation des RWA :** Dégradation de la notation du portefeuille Corporate.
* **Risque Climatique :** Pénalité sur les "Actifs Bruns" (Risque de transition).

## Structure du Projet
Le dépôt est organisé comme suit :

* **1_Bilan_source :** Données comptables d'entrée.
* **2_Mapping :** Mapping des lignes comptables vers les classes d'exposition CRR.
* **3_RWA_Calculs :** Moteur de calcul pour les RWA Crédit et Opérationnel.
* **4_Ratio_CET1 :** Agrégation du ratio de solvabilité de base.
* **5_Stress_Test :** Définition des paramètres de choc et calcul post-stress.
* **6_Waterfall :** Analyse des écarts (Effet Capital vs Effet RWA).
* **7_Controles :** Vérifications de cohérence des données.

## Résultats Clés (Simulation)
* **Ratio CET1 Initial :** 10.42%
* **Ratio CET1 Post-Stress :** 4.81%
* **Conclusion :** Le stress test met en évidence la forte sensibilité du ratio aux chocs sur le coût du risque.

## Technologies
* **Excel :** Modélisation complète, tables de sensibilité et visualisation graphique.

## Auteur
**Théo Paradis**
Master Analyse des Risques Bancaires | Université de Montpellier
Recherche un stage en Solvabilité / Pilotage des Risques (Mai 2026).
