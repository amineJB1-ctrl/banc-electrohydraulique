Capteurs et instrumentation
===========================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Identifier les cinq types de capteurs présents sur le banc TDS DIDACTIC
   - Distinguer un capteur mécanique à contact d'un capteur sans contact
   - Expliquer le principe de détection de chaque capteur
   - Distinguer un signal TOR NO d'un signal TOR NF et justifier le choix de l'un ou l'autre
   - Câbler correctement un capteur 3 fils (BN, BU, BK) vers une entrée d'API
   - Lire la pression affichée par un manomètre et identifier sa position dans le circuit
   - Interpréter le changement d'état d'un pressostat lors d'une montée en pression

----

Vue d'ensemble
--------------

Dans un système électro-hydraulique automatisé, les capteurs constituent la **couche
d'acquisition** : ils transforment une information physique (position, pression) en
signal électrique exploitable par l'automate programmable (API). Sans capteurs, l'API
est aveugle — il ne peut ni déclencher une séquence au bon moment, ni protéger le
circuit contre une surpression.

Sur le banc TDS DIDACTIC, cinq types de capteurs et instruments sont présents [S22]_ :

.. list-table:: Capteurs et instruments présents sur le banc TDS DIDACTIC
   :header-rows: 1
   :widths: 30 25 45

   * - Capteur / Instrument
     - Grandeur mesurée
     - Type de signal
   * - Fin de course (NF)
     - Position mécanique
     - TOR — contact NF
   * - Fin de course (NO)
     - Position mécanique
     - TOR — contact NO
   * - Détecteur inductif de proximité
     - Présence métal (sans contact)
     - TOR — 3 fils
   * - Capteur magnétique à LED (forme A)
     - Position du piston vérin
     - TOR — 3 fils
   * - Pressostat électrique (relais de pression)
     - Seuil de pression fluide
     - TOR — contact NO/NF
   * - Manomètre
     - Pression fluide (affichage)
     - Aucun (lecture visuelle)

.. note::

   **Signal TOR (Tout Ou Rien) :** un signal TOR ne prend que deux états possibles —
   **0** (contact ouvert, tension nulle) ou **1** (contact fermé, +24 V DC). C'est
   le type de signal standard pour les entrées numériques d'un API.

   - **NO (Normalement Ouvert)** : au repos, le contact est ouvert → signal à 0.
     Il se ferme et passe à 1 quand la condition est remplie (objet détecté, pression
     atteinte, fin de course actionné).
   - **NF (Normalement Fermé)** : au repos, le contact est fermé → signal à 1.
     Il s'ouvre et passe à 0 quand la condition est remplie. Préféré en sécurité
     car une coupure de fil est automatiquement interprétée comme un déclenchement.

----

1. Fin de course mécanique
---------------------------

1.1 Description
~~~~~~~~~~~~~~~

Le fin de course est un **capteur de position mécanique à contact**. Il est installé
sur un vérin ou une structure mobile pour détecter physiquement l'arrivée en position
finale. Contrairement aux capteurs sans contact, il nécessite un contact direct entre
son actionneur (galet, tige, levier) et l'élément mobile pour commuter [S29]_.


.. figure:: images/fin_course_reel.png
   :align: center
   :width: 40%
   :alt: Structure d'un fin de course mécanique

   *Fig. 1 — Structure d'un fin de course mécanique :*
   *tête de commande avec dispositif d'attaque (1), corps (2), contact électrique (3)*
   *(Source : Technomoussi)*

1.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le fin de course détecte la position du piston ou de la tige d'un vérin et envoie
un signal électrique TOR à l'API pour déclencher une action : arrêt du mouvement,
inversion de sens, passage à l'étape suivante du cycle automatique.

1.3 Principe de fonctionnement commun
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Lorsque l'élément mobile (tige du vérin, plaque de butée) vient en contact avec
l'actionneur du fin de course (galet ou levier), il force mécaniquement le déplacement
du contact interne. Selon le type de contact (NO ou NF), l'état électrique de sortie
change différemment [S29]_ :

