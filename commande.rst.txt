Automatisation et commande
==========================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Décrire le cycle de fonctionnement d'un API (lecture entrées → traitement → écriture sorties)
   - Identifier les modules d'entrées/sorties de l'API DELTA DVP et leurs connexions
   - Établir le tableau d'adressage E/S d'un circuit hydraulique simple
   - Lire et interpréter un diagramme GRAFCET d'un cycle automatique
   - Identifier le rôle des relais, relais temporisés, boutons poussoirs et voyants sur le banc
   - Expliquer le rôle du switch réseau dans la communication API ↔ PC

----

Vue d'ensemble de la couche commande
--------------------------------------

La couche commande est l'intelligence du banc TDS DIDACTIC. Elle relie les capteurs
(informations sur l'état du système) aux actionneurs (électrovannes, pompe) via un
programme logique stocké dans l'API. C'est cette couche qui transforme un simple
circuit hydraulique en un **système automatisé** capable d'exécuter des cycles
répétitifs sans intervention humaine [S30]_.

.. code-block:: text

   Capteurs & boutons                   Actionneurs & voyants
   (Fins de course, inductifs,     API     (Électrovannes 24V DC,
    magnétiques, pressostat,      DELTA     relais de puissance,
    boutons poussoirs)             DVP      voyants lumineux)
          │                         │               │
          └─── Entrées numériques ──┤               │
                                    ├── Sorties numériques ──┘
          PC (ISPSoft) ─ USB/Ethernet ─┘

----

1. Automate programmable industriel — API DELTA DVP
-----------------------------------------------------

1.1 Description
~~~~~~~~~~~~~~~

L'API DELTA DVP est un automate programmable industriel modulaire. Il constitue
l'unité centrale de traitement du banc TDS DIDACTIC. Sa conception modulaire
lui permet d'être étendu par l'ajout de modules d'entrées/sorties supplémentaires
selon les besoins du circuit à automatiser [S30]_.

.. figure:: images/api_reel.png
   :align: center
   :width: 65%
   :alt: Automate programmable industriel DELTA DVP

   *Fig. 1 — Automate programmable industriel DELTA DVP utilisé dans le système*
   *(Source : Venara Collective)*

1.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

L'API centralise la logique de commande : il reçoit les signaux de tous les capteurs
du circuit, exécute le programme de commande (Ladder ou GRAFCET), et envoie les ordres
aux électrovannes pour piloter les mouvements des vérins selon une séquence définie.

1.3 Cycle de fonctionnement de l'API [S31]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

L'API fonctionne de manière cyclique et répétitive. Chaque cycle comprend trois phases
enchaînées en permanence :

.. list-table::
   :header-rows: 1
   :widths: 10 25 65

   * - Phase
     - Nom
     - Description
   * - 1
     - **Lecture des entrées**
     - L'API lit l'état de toutes ses bornes d'entrée (capteurs, boutons) et
       mémorise leur valeur dans une zone mémoire interne appelée "image des entrées"
   * - 2
     - **Traitement du programme**
     - Le processeur exécute le programme Ladder ou GRAFCET ligne par ligne en
       utilisant l'image des entrées pour calculer l'état des sorties
   * - 3
     - **Écriture des sorties**
     - L'API applique les résultats du calcul sur ses bornes de sortie physiques,
       ce qui active ou désactive les électrovannes, relais et voyants

.. figure:: images/api_schema.png
   :align: center
   :width: 60%
   :alt: Cycle de fonctionnement de l'API

   *Fig. 2 — Cycle de fonctionnement d'un automate programmable :*
   *lecture entrées → traitement → écriture sorties (Source : Tech3Elec)*

.. note::

   La durée d'un cycle complet s'appelle le **temps de cycle** (ou scan time). Pour
   l'API DELTA DVP en application hydraulique didactique, ce temps est typiquement de
   l'ordre de 1 à 5 ms — largement suffisant pour des déplacements de vérins dont les
   vitesses sont de l'ordre de quelques cm/s.

1.4 Tableau d'adressage E/S du banc TDS DIDACTIC [S30]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le tableau ci-dessous propose un adressage type pour le câblage du banc. Les adresses
réelles dépendent du module DELTA DVP utilisé et peuvent être adaptées.

.. list-table:: Entrées numériques (I) — capteurs et commandes
   :header-rows: 1
   :widths: 15 35 50

   * - Adresse
     - Composant raccordé
     - Rôle dans le programme
   * - I0.0
     - Fin de course NF — vérin 1 avant
     - Détecte la position avant du vérin 1
   * - I0.1
     - Fin de course NF — vérin 1 arrière
     - Détecte la position arrière du vérin 1
   * - I0.2
     - Fin de course NO — vérin 2 avant
     - Détecte la position avant du vérin 2
   * - I0.3
     - Fin de course NO — vérin 2 arrière
     - Détecte la position arrière du vérin 2
   * - I0.4
     - Détecteur inductif 1
     - Détecte la présence d'une pièce métallique
   * - I0.5
     - Détecteur inductif 2
     - Détecte la présence d'une pièce métallique
   * - I0.6
     - Capteur magnétique 1 (noir)
     - Position piston vérin 1
   * - I0.7
     - Capteur magnétique 2 (noir)
     - Position piston vérin 2
   * - I1.0
     - Capteur magnétique 3 (gris)
     - Position intermédiaire du piston
   * - I1.1
     - Pressostat électrique
     - Signal quand seuil de pression atteint
   * - I1.2
     - Bouton poussoir Démarrage (NO)
     - Lance le cycle automatique
   * - I1.3
     - Bouton poussoir Arrêt (NF)
     - Arrête le cycle en cours
   * - I1.4
     - Switch (interrupteur à clé)
     - Sélection mode manuel / automatique

.. list-table:: Sorties numériques (Q) — actionneurs et voyants
   :header-rows: 1
   :widths: 15 35 50

   * - Adresse
     - Composant raccordé
     - Rôle dans le programme
   * - Q0.0
     - Électrovanne 4/2 — bobine (vérin 1 sortie)
     - Commande la sortie de tige du vérin 1
   * - Q0.1
     - Électrovanne 4/3 — bobine L1 (vérin 1)
     - Commande le sens aller du vérin 1
   * - Q0.2
     - Électrovanne 4/3 — bobine L2 (vérin 1)
     - Commande le sens retour du vérin 1
   * - Q0.3
     - Électrovanne 4/3 — bobine L1 (vérin 2)
     - Commande le sens aller du vérin 2
   * - Q0.4
     - Électrovanne 4/3 — bobine L2 (vérin 2)
     - Commande le sens retour du vérin 2
   * - Q0.5
     - Relais pompe
     - Démarre ou arrête le moteur de la pompe
   * - Q0.6
     - Voyant vert (système en marche)
     - S'allume quand le cycle est actif
   * - Q0.7
     - Voyant rouge (arrêt / défaut)
     - S'allume en cas d'arrêt ou de défaut détecté

1.5 Exemple de GRAFCET — cycle automatique simple [S31]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Voici un exemple de GRAFCET pour un cycle automatique de va-et-vient du vérin 1 :

.. code-block:: text

   ┌───────────────────────────────────┐
   │  Étape 0 — Initialisation         │  Action : Arrêt pompe, distributeur position repos
   └──────────────┬────────────────────┘
                  │ Démarrage (I1.2 = 1)
   ┌──────────────▼────────────────────┐
   │  Étape 1 — Démarrage pompe        │  Action : Q0.5 = 1 (pompe ON)
   └──────────────┬────────────────────┘
                  │ Temporisation 1 s (pression stabilisée)
   ┌──────────────▼────────────────────┐
   │  Étape 2 — Sortie tige vérin 1    │  Action : Q0.1 = 1 (bobine L1 ON → tige sort)
   └──────────────┬────────────────────┘
                  │ I0.0 = 1 (fin de course avant atteint)
   ┌──────────────▼────────────────────┐
   │  Étape 3 — Attente 2 s            │  Action : Q0.1 = 0 (bobine OFF → position tenue)
   └──────────────┬────────────────────┘
                  │ Temporisation 2 s écoulée
   ┌──────────────▼────────────────────┐
   │  Étape 4 — Rentrée tige vérin 1   │  Action : Q0.2 = 1 (bobine L2 ON → tige rentre)
   └──────────────┬────────────────────┘
                  │ I0.1 = 1 (fin de course arrière atteint)
   ┌──────────────▼────────────────────┐
   │  Étape 5 — Fin de cycle           │  Action : Q0.2 = 0 — retour étape 2 si cycle continu
   └───────────────────────────────────┘

1.6 Logiciel de programmation
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

L'API DELTA DVP se programme avec le logiciel **ISPSoft**, fourni gratuitement par Delta Electronics. La connexion entre
le PC et l'API s'effectue via le port **USB** ou **Ethernet** du banc [S32]_.

Le langage principal utilisé dans les TPs est le **Ladder** (schéma à contacts),
qui représente le programme sous forme de circuits électriques virtuels. Les blocs
fonctionnels TON (temporisation à l'enclenchement) et TOF (temporisation au
déclenchement) sont disponibles nativement dans WPLSoft.

1.7 Caractéristiques techniques [S30]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Marque / Modèle
     - Delta Electronics — gamme DVP
   * - Nombre de modules
     - 2 modules multifonction
   * - Entrées numériques
     - 8 entrées numériques capteurs
   * - Sorties numériques
     - 6 sorties relais pour électrovannes
   * - Entrées/sorties analogiques
     - 8 entrées + 4 sorties analogiques 0 – 10 V
   * - Communication PC
     - USB + Ethernet (port RJ45)
   * - Logiciel de programmation
     - ISPSoft (Delta Electronics)
   * - Langages supportés
     - Ladder, SFC (GRAFCET), FBD, IL

----

2. Modules d'entrées/sorties (I/O)
------------------------------------

2.1 Description
~~~~~~~~~~~~~~~

Les modules d'entrées/sorties sont les interfaces physiques entre le monde réel
(capteurs, actionneurs) et l'unité centrale de l'API. Ils assurent la conversion
des niveaux de tension, l'isolation galvanique et la protection des circuits
d'entrée contre les surtensions [S33]_.

.. figure:: images/io_fonctionnement.png
   :align: center
   :width: 65%
   :alt: Interface entre capteurs, API et actionneurs

   *Fig. 3 — Architecture de la couche E/S : capteurs → interface d'entrée →*
   *processeur → interface de sortie → préactionneurs (Source : Tech3Elec)*

2.2 Modules d'entrées numériques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Chaque borne d'entrée reçoit un signal TOR (0 V ou +24 V DC) depuis un capteur.
Le module d'entrée convertit ce signal en niveau logique 0 ou 1 pour le processeur.
Il assure également une **isolation optique** (optocoupleur) entre le circuit capteur
et le circuit interne de l'API — protégeant l'automate contre les perturbations
électriques du circuit hydraulique [S33]_.

2.3 Modules de sorties numériques (relais)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Sur le banc TDS DIDACTIC, les sorties sont de type **relais** : chaque sortie Qx.x
commande la bobine d'un relais interne. Lorsque la sortie est activée par le programme,
le relais se ferme et alimente la charge (bobine solénoïde de l'électrovanne ou
voyant lumineux) en **24 V DC** [S30]_.

.. warning::

   Les sorties relais du DELTA DVP supportent une charge maximale de **2 A par contact**.
   Ne jamais raccorder directement un moteur ou une charge inductive importante sans
   interposer un relais de puissance externe — le relais interne serait endommagé par
   les pics de courant au démarrage.

----

3. Relais électrique
----------------------

3.1 Description
~~~~~~~~~~~~~~~

Le relais est un composant électromécanique qui assure une **isolation galvanique**
entre le circuit de commande (faible tension, API) et le circuit de puissance
(tension et courant plus élevés pour les actionneurs). 

.. figure:: images/relais_fonctionnement.png
   :align: center
   :width: 55%
   :alt: Fonctionnement d'un relais électrique

   *Fig. 4 — Fonctionnement d'un relais électrique : bobine en repos (contacts NF fermés,*
   *NO ouverts) et bobine alimentée (contacts inversés) (Source : ElectroSchema)*

