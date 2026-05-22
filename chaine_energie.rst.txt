Chaîne d'énergie
================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Décrire la structure de la chaîne d'énergie d'un système électro-hydraulique
   - Identifier le rôle de chaque composant : moteur, pompe et réservoir
   - Expliquer comment l'énergie électrique est convertie en énergie hydraulique
   - Lire les symboles normalisés ISO 1219 de la pompe, du moteur et du réservoir
   - Citer les caractéristiques techniques du banc TDS DIDACTIC relatives à la chaîne d'énergie

----

Vue d'ensemble de la chaîne d'énergie
---------------------------------------

Dans un système électro-hydraulique, l'énergie suit un chemin précis avant d'atteindre
les actionneurs. Ce chemin s'appelle la **chaîne d'énergie**. Elle regroupe l'ensemble des
composants qui produisent, transmettent et transforment l'énergie depuis la source
électrique jusqu'au fluide hydraulique sous pression.

Sur le banc TDS DIDACTIC, cette chaîne comprend trois éléments principaux, agencés
dans l'ordre suivant [S1]_ :

.. code-block:: text

   Réseau électrique
         │
         ▼
   Moteur électrique asynchrone (400 W – 1500 tr/min)
   + Variateur de vitesse 
         │  liaison mécanique (arbre)
         ▼
   Pompe hydraulique à engrenages externes
   (débit : 10 L/min – pression max : 1,6 MPa)
         │  huile sous pression
         ▼
   Circuit hydraulique → Distributeurs → Actionneurs

.. note::

   Le variateur de vitesse permet d'ajuster la vitesse de rotation du moteur, ce qui
   modifie directement le débit d'huile fourni par la pompe et donc la vitesse de
   déplacement des vérins.

----

1. Moteur électrique asynchrone avec variateur de vitesse
----------------------------------------------------------

1.1 Description
~~~~~~~~~~~~~~~

Le groupe moteur-variateur est le point d'entrée de la chaîne d'énergie. Il s'agit d'un
moteur asynchrone triphasé d'une puissance de **400 W** et d'une vitesse nominale de
**1 500 tr/min**, couplé à un variateur de vitesse.
Ce type de moteur est très répandu dans l'industrie en raison de sa robustesse, de son
faible coût d'entretien et de sa capacité à fonctionner en continu sous charge [S2]_.

.. figure:: images/moteur_variateur.png
   :align: center
   :width: 65%
   :alt: Moteur asynchrone triphasé et variateur de vitesse Siemens SINAMICS

   *Fig. 1 — Moteur asynchrone triphasé associé au variateur de vitesse Siemens SINAMICS*
   *(Source : Automation Sense)*

1.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le moteur a pour mission de fournir l'énergie mécanique de rotation nécessaire à
l'entraînement de la pompe hydraulique. Le variateur de vitesse, placé entre le réseau
et le moteur, permet de régler la fréquence d'alimentation et donc la vitesse de
rotation. En faisant varier cette vitesse, on contrôle indirectement le débit d'huile
produit par la pompe et, par extension, la rapidité des mouvements des vérins.

1.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Un moteur asynchrone fonctionne grâce à l'interaction entre le champ magnétique
tournant créé par le stator et les courants induits dans le rotor. Cette interaction
produit un couple mécanique qui entraîne l'arbre en rotation. Le décalage de vitesse
entre le champ statorique et le rotor — appelé **glissement** — est à l'origine de la
force motrice.

Le variateur de vitesse intervient en modifiant la fréquence et l'amplitude de la
tension alternative fournie au moteur [S3]_. Il est composé de trois étages :

- **Redresseur** : convertit la tension alternative du réseau en tension continue
- **Filtre** : lisse la tension continue pour limiter les ondulations
- **Onduleur** : reconvertit la tension continue en tension alternative de fréquence
  réglable, permettant de contrôler la vitesse du moteur

.. figure:: images/variateur_schema.png
   :align: center
   :width: 60%
   :alt: Schéma de principe du variateur de vitesse

   *Fig. 2 — Principe de fonctionnement d'un variateur de vitesse (redresseur, filtre, onduleur)*
   *(Source : ABC CLIM)*

1.4 Structure interne du moteur
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Un moteur asynchrone est constitué des éléments suivants [S4]_ :