.. figure:: images/fin_course_schema.png
   :align: center
   :width: 65%
   :alt: Principe de fonctionnement d'un fin de course mécanique

   *Fig. 2 — Principe de fonctionnement d'un fin de course mécanique*
   *pour mouvement rectiligne et angulaire (Source : École La Mache)*

1.4 Fin de course NF — normalement fermé
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 30 35 35

   * - État
     - Contact interne
     - Signal vers l'API
   * - **Repos** (fin de course non actionné)
     - Fermé
     - 1 (+24 V DC)
   * - **Actionné** (tige en butée)
     - Ouvert
     - 0 (0 V)

**Symbole normalisé IEC 60617 [S29]_ :**

.. figure:: images/fin_course_symbole.png
   :align: center
   :width: 30%
   :alt: Symbole d'un fin de course normalement fermé NF

   *Fig. 3 — Symbole d'un fin de course normalement fermé (NF)*
   *— bornes 11 et 12 (Source : OMCH)*

**Utilisation sur le banc :** le contact NF est câblé sur les entrées de sécurité
de l'API. Si le fil est coupé ou le capteur arraché, le signal passe de 1 à 0,
ce que l'automate interprète comme un arrêt d'urgence — comportement sécurisé par
défaut (fail-safe).

1.5 Fin de course NO — normalement ouvert
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 30 35 35

   * - État
     - Contact interne
     - Signal vers l'API
   * - **Repos** (fin de course non actionné)
     - Ouvert
     - 0 (0 V)
   * - **Actionné** (tige en butée)
     - Fermé
     - 1 (+24 V DC)

**Symbole normalisé IEC 60617 [S29]_ :**

.. figure:: images/fin_course_no_symbole.png
   :align: center
   :width: 30%
   :alt: Symbole d'un fin de course normalement ouvert NO

   *Fig. 4 — Symbole d'un fin de course normalement ouvert (NO)*
   *— bornes 13 et 14 (Source : OMCH)*

**Utilisation sur le banc :** le contact NO est câblé sur les entrées de détection
de position de l'API. L'automate attend un passage de 0 à 1 pour valider qu'une
position est atteinte avant de lancer l'étape suivante du cycle.

1.6 Connexions électriques
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 20 20 60

   * - Borne
     - Type
     - Raccordement
   * - **11 / 13**
     - Commune
     - Reliée au +24 V DC (alimentation)
   * - **12**
     - NF
     - Vers entrée numérique API → signal à 1 au repos
   * - **14**
     - NO
     - Vers entrée numérique API → signal à 0 au repos

.. warning::

   Ne jamais actionner manuellement un fin de course sous tension sans vérifier
   que le circuit hydraulique est à l'arrêt. L'actionnement du fin de course
   peut déclencher immédiatement un mouvement de vérin si le programme API
   est en cours d'exécution.

----

2. Détecteur inductif de proximité
------------------------------------

2.1 Description
~~~~~~~~~~~~~~~

Le détecteur inductif de proximité est un capteur électronique sans contact qui détecte
la présence de tout objet **métallique conducteur** à une distance de quelques
millimètres. Il ne nécessite aucun contact physique avec la cible, ce qui lui confère
une durée de vie très longue et une insensibilité aux chocs [S23]_.

Sur le banc TDS DIDACTIC, ce détecteur est utilisé pour signaler la présence ou la
position d'une pièce mobile métallique (plaque de butée, support de vérin, etc.).

2.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le détecteur inductif génère un signal électrique TOR dès qu'une surface métallique
s'approche à moins de sa distance de commutation. Ce signal est envoyé directement à
une entrée numérique de l'API, qui peut alors déclencher une action : arrêt du vérin,
inversion de mouvement, démarrage d'une séquence suivante.

2.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le capteur renferme un oscillateur électronique qui génère en permanence un **champ
électromagnétique alternatif** à sa face active. Lorsqu'un objet métallique pénètre
dans ce champ, les courants de Foucault induits dans le métal augmentent les pertes
énergétiques de l'oscillateur, ce qui réduit son amplitude d'oscillation. Un circuit
de détection interne surveille cette amplitude : lorsqu'elle descend sous un seuil
prédéfini, il commute la sortie du capteur [S23]_.

