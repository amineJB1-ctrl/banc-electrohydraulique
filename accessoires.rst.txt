Connexions et accessoires
==========================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Identifier les éléments de connexion hydrauliques et électriques du banc TDS DIDACTIC
   - Distinguer un raccord 3 voies d'un raccord 4 voies et choisir le bon selon le circuit
   - Lire les symboles ISO 1219 des conduites hydrauliques
   - Appliquer les règles de montage et de sécurité des tuyaux hydrauliques
   - Identifier les différentes catégories de câbles électriques selon leur usage
   - Utiliser correctement la grille profilée et les systèmes de fixation du banc

----

Vue d'ensemble
--------------

Ce module regroupe tous les éléments qui **relient** les composants hydrauliques et
électriques entre eux. Ces accessoires ne transforment pas l'énergie — ils assurent
la circulation du fluide et des signaux dans les bonnes directions, en toute sécurité.

Sur le banc TDS DIDACTIC, la connexion hydraulique repose sur des **raccords rapides
anti-fuite** qui permettent un montage et un démontage rapide des flexibles sans fuite
d'huile, même sous légère pression résiduelle [S57]_.

.. list-table:: Éléments de connexion et accessoires du banc TDS DIDACTIC
   :header-rows: 1
   :widths: 50 50

   * - Composant
     - Rôle
   * - Raccord 3 voies 
     - Distribution/jonction de 3 conduites hydrauliques
   * - Raccord 4 voies 
     - Distribution/jonction de 4 conduites hydrauliques
   * - Tuyaux hydrauliques flexibles
     - Transport de l'huile entre les composants
   * - Raccords rapides anti-fuite
     - Connexion/déconnexion rapide sans fuite
   * - Câbles électriques
     - Alimentation, commande et signaux
   * - Plaque de fixation / grille profilée 
     - Fixation et positionnement des composants
   * - Outils 
     - Montage, réglage et maintenance

----

PARTIE 1 — Connexions hydrauliques
------------------------------------

1. Raccord 3 voies
-------------------

1.1 Description
~~~~~~~~~~~~~~~

Le raccord 3 voies est un corps métallique percé de trois orifices filetés disposés
en T ou en Y selon le modèle, permettant de créer une jonction entre trois conduites
hydrauliques. Sur le banc TDS DIDACTIC, il est utilisé notamment pour dériver la
ligne de pression principale vers un manomètre ou un pressostat, sans interrompre
l'alimentation du circuit principal [S57]_.

.. figure:: images/raccord_3_voies_reel.png
   :align: center
   :width: 35%
   :alt: Raccord hydraulique 3 voies

   *Fig. 1 — Raccord hydraulique 3 voies utilisé pour la distribution du fluide*
   *(Source : Buisard Distribution)*

1.2 Rôle dans le circuit
~~~~~~~~~~~~~~~~~~~~~~~~~

Le raccord 3 voies sert exclusivement de **point de jonction** — il ne régule ni
le débit ni la pression. Il peut être utilisé dans deux configurations opposées :

- **Dérivation (1 entrée → 2 sorties)** : divise un flux principal en deux branches.
  Attention — si les deux sorties ne sont pas équilibrées en pression, le débit se
  concentre naturellement vers la branche de moindre résistance.
- **Confluence (2 entrées → 1 sortie)** : réunit deux flux en un seul. Utilisé en
  retour de circuit pour ramener l'huile de deux actionneurs vers un seul tuyau
  de retour réservoir.

1.3 Symbole normalisé ISO 1219 [S58]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le raccord 3 voies est représenté par une **ligne principale** avec un **trait
perpendiculaire** portant un point de connexion, indiquant que les trois conduites
communiquent entre elles.

.. figure:: images/raccord_3_voies_symbole.png
   :align: center
   :width: 25%
   :alt: Symbole ISO 1219 raccord 3 voies

   *Fig. 2 — Symbole normalisé ISO 1219 d'un raccord hydraulique 3 voies*
   *(Source : BPMEI Prades)*

