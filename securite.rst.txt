Organes de sécurité
===================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Identifier les trois organes de sécurité présents sur le banc TDS DIDACTIC
   - Expliquer le principe de détection d'un défaut différentiel (courant de fuite)
   - Justifier l'utilisation d'un contact NF pour l'arrêt d'urgence (logique fail-safe)
   - Décrire la procédure de réarmement après un arrêt d'urgence
   - Distinguer le rôle de chaque organe de sécurité dans la chaîne de protection du banc

----

Vue d'ensemble — chaîne de sécurité du banc TDS DIDACTIC
----------------------------------------------------------

La sécurité d'un banc électro-hydraulique repose sur plusieurs niveaux de protection
complémentaires. Sur le banc TDS DIDACTIC, trois organes assurent cette protection,
organisés en deux couches distinctes [S46]_ :

.. list-table:: Organes de sécurité du banc TDS DIDACTIC
   :header-rows: 1
   :widths: 25 20 55

   * - Composant
     - Couche
     - Rôle principal
   * - Disjoncteur différentiel 30 mA
     - Protection électrique
     - Détecte les fuites de courant vers la terre — protège les personnes
   * - Interrupteur à clé
     - Contrôle d'accès
     - Empêche toute mise en marche non autorisée du banc
   * - Arrêt d'urgence (coup de poing)
     - Arrêt d'urgence
     - Coupe immédiatement toute la commande en cas de danger

.. warning::

   **Procédure obligatoire avant toute manipulation sur le banc :**

   1. Vérifier que l'interrupteur à clé est en position **OFF**
   2. Vérifier que l'arrêt d'urgence n'est **pas enfoncé** (tiré / déverrouillé)
   3. Vérifier que le disjoncteur différentiel est en position **ON**
   4. S'assurer qu'aucune fuite d'huile n'est visible sur le circuit hydraulique
   5. Mettre les **EPI** (lunettes, gants résistants aux huiles)
   6. Tourner la clé en position **ON** pour autoriser la mise sous tension

----

1. Disjoncteur différentiel
-----------------------------

1.1 Description
~~~~~~~~~~~~~~~

Le disjoncteur différentiel est un dispositif de protection électrique installé dans
le tableau de distribution du banc. Il assure simultanément deux fonctions : la
protection des **personnes** contre l'électrocution (via la détection différentielle)
et la protection de l'**installation** contre les surcharges et courts-circuits
(via le mécanisme disjoncteur) [S47]_.

Sur le banc TDS DIDACTIC, le différentiel est calibré à **30 mA** et le disjoncteur
à **16 A** (réf. fiche technique : 1× disjoncteur + différentiel 30 mA).

.. figure:: images/disjoncteur_schema.png
   :align: center
   :width: 60%
   :alt: Schéma de principe du disjoncteur différentiel

   *Fig. 1 — Schéma de principe du fonctionnement du disjoncteur différentiel*
   *(Source : Ekwateur)*

1.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le disjoncteur différentiel protège contre quatre types de dangers [S47]_ :

- **Électrocution par contact indirect** : si une personne touche une pièce
  métallique sous tension (défaut d'isolement), un courant de fuite apparaît
  vers la terre — le différentiel coupe en moins de 30 ms.
- **Électrocution par contact direct** : si le courant de fuite dépasse 30 mA
  (seuil de fibrillation cardiaque), le déclenchement est quasi instantané.
- **Surcharge** : si le courant dépasse 16 A (moteur bloqué, court-circuit
  partiel), le disjoncteur thermique déclenche.
- **Court-circuit franc** : le déclenchement magnétique est immédiat.

1.3 Principe de fonctionnement [S47]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le différentiel surveille en permanence la différence entre le courant entrant
par la phase (L) et le courant sortant par le neutre (N). En fonctionnement
normal, ces deux courants sont rigoureusement égaux : toute l'énergie qui entre
par la phase ressort par le neutre.

En cas de défaut d'isolement (fil dénudé touchant le boîtier métallique du moteur
par exemple), une fraction du courant s'écoule vers la terre via le conducteur PE
au lieu de revenir par le neutre. Il apparaît alors une différence — appelée
**courant différentiel** ou **courant de défaut** — entre I(phase) et I(neutre).
Lorsque cette différence dépasse **30 mA**, un tore magnétique interne détecte le
déséquilibre et déclenche le mécanisme de coupure en moins de **30 ms** [S47]_.

1.4 Symbole normalisé [S48]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/disjoncteur_symbole.png
   :align: center
   :width: 30%
   :alt: Symbole simplifié du disjoncteur différentiel

   *Fig. 2 — Symbole simplifié du disjoncteur différentiel :*
   *partie interrupteur (haut) + partie différentielle (bas) (Source : Cabanis Brive)*

1.5 Connexions
~~~~~~~~~~~~~~

Installé **en amont** de tout le circuit électrique du banc :