.. figure:: images/detecteur_inductif_schema.png
   :align: center
   :width: 60%
   :alt: Principe de fonctionnement d'un détecteur inductif de proximité

   *Fig. 5 — Principe de fonctionnement d'un détecteur inductif : sans objet (état repos)*
   *et avec objet métallique (état commuté). La distance P/2 indique la portée utile.*
   *(Source : BPMEI Prades)*

2.4 Symbole normalisé [S24]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole d'un détecteur inductif représente un **carré** contenant un losange (symbole
de la détection inductive) et une onde sinusoïdale (champ électromagnétique généré),
avec trois fils de raccordement : BN (alimentation), BU (masse), BK (sortie signal).

.. figure:: images/detecteur_inductif.png
   :align: center
   :width: 28%
   :alt: Symbole normalisé d'un détecteur inductif de proximité 3 fils

   *Fig. 6 — Symbole normalisé d'un détecteur inductif de proximité (3 fils : BN, BU, BK)*
   *(Source : École La Mache)*

2.5 Câblage 3 fils vers l'API [S22]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 15 15 20 50

   * - Fil
     - Couleur
     - Raccordement
     - Fonction
   * - BN
     - Marron
     - +24 V DC
     - Alimentation positive du capteur
   * - BU
     - Bleu
     - 0 V (GND)
     - Masse commune du capteur
   * - BK
     - Noir
     - Entrée API (ex. : I0.0)
     - Signal de sortie — passe à +24 V quand un objet est détecté (NO)

.. warning::

   Ne jamais inverser le fil BN (+24 V) et le fil BK (sortie signal) — cela court-circuite
   la sortie du capteur et détruit l'étage de sortie électronique. Toujours vérifier le
   schéma de câblage du fabricant avant raccordement.

2.6 Caractéristiques techniques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Type de détection
     - Inductive (courants de Foucault)
   * - Cibles détectables
     - Métaux ferreux et non ferreux
   * - Distance de commutation typique
     - 2 à 8 mm (selon modèle)
   * - Tension d'alimentation
     - 10 – 30 V DC
   * - Type de sortie
     - TOR — NPN ou PNP, NO ou NF
   * - Nombre sur banc TDS
     - 2 unités

----

3. Capteur magnétique à LED (forme A)
---------------------------------------

3.1 Description
~~~~~~~~~~~~~~~

Le capteur magnétique à LED est un capteur de position **sans contact** spécialement
conçu pour détecter la position du piston à l'intérieur du corps d'un vérin. Il est
fixé à l'extérieur du corps du vérin et détecte le champ magnétique permanent d'un
aimant intégré dans le piston. Une LED verte s'allume pour confirmer visuellement la
détection [S25]_.


3.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le capteur magnétique informe l'API que le piston d'un vérin a atteint une position
précise dans sa course. C'est le signal qui déclenche les transitions dans le GRAFCET :
"vérin en position avant → activer le distributeur suivant", etc. Sans ces capteurs,
aucun cycle automatique séquencé n'est possible.

3.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Chaque piston des vérins du banc est équipé d'un **aimant permanent** moulé dans sa
masse. Lorsque le piston se déplace jusqu'à la position du capteur fixé sur le corps
du vérin, le champ magnétique de l'aimant traverse la paroi non magnétique du corps
et est capté par un élément sensible au champ magnétique (effet Hall ou magnétorésistance).
Ce changement de champ commute la sortie électronique du capteur et allume
simultanément la LED témoin [S25]_.

.. figure:: images/capteur_magnetique_schema.png
   :align: center
   :width: 65%
   :alt: Principe de fonctionnement d'un capteur magnétique sur vérin

   *Fig. 7 — Principe de fonctionnement d'un capteur magnétique sur vérin :*
   *aimant hors zone (contact ouvert) et aimant dans la zone de détection (contact fermé)*
   *(Source : BPMEI Prades)*

