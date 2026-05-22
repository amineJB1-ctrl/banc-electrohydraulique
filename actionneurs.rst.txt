Actionneurs hydrauliques
========================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Définir le rôle d'un actionneur hydraulique dans un circuit électro-hydraulique
   - Distinguer le vérin double effet du vérin simple effet à rappel par ressort
   - Expliquer le principe de fonctionnement de chaque type de vérin
   - Lire et interpréter les symboles normalisés ISO 1219 des vérins
   - Appliquer les formules de force et de vitesse d'un vérin hydraulique
   - Identifier la plaque d'arrêt et justifier son utilité sur le banc TDS DIDACTIC

----

Vue d'ensemble
--------------

Dans la chaîne d'énergie d'un système hydraulique, les actionneurs occupent la position
terminale : ils reçoivent l'énergie hydraulique sous forme de pression et de débit, et
la convertissent en **énergie mécanique utile** — c'est-à-dire en force et en
déplacement. Sur le banc TDS DIDACTIC, deux types de vérins linéaires sont utilisés :
le vérin double effet avec butée de fin de course, et le vérin simple effet à rappel
par ressort [S11]_.

.. list-table:: Comparatif des deux types de vérins du banc TDS DIDACTIC
   :header-rows: 1
   :widths: 30 35 35

   * - Caractéristique
     - Vérin double effet
     - Vérin simple effet (ressort)
   * - Sens de commande
     - 2 sens (aller ET retour commandés)
     - 1 sens (aller commandé, retour automatique)
   * - Nombre d'orifices
     - 2 (orifice A et orifice B)
     - 1 seul
   * - Source de retour
     - Pression hydraulique (orifice B)
     - Ressort interne
   * - Effort en retour
     - Élevé (hydraulique)
     - Limité (force du ressort)
   * - Application typique
     - Presse, translation bidirectionnelle
     - Clamp, serrage, poussée simple

----

1. Formules fondamentales des vérins hydrauliques
--------------------------------------------------

Avant d'étudier chaque type de vérin, il est essentiel de connaître les deux relations
physiques qui gouvernent leur comportement [S12]_.

**Force développée par le vérin :**

.. math::

   F = P \times S

où :

- :math:`F` = force développée (N)
- :math:`P` = pression du fluide (Pa)
- :math:`S` = section active du piston (m²)

**Vitesse de déplacement du piston :**

.. math::

   v = \frac{Q}{S}

où :

- :math:`v` = vitesse de déplacement (m/s)
- :math:`Q` = débit volumique fourni par la pompe (m³/s)
- :math:`S` = section active du piston (m²)

.. note::

   **Exemple chiffré (banc TDS DIDACTIC) :**

   Pour P = 1,6 MPa = 1 600 000 Pa, et un piston de diamètre d = 25 mm
   (soit S = π × (0,025/2)² ≈ 4,91 × 10⁻⁴ m²) :

   F = 1 600 000 × 4,91 × 10⁻⁴ ≈ **785 N**

   Pour Q = 10 L/min = 1,67 × 10⁻⁴ m³/s :

   v = 1,67 × 10⁻⁴ / 4,91 × 10⁻⁴ ≈ **0,34 m/s**

   On voit ainsi concrètement que la **pression** détermine la force, et le **débit**
   détermine la vitesse — deux paramètres indépendants et réglables séparément.

----

2. Vérin hydraulique double effet avec butée de fin de course
--------------------------------------------------------------

2.1 Description
~~~~~~~~~~~~~~~

Le vérin double effet est un actionneur linéaire qui convertit la pression hydraulique
en mouvement de translation dans **les deux directions**. Son corps cylindrique renferme
un piston mobile qui délimite deux chambres étanches : la chambre fond (côté tige
rentrée) et la chambre tige (côté tige sortie). L'alimentation en huile sous pression
d'une chambre ou de l'autre détermine le sens de déplacement de la tige. Ce vérin est
équipé d'une **butée de fin de course** réglable, qui arrête mécaniquement la tige à une
position précise et reproductible [S13]_.

.. figure:: images/verin_double.png
   :align: center
   :width: 70%
   :alt: Coupe d'un vérin hydraulique double effet

   *Fig. 1 — Fonctionnement d'un vérin hydraulique double effet (extension et rétraction)*
   *(Source : Hidraoil)*

2.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Sur le banc TDS DIDACTIC, le vérin double effet assure le déplacement contrôlé d'une
charge dans les deux sens, avec une force de poussée et une force de traction toutes
deux commandées hydrauliquement. La butée de fin de course garantit un arrêt précis
de la tige quelle que soit la charge, sans risque de dépassement ni de choc violent
sur les éléments de structure.

2.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le fonctionnement repose sur la différence de pression appliquée de part et d'autre du
piston. Lorsque l'huile sous pression entre par l'orifice A (chambre fond), elle pousse
le piston vers l'avant et la tige sort du corps. L'huile contenue dans la chambre tige
est simultanément évacuée vers le réservoir via l'orifice B [S13]_.