3.2 Principe de fonctionnement [S34]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Lorsque la bobine du relais reçoit une tension d'alimentation (24 V DC depuis une
sortie de l'API), elle crée un champ magnétique qui attire un armature métallique
mobile. Ce déplacement modifie simultanément l'état de tous les contacts du relais :

- Les contacts **NO** (Normalement Ouverts) **se ferment** → circuit de puissance alimenté
- Les contacts **NF** (Normalement Fermés) **s'ouvrent** → circuit de puissance coupé

Dès que la bobine est désalimentée, un ressort de rappel ramène l'armature en position
initiale et les contacts retrouvent leur état de repos.

3.3 Symboles normalisés [S34]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/relais_bobine.png
   :align: center
   :width: 22%
   :alt: Symbole de la bobine du relais

   *Fig. 5 — Symbole de la bobine du relais (bornes A1 et A2)*
   *(Source : GEYA)*

.. figure:: images/relais_contacts.png
   :align: center
   :width: 32%
   :alt: Symboles contacts NO et NF du relais

   *Fig. 6 — Symboles des contacts NO (normalement ouvert) et NF (normalement fermé)*
   *(Source : GEYA)*

3.4 Connexions
~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 20 80

   * - Borne
     - Fonction
   * - **A1**
     - Alimentation bobine (+) — raccordée à une sortie de l'API (Q0.x)
   * - **A2**
     - Alimentation bobine (−) — raccordée au 0 V commun (GND)
   * - **COM**
     - Borne commune des contacts (point de commutation)
   * - **NO**
     - Contact normalement ouvert — se ferme quand la bobine est alimentée
   * - **NF**
     - Contact normalement fermé — s'ouvre quand la bobine est alimentée