.. figure:: images/capteur_magnetique_reel.png
   :align: center
   :width: 60%
   :alt: Capteur magnétique monté sur un vérin hydraulique

   *Fig. 8 — Capteur magnétique à LED monté sur un vérin hydraulique —*
   *il glisse dans la rainure du corps du vérin et se fixe par serrage*
   *(Source : BPMEI Prades)*

3.4 Symbole normalisé [S24]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole d'un capteur magnétique est identique à celui du détecteur inductif, mais
le symbole interne du carré représente un **aimant permanent** (symbole « condensateur »
avec polarités) au lieu du losange inductif. Les trois fils de raccordement sont
identiques : BN, BU, BK.

.. figure:: images/capteur_magnetique.png
   :align: center
   :width: 28%
   :alt: Symbole normalisé d'un capteur magnétique de position

   *Fig. 9 — Symbole normalisé d'un capteur magnétique de position (3 fils : BN, BU, BK)*
   *(Source : École La Mache)*

3.5 Câblage 3 fils vers l'API [S22]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le câblage est identique au détecteur inductif :

.. list-table::
   :header-rows: 1
   :widths: 15 15 20 50

   * - Fil
     - Couleur
     - Raccordement
     - Fonction
   * - BN (marron)
     - Marron
     - +24 V DC
     - Alimentation positive du capteur
   * - BU (bleu)
     - Bleu
     - 0 V (GND)
     - Masse commune
   * - BK (noir)
     - Noir
     - Entrée API (ex. : I0.1, I0.2…)
     - Signal : +24 V quand aimant détecté

3.6 Positionnement sur le vérin
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le capteur magnétique coulisse dans une **rainure longitudinale** usinée sur le corps
du vérin et se verrouille en position par une vis de serrage. Pour régler une position
de détection précise, on déplace le capteur le long de la rainure, on vérifie que la
LED s'allume à la position souhaitée, puis on serre la vis. Ce réglage est à effectuer
**avant** la mise sous pression du circuit [S25]_.

3.7 Caractéristiques techniques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Type de détection
     - Magnétique (aimant permanent dans le piston)
   * - Montage
     - Rainure externe du corps du vérin
   * - Tension d'alimentation
     - 5 – 30 V DC
   * - Type de sortie
     - TOR — NPN, NO ou NF
   * - Indicateur visuel
     - LED verte (s'allume quand le piston est détecté)
   * - Nombre sur banc TDS
     - 3 unités (2 noirs forme A + 1 gris forme A)

----

4. Pressostat électrique
--------------------------

4.1 Description
~~~~~~~~~~~~~~~

Le pressostat électrique est un capteur de pression qui convertit un seuil de pression
hydraulique en signal électrique TOR. Contrairement au manomètre qui affiche la pression
en continu, le pressostat ne produit qu'un signal binaire : la pression est au-dessus ou
en dessous du seuil réglé. Il est raccordé directement dans la ligne de pression du
circuit hydraulique via un raccord fileté [S26]_.

4.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le pressostat du banc TDS DIDACTIC remplit deux fonctions complémentaires :

1. **Protection** : il coupe l'alimentation de la pompe ou déclenche une alarme dès
   que la pression dépasse la valeur de consigne — évitant la surpression.
2. **Séquençage automatique** : il signale à l'API qu'une pression suffisante est
   atteinte pour passer à l'étape suivante du cycle (par exemple, "pression de serrage
   atteinte → ouvrir le distributeur suivant").

4.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le fluide hydraulique sous pression agit sur un **élément de mesure** (membrane
flexible ou piston interne) qui se déforme proportionnellement à la pression. Lorsque
la déformation atteint la valeur correspondant au seuil réglé par la **vis de
réglage**, un mécanisme à bascule fait commuter le contact électrique interne [S26]_.

.. figure:: images/pressostat_structure.png
   :align: center
   :width: 50%
   :alt: Structure interne d'un pressostat électrique

   *Fig. 10 — Structure interne d'un pressostat électrique :*
   *raccord process (bas), éléments de mesure, contact et raccordement électrique (haut)*
   *(Source : WIKA)*

.. figure:: images/pressostat_fonctionnement.png
   :align: center
   :width: 65%
   :alt: Principe de fonctionnement du pressostat

   *Fig. 11 — Principe de fonctionnement du pressostat : sans pression (repos) et*
   *sous pression (seuil atteint → commutation du contact)*
   *(Source : BPMEI Prades)*

4.4 Symboles normalisés ISO 1219 [S26]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole d'un pressostat associe le symbole de mesure de pression (carré avec la
lettre **P**) à un contact électrique à commande par pression (ligne tiretée indiquant
que la commande est hydraulique).

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Variante
     - Symbole et comportement
   * - **Pressostat NF**
     - Contact fermé au repos (0 bar) ; s'ouvre quand la pression atteint le seuil réglé
   * - **Pressostat NO**
     - Contact ouvert au repos ; se ferme quand la pression atteint le seuil réglé