.. list-table::
   :header-rows: 1
   :widths: 20 80

   * - Élément
     - Rôle
   * - Stator
     - Partie fixe portant les bobinages alimentés par le réseau triphasé ; crée le champ magnétique tournant
   * - Rotor bobiné (ou à cage)
     - Partie tournante ; les courants induits y créent une force qui le met en rotation
   * - Roulements
     - Supportent mécaniquement l'arbre en rotation et réduisent les frottements
   * - Ventilateur
     - Assure le refroidissement du moteur par circulation d'air forcé
   * - Capot de ventilation
     - Protège le ventilateur et canalise le flux d'air

.. figure:: images/moteur_structure.png
   :align: center
   :width: 65%
   :alt: Constitution interne d'un moteur asynchrone

   *Fig. 3 — Constitution interne d'un moteur asynchrone triphasé*
   *(Source : P&M)*

1.5 Symboles normalisés (ISO 1219 / IEC 60617) [S6]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Composant
     - Symbole
   * - Moteur électrique (symbole ISO / IEC)
     - Cercle avec la lettre M à l'intérieur et un arbre sortant (Fig. 4)
   * - Variateur de vitesse (symbole électrique)
     - Rectangle traversé d'une flèche en diagonale sur fond de symbole alternatif (Fig. 5)

.. figure:: images/moteur.png
   :align: center
   :width: 25%
   :alt: Symbole normalisé du moteur électrique

   *Fig. 4 — Symbole normalisé du moteur électrique (ISO / IEC 60617)*
   *(Source : Hidraoil)*

.. figure:: images/variateur.png
   :align: center
   :width: 25%
   :alt: Symbole normalisé du variateur de vitesse

   *Fig. 5 — Symbole normalisé du variateur de vitesse*
   *(Source : Electrotoile)* [S9]_

1.6 Connexions
~~~~~~~~~~~~~~

- **Entrée électrique** : réseau triphasé 230/400 V – 50 Hz
- **Sortie mécanique** : arbre de rotation solidaire de l'axe de la pompe hydraulique

1.7 Caractéristiques techniques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Type de moteur
     - Asynchrone triphasé
   * - Puissance nominale
     - 400 W
   * - Vitesse nominale
     - 1 500 tr/min
   * - Variateur de vitesse
     - Siemens SINAMICS (réglage fréquence 0–50 Hz)
   * - Alimentation
     - 230 / 400 V AC – 50 Hz

----

2. Pompe hydraulique à engrenages externes
-------------------------------------------

2.1 Description
~~~~~~~~~~~~~~~

La pompe hydraulique à engrenages externes est une **pompe volumétrique**. Ce qualificatif
signifie qu'elle déplace le fluide par variation de volume interne, indépendamment de la
pression en aval. Elle est entraînée directement par le moteur électrique via
l'accouplement mécanique de l'arbre. Sa fonction est de transformer l'énergie mécanique
de rotation reçue du moteur en énergie hydraulique sous forme de débit et de pression.

2.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

La pompe est le cœur de la chaîne d'énergie hydraulique. Elle aspire l'huile stockée
dans le réservoir et la refoule sous pression vers le circuit hydraulique. Sans la pompe,
aucun mouvement des actionneurs n'est possible, car ce sont la pression et le débit
qu'elle génère qui alimentent les distributeurs et les vérins.

2.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le corps de la pompe contient deux engrenages en prise directe, l'un menant (lié à
l'arbre moteur) et l'autre mené. Lors de la rotation, les dents des engrenages se
dégagent côté aspiration, créant une dépression qui attire l'huile depuis le réservoir.
Le fluide est ensuite emprisonné dans l'espace entre les dents et le carter, et transporté
en arc de cercle jusqu'au côté refoulement. Là, les dents se ré-engrènent et compriment
le fluide, qui est alors expulsé sous pression vers le circuit.

Ce cycle se répète en continu à chaque tour d'engrenage, produisant un débit pratiquement
constant pour une vitesse de rotation donnée [S5]_.

.. figure:: images/schema_pompe.png
   :align: center
   :width: 70%
   :alt: Schéma de fonctionnement d'une pompe à engrenages

   *Fig. 6 — Schéma de fonctionnement d'une pompe à engrenages (phases aspiration, transport, refoulement)*
   *(Source : Savree)*

.. note::

   **Relation débit-vitesse :** le débit Q fourni par une pompe volumétrique est
   directement proportionnel à sa vitesse de rotation n et à sa cylindrée (volume
   déplacé par tour) :

   .. math::

      Q = C_v \times n \times \eta_v

   où :

   - :math:`Q` = débit (L/min)
   - :math:`C_v` = cylindrée (cm³/tr)
   - :math:`n` = vitesse de rotation (tr/min)
   - :math:`\eta_v` = rendement volumétrique (sans unité, ≤ 1)

   C'est pourquoi le variateur de vitesse permet indirectement de contrôler le débit.

