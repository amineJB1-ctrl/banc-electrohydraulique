Distributeurs et électrodistributeurs hydrauliques
==================================================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Expliquer le rôle d'un distributeur dans un circuit hydraulique
   - Décoder la notation m/n d'un distributeur (nombre d'orifices / nombre de positions)
   - Lire et interpréter le symbole normalisé ISO 1219 d'un distributeur
   - Distinguer les différents types de centre d'un distributeur 4/3 ou 5/3
   - Identifier le câblage électrique d'une bobine solénoïde (tension, bornes A1/A2)
   - Choisir le type de distributeur adapté à une application donnée

----

Vue d'ensemble
--------------

Un distributeur hydraulique est un organe de **commande directionnelle** : il décide
dans quel sens le fluide circule dans le circuit, et donc dans quel sens un actionneur
se déplace — ou s'immobilise. Sans distributeur, la pompe pousserait l'huile dans une
seule direction fixe et aucun mouvement contrôlé ne serait possible [S16]_.

Sur le banc TDS DIDACTIC, tous les distributeurs sont commandés **électriquement** via
des bobines solénoïdes alimentées en **24 V DC** depuis l'API DELTA DVP. On parle alors
d'**électrodistributeurs** ou d'**électrovannes**. Cette commande électrique est ce qui
permet à l'automate de piloter les vérins automatiquement, sans intervention manuelle
sur le distributeur [S17]_.

.. note::

   **Comment lire la notation m/n d'un distributeur :**

   - **m** = nombre d'orifices hydrauliques (voies)
   - **n** = nombre de positions du tiroir

   Exemples : 4/2 = 4 orifices, 2 positions — 4/3 = 4 orifices, 3 positions —
   5/3 = 5 orifices, 3 positions.

   Les orifices standards sont nommés : **P** (pression — alimentation depuis la pompe),
   **T** (tank — retour vers le réservoir), **A** et **B** (utilisation — vers
   les chambres du vérin).

----

**Comment lire un symbole de distributeur ISO 1219** [S18]_

Le symbole d'un distributeur se compose de cases juxtaposées, chacune représentant
une position du tiroir :