Pour inverser le mouvement, le distributeur hydraulique redirige le flux : l'huile entre
alors par l'orifice B (chambre tige) et repousse le piston vers l'arrière, provoquant la
rentrée de la tige. L'huile de la chambre fond s'écoule vers le réservoir via l'orifice A.

.. note::

   **Dissymétrie des forces :** la force en sortie de tige (extension) est plus grande
   qu'en rentrée de tige (rétraction), car la section utile côté tige est réduite par
   la présence de la tige elle-même. Pour un effort identique dans les deux sens, il
   faut appliquer une pression légèrement plus élevée lors de la rentrée. C'est
   précisément ce qu'on observe dans le TP 1 : la pression de rentrée affichée au
   manomètre est supérieure à la pression de sortie.

2.4 Constitution interne
~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 25 75

   * - Élément
     - Rôle
   * - Corps cylindrique
     - Enveloppe rigide qui contient le piston et le fluide sous pression
   * - Piston
     - Partie mobile qui divise le corps en deux chambres étanches
   * - Tige de vérin
     - Transmet la force du piston vers la charge extérieure
   * - Joints d'étanchéité
     - Assurent l'étanchéité entre les deux chambres et vers l'extérieur
   * - Butée de fin de course
     - Arrête mécaniquement la tige à une position définie et réglable
   * - Orifices A et B
     - Raccordements hydrauliques pour l'alimentation et le retour du fluide

2.5 Symbole normalisé ISO 1219 [S14]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole d'un vérin double effet se représente par un **rectangle** symbolisant le
corps du vérin, avec **deux traits** perpendiculaires représentant les orifices
d'alimentation de chaque chambre, et une **tige** sortant d'un côté du rectangle. Les
deux côtés alimentés sont identifiables par les deux connexions symétriques.

.. figure:: images/symbole_verin_double.png
   :align: center
   :width: 22%
   :alt: Symbole normalisé ISO 1219 d'un vérin double effet

   *Fig. 2 — Symbole normalisé ISO 1219 d'un vérin hydraulique double effet*
   *(Source : Hidraoil)*

2.6 Connexions
~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 20 80

   * - Orifice
     - Fonction
   * - Orifice A (chambre fond)
     - Entrée d'huile sous pression → tige sort ; retour d'huile → tige rentre
   * - Orifice B (chambre tige)
     - Entrée d'huile sous pression → tige rentre ; retour d'huile → tige sort

2.7 Caractéristiques techniques (banc TDS DIDACTIC)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Type
     - Vérin double effet avec butée de fin de course
   * - Pression maximale de service
     - 1,6 MPa (16 bar)
   * - Fluide utilisé
     - Huile hydraulique minérale ISO VG 46
   * - Sens de commande
     - Bidirectionnel (aller et retour commandés)
   * - Butée de fin de course
     - Mécanique, réglable en position

----

3. Vérin simple effet à rappel par ressort
-------------------------------------------

3.1 Description
~~~~~~~~~~~~~~~

Le vérin simple effet à rappel par ressort est un actionneur linéaire qui ne reçoit la
pression hydraulique que dans **un seul sens**. Un ressort de rappel interne, comprimé
lors de la sortie de la tige, assure automatiquement le retour du piston à sa position
initiale dès que la pression hydraulique est supprimée. Ce type de vérin nécessite donc
un seul raccordement hydraulique [S13]_.

3.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Sur le banc TDS DIDACTIC, ce vérin est utilisé pour des applications où le retour
automatique est suffisant — typiquement des opérations de serrage, de blocage ou de
poussée simple. Son raccordement simplifié (un seul orifice) facilite le câblage et
réduit le nombre de flexibles nécessaires dans le circuit.

3.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Lorsque l'huile sous pression pénètre dans la chambre active par le seul orifice du
vérin, elle exerce une force sur le piston et comprime le ressort de rappel simultanément.
La tige avance et effectue le travail utile. Dès que la pression est coupée — par
passage du distributeur en position neutre ou retour en position initiale — le ressort
détendu repousse le piston vers sa position de repos et l'huile est expulsée vers le
réservoir par ce même orifice [S13]_.

.. figure:: images/verin_sortie.png
   :align: center
   :width: 65%
   :alt: Sortie du piston sous l'effet de la pression

   *Fig. 3 — Phase d'extension : l'huile sous pression pousse le piston et comprime le ressort*
   *(Source : Scribd)*

.. figure:: images/verin_retour.png
   :align: center
   :width: 65%
   :alt: Retour du piston grâce au ressort

   *Fig. 4 — Phase de retour : la pression est supprimée, le ressort ramène le piston en position de repos*
   *(Source : Scribd)*

.. warning::

   La force de retour d'un vérin simple effet est **limitée par la raideur du ressort**.
   Si la charge à déplacer en retour est trop importante (frottement élevé, charge
   suspendue), le ressort peut ne pas suffire à ramener la tige. Toujours vérifier que
   la force du ressort est supérieure à la somme des forces résistantes en retour.