----

4. Relais temporisé
---------------------

4.1 Description
~~~~~~~~~~~~~~~

Le relais temporisé est un relais standard augmenté d'un **circuit de temporisation
intégré** à réglage mécanique (potentiomètre). Il introduit un délai réglable entre
la réception du signal de commande et la commutation de ses contacts. 

.. figure:: images/relais_temp_reel.png
   :align: center
   :width: 38%
   :alt: Relais temporisé industriel

   *Fig. 7 — Relais temporisé industriel sur rail DIN (Source : Legrand)*

4.2 Les deux types de temporisation [S35]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 20 35 45

   * - Type
     - Comportement
     - Application sur le banc
   * - **TON** — Temporisation à l'enclenchement
     - La bobine est alimentée → les contacts changent d'état après le délai T réglé
     - Attente avant de lancer le mouvement suivant (ex. : stabilisation de pression)
   * - **TOF** — Temporisation au déclenchement
     - La bobine est désalimentée → les contacts changent d'état après le délai T réglé
     - Maintien d'une action pendant T secondes après la fin de la commande

.. figure:: images/relais_temp_ton.png
   :align: center
   :width: 35%
   :alt: Symbole relais temporisé TON

   *Fig. 8 — Relais temporisé à l'enclenchement (TON)*
   *(Source : Michel All)*