.. figure:: images/pressostat_nf.png
   :align: center
   :width: 25%
   :alt: Symbole pressostat NF

   *Fig. 12 — Symbole d'un pressostat normalement fermé (NF)*
   *(Source : Tameson)*

.. figure:: images/pressostat_no.png
   :align: center
   :width: 25%
   :alt: Symbole pressostat NO

   *Fig. 13 — Symbole d'un pressostat normalement ouvert (NO)*
   *(Source : Tameson)*

4.5 Connexions
~~~~~~~~~~~~~~

- **Entrée hydraulique** : raccord fileté inséré sur la ligne de pression principale
  du circuit (entre pompe et distributeur)
- **Sortie électrique** : contact TOR (NO ou NF) — raccordé à une entrée numérique
  de l'API ou à un relais de protection
- **Vis de réglage** : accessible par le haut du pressostat — tourne dans le sens
  horaire pour augmenter le seuil de déclenchement

4.6 Caractéristiques techniques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Type de mesure
     - Seuil de pression (TOR)
   * - Plage de réglage typique
     - 0 – 1,6 MPa (0 – 16 bar) sur banc TDS
   * - Connexion hydraulique
     - Raccord fileté (NPT ou BSP selon modèle)
   * - Type de sortie électrique
     - Contact sec NO/NF
   * - Nombre sur banc TDS
     - 1 unité (réf. N°24)

----

5. Manomètre
-------------

5.1 Description
~~~~~~~~~~~~~~~

Le manomètre est un instrument de **mesure analogique et visuelle** de la pression.
Il affiche en continu la pression régnant dans la ligne hydraulique à laquelle il est
raccordé, sans aucune connexion électrique. C'est l'outil de première lecture lors de
la mise en service et du réglage du circuit [S27]_.

5.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le manomètre permet à l'opérateur de :

- **Vérifier la pression de refoulement** de la pompe en temps réel
- **Surveiller les variations** de pression lors des déplacements des vérins
- **Régler le limiteur de pression** en observant la montée jusqu'au seuil voulu
- **Détecter visuellement** une anomalie (pression nulle = pas d'huile ; pression
  maximale = vérin bloqué ou clapet fermé)

5.3 Principe de fonctionnement — tube de Bourdon
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le manomètre à tube de Bourdon est le type le plus répandu en hydraulique industrielle.
Son élément sensible est un **tube incurvé de section ovale** (le tube de Bourdon),
hermétiquement fermé à son extrémité libre et raccordé à la pression à mesurer à son
extrémité fixe. Sous l'effet de la pression, ce tube tend à se redresser légèrement.
Ce déplacement, amplifié par un mécanisme de secteur cranté et de pignon, déplace
l'aiguille indicatrice sur le cadran gradué [S27]_.

La graduation du cadran est directement en bar ou en MPa, ce qui permet une lecture
directe sans conversion.

.. figure:: images/manometre_schema.png
   :align: center
   :width: 55%
   :alt: Principe du manomètre à tube de Bourdon

   *Fig. 14 — Coupe d'un manomètre à tube de Bourdon :*
   *A = aiguille, B = boîtier, C = entrée de pression, D = tube de Bourdon, E = membrane*
   *(Source : Tameson)*