- **L** (Phase) : entrée depuis le réseau 230 V AC
- **N** (Neutre) : retour vers le réseau
- **PE** (Terre) : conducteur de protection vers la barrette de terre du banc

.. note::

   Après un déclenchement différentiel, il faut **identifier et éliminer la cause
   du défaut** avant de réenclencher le disjoncteur. Ne jamais réenclencher
   directement sans rechercher la fuite de courant — le défaut peut persister
   et représenter un danger immédiat.

----

2. Interrupteur à clé
-----------------------

2.1 Description
~~~~~~~~~~~~~~~

L'interrupteur à clé est un interrupteur rotatif dont l'actionnement est conditionné
par l'insertion d'une **clé physique amovible**. Sans la clé, le contact reste dans
sa dernière position et ne peut pas être modifié. 

.. figure:: images/interrupteur_cle_reel.png
   :align: center
   :width: 40%
   :alt: Interrupteur à clé

   *Fig. 3 — Interrupteur à clé utilisé pour la commande sécurisée du banc*
   *(Source : RS Components)*

2.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

L'interrupteur à clé remplit trois fonctions de sécurité complémentaires sur le banc :

1. **Contrôle d'accès** : seule la personne en possession de la clé peut mettre le
   banc sous tension — empêche toute utilisation non autorisée par des personnes
   non formées.
2. **Consignation pédagogique** : en retirant la clé, l'enseignant peut interdire
   physiquement la mise en marche pendant l'explication d'une procédure de câblage,
   garantissant que le banc ne sera pas mis sous tension accidentellement.
3. **Arrêt sécurisé** : en position OFF avec retrait de la clé, le banc est consigné
   — aucune action involontaire ne peut le remettre en marche.

2.3 Principe de fonctionnement [S49]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

L'interrupteur à clé fonctionne comme un interrupteur rotatif ordinaire, mais le
mécanisme de rotation est verrouillé mécaniquement en l'absence de la clé. La clé
s'insère dans le barillet, se tourne (généralement de 0° à 90°) et entraîne un
disque de came qui fait basculer les contacts internes. La clé peut être retirée
uniquement dans certaines positions (selon le modèle : position OFF uniquement,
ou dans toutes les positions).

2.4 Symbole normalisé [S48]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/interrupteur_cle_symbole.png
   :align: center
   :width: 30%
   :alt: Symbole électrique de l'interrupteur à clé

   *Fig. 4 — Symbole électrique d'un interrupteur à clé (contact NO bornes 13-14)*
   *(Source : Maxicours)*

2.5 Connexions
~~~~~~~~~~~~~~

Câblé **en série** dans le circuit de commande 24 V DC, en aval du disjoncteur
différentiel et en amont de l'API :

- **Position ON** (clé tournée) : contact fermé → circuit de commande alimenté
- **Position OFF** (clé à la position initiale) : contact ouvert → toute commande impossible
- **Bornes 13-14** : contact NO (normalement ouvert) — s'utilise avec une logique
  positive (le banc ne fonctionne QUE si la clé est insérée et tournée)

----

3. Arrêt d'urgence
--------------------

3.1 Description
~~~~~~~~~~~~~~~

L'arrêt d'urgence (AU) est un bouton-poussoir à **accrochage mécanique** — une fois
enfoncé, il reste verrouillé en position ouverte jusqu'à un déverrouillage manuel
intentionnel (rotation du bouton dans le sens de la flèche gravée, ou tirage selon
le modèle). Il est normalement fermé (NF) et est reconnaissable à son **champignon
rouge sur fond jaune**, conformément à la norme EN ISO 13850 [S50]_.


3.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

L'arrêt d'urgence coupe **immédiatement et physiquement** l'alimentation du circuit
de commande, ce qui provoque la désexcitation de toutes les bobines d'électrovannes
et l'arrêt du moteur de la pompe. Son action est indépendante de l'API — même si
l'automate est en défaut ou en cours d'exécution d'un programme, l'AU l'emporte [S50]_.

3.3 Principe de fonctionnement [S50]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le bouton d'arrêt d'urgence utilise un **contact normalement fermé (NF)** câblé en
série dans le circuit de commande principale. En fonctionnement normal, le contact
est fermé et le circuit de commande est alimenté. Lorsque l'opérateur appuie sur
le champignon, le mécanisme à came force l'ouverture du contact NF, coupant
instantanément toute la commande.

Le système **reste arrêté** tant que le bouton n'a pas été déverrouillé manuellement
— il est impossible de remettre en marche sans action volontaire de l'opérateur.
C'est ce qu'on appelle la fonction **LOTO** (Lock Out / Tag Out) au niveau du bouton.

.. figure:: images/arret_urgence_schema.png
   :align: center
   :width: 65%
   :alt: Schéma de commande avec arrêt d'urgence

   *Fig. 5 — Schéma de commande d'un moteur avec arrêt d'urgence (NF) et bouton de marche (NO)*
   *(Source : Sitelec)*