1.4 Connexions
~~~~~~~~~~~~~~

- **3 orifices filetés** (BSP ou NPT selon modèle) pour raccordement de tuyaux flexibles
- Filetage identique sur les trois orifices — aucune orientation imposée
- Sur le banc TDS : raccordement via embouts rapides anti-fuite vissés

----

2. Raccord 4 voies
-------------------

2.1 Description
~~~~~~~~~~~~~~~

Le raccord 4 voies (raccord en croix) possède quatre orifices disposés en croix
à 90°. Il permet de connecter quatre conduites en un seul point de jonction.
Il est utilisé pour des jonctions de retour réservoir où plusieurs lignes de drain ou de retour se rejoignent avant
de repartir vers le réservoir principal [S57]_.

.. figure:: images/raccord_4_voies_reel.png
   :align: center
   :width: 35%
   :alt: Raccord hydraulique 4 voies

   *Fig. 3 — Raccord hydraulique 4 voies (raccord en croix)*
   *(Source : ManoMano)*

2.2 Symbole normalisé ISO 1219 [S58]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole du raccord 4 voies représente deux lignes qui se croisent avec un
**point de connexion** à leur intersection, indiquant que les quatre conduites
communiquent entre elles. Sans point, deux lignes qui se croisent ne communiquent
pas (elles se chevauchent simplement sur le schéma).

.. figure:: images/raccord_4_voies_symbole.png
   :align: center
   :width: 22%
   :alt: Symbole ISO 1219 raccord 4 voies

   *Fig. 4 — Symbole normalisé ISO 1219 d'un raccord hydraulique 4 voies*
   *(Source : BPMEI Prades)*