2.4 Symbole normalisé ISO 1219 [S10]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole d'une pompe hydraulique à déplacement fixe unidirectionnelle est représenté
par un **cercle** avec une **flèche pleine** orientée vers l'extérieur (indiquant le sens
du débit), et deux traits représentant les orifices d'aspiration et de refoulement.

.. figure:: images/symbole_pompe.png
   :align: center
   :width: 22%
   :alt: Symbole normalisé ISO 1219 d'une pompe hydraulique à déplacement fixe

   *Fig. 7 — Symbole normalisé ISO 1219 d'une pompe hydraulique à déplacement fixe unidirectionnelle*
   *(Source : Hidraoil)*

2.5 Connexions
~~~~~~~~~~~~~~

- **Entrée (aspiration)** : reliée au réservoir d'huile principal par une conduite flexible
- **Sortie (refoulement)** : reliée à la ligne de pression principale vers les distributeurs

2.6 Caractéristiques techniques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Type
     - Pompe volumétrique à engrenages externes
   * - Débit nominal
     - 10 L/min
   * - Pression maximale de service
     - 1,6 MPa (≈ 16 bar)
   * - Sens de rotation
     - Unidirectionnel (fixé par le moteur)
   * - Fluide utilisé
     - Huile hydraulique minérale (ISO VG 46 recommandé)

.. warning::

   La pression de 1,6 MPa est la **pression maximale admissible** sur ce banc.
   Ne jamais bloquer le circuit sans limiteur de pression correctement réglé —
   la montée en pression non contrôlée peut endommager les composants ou
   provoquer une rupture de flexible.

----

3. Réservoir d'huile hydraulique principal
-------------------------------------------

3.1 Description
~~~~~~~~~~~~~~~

Le réservoir hydraulique est une cuve métallique fermée qui contient le volume d'huile
nécessaire au fonctionnement du circuit [S8]_. Il joue plusieurs rôles simultanément : stockage
du fluide, séparation de l'air dissous, décantation des impuretés et dissipation de la
chaleur générée par le fonctionnement du système.

.. figure:: images/reservoir_reel.png
   :align: center
   :width: 50%
   :alt: Réservoir hydraulique réel

   *Fig. 8 — Réservoir hydraulique réel avec jauge de niveau et bouchon de remplissage*
   *(Source : CMS Constructeur)*

3.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le réservoir remplit quatre fonctions essentielles dans le circuit hydraulique :

1. **Stockage** : il contient le volume total d'huile disponible pour l'alimentation
   du circuit.
2. **Refroidissement** : les parois métalliques de la cuve dissipent la chaleur
   produite par les pertes de charge et le frottement dans le circuit.
3. **Décantation** : en ralentissant la circulation de l'huile à l'intérieur de la
   cuve, il permet aux particules solides de se déposer au fond.
4. **Dégazage** : l'huile de retour, qui peut contenir de l'air dissous sous forme de
   microbulles, se dégage naturellement à la surface libre du réservoir.

3.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le circuit hydraulique fonctionne en boucle fermée du point de vue du fluide :
la pompe aspire l'huile dans le réservoir via la conduite d'aspiration, l'envoie
sous pression dans le circuit, puis l'huile revient au réservoir par la conduite de
retour après avoir traversé les distributeurs et les actionneurs.

À l'intérieur du réservoir, une cloison de déflecteur sépare les orifices d'aspiration
et de retour [S7]_. Cette disposition force l'huile de retour à parcourir un chemin plus long
avant d'être à nouveau aspirée, lui laissant ainsi le temps de se refroidir, de
décanter et de se dégazer.

.. figure:: images/schema_reservoir.png
   :align: center
   :width: 60%
   :alt: Schéma de fonctionnement du réservoir hydraulique

   *Fig. 9 — Schéma de fonctionnement du réservoir hydraulique (aspiration, retour, drain)*
   *(Source : Experts Insitu)*

3.4 Symbole normalisé ISO 1219 [S6]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le réservoir hydraulique est représenté par **trois traits verticaux parallèles**
posés sur une ligne horizontale, symbolisant la surface libre du liquide et les parois
de la cuve.

.. figure:: images/symbole_reservoir.png
   :align: center
   :width: 18%
   :alt: Symbole normalisé ISO 1219 du réservoir hydraulique

   *Fig. 10 — Symbole normalisé ISO 1219 du réservoir hydraulique*
   *(Source : Hidraoil)*