3.4 Pourquoi le contact NF est obligatoire [S51]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

L'arrêt d'urgence doit impérativement utiliser un contact **NF** (et non NO) pour
deux raisons de sécurité fondamentales :

1. **Rupture de fil = arrêt** : si le câble reliant l'AU à l'API est sectionné
   (usure, rongement, arrachement), le signal passe de 1 à 0 — l'API interprète
   cela comme un arrêt d'urgence et coupe la commande. Avec un contact NO,
   une rupture de fil passerait inaperçue.
2. **Conformité normative** : la norme EN ISO 13850 (Sécurité des machines —
   Arrêt d'urgence) impose que les circuits d'arrêt d'urgence utilisent des
   contacts à ouverture forcée et une logique NF.

3.5 Procédure de réarmement [S50]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Après un arrêt d'urgence, la procédure de réarmement est la suivante :

1. **Identifier** la cause de l'arrêt d'urgence (danger résolu ?)
2. **Déverrouiller** le bouton AU : le tourner dans le sens de la flèche jusqu'au déclic
3. **Vérifier** visuellement que le circuit hydraulique et électrique est en état sûr
4. **Appuyer** sur le bouton de remise en marche (Démarrage) pour relancer le cycle

.. warning::

   Ne jamais déverrouiller l'arrêt d'urgence sans avoir identifié et éliminé la cause
   du déclenchement. Le réarmement sans diagnostic préalable peut exposer les
   personnes au même danger qui a provoqué l'arrêt initial.

3.6 Symbole normalisé [S48]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/arret_urgence_symbole.png
   :align: center
   :width: 25%
   :alt: Symbole d'un bouton d'arrêt d'urgence NF

   *Fig. 6 — Symbole d'un bouton d'arrêt d'urgence (contact NF à ouverture forcée)*
   *(Source : Omega Composants)*

3.7 Connexions
~~~~~~~~~~~~~~

Câblé **en série** dans le circuit de commande principal, en aval de l'interrupteur
à clé et en amont de l'API :

- **Contact NF** : fermé au repos, s'ouvre à l'appui
- **Câblage en série** avec tous les autres dispositifs d'arrêt d'urgence
  (si plusieurs AU sont présents)
- L'ouverture du contact coupe l'alimentation 24 V DC vers l'API et les bobines

----

4. Architecture complète de la chaîne de sécurité
---------------------------------------------------

.. code-block:: text

   Réseau 230 V AC
         │
   ┌─────▼──────────────────────────────────┐
   │  Disjoncteur différentiel 30 mA / 16 A │  ← Coupe si fuite > 30 mA ou surcharge > 16 A
   └─────┬──────────────────────────────────┘
         │  230 V AC
   ┌─────▼──────────────┐
   │  Alimentation 24 V │  → convertit 230 V AC en 24 V DC
   └─────┬──────────────┘
         │  24 V DC
   ┌─────▼────────────────────┐
   │  Interrupteur à clé (NO) │  ← Ouvert si clé retirée ou en position OFF
   └─────┬────────────────────┘
         │  24 V DC (si clé ON)
   ┌─────▼───────────────────────────┐
   │  Arrêt d'urgence (NF)           │  ← S'ouvre si bouton enfoncé
   └─────┬───────────────────────────┘
         │  24 V DC (si AU non enfoncé)
   ┌─────▼────────────────────────────────────────────────────┐
   │  API DELTA DVP + Bobines électrovannes + Moteur pompe    │
   └──────────────────────────────────────────────────────────┘

**Lecture de la chaîne :** pour que le banc fonctionne, les trois organes de sécurité
doivent être simultanément en état normal — disjoncteur enclenché, clé en position ON,
arrêt d'urgence déverrouillé. L'ouverture de l'un d'eux suffit à couper toute la commande.

----

.. rubric:: Sources utilisées dans ce module

.. [S46] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
         Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S47] Ekwateur, *Disjoncteur différentiel — principe de fonctionnement et protection
         des personnes*, disponible en ligne : https://www.ekwateur.fr (consulté en 2024)

.. [S48] Maxicours, *Symboles électriques normalisés — disjoncteur, interrupteur à clé
         et arrêt d'urgence*, ressource pédagogique,
         disponible en ligne : https://www.maxicours.com (consulté en 2024)

.. [S49] RS Components, *Interrupteurs à clé industriels — sélection et câblage*,
         documentation produit, disponible en ligne : https://www.rs-online.com
         (consulté en 2024)

.. [S50] Omega Composants, *Arrêts d'urgence — norme EN ISO 13850, contact NF,
         réarmement et câblage*, documentation technique,
         disponible en ligne : https://www.omega-composants.fr (consulté en 2024)

.. [S51] EN ISO 13850:2015, *Sécurité des machines — Fonction d'arrêt d'urgence —
         Principes de conception*, Organisation internationale de normalisation,
         Genève, 2015.