5.4 Symbole normalisé ISO 1219 [S28]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole d'un manomètre est représenté par un **cercle** avec une **aiguille
inclinée** à l'intérieur et un trait vertical en bas symbolisant le raccordement
hydraulique.

.. figure:: images/manometre_symbole.png
   :align: center
   :width: 20%
   :alt: Symbole normalisé ISO 1219 du manomètre

   *Fig. 15 — Symbole normalisé ISO 1219 du manomètre*
   *(Source : Hidraoil)*

5.5 Connexions
~~~~~~~~~~~~~~

- **Entrée** : raccord fileté vissé sur une prise de pression du circuit (ligne principale
  entre pompe et distributeur)
- **Aucune connexion électrique** — instrument purement mécanique

5.6 Lecture pratique sur le banc
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Les valeurs habituellement observées lors des TPs sont :

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Situation du circuit
     - Pression typique observée
   * - Pompe démarrée, distributeur en position neutre (centre ouvert)
     - 0 à 0,5 bar (faibles pertes de charge)
   * - Vérin en mouvement (sortie de tige)
     - 2,5 à 4 bar environ (selon charge)
   * - Vérin en butée fin de course
     - Montée jusqu'au seuil du limiteur (≈ 16 bar)
   * - Vérin en rentrée de tige
     - Légèrement supérieure à la sortie (surface annulaire plus petite)

----

6. Tableau récapitulatif — tous les capteurs du banc TDS DIDACTIC
------------------------------------------------------------------

.. list-table::
   :header-rows: 1
   :widths: 22 18 15 45

   * - Capteur / Instrument
     - Grandeur
     - Signal
     - Connexion API (exemple)
   * - Fin de course NF
     - Position mécanique
     - TOR — 2 fils
     - Borne 12 → I0.0 / I0.1 (signal 1 au repos)
   * - Fin de course NO
     - Position mécanique
     - TOR — 2 fils
     - Borne 14 → I0.2 / I0.3 (signal 0 au repos)
   * - Détecteur inductif
     - Présence métal
     - TOR — 3 fils
     - BN→+24V, BU→0V, BK→I0.4 / I0.5
   * - Capteur magnétique LED
     - Position piston vérin
     - TOR — 3 fils
     - BN→+24V, BU→0V, BK→I0.6 / I0.7 / I1.0
   * - Pressostat
     - Seuil pression
     - TOR — 2 fils
     - Contact NO → I1.1
   * - Manomètre
     - Pression (affichage)
     - Aucun
     - — (lecture visuelle uniquement)

----

.. rubric:: Sources utilisées dans ce module

.. [S22] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
        Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S23] BPMEI Prades, *Détecteurs inductifs de proximité — principe, câblage et
        mise en œuvre*, ressource pédagogique, disponible en ligne :
        https://www.bpmei-prades.fr (consulté en 2024)

.. [S24] École La Mache, *Symboles des capteurs TOR : inductifs, magnétiques et
        mécaniques*, ressource pédagogique technique,
        disponible en ligne : https://www.lamache.org (consulté en 2024)

.. [S25] BPMEI Prades, *Capteurs magnétiques sur vérins — montage, réglage et
        raccordement*, ressource pédagogique, disponible en ligne :
        https://www.bpmei-prades.fr (consulté en 2024)

.. [S26] WIKA Alexander Wiegand, *Pressostats électriques — principe, sélection et
        montage*, documentation technique, disponible en ligne :
        https://www.wika.fr (consulté en 2024)

.. [S27] Tameson, *Guide des manomètres — tube de Bourdon, lecture et applications*,
        disponible en ligne : https://www.tameson.fr (consulté en 2024)

.. [S28] Hidraoil, *Symboles hydrauliques normalisés ISO 1219 — manomètre et instruments
        de mesure*, disponible en ligne : https://www.hidraoil.es (consulté en 2024)

.. [S29] OMCH, *Fins de course mécaniques — contacts NF et NO, symboles IEC 60617
        et câblage*, documentation technique,
        disponible en ligne : https://www.omch.fr (consulté en 2024)