- Chaque **case** = une position du distributeur
- Les **flèches** dans une case = passage du fluide dans ce sens
- Les **barrettes perpendiculaires** aux orifices = obturation (orifice fermé)
- Les **traits de commande** à l'extérieur des cases = type d'actionneur
  (solénoïde = symbole d'électroaimant, ressort = zigzag)
- La **case active au repos** est celle qui se trouve du côté du ressort de rappel

----

PARTIE 1 — Distributeurs hydrauliques à commande manuelle
---------------------------------------------------------

1. Distributeur 4/2
~~~~~~~~~~~~~~~~~~~~

1.1 Description
^^^^^^^^^^^^^^^

Le distributeur 4/2 possède **quatre orifices** (P, T, A, B) et **deux positions**
stables. Il est principalement utilisé pour commander les vérins double effet : sa
commutation entre les deux positions inverse la direction du fluide et donc le sens
de déplacement de la tige [S16]_.

Sa structure interne est à **tiroir coulissant** : un cylindre allongé (le tiroir)
se translate à l'intérieur du corps du distributeur et, selon sa position, ouvre ou
ferme les passages entre les orifices.

.. figure:: images/schema_interne_4_2.gif
   :align: center
   :width: 65%
   :alt: Structure interne d'un distributeur hydraulique à tiroir

   *Fig. 1 — Structure interne d'un distributeur hydraulique à tiroir (orifices T, A, P, B)*
   *(Source : Université de Limoges)*

.. figure:: images/distributeur_reel.png
   :align: center
   :width: 55%
   :alt: Distributeur électro-hydraulique réel

   *Fig. 2 — Exemple de distributeur électro-hydraulique réel (source : EBS Tunisie)*

1.2 Rôle dans le système
^^^^^^^^^^^^^^^^^^^^^^^^^

Le distributeur 4/2 contrôle le sens de déplacement d'un vérin double effet en
aiguillant l'huile sous pression alternativement vers l'une ou l'autre chambre du vérin,
tout en assurant simultanément le retour de l'huile de la chambre opposée vers le
réservoir.

1.3 Fonctionnement des deux positions [S16]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1
   :widths: 20 40 40

   * - Position
     - Connexions actives
     - Effet sur le vérin double effet
   * - **Repos** (bobine non alimentée)
     - P → A et B → T
     - Huile vers chambre fond → tige sort
   * - **Travail** (bobine alimentée)
     - P → B et A → T
     - Huile vers chambre tige → tige rentre

1.4 Commande électrique
^^^^^^^^^^^^^^^^^^^^^^^^

La commutation entre les deux positions s'effectue par l'alimentation d'une
**bobine solénoïde** en 24 V DC depuis l'API. Lorsque la bobine est mise sous tension,
son champ magnétique attire le noyau ferromagnétique solidaire du tiroir, qui se déplace
et modifie les connexions entre orifices. À la coupure de l'alimentation, un **ressort
de rappel** ramène automatiquement le tiroir en position de repos [S17]_.

1.5 Symbole normalisé ISO 1219 [S18]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/4_2.png
   :align: center
   :width: 30%
   :alt: Symbole normalisé ISO 1219 du distributeur 4/2

   *Fig. 3 — Symbole normalisé ISO 1219 du distributeur 4/2*
   *(Source : Université de Limoges)*

1.6 Connexions
^^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1
   :widths: 15 85

   * - Orifice
     - Fonction
   * - **P**
     - Alimentation — raccordé à la ligne de pression (sortie pompe)
   * - **T**
     - Retour — raccordé au réservoir hydraulique
   * - **A**
     - Utilisation — raccordé à la chambre fond du vérin
   * - **B**
     - Utilisation — raccordé à la chambre tige du vérin

----

2. Distributeur 4/3
~~~~~~~~~~~~~~~~~~~~

2.1 Description
^^^^^^^^^^^^^^^

Le distributeur 4/3 possède les mêmes **quatre orifices** (P, T, A, B) que le 4/2,
mais dispose d'une **troisième position centrale**. Cette position intermédiaire,
maintenue par deux ressorts en opposition, assure l'arrêt et le maintien du vérin
en cours de déplacement sans couper la pompe [S16]_.

Le comportement en position centrale varie selon le **type de centre** choisi à la
conception :

.. list-table:: Types de centre d'un distributeur 4/3
   :header-rows: 1
   :widths: 25 40 35

   * - Type de centre
     - Connexions en position centrale
     - Effet sur le vérin
   * - **Centre fermé**
     - P, T, A, B tous isolés
     - Vérin bloqué en position (charge maintenue)
   * - **Centre ouvert**
     - P → T (déchargé), A et B libres
     - Vérin libre, pompe déchargée
   * - **Centre en pression**
     - P → A et B, T isolé
     - Vérin maintenu sous pression dans les deux chambres

.. note::

   Le banc TDS DIDACTIC est équipé de distributeurs **4/3 à centre fermé** (3 au
   total selon la fiche technique). C'est le choix le plus sûr pour des applications
   de maintien de position sous charge — si l'alimentation électrique est coupée,
   le vérin reste immobilisé.

2.2 Fonctionnement des trois positions [S16]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/schema_4_3.png
   :align: center
   :width: 70%
   :alt: Fonctionnement d'un distributeur 4/3 à trois positions

   *Fig. 4 — Fonctionnement d'un distributeur 4/3 : position repos, position 1 et position 2*
   *(Source : Université de Limoges)*

.. list-table::
   :header-rows: 1
   :widths: 20 40 40

   * - Position
     - Connexions actives
     - Effet sur le vérin
   * - **Centrale** (repos, bobines non alimentées)
     - Tous orifices isolés (centre fermé)
     - Vérin immobilisé, pression maintenue
   * - **Position 1** (bobine L1 alimentée)
     - P → B et A → T
     - Huile vers chambre tige → tige rentre
   * - **Position 2** (bobine L2 alimentée)
     - P → A et B → T
     - Huile vers chambre fond → tige sort

2.3 Symbole normalisé ISO 1219 [S18]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/4_3.png
   :align: center
   :width: 40%
   :alt: Symbole normalisé ISO 1219 du distributeur 4/3

   *Fig. 5 — Symbole normalisé ISO 1219 du distributeur 4/3 à commande électrique et rappel par ressort*
   *(Source : Université de Limoges)*

2.4 Connexions
^^^^^^^^^^^^^^

Identiques au 4/2 : P (pression), T (retour réservoir), A et B (vers les deux
chambres du vérin). Les **deux bobines** de commande (L1 et L2) sont reliées à deux
sorties distinctes de l'API.

----

PARTIE 2 — Électrovannes
------------------------

Les électrovannes sont des distributeurs à commande **entièrement électrique**.
Contrairement aux distributeurs manuels, elles ne possèdent pas de levier de commande
manuelle — elles sont pilotées exclusivement par les sorties numériques de l'API.

3. Électrovanne 2/2
~~~~~~~~~~~~~~~~~~~~

3.1 Description
^^^^^^^^^^^^^^^

L'électrovanne 2/2 est le distributeur le plus simple : **2 orifices** (entrée et sortie)
et **2 positions** (ouverte / fermée). Elle joue le rôle d'un interrupteur hydraulique —
elle autorise ou bloque le passage du fluide. Elle existe en deux versions selon l'état
de repos [S19]_ :

- **Normalement Fermée (NF)** : au repos (bobine non alimentée), le passage est obturé.
  Dès que la bobine est alimentée, un champ magnétique attire le noyau plongeur et ouvre
  le passage. C'est la version la plus courante en hydraulique industrielle pour des
  raisons de sécurité.
- **Normalement Ouverte (NO)** : au repos, le passage est libre. L'alimentation de la
  bobine ferme la vanne. Utilisée lorsqu'on souhaite que le fluide circule par défaut.

.. figure:: images/electrovanne_2_2.png
   :align: center
   :width: 40%
   :alt: Électrovanne 2/2

   *Fig. 6 — Électrovanne 2/2 utilisée pour le contrôle du fluide*
   *(Source : Tameson)*

3.2 Symbole normalisé ISO 1219 [S18]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/electrovanne_2_2_no_nf.png
   :align: center
   :width: 50%
   :alt: Symboles NF et NO d'une électrovanne 2/2

   *Fig. 7 — Symboles d'une électrovanne 2/2 normalement fermée (NF) et normalement ouverte (NO)*
   *(Source : Wikipédia)*

3.3 Connexions
^^^^^^^^^^^^^^

- **Hydraulique** : 1 entrée (orifice 1), 1 sortie (orifice 2)
- **Électrique** : bobine solénoïde 24 V DC — borne A1 (+), borne A2 (−)

----

4. Électrovanne 4/2
~~~~~~~~~~~~~~~~~~~~

4.1 Description
^^^^^^^^^^^^^^^

L'électrovanne 4/2 est la version entièrement électrique du distributeur 4/2 décrit
en Partie 1. Elle possède les mêmes **4 orifices** (P, T, A, B) et les mêmes **2 positions**,
mais sa commutation est assurée par une bobine solénoïde unique associée à un ressort
de rappel [S20]_.

.. figure:: images/electrovanne_4_2_reel.png
   :align: center
   :width: 45%
   :alt: Électrovanne 4/2

   *Fig. 8 — Électrovanne 4/2 utilisée pour le contrôle d'un vérin double effet*
   *(Source : Bürkert)*

4.2 Fonctionnement
^^^^^^^^^^^^^^^^^^

La bobine unique déplace le tiroir vers sa deuxième position lorsqu'elle est alimentée.
En l'absence de commande, le ressort de rappel ramène le tiroir en position initiale.
Cette conception **monostable** convient aux applications où la position de sécurité
doit être la position de repos (tiroir retourné automatiquement en cas de coupure de
courant).

4.3 Symbole normalisé ISO 1219 [S18]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/electrovanne_4_2.png
   :align: center
   :width: 35%
   :alt: Symbole normalisé d'une électrovanne 4/2

   *Fig. 9 — Symbole normalisé ISO 1219 d'une électrovanne 4/2 (solénoïde + rappel ressort)*
   *(Source : Université de Limoges)*

4.4 Connexions
^^^^^^^^^^^^^^

- **P** : alimentation pression (pompe)
- **T** (ou R) : retour réservoir
- **A** et **B** : vers les chambres du vérin
- **Bobine** : 24 V DC — borne A1 (+), borne A2 (−)

----

5. Électrovanne 4/3
~~~~~~~~~~~~~~~~~~~~

5.1 Description
^^^^^^^^^^^^^^^

L'électrovanne 4/3 est la version électrique du distributeur 4/3. Elle possède **4 orifices**
et **3 positions**, commandées par **deux bobines indépendantes** (une pour chaque sens
de déplacement du tiroir) et un double rappel par ressorts pour la position centrale.
L'alimentation de la bobine L1 (repère **a** sur le symbole) déplace le tiroir vers
la droite ; celle de la bobine L2 (repère **b**) vers la gauche [S20]_.

.. figure:: images/electrovanne_4_3.png
   :align: center
   :width: 45%
   :alt: Électrovanne 4/3

   *Fig. 10 — Électrovanne 4/3 utilisée dans un système hydraulique*
   *(Source : Tameson)*

5.2 Symbole normalisé ISO 1219 [S18]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/electrovanne_4_3_symbole.png
   :align: center
   :width: 45%
   :alt: Symbole normalisé d'une électrovanne 4/3

   *Fig. 11 — Symbole normalisé ISO 1219 d'un distributeur 4/3 à commande électrique*
   *et rappel par ressort (Source : Tameson)*

5.3 Commande électrique depuis l'API [S17]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. list-table::
   :header-rows: 1
   :widths: 30 30 40

   * - État des bobines
     - Position du tiroir
     - Effet sur le vérin
   * - L1 = 0 et L2 = 0
     - Centrale (repos)
     - Vérin immobilisé
   * - L1 = 1 et L2 = 0
     - Position a (gauche)
     - Tige sort (P→A, B→T)
   * - L1 = 0 et L2 = 1
     - Position b (droite)
     - Tige rentre (P→B, A→T)
   * - L1 = 1 et L2 = 1
     - **Interdit** — à éviter
     - Risque de blocage mécanique

.. warning::

   Ne jamais alimenter les deux bobines L1 et L2 simultanément. Cette situation crée
   des forces antagonistes sur le tiroir qui peuvent bloquer mécaniquement le
   distributeur et endommager les bobines.

5.4 Connexions
^^^^^^^^^^^^^^

- **P** : alimentation pression (pompe)
- **T** : retour réservoir
- **A** et **B** : vers les deux chambres du vérin
- **Bobine L1** (borne a) : sortie API → tige sort
- **Bobine L2** (borne b) : sortie API → tige rentre
- Tension de commande : **24 V DC**

----

6. Électrovanne 5/3
~~~~~~~~~~~~~~~~~~~~

6.1 Description
^^^^^^^^^^^^^^^

L'électrovanne 5/3 possède **5 orifices** et **3 positions**. Elle diffère du 4/3 par
la présence de **deux orifices de retour séparés** (T1 et T2) au lieu d'un seul.
Cette configuration est utilisée lorsqu'il est nécessaire de séparer les circuits de
retour des deux chambres du vérin — par exemple pour mesurer indépendamment la
contre-pression de chaque chambre ou pour insérer des étranglements de débit séparés
sur chaque voie de retour [S19]_.

.. figure:: images/electrovanne_5_3_image.png
   :align: center
   :width: 55%
   :alt: Électrovanne 5/3

   *Fig. 12 — Électrovanne 5/3 utilisée pour le contrôle d'un vérin double effet*
   *(Source : RS Components)*

6.2 Les trois types de centre
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

La position centrale d'un 5/3 détermine le comportement du vérin en l'absence de
commande. Trois variantes existent [S21]_ :

.. list-table::
   :header-rows: 1
   :widths: 25 40 35

   * - Type de centre
     - Connexions en position centrale
     - Application typique
   * - **Centre fermé**
     - Orifices 1(P), 2(A), 4(B), 3(T1), 5(T2) tous isolés
     - Maintien de position sous charge
   * - **Centre ouvert**
     - 2(A) et 4(B) reliés aux retours 3 et 5
     - Vérin libre (déplaçable manuellement)
   * - **Centre en pression**
     - 1(P) relié à 2(A) et 4(B) simultanément
     - Maintien sous pression dans les deux sens

6.3 Symboles normalisés des trois centres [S18]_
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. figure:: images/electrovanne_5_3.png
   :align: center
   :width: 65%
   :alt: Les trois types de centre d'une électrovanne 5/3

   *Fig. 13 — Symboles des trois types de centre d'une électrovanne 5/3 :*
   *fermé, ouvert et en pression (Source : Maxicours)*

6.4 Connexions et correspondance numérique
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Les électrovannes 5/3 utilisent fréquemment une **numérotation des orifices**
en lieu et place des lettres :

.. list-table::
   :header-rows: 1
   :widths: 20 15 65

   * - Lettre ISO
     - N° ISO
     - Fonction
   * - P
     - 1
     - Alimentation pression (pompe)
   * - A
     - 2
     - Sortie vers chambre fond du vérin
   * - B
     - 4
     - Sortie vers chambre tige du vérin
   * - T1
     - 3
     - Retour réservoir (côté B)
   * - T2
     - 5
     - Retour réservoir (côté A)

- **Bobines** : 12 (commande position a) et 14 (commande position b) — 24 V DC
- **Rappel au centre** : double ressort

----

7. Tableau comparatif — tous les distributeurs du module
---------------------------------------------------------

.. list-table::
   :header-rows: 1
   :widths: 15 12 12 30 31

   * - Type
     - Orifices
     - Positions
     - Commande
     - Application principale
   * - 4/2
     - 4 (P,T,A,B)
     - 2
     - Solénoïde + ressort
     - Vérin DE — 2 sens
   * - 4/3
     - 4 (P,T,A,B)
     - 3
     - 2 solénoïdes + 2 ressorts
     - Vérin DE — 2 sens + arrêt
   * - 2/2
     - 2 (entrée/sortie)
     - 2
     - Solénoïde + ressort
     - Ouverture/fermeture simple
   * - 5/3
     - 5 (P,A,B,T1,T2)
     - 3
     - 2 solénoïdes + 2 ressorts
     - Vérin DE — retours séparés

----

.. rubric:: Sources utilisées dans ce module

.. [S16] Université de Limoges, *Hydraulique industrielle — distributeurs à tiroir,
        symboles et fonctionnement*, Département Génie Mécanique et Productique,
        disponible en ligne : https://www.unilim.fr 

.. [S17] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
        Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S18] ISO 1219-1:2012, *Transmissions hydrauliques et pneumatiques — Symboles
        graphiques et schémas de circuits*, Organisation internationale de normalisation,
        Genève, 2012.

.. [S19] Tameson, *Guide des électrovannes hydrauliques — types, fonctionnement
        et sélection*, disponible en ligne : https://www.tameson.fr
        

.. [S20] Bürkert Fluid Control Systems, *Solenoid valves — product catalogue and
        technical specifications*, disponible en ligne : https://www.burkert.com
        

.. [S21] Maxicours, *Les distributeurs hydrauliques — types de centre et
        applications*, ressource pédagogique en ligne : https://www.maxicours.com
        