3.5 Connexions
~~~~~~~~~~~~~~

- **Sortie (aspiration)** : reliée à l'entrée de la pompe hydraulique
- **Entrée (retour)** : reçoit l'huile de retour depuis les actionneurs et distributeurs
- **Orifice de remplissage / évent** : bouchon fileté avec filtre, permettant d'ajouter
  de l'huile et d'équilibrer la pression atmosphérique
- **Jauge de niveau** : indicateur visuel du volume d'huile dans la cuve

----

4. Réservoir auxiliaire
------------------------

4.1 Description et rôle
~~~~~~~~~~~~~~~~~~~~~~~~

Le banc TDS DIDACTIC est équipé d'un **réservoir auxiliaire** en complément du réservoir
principal. Ce réservoir secondaire sert à augmenter la capacité totale de stockage de
l'huile, à compenser les variations de volume dues à la dilatation thermique du fluide
et à garantir une alimentation stable du circuit lors de cycles prolongés.

4.2 Fonctionnement
~~~~~~~~~~~~~~~~~~

L'huile du réservoir auxiliaire peut rejoindre le circuit principal selon les besoins
ou recevoir l'excédent d'huile de retour lorsque le niveau du réservoir principal est
trop élevé. Les deux réservoirs sont reliés par une conduite de compensation qui
s'équilibre automatiquement par gravité.

4.3 Connexions
~~~~~~~~~~~~~~

- **Entrée** : retour d'huile ou excédent depuis le circuit
- **Sortie** : vers le circuit principal ou la conduite d'aspiration de la pompe

----

5. Bilan de la chaîne d'énergie — tableau récapitulatif
---------------------------------------------------------

.. list-table:: Récapitulatif des composants de la chaîne d'énergie
   :header-rows: 1
   :widths: 20 25 30 25

   * - Composant
     - Énergie en entrée
     - Énergie en sortie
     - Paramètres clés (banc TDS)
   * - Moteur électrique
     - Électrique (230/400 V AC)
     - Mécanique (couple, rotation)
     - 400 W – 1 500 tr/min
   * - Variateur de vitesse
     - Électrique (fréquence fixe)
     - Électrique (fréquence variable)
     - 0 – 50 Hz réglable
   * - Pompe à engrenages
     - Mécanique (rotation)
     - Hydraulique (débit + pression)
     - 10 L/min – 1,6 MPa max
   * - Réservoir principal
     - Hydraulique (retour)
     - Hydraulique (aspiration)
     - Stockage, refroidissement, décantation
   * - Réservoir auxiliaire
     - Hydraulique (excédent)
     - Hydraulique (appoint)
     - Compensation de volume

----

.. rubric:: Sources utilisées dans ce module

.. [S1] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
        Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S2] Automation Sense, *Moteur asynchrone triphasé et variateur de vitesse — principes
        et applications*, disponible en ligne : https://www.automationsense.fr
        (consulté en 2024)

.. [S3] ABC CLIM, *Principe de fonctionnement d'un variateur de fréquence*,
        disponible en ligne : https://www.abcclim.net
        (consulté en 2024)

.. [S4] P&M, *Constitution interne d'un moteur asynchrone triphasé*,
        disponible en ligne : https://www.pm-moteurs.fr
        (consulté en 2024)

.. [S5] Savree, *Gear pump — how it works*, animation pédagogique,
        disponible en ligne : https://www.savree.com
        (consulté en 2024)

.. [S6] Hidraoil, *Symboles hydrauliques normalisés ISO 1219 — pompe, moteur, réservoir*,
        disponible en ligne : https://www.hidraoil.es
        (consulté en 2024)

.. [S7] Experts Insitu, *Circuit hydraulique : rôle et fonctionnement du réservoir*,
        disponible en ligne : https://www.experts-insitu.fr
        (consulté en 2024)

.. [S8] CMS Constructeur, *Réservoirs hydrauliques industriels — caractéristiques et montage*,
        disponible en ligne : https://www.cms-hydraulique.fr
        (consulté en 2024)

.. [S9] Electrotoile, *Symboles électriques des variateurs de vitesse*,
        disponible en ligne : https://www.electrotoile.eu
        (consulté en 2024)

.. [S10] ISO 1219-1:2012, *Transmissions hydrauliques et pneumatiques — Symboles
         graphiques et schémas de circuits*, Organisation internationale de normalisation,
         Genève, 2012.