3.4 Symbole normalisé ISO 1219 [S14]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole d'un vérin simple effet se distingue du double effet par la présence d'un
**ressort schématisé** à l'intérieur du rectangle représentant le corps du vérin, du côté
opposé à la tige. Un seul raccordement hydraulique est visible, côté chambre active.

.. figure:: images/symbole_verin_simple.png
   :align: center
   :width: 22%
   :alt: Symbole normalisé ISO 1219 d'un vérin simple effet à rappel par ressort

   *Fig. 5 — Symbole normalisé ISO 1219 d'un vérin simple effet à rappel par ressort*
   *(Source : Hidraoil)*

3.5 Connexions
~~~~~~~~~~~~~~

- **Un seul orifice** : sert alternativement d'entrée (huile sous pression → tige sort)
  et de retour (huile évacuée → tige rentre sous l'effet du ressort).

3.6 Caractéristiques techniques
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Paramètre
     - Valeur
   * - Type
     - Vérin simple effet à rappel par ressort
   * - Pression maximale de service
     - 1,6 MPa (16 bar)
   * - Fluide utilisé
     - Huile hydraulique minérale ISO VG 46
   * - Sens de commande
     - Unidirectionnel (sortie commandée, rentrée par ressort)
   * - Nombre d'orifices hydrauliques
     - 1

----

4. Plaque d'arrêt de vérin
---------------------------

4.1 Description
~~~~~~~~~~~~~~~

La plaque d'arrêt de vérin est un accessoire mécanique monté sur le banc TDS DIDACTIC
pour **limiter physiquement la course de sortie de la tige** du vérin. Il s'agit d'une
pièce métallique percée de plusieurs trous de fixation, permettant de la positionner à
différents endroits de la grille profilée du banc selon la course utile souhaitée [S15]_.

.. figure:: images/plaque_arret_verin.png
   :align: center
   :width: 45%
   :alt: Plaque d'arrêt de vérin

   *Fig. 6 — Plaque d'arrêt de vérin pour limitation de course et fixation des composants*
   *(Source : Air Techniques)*

4.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

La plaque d'arrêt remplit trois fonctions sur le banc :

1. **Limiter la course** : elle définit la position maximale de sortie de la tige,
   transformant ainsi un déplacement illimité en un déplacement défini et reproductible.
2. **Absorber les chocs** : lors de l'arrivée de la tige en butée, la plaque absorbe
   l'énergie cinétique résiduelle et évite les chocs directs sur les raccords ou les
   composants adjacents.
3. **Assurer la fixation** : elle maintient le vérin solidement ancré sur la grille du
   banc, empêchant tout déplacement axial lors des cycles de travail.

4.3 Principe de fonctionnement
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

En fin de course, la tige du vérin vient en contact avec la face de la plaque d'arrêt.
La plaque, rigidement fixée à la structure du banc par ses boulons de serrage, encaisse
la poussée sans se déplacer. Le limiteur de pression du circuit prend alors le relais en
plafonnant la pression montante, ce qui protège l'ensemble du circuit hydraulique d'une
surpression dangereuse.

4.4 Utilisation sur le banc
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Fixée directement sur la grille profilée 50 × 50 mm du banc, par boulonnage dans
  les rails de la grille [S11]_.
- Sa position est réglable manuellement le long des rails, permettant de modifier la
  course utile du vérin sans outil spécifique.
- Placée en bout de course avant la mise en service ; toujours vérifier son serrage
  avant de mettre le circuit sous pression.

----

5. Tableau récapitulatif — actionneurs du banc TDS DIDACTIC
------------------------------------------------------------

.. list-table::
   :header-rows: 1
   :widths: 25 25 25 25

   * - Composant
     - Type
     - Sens d'action
     - Éléments associés
   * - Vérin double effet
     - Linéaire hydraulique
     - Bidirectionnel
     - Distributeur 4/2 ou 4/3, 2 flexibles
   * - Vérin simple effet (ressort)
     - Linéaire hydraulique
     - Unidirectionnel + retour ressort
     - Distributeur 3/2 ou 4/2, 1 flexible
   * - Plaque d'arrêt
     - Butée mécanique
     - Fin de course (sortie)
     - Fixation sur grille 50×50 mm

----

.. rubric:: Sources utilisées dans ce module

.. [S11] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
        Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S12] Parker Hannifin, *Hydraulic cylinder — force, speed and power calculations*,
        Parker Engineering Your Success, Technical Training Document,
        disponible en ligne : https://www.parker.com (consulté en 2024)

.. [S13] Hidraoil, *Vérins hydrauliques : double effet et simple effet — principes
        et symboles ISO 1219*, disponible en ligne : https://www.hidraoil.es
        (consulté en 2024)

.. [S14] ISO 1219-1:2012, *Transmissions hydrauliques et pneumatiques — Symboles
        graphiques et schémas de circuits*, Organisation internationale de normalisation,
        Genève, 2012.

.. [S15] Air Techniques, *Plaques d'arrêt et accessoires de montage pour vérins
        hydrauliques*, catalogue produits, disponible en ligne : https://www.airtechniques.fr
        (consulté en 2024)