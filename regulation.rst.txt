Organes de régulation
=====================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Distinguer les organes de régulation de pression des organes de régulation de débit
   - Expliquer la différence entre un limiteur de pression à action directe et un limiteur piloté
   - Comprendre pourquoi le limiteur de pression et la soupape de décharge sont le même composant
   - Identifier le réducteur de pression et expliquer son action sur la pression aval
   - Comparer la vanne d'étranglement et la vanne de régulation de vitesse
   - Expliquer le principe de fonctionnement d'une vanne séquentielle
   - Retrouver sur le banc TDS DIDACTIC chaque composant et sa quantité

----

Vue d'ensemble
--------------

Les organes de régulation se divisent en deux catégories selon la grandeur qu'ils
contrôlent [S39]_ :

.. list-table:: Classification des organes de régulation
   :header-rows: 1
   :widths: 30 35 35

   * - Catégorie
     - Composants
     - Grandeur contrôlée
   * - **Régulation de pression**
     - Limiteur, limiteur piloté, soupape de décharge, réducteur
     - Pression (MPa / bar)
   * - **Régulation de débit**
     - Vanne d'étranglement, vanne de régulation de vitesse, vanne séquentielle
     - Débit (L/min) → vitesse des vérins

.. list-table:: Organes de régulation présents sur le banc TDS DIDACTIC
   :header-rows: 1
   :widths: 50 50 

   * - Désignation
     - Rôle principal
   * - Soupape de décharge (= limiteur pression direct)
     - Protection anti-surpression du circuit
   * - Vanne de régulation (étrangleur)
     - Réglage du débit / vitesse
   * - Vanne de régulation de vitesse
     - Contrôle vitesse vérin (étranglement + clapet)
   * - Vanne séquentielle
     - Enchaînement automatique de mouvements
   * - Réducteur de pression
     - Pression réduite dans une branche du circuit
   * - Limiteur de pression piloté (modifié)
     - Limitation précise haute pression

----

.. rubric:: Clarification importante — limiteur de pression et soupape de décharge

.. note::

   **Le limiteur de pression à action directe et la soupape de décharge sont le même
   composant physique**, nommé différemment selon le contexte d'utilisation [S39]_ :

   - Quand il est réglé en permanence pour **plafonner** la pression maximale du circuit
     (protection générale de la pompe) → on l'appelle **limiteur de pression**
   - Quand il est placé pour **évacuer** l'excès de pression lors d'un pic ponctuel
     (protection contre surpression accidentelle) → on l'appelle **soupape de décharge**

   Dans les deux cas, la construction est identique : un clapet conique ou à bille maintenu
   fermé par un ressort de tarage réglable.

----

PARTIE 1 — Régulation de pression
-----------------------------------

1. Limiteur de pression à action directe (= soupape de décharge)
-----------------------------------------------------------------

1.1 Description
~~~~~~~~~~~~~~~

Le limiteur de pression à action directe est un organe de sécurité normalement fermé,
monté en dérivation à la sortie de la pompe. Sa construction est simple : un clapet
conique (ou à bille) est maintenu appliqué sur son siège par un ressort dont la tension
est réglable par une vis de tarage. Il détermine la pression maximale admissible dans
le circuit [S39]_.


1.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le limiteur de pression garantit que la pression dans le circuit ne dépasse jamais la
valeur de tarage réglée. Cela protège simultanément la pompe (qui ne peut pas dépasser
sa pression maximale sans risque de casse), les vérins, les distributeurs et les flexibles.
Sans ce composant, tout blocage d'un actionneur entraînerait une montée de pression
sans limite, pouvant aboutir à une rupture de flexible ou à la destruction de la pompe.

1.3 Principe de fonctionnement [S40]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

En fonctionnement normal, la pression du circuit est inférieure à la force du ressort.
Le clapet reste fermé et tout le débit de la pompe alimente les actionneurs. Lorsqu'un
actionneur est bloqué ou que la charge dépasse la consigne, la pression monte dans le
circuit. Dès qu'elle égale la force exercée par le ressort de tarage, le clapet s'écarte
de son siège, ouvrant un passage direct de la ligne de pression vers le réservoir.
L'excès d'huile est alors évacué, maintenant la pression stable à la valeur de tarage.
Dès que la pression redescend, le ressort referme automatiquement le clapet.

.. figure:: images/limiteur_schema.png
   :align: center
   :width: 65%
   :alt: Schéma de fonctionnement du limiteur de pression

   *Fig. 1 — Schéma de fonctionnement du limiteur de pression :*
   *clapet (vert), ressort de tarage, vis de réglage (Source : Wikipédia)*

