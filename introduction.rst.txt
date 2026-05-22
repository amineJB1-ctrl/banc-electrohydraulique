Introduction générale
=====================

Contexte et motivation
-----------------------

Les systèmes électro-hydrauliques sont très importants dans l'industrie moderne. On les utilise dans les presses industrielles, les machines de production, les engins de chantier, les systèmes de manutention et les équipements de contrôle de précision. Il est donc essentiel pour tout technicien ou ingénieur en automatisme industriel de bien comprendre ces systèmes.

Ce travail a pour but de proposer une documentation pédagogique complète et facile à comprendre sur le banc didactique électro-hydraulique TDS DIDACTIC. Ce banc utilise à la fois les technologies hydraulique et électrique pour créer des mouvements de précision commandés par un automate programmable industriel, l'API DELTA DVP.

.. figure:: images/banc_schema.png
   :align: center
   :width: 70%
   :alt: Banc électro-hydraulique didactique TDS DIDACTIC

   *Fig. 1 — Banc électro-hydraulique didactique TDS DIDACTIC (source : fiche technique TDS DIDACTIC)*

Présentation du banc didactique
--------------------------------

Le banc didactique électro-hydraulique TDS DIDACTIC est une plateforme modulaire
simple face, montée sur châssis métallique mobile. Il est conçu pour l'apprentissage,
l'expérimentation et la maintenance des systèmes électro-hydrauliques industriels.

Ses principales caractéristiques techniques sont les suivantes :

.. list-table:: Caractéristiques techniques principales du banc TDS DIDACTIC
   :header-rows: 1
   :widths: 35 65

   * - Paramètre
     - Valeur / Description
   * - Marque
     - TDS DIDACTIC (Technology Development Systems)
   * - Structure
     - Banc mobile simple face, châssis métallique robuste
   * - Grille d'exercice
     - Profilée 50 × 50 mm — fixation rapide de tous les composants
   * - Automate programmable
     - DELTA DVP 
   * - Entrées numériques
     - entrées numériques capteurs
   * - Sorties numériques
     - sorties numériques pour électrovannes (relais)
   * - Entrées/sorties analogiques
     - entrées + sorties analogiques 0–10 V
   * - Communication
     - Port USB / Ethernet — connexion directe PC ↔ API
   * - Distributeurs hydrauliques
     - distributeurs 4/2 voies + distributeurs 4/3 voies
   * - Capteurs
     - détecteurs inductifs de proximité, capteurs magnétiques à LED, pressostat électrique
   * - Sécurité électrique
     - Modules réseau CA 230 V / 16 A, disjoncteur + différentiel 30 mA
   * - Raccordements hydrauliques
     - Raccords rapides anti-fuite

Le banc permet aux apprenants d'étudier les principes et composants des circuits
électro-hydrauliques, de réaliser leur câblage, de les mettre en service, et d'exécuter
des séquences automatisées via l'automate programmable.

Objectifs pédagogiques
-----------------------

À l'issue de ce cours, l'étudiant sera capable de :

1. **Identifier** les composants d'un circuit électro-hydraulique (pompe, distributeurs,
   vérins, capteurs, organes de régulation et de sécurité) et d'en expliquer le rôle.

2. **Lire et interpréter** un schéma hydraulique normalisé (norme ISO 1219) et un
   schéma électrique de commande associé.

3. **Câbler** un circuit électro-hydraulique simple sur le banc TDS DIDACTIC en
   respectant les règles de sécurité.

4. **Régler** les organes de régulation (limiteur de pression, régulateur de débit) et
   vérifier leur effet sur le comportement du système.

5. **Programmer** un cycle automatique sur l'API DELTA DVP en langage Ladder ou
   GRAFCET pour commander le mouvement d'un ou plusieurs vérins.

6. **Diagnostiquer** une anomalie de fonctionnement (fuite, blocage, défaut capteur)
   et proposer une action corrective.

.. note::

   Ces objectifs sont progressivement abordés tout au long du cours et mis en pratique
   dans les travaux pratiques associés.

Prérequis
----------

Pour suivre ce cours dans de bonnes conditions, l'étudiant doit avoir des notions de
base dans les domaines suivants :

- **Mécanique** : notions de force, pression, débit, puissance
- **Électricité** : loi d'Ohm, circuits série/parallèle, notion de relais et contacteur
- **Automatisme** : notions de base sur les capteurs TOR (tout ou rien) et les actionneurs

Aucune connaissance préalable en hydraulique n'est requise — ce cours part de zéro.

Organisation du cours
----------------------

Le document est structuré de manière progressive, en suivant la logique de la chaîne
d'énergie du système électro-hydraulique, du générateur d'énergie jusqu'à l'élément final :

.. list-table:: Modules du cours
   :header-rows: 1
   :widths: 10 35 55

   * - N°
     - Module
     - Contenu principal
   * - 1
     - Vue globale du système
     - Architecture générale, chaîne d'énergie, vue d'ensemble des composants
   * - 2
     - Chaîne d'énergie
     - Moteur électrique, pompe hydraulique à engrenages, réservoir d'huile
   * - 3
     - Actionneurs hydrauliques
     - Vérin double effet, vérin simple effet à rappel par ressort
   * - 4
     - Distributeurs hydrauliques
     - Distributeurs 4/2 et 4/3, électrodistributeurs, symbolisme ISO 1219
   * - 5
     - Organes de régulation
     - Limiteur de pression, régulateur de débit, diviseur de débit
   * - 6
     - Organes de sécurité
     - Soupape de sécurité, filtre, clapet anti-retour piloté
   * - 7
     - Organes de retenue
     - Clapet anti-retour simple, clapet à bille
   * - 8
     - Capteurs et instrumentation
     - Capteurs de fin de course, inductifs, magnétiques, pressostat, manomètre
   * - 9
     - Automatisation et commande
     - API DELTA DVP, GRAFCET, programmation Ladder, tableau E/S
   * - 10
     - Connexions et accessoires
     - Raccords rapides, flexibles, joints, règles de montage

Chaque module est construit selon la même structure pédagogique :
**Description → Rôle → Principe de fonctionnement → Symbole normalisé (ISO 1219) →
Schéma de fonctionnement → Connexions → Caractéristiques techniques**.

.. warning::

   **Sécurité — règles générales**

   Avant toute manipulation sur le banc, l'apprenant doit :

   - Porter les équipements de protection individuelle (EPI) : lunettes de protection,
     gants résistants aux huiles.
   - Vérifier que la pression maximale du banc (1,6 MPa) n'est pas dépassée.
   - Ne jamais desserrer un raccord hydraulique sous pression.
   - Signaler immédiatement toute fuite d'huile à l'enseignant responsable.
   - Couper l'alimentation électrique avant toute intervention sur le câblage.

Documentation et outils utilisés
----------------------------------

Ce cours est présenté sous forme d'un site web pédagogique interactif généré avec
**Sphinx**, permettant une navigation intuitive, une mise à jour facile du contenu et
une consultation en ligne ou hors ligne.

Les outils logiciels utilisés dans les travaux pratiques sont :

- **FluidSIM** (Festo) : simulation de circuits hydrauliques et électropneumatiques
- **ISPSoft** (Delta Electronics) : programmation de l'API DELTA DVP en
  langage Ladder et en GRAFCET

.. seealso::

   - Fiche technique complète du banc TDS DIDACTIC → voir Annexes
   - Norme ISO 1219-1 : Symbolisme hydraulique
   - Travaux pratiques → voir section Travaux Pratiques