.. figure:: images/relais_temp_tof.png
   :align: center
   :width: 35%
   :alt: Symbole relais temporisé TOF

   *Fig. 9 — Relais temporisé au déclenchement (TOF)*
   *(Source : Michel All)*

4.3 Connexions
~~~~~~~~~~~~~~

Identiques au relais standard :
- **A1 / A2** : alimentation bobine (+/−)
- **NO / NF** : contacts temporisés (changent d'état après le délai T)

----

5. Bouton poussoir
-------------------

5.1 Description
~~~~~~~~~~~~~~~

Le bouton poussoir est un interrupteur à actionnement manuel et à rappel automatique
par ressort. Appuyé, il change l'état de son contact ; relâché, il revient
immédiatement à son état de repos. 

5.2 Les deux types de contact [S36]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 20 35 45

   * - Type
     - Au repos
     - Quand appuyé
   * - **NO** (normalement ouvert)
     - Contact ouvert → signal à 0
     - Contact se ferme → signal à 1
   * - **NF** (normalement fermé)
     - Contact fermé → signal à 1
     - Contact s'ouvre → signal à 0

**Usage typique sur le banc :**
- Bouton **Démarrage** : NO — le signal passe de 0 à 1 pour lancer le cycle
- Bouton **Arrêt d'urgence** : NF — le signal passe de 1 à 0 pour stopper immédiatement (comportement sécurisé : une coupure de fil arrête aussi le système)

.. figure:: images/bouton_nf.png
   :align: center
   :width: 30%
   :alt: Symbole bouton poussoir NF

   *Fig. 10 — Symbole d'un bouton poussoir normalement fermé (NF)*
   *(Source : BPMEI Prades)*

.. figure:: images/bouton_no.png
   :align: center
   :width: 30%
   :alt: Symbole bouton poussoir NO

   *Fig. 11 — Symbole d'un bouton poussoir normalement ouvert (NO)*
   *(Source : BPMEI Prades)*

5.3 Connexions
~~~~~~~~~~~~~~

- **COM** : borne commune (reliée au +24 V ou au 0 V selon schéma)
- **NO** : vers entrée API — signal à 1 quand le bouton est appuyé
- **NF** : vers entrée API — signal à 0 quand le bouton est appuyé

----

6. Voyant lumineux
-------------------

6.1 Description
~~~~~~~~~~~~~~~

Le voyant lumineux est un indicateur visuel à LED qui signale l'état opérationnel
du système à l'opérateur.

6.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Les voyants transmettent en temps réel des informations sur l'état du cycle :

- **Voyant vert** : système en marche, cycle en cours
- **Voyant rouge** : arrêt, défaut détecté ou arrêt d'urgence actionné

6.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Une LED à l'intérieur du voyant s'allume dès qu'une tension de 24 V DC est appliquée
à ses bornes par la sortie de l'API. L'extinction correspond à l'absence de tension
en sortie (Q = 0).

6.4 Symbole et connexions [S36]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/voyant_symbole.png
   :align: center
   :width: 22%
   :alt: Symbole d'un voyant lumineux

   *Fig. 12 — Symbole d'un voyant lumineux (Source : Positron Libre)*

- **Entrée** : +24 V DC depuis sortie API (Q0.6 ou Q0.7)
- **Retour** : 0 V commun (GND)

----

7. Interface d'alimentation
-----------------------------

7.1 Description
~~~~~~~~~~~~~~~

L'interface d'alimentation assure la distribution et la protection de l'énergie
électrique vers tous les composants du banc. Elle reçoit le réseau 230 V AC
via un disjoncteur différentiel 30 mA (protection des personnes) et le distribue
après conversion en **24 V DC** vers les circuits de commande [S30]_.

7.2 Architecture d'alimentation [S37]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Niveau
     - Description
   * - 230 V AC — réseau
     - Alimentation principale du banc (moteur, transformateur d'alimentation)
   * - Protection réseau
     - 2× modules 230 V/16 A + 1× disjoncteur + différentiel 30 mA
   * - 24 V DC — commande
     - Alimentation de l'API, capteurs, bobines électrovannes, voyants
   * - Distribution
     - Via bornes de connexion vers API, capteurs, relais, électrovannes

.. figure:: images/alimentation.png
   :align: center
   :width: 40%
   :alt: Sources d'alimentation DC et AC

   *Fig. 13 — Symboles des sources d'alimentation : courant continu (DC) et courant*
   *alternatif (AC) (Source : PCBasic)*

.. warning::

   Ne jamais intervenir sur le câblage électrique du banc sans avoir d'abord coupé
   le disjoncteur principal et consigné le banc. La présence simultanée de 230 V AC
   (puissance) et 24 V DC (commande) impose une vigilance particulière lors du câblage.

----


9. Tableau récapitulatif — composants de la couche commande
------------------------------------------------------------

.. list-table::
   :header-rows: 1
   :widths: 25 35 40

   * - Composant
     - Référence/Marque
     - Rôle principal
   * - API DELTA DVP
     - Delta Electronics DVP
     - Unité centrale — exécute le programme Ladder/GRAFCET
   * - Modules I/O
     - DVP — 8E numériques + 6S relais
     - Interface capteurs ↔ API ↔ actionneurs
   * - Relais électrique
     - Standard 24 V DC
     - Isolation puissance / commande
   * - Relais temporisé
     - TON/TOF
     - Temporisations dans les séquences
   * - Bouton poussoir
     - NO + NF
     - Commandes manuelles opérateur
   * - Voyant lumineux
     - LED 24 V DC
     - Signalisation état du système
   * - Interface alimentation
     - 230 V AC → 24 V DC
     - Distribution et protection électrique


----

.. rubric:: Sources utilisées dans ce module

.. [S30] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
        Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S31] Tech3Elec, *Fonctionnement d'un automate programmable industriel — cycle,
        entrées/sorties et adressage*, ressource pédagogique,
        disponible en ligne : https://www.tech3elec.fr (consulté en 2024)

.. [S32] Delta Electronics, *WPLSoft — logiciel de programmation API DELTA DVP,
        guide de démarrage rapide*, documentation officielle,
        disponible en ligne : https://www.deltaww.com (consulté en 2024)

.. [S33] Tech3Elec, *Modules d'entrées/sorties des API — isolation optique et
        câblage*, ressource pédagogique,
        disponible en ligne : https://www.tech3elec.fr (consulté en 2024)

.. [S34] GEYA Electric, *Relais électromécaniques — symboles, câblage et
        caractéristiques*, documentation produit,
        disponible en ligne : https://www.geya.net (consulté en 2024)

.. [S35] Michel All (ElectroSchéma), *Relais temporisés TON et TOF — symboles
        et applications en automatisme*, ressource pédagogique,
        disponible en ligne : https://www.electroschema.fr (consulté en 2024)

.. [S36] BPMEI Prades, *Boutons poussoirs et voyants lumineux — symboles et
        câblage vers API*, ressource pédagogique,
        disponible en ligne : https://www.bpmei-prades.fr (consulté en 2024)

.. [S37] PCBasic, *Sources d'alimentation électrique DC et AC — symboles et
        protection*, documentation technique,
        disponible en ligne : https://www.pcbasic.fr (consulté en 2024)