.. note::

   **Règle de lecture des schémas hydrauliques :**
   Sur un schéma ISO 1219, deux lignes qui se **croisent sans point** ne communiquent
   pas (une ligne passe au-dessus de l'autre). Deux lignes qui se croisent
   **avec un point** communiquent — c'est une jonction. Cette règle est la même
   qu'en schéma électrique.

----

3. Tuyaux hydrauliques flexibles
----------------------------------

3.1 Description
~~~~~~~~~~~~~~~

Les tuyaux hydrauliques du banc TDS DIDACTIC sont des **flexibles haute pression**
à armature tressée. Leur construction en couches superposées (tube intérieur en
caoutchouc synthétique, couche(s) d'armature en fils d'acier, gaine extérieure
en caoutchouc) leur permet de résister à la pression de service de 1,6 MPa tout
en absorbant les vibrations et les légères variations d'alignement entre
composants [S59]_.

.. figure:: images/tuyaux_hydrauliques.png
   :align: center
   :width: 55%
   :alt: Tuyaux hydrauliques flexibles

   *Fig. 5 — Tuyaux hydrauliques flexibles armés utilisés sur le banc*
   *(Source : Deremaux)*

3.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Les tuyaux assurent le transport de l'huile sous pression entre tous les composants
du circuit : pompe → distributeurs → vérins → retour réservoir. Leur flexibilité
permet le reconfiguration du circuit entre les TPs — les composants peuvent être
déplacés et reconnectés sans contrainte de rigidité.

3.3 Symboles normalisés ISO 1219 [S58]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Type de conduite
     - Représentation ISO 1219
   * - **Conduite principale** (haute pression)
     - Ligne continue épaisse
   * - **Conduite de retour** (basse pression)
     - Ligne continue fine
   * - **Conduite de pilotage / drain**
     - Ligne tiretée fine
   * - **Flexible** (tuyau souple)
     - Ligne courbe avec deux points d'extrémité (arc)

.. figure:: images/tuyau_symbole.png
   :align: center
   :width: 35%
   :alt: Représentation simplifiée d'un tuyau hydraulique

   *Fig. 6 — Représentation simplifiée d'un tuyau hydraulique flexible (ligne de liaison)*
   *(Source : Target Hydraulics)*

3.4 Règles de montage et de sécurité [S59]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. warning::

   Les règles suivantes sont **obligatoires** pour le montage des flexibles sur le banc :

   - Ne jamais plier un flexible à un rayon inférieur à son rayon de courbure minimal
     (indiqué sur l'étiquette du flexible) — la tresse d'acier se rompt et le
     flexible éclate sous pression.
   - Ne jamais visser une extrémité de flexible en maintenant l'autre extrémité fixe
     — cela tord le tuyau et endommage l'armature interne.
   - Vérifier que chaque raccord est **vissé à fond** avant la mise sous pression —
     un raccord partiellement serré fuit ou se déconnecte brutalement.
   - Après une déconnexion, toujours **obturer les embouts** avec les bouchons
     fournis pour éviter la contamination de l'huile par des impuretés.
   - Ne jamais mettre le circuit sous pression si un flexible présente une **boursouflure,
     une fissure ou une abrasion** visible sur la gaine extérieure.

3.5 Raccords rapides anti-fuite [S57]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Tous les tuyaux du banc TDS DIDACTIC sont équipés de **raccords rapides anti-fuite**
(push-to-connect hydrauliques). Ces raccords intègrent un mécanisme à bille ou
à membrane qui se ferme automatiquement dès que l'embout est déconnecté du composant.
Cela permet de déconnecter un flexible sans vider le circuit ni projeter d'huile.

Pour connecter : insérer l'embout jusqu'au déclic.
Pour déconnecter : appuyer sur la bague de déverrouillage tout en tirant l'embout.

----

PARTIE 2 — Connexions électriques
------------------------------------

4. Câbles électriques
-----------------------

4.1 Description
~~~~~~~~~~~~~~~

Le banc TDS DIDACTIC utilise plusieurs catégories de câbles électriques selon
la nature du signal transporté. Chaque catégorie est identifiable par sa section
(en mm²), sa couleur et son type de connecteur [S60]_.

4.2 Catégories de câbles présents sur le banc [S60]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 30 20 20 30

   * - Catégorie
     - Tension / signal
     - Section typique
     - Raccordement
   * - Alimentation puissance
     - 230 V AC
     - 1,5 à 2,5 mm²
     - Réseau → disjoncteur → alimentation
   * - Alimentation commande
     - 24 V DC
     - 0,75 à 1,5 mm²
     - Alimentation → API, relais, bobines
   * - Signaux capteurs
     - 24 V DC (TOR)
     - 0,5 à 0,75 mm²
     - Capteurs → entrées API (I0.x)
   * - Signaux sorties
     - 24 V DC (TOR)
     - 0,75 mm²
     - Sorties API (Q0.x) → relais / bobines
   * - Communication
     - Ethernet / USB
     - Câble blindé RJ45 ou USB-B
     - API → switch réseau → PC

4.3 Symbole normalisé [S60]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/cable_symbole.png
   :align: center
   :width: 30%
   :alt: Représentation simplifiée d'un câble électrique

   *Fig. 7 — Représentation simplifiée d'un câble électrique (trait continu)*
   *(Source : Physique-Chimie Collège)*

4.4 Règles de câblage sur le banc
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- **Séparation des câbles puissance et signaux** : ne jamais faire cheminer un câble
  230 V AC à côté d'un câble de signal capteur — les champs électriques induisent
  des perturbations qui peuvent provoquer des commutations intempestives de l'API.
- **Identification des câbles** : utiliser des couleurs normalisées : rouge = +24 V,
  bleu = 0 V, noir = signal, vert/jaune = terre PE.
- **Longueur libre suffisante** : prévoir un léger excédent de longueur pour permettre
  le démontage des composants sans arracher les connexions.

----

PARTIE 3 — Fixation et outillage
-----------------------------------

5. Plaque de fixation et grille profilée
------------------------------------------

5.1 Description
~~~~~~~~~~~~~~~

Le banc TDS DIDACTIC est équipé d'une **grille d'exercice profilée 50 × 50 mm**
sur laquelle tous les composants hydrauliques et électriques peuvent être fixés et
repositionnés librement. Chaque composant hydraulique est monté sur une base
métallique rigide compatible avec les rails de la grille [S57]_.

.. figure:: images/plaque_fixation.png
   :align: center
   :width: 60%
   :alt: Plaque de fixation et composants montés sur le banc

   *Fig. 8 — Composants montés sur la grille profilée du banc didactique —*
   *vérin, distributeurs et capteur fixés par bases métalliques sur rails*
   *(Source : TDS DIDACTIC)*

5.2 Rôle pédagogique de la grille
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La grille profilée est l'élément qui donne au banc sa **modularité pédagogique** :
les composants peuvent être repositionnés pour chaque TP afin de construire
différentes configurations de circuit. Le passage d'un circuit simple (1 vérin,
1 distributeur) à un circuit complexe (2 vérins, régulateurs, clapets) se fait
en déplaçant les bases métalliques sur la grille, sans outil spécial [S57]_.

5.3 Règles de fixation
~~~~~~~~~~~~~~~~~~~~~~~

- Vérifier que chaque composant est **serré fermement** dans les rails avant la
  mise sous pression — un composant mal fixé peut se déplacer sous l'effet
  des forces de réaction hydrauliques.
- Respecter un **dégagement minimal de 5 cm** entre les composants pour permettre
  l'accès aux raccords de connexion.
- Après chaque TP, **remettre les composants en position de rangement** définie
  par l'enseignant avant de les démonter — facilite l'inventaire et détecte
  les pièces manquantes.

----

6. Outils
-----------

6.1 Description
~~~~~~~~~~~~~~~

Le banc TDS DIDACTIC est livré avec un **ensemble d'outils** nécessaires
à l'assemblage, au réglage et à la maintenance de l'installation. Ces outils permettent
à l'étudiant d'effectuer lui-même les opérations de montage des raccords, de réglage
des limiteurs de pression et de câblage électrique [S61]_.

.. figure:: images/outils.png
   :align: center
   :width: 60%
   :alt: Ensemble d'outils pour le montage et la maintenance

   *Fig. 9 — Ensemble d'outils utilisés pour le montage et la maintenance du banc*
   *(Source : SAM Outillage)*

6.2 Outils principaux et leur usage sur le banc
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Outil
     - Usage sur le banc TDS DIDACTIC
   * - Clés à molette / clés plates
     - Serrage des raccords filetés hydrauliques — toujours utiliser deux clés
       (une pour tenir, une pour serrer) pour éviter de tordre les tuyaux
   * - Tournevis plat et cruciforme
     - Serrage des bornes électriques sur l'API, les relais et les capteurs
   * - Clé Allen (hexagonale)
     - Fixation des composants hydrauliques sur les bases métalliques de la grille
   * - Multimètre
     - Vérification des connexions électriques, mesure de la tension 24 V DC,
       test de continuité des câbles
   * - Pince à dénuder / sertir
     - Préparation des extrémités de câbles pour raccordement sur les bornes

----

.. rubric:: Sources utilisées dans ce module

.. [S57] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
         Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S58] BPMEI Prades, *Symboles ISO 1219 des connexions hydrauliques — raccords et
         conduites*, ressource pédagogique,
         disponible en ligne : https://www.bpmei-prades.fr (consulté en 2024)

.. [S59] Deremaux, *Flexibles hydrauliques armés — choix, montage et règles de sécurité*,
         documentation technique, disponible en ligne : https://www.deremaux.fr
         (consulté en 2024)

.. [S60] Physique-Chimie Collège / Sitelec, *Câbles électriques industriels — catégories,
         sections et règles de câblage*, ressources pédagogiques,
         disponibles en ligne : https://www.sitelec.org (consulté en 2024)

.. [S61] SAM Outillage, *Ensembles d'outils pour installation industrielle — clés,
         tournevis et pinces*, catalogue produits,
         disponible en ligne : https://www.sam-outillage.fr (consulté en 2024)