.. warning::

   Sur le banc TDS DIDACTIC, la **pression maximale de tarage est de 1,6 MPa (16 bar)**.
   Ne jamais dépasser cette valeur lors du réglage — au-delà, les flexibles et raccords
   du banc risquent une rupture. Toujours régler le limiteur en montant progressivement
   la pression depuis 0, en observant le manomètre.

1.4 Symbole normalisé ISO 1219 [S39]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/limiteur_symbole.png
   :align: center
   :width: 25%
   :alt: Symbole ISO 1219 du limiteur de pression

   *Fig. 2 — Symbole normalisé ISO 1219 du limiteur de pression (soupape de décharge)*
   *(Source : FTA)*

1.5 Connexions
~~~~~~~~~~~~~~

Montage **en dérivation** (en parallèle) du circuit principal :

- **Port P** : relié à la ligne de pression principale (sortie pompe)
- **Port T** : relié au réservoir hydraulique

----

2. Limiteur de pression piloté
--------------------------------

2.1 Description
~~~~~~~~~~~~~~~

Le limiteur de pression piloté (réf. "modifié" sur le banc TDS) est une variante
perfectionnée du limiteur direct. Il fonctionne en deux étages — un étage pilote et
un étage principal — ce qui lui confère une meilleure précision de réglage et une
stabilité accrue, particulièrement aux débits élevés [S41]_.

2.2 Principe de fonctionnement en deux étages [S41]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 15 85

   * - Étage
     - Description
   * - **Étage pilote**
     - Une petite soupape pilote (faible débit) surveille en permanence la pression
       du circuit. Dès que la pression dépasse la valeur réglée par le ressort pilote,
       cette soupape s'ouvre légèrement.
   * - **Étage principal**
     - L'ouverture de la soupape pilote crée une chute de pression dans la chambre
       de pilotage du clapet principal. Cette différence de pression déséquilibre le
       clapet principal, qui s'ouvre à son tour, permettant l'évacuation du débit principal
       vers le réservoir.

.. figure:: images/limiteur_pilote_schema.png
   :align: center
   :width: 65%
   :alt: Schéma structurel du limiteur de pression piloté

   *Fig. 3 — Schéma structurel du limiteur de pression piloté :*
   *ressort réglable, valve pilote, clapet principal, ligne de pilotage (Source : Experts Insitu)*

2.3 Avantage sur le limiteur direct
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dans un limiteur à action directe, la pression varie légèrement selon le débit évacué
(phénomène de "chasse" du ressort). Dans le limiteur piloté, le clapet principal est
commandé par la pression et non par le débit — la pression de tarage reste donc
constante quel que soit le débit, ce qui donne une meilleure régulation [S41]_.

2.4 Symbole normalisé ISO 1219 [S39]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/limiteur_pilote_symbole.png
   :align: center
   :width: 30%
   :alt: Symbole ISO 1219 du limiteur de pression piloté

   *Fig. 4 — Symbole normalisé ISO 1219 du limiteur de pression piloté*
   *(Source : Air Techniques)*

2.5 Connexions
~~~~~~~~~~~~~~

Montage en **dérivation** du circuit principal, généralement à la sortie de la pompe.

----

3. Réducteur de pression
--------------------------

3.1 Description
~~~~~~~~~~~~~~~

Le réducteur de pression se distingue fondamentalement des deux composants précédents :
c'est une vanne **normalement ouverte** qui agit sur la **pression aval** (sortie) et
non sur la pression amont (entrée). Son rôle est d'alimenter une branche du circuit à
une pression inférieure à la pression principale, et de maintenir cette pression réduite
constante quelle que soit la charge [S42]_.


3.2 Différence fondamentale avec le limiteur
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 30 30

   * - Critère
     - Limiteur de pression
     - Réducteur de pression
   * - État au repos
     - Normalement **fermé**
     - Normalement **ouvert**
   * - Agit sur
     - Pression **amont** (entrée)
     - Pression **aval** (sortie)
   * - Montage dans le circuit
     - En **dérivation** (parallèle)
     - En **série** dans une branche
   * - Évacue vers
     - Le réservoir (décharge)
     - Ne décharge pas — régule le passage
   * - Rôle
     - Limiter la pression max du circuit
     - Alimenter un composant à pression réduite

3.3 Principe de fonctionnement [S42]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le réducteur laisse passer librement l'huile de son entrée A vers sa sortie B tant
que la pression en sortie est inférieure à la valeur de tarage. Un tiroir interne
surveille en permanence la pression aval via une ligne de pilotage interne. Dès que
la pression de sortie atteint la valeur réglée, le tiroir se déplace et réduit la
section de passage, limitant ainsi l'apport de fluide pour maintenir la pression
aval constante.

.. figure:: images/reducteur_schema.png
   :align: center
   :width: 65%
   :alt: Schéma interne du réducteur de pression

   *Fig. 5 — Schéma interne du réducteur de pression (P = ligne haute pression,*
   *T = drain vers réservoir) (Source : Experts Insitu)*

3.4 Symbole normalisé ISO 1219 [S39]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/reducteur_symbole.png
   :align: center
   :width: 28%
   :alt: Symbole ISO 1219 du réducteur de pression

   *Fig. 6 — Symbole normalisé ISO 1219 du réducteur de pression*
   *(Source : Electronique1)*

3.5 Connexions
~~~~~~~~~~~~~~

Montage **en série** dans une branche secondaire du circuit :

- **A** : entrée (haute pression, depuis la pompe)
- **B** : sortie (pression réduite, vers le composant sensible)
- **T** : drain (retour au réservoir pour l'huile de fuite interne)

----

PARTIE 2 — Régulation de débit
--------------------------------

4. Vanne d'étranglement (étrangleur)
--------------------------------------

4.1 Description
~~~~~~~~~~~~~~~

La vanne d'étranglement est un orifice réglable manuellement qui réduit la section
de passage du fluide, provoquant une **perte de charge** et limitant ainsi le débit
qui traverse le composant. La pression en amont augmente légèrement ; la pression en
aval diminue.

.. figure:: images/vanne_etranglement_photo.png
   :align: center
   :width: 40%
   :alt: Vanne d'étranglement réelle

   *Fig. 7 — Vanne d'étranglement réelle utilisée en hydraulique*
   *(Source : Armour Valve)*

4.2 Rôle et limite
~~~~~~~~~~~~~~~~~~~

Elle régule la vitesse d'un actionneur en limitant le débit qui l'alimente. Cependant,
sa limitation principale est que le débit dépend aussi de la **différence de pression**
aux bornes de l'étrangleur : si la charge du vérin varie, la vitesse varie également,
même sans toucher au réglage. Elle n'est donc pas un régulateur de débit au sens strict [S43]_.

4.3 Principe de fonctionnement [S43]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

En réduisant mécaniquement la section de passage (aiguille conique, vis de réglage),
la vanne crée une résistance au passage du fluide. L'énergie dissipée dans l'étranglement
se transforme en chaleur — c'est une perte de charge intentionnelle. Le débit résultant
Q est proportionnel à la racine carrée de la différence de pression ΔP de part et d'autre
de l'étrangleur : Q = Cd × A × √(2ΔP/ρ), où Cd est le coefficient de décharge et A
la section de passage.

4.4 Symbole normalisé ISO 1219 [S39]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/vanne_etranglement_symbole.png
   :align: center
   :width: 28%
   :alt: Symbole ISO 1219 vanne d'étranglement réglable

   *Fig. 8 — Symbole normalisé ISO 1219 d'une vanne d'étranglement réglable*
   *(Source : Tri-Matic)*

4.5 Connexions
~~~~~~~~~~~~~~

Montage **en série** dans le circuit hydraulique :

- Sur la **ligne d'alimentation** du vérin (meter-in) : contrôle la vitesse de sortie
- Sur la **ligne de retour** du vérin (meter-out) : contrôle la vitesse de rentrée

----

5. Vanne de régulation de vitesse
------------------------------------

5.1 Description
~~~~~~~~~~~~~~~

La vanne de régulation de vitesse combine un **étrangleur réglable** et un **clapet
anti-retour** dans un seul corps. Elle corrige la limitation principale de l'étrangleur
simple : grâce au clapet anti-retour intégré, le passage du fluide est libre dans
un sens et étranglé dans l'autre. Cela permet de contrôler la vitesse dans un seul
sens de déplacement du vérin tout en assurant un retour libre [S44]_.


5.2 Principe de fonctionnement [S44]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dans le sens de débit contrôlé (sens d'étranglement), le fluide ne peut passer que
par l'orifice réglable de l'étrangleur — le clapet anti-retour est fermé dans ce sens.
Dans le sens inverse, le clapet anti-retour s'ouvre et le fluide passe librement,
sans restriction de débit. Cette asymétrie de comportement est représentée dans le
symbole par les deux chemins parallèles : un avec l'étranglement, un avec le clapet.

5.3 Avantage sur l'étrangleur simple
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La vanne de régulation de vitesse offre deux avantages majeurs par rapport à l'étrangleur
simple [S44]_ :

1. **Liberté de retour** : le clapet anti-retour permet un retour rapide du vérin sans
   restriction, même si l'étrangleur est réglé sur un débit très faible.
2. **Meilleure stabilité** : en montage meter-out (sur la sortie du vérin), la pression
   en aval du vérin est maintenue ce qui évite l'emballement du vérin sous charge.

5.4 Symbole normalisé ISO 1219 [S39]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/regulateur_vitesse_symbole.png
   :align: center
   :width: 30%
   :alt: Symbole ISO 1219 vanne de régulation de vitesse

   *Fig. 9 — Symbole normalisé ISO 1219 d'une vanne de régulation de vitesse*
   *(étranglement réglable + clapet anti-retour intégré) (Source : Hydraflu)*

5.5 Connexions et montages
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 30 70

   * - Montage
     - Description
   * - **Meter-out** (sortie du vérin)
     - Placée sur la conduite de retour du vérin. C'est le montage privilégié en
       hydraulique car il maintient une contre-pression qui stabilise le mouvement,
       même avec une charge tirant sur la tige.
   * - **Meter-in** (entrée du vérin)
     - Placée sur la conduite d'alimentation du vérin. Utilisée dans certains cas
       spécifiques mais moins stable que le meter-out sous charge variable.

----

6. Vanne séquentielle
-----------------------

6.1 Description
~~~~~~~~~~~~~~~

La vanne séquentielle est un **organe de régulation de pression normalement fermé**
qui permet d'ordonner automatiquement le démarrage d'un second actionneur après
que le premier a terminé son mouvement (c'est-à-dire quand la pression monte parce
que le premier vérin est arrivé en butée). Elle crée une séquence mécanique sans
nécessiter de signal électrique de l'API [S45]_.


.. figure:: images/vanne_sequentielle_photo.png
   :align: center
   :width: 40%
   :alt: Vanne séquentielle hydraulique

   *Fig. 10 — Vanne séquentielle hydraulique (Source : Seven Ocean)*

6.2 Principe de fonctionnement [S45]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La vanne séquentielle reste fermée tant que la pression en entrée est inférieure à
sa valeur de tarage. Lorsque le premier vérin arrive en butée mécanique, la pression
dans la ligne monte brutalement car la pompe continue de débiter dans un volume bloqué.
Cette montée de pression atteint le seuil de la vanne séquentielle, qui s'ouvre alors
et alimente le deuxième actionneur. Le réglage du seuil de la vanne détermine l'ordre
d'enchaînement des mouvements.

6.3 Symbole normalisé ISO 1219 [S39]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: images/vanne_sequentielle_symbole.png
   :align: center
   :width: 32%
   :alt: Symbole ISO 1219 vanne séquentielle à pilotage interne

   *Fig. 11 — Symbole normalisé ISO 1219 d'une vanne séquentielle à pilotage interne*
   *(Source : Université de Limoges)*

6.4 Connexions
~~~~~~~~~~~~~~

Montage **en série** entre le distributeur et un actionneur secondaire :

- **Port P** : entrée (pression principale depuis le distributeur)
- **Port A** : sortie vers l'actionneur secondaire (s'ouvre quand seuil atteint)
- **Port T** : retour réservoir (présent sur certains modèles)

----

7. Tableau comparatif — organes de régulation de pression
----------------------------------------------------------

.. list-table::
   :header-rows: 1
   :widths: 25 15 15 20 25

   * - Composant
     - État repos
     - Agit sur
     - Montage
     - Différence clé
   * - Limiteur / Soupape de décharge
     - Fermé
     - Pression amont
     - Dérivation
     - Plafonne la pression max du circuit
   * - Limiteur piloté
     - Fermé
     - Pression amont
     - Dérivation
     - 2 étages — plus précis et stable
   * - Réducteur de pression
     - Ouvert
     - Pression aval
     - Série
     - Réduit et maintient une pression inférieure

----

.. rubric:: Sources utilisées dans ce module

.. [S39] ISO 1219-1:2012, *Transmissions hydrauliques et pneumatiques — Symboles
         graphiques et schémas de circuits*, Organisation internationale de normalisation,
         Genève, 2012.

.. [S40] Wikipédia, *Limiteur de pression hydraulique — principe de fonctionnement*,
         disponible en ligne : https://fr.wikipedia.org 

.. [S41] Experts Insitu, *Limiteur de pression piloté — fonctionnement en deux étages*,
         ressource technique, disponible en ligne : https://www.experts-insitu.fr
         

.. [S42] Experts Insitu, *Réducteur de pression hydraulique — principe et montage*,
         ressource technique, disponible en ligne : https://www.experts-insitu.fr
         

.. [S43] Tri-Matic, *Vannes d'étranglement hydrauliques — fonctionnement et sélection*,
         documentation technique, disponible en ligne : https://www.tri-matic.com
         

.. [S44] Hydraflu, *Vannes de régulation de vitesse — montage meter-in et meter-out*,
         documentation technique, disponible en ligne : https://www.hydraflu.fr
         

.. [S45] Université de Limoges, *Vannes séquentielles hydrauliques — principe et
         applications*, ressource pédagogique Génie Mécanique,
         disponible en ligne : https://www.unilim.fr 