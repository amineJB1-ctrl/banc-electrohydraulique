Organes de retenue
==================

.. admonition:: Objectifs de ce module

   À l'issue de ce module, l'étudiant sera capable de :

   - Distinguer le clapet anti-retour simple du clapet piloté
   - Expliquer pourquoi un clapet piloté est nécessaire pour maintenir une charge verticale
   - Identifier l'orifice de pilotage (X) et expliquer son rôle
   - Calculer la pression de pilotage minimale nécessaire à l'ouverture d'un clapet piloté
   - Lire et interpréter les symboles ISO 1219 des deux types de clapets
   - Localiser ces composants sur le banc TDS DIDACTIC et justifier leur présence

----

Vue d'ensemble
--------------

Les organes de retenue sont des composants **passifs** qui autorisent le passage du
fluide dans un seul sens et le bloquent dans l'autre. Ils ne consomment pas d'énergie
hydraulique — leur action résulte uniquement de la pression différentielle et, pour le
clapet piloté, d'une pression de commande externe [S52]_.

Sur le banc TDS DIDACTIC, deux types d'organes de retenue sont présents [S52]_ :

.. list-table::
   :header-rows: 1
   :widths: 40 60

   * - Composant
     - Rôle principal sur le banc
   * - Clapet anti-retour simple 
     - Empêche le retour d'huile non souhaité — protège la pompe et les circuits
   * - Clapet piloté 
     - Maintient un vérin en position sous charge — empêche la dérive gravitationnelle

.. note::

   **Différence fondamentale entre les deux clapets :**

   Le **clapet anti-retour** bloque toujours le sens inverse — aucune exception.
   Le **clapet piloté** bloque le sens inverse **sauf** quand une pression de pilotage
   est volontairement appliquée sur son orifice X pour l'ouvrir. C'est ce qui
   le rend utile pour maintenir une charge : la charge est bloquée tant qu'aucun
   ordre de mouvement n'est envoyé.

----

1. Clapet anti-retour simple
------------------------------

1.1 Description
~~~~~~~~~~~~~~~

Le clapet anti-retour (ou clapet de non-retour) est le composant le plus simple
des organes de retenue. Sa construction est réduite à l'essentiel : un corps fileté,
un siège conique usiné, un obturateur (bille ou champignon conique) et un ressort
de rappel. Ce ressort n'est pas obligatoire — certains clapets fonctionnent
uniquement par différence de pression — mais il améliore la fermeture à faible
débit [S53]_.

1.2 Rôle dans le système
~~~~~~~~~~~~~~~~~~~~~~~~~

Le clapet anti-retour remplit quatre fonctions sur le banc TDS DIDACTIC [S52]_ :

1. **Protection de la pompe** : monté en sortie de pompe, il empêche l'huile de
   refouler vers la pompe quand elle est arrêtée — évitant une rotation inverse
   qui userait prématurément les engrenages.
2. **Maintien de pression** : dans certaines branches du circuit, il conserve
   la pression hydraulique même après l'arrêt de la pompe.
3. **Intégration dans la vanne de régulation de vitesse** : le clapet anti-retour
   est le composant qui donne à la vanne de régulation de vitesse sa propriété
   de "libre dans un sens, étranglé dans l'autre" (cf. module Régulation).
4. **Séparation de circuits** : dans un circuit multi-vérins, il empêche un vérin
   d'alimenter involontairement un autre via les conduites communes.

1.3 Principe de fonctionnement [S53]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le fonctionnement repose entièrement sur la **différence de pression** entre l'amont
(entrée A) et l'aval (sortie B) :

- **Sens passant (A → B)** : lorsque la pression en A dépasse la pression en B
  augmentée de la force du ressort (Pression d'ouverture ≈ 0,3 à 1 bar selon modèle),
  l'obturateur s'écarte de son siège. Le fluide s'écoule librement vers B.
- **Sens bloquant (B → A)** : si la pression en B est supérieure ou égale à celle
  en A, l'obturateur est plaqué contre son siège par la pression et le ressort.
  Le passage est hermétiquement obturé — aucune fuite n'est possible.

.. figure:: images/clapet_antiretour_schema.png
   :align: center
   :width: 55%
   :alt: Principe de fonctionnement du clapet anti-retour

   *Fig. 1 — Principe de fonctionnement du clapet anti-retour :*
   *position fermée (pression aval > amont) et position ouverte (pression amont > aval)*
   *(Source : Tameson)*

1.4 Symbole normalisé ISO 1219 [S54]_ [S56]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole du clapet anti-retour représente la direction du sens passant par une
**flèche** pointant vers la sortie, et le blocage dans l'autre sens par une **bille**
appliquée contre un siège. Le ressort est visible sous la bille sur certaines
représentations.

.. figure:: images/clapet_antiretour_symbole.png
   :align: center
   :width: 45%
   :alt: Symbole ISO 1219 du clapet anti-retour — montage en série et en parallèle

   *Fig. 2 — Symbole normalisé ISO 1219 du clapet anti-retour :*
   *montage en série (gauche) et en parallèle avec un autre composant (droite)*
   *(Source : Université de Limoges)*

1.5 Connexions
~~~~~~~~~~~~~~

Montage **en série** dans une conduite hydraulique, dans le sens de la flèche du symbole :

- **Orifice A (entrée)** : relié à la source de pression (pompe ou distributeur)
- **Orifice B (sortie)** : relié à l'élément à alimenter (vérin, circuit aval)

.. warning::

   Le sens de montage est **critique** — un clapet anti-retour monté à l'envers
   bloque complètement le circuit dans le sens voulu et laisse passer l'huile
   dans le sens indésirable. Toujours vérifier la flèche gravée sur le corps
   du clapet avant l'installation.

----

2. Clapet piloté
------------------

2.1 Description
~~~~~~~~~~~~~~~

Le clapet piloté est une version perfectionnée du clapet anti-retour. Il conserve
les mêmes propriétés de base (libre dans un sens, bloquant dans l'autre) mais ajoute
un **orifice de pilotage (X)** qui permet, sur commande externe, d'ouvrir le clapet
dans le sens normalement bloqué [S55]_.

Cette capacité d'ouverture commandée est ce qui le rend indispensable pour les
applications de **maintien de charge** : le vérin est bloqué hydrauliquement en
position, et son déverrouillage nécessite une commande délibérée via la pression
de pilotage.


2.2 Rôle dans le système — maintien de charge [S55]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Sans clapet piloté, un vérin vertical portant une charge fuit lentement dans les
distributeurs et descend progressivement par gravité — même distributeur en position
neutre, même pompe arrêtée. C'est la **dérive gravitationnelle**.

Le clapet piloté, monté entre le distributeur et la chambre fond du vérin, bloque
hermétiquement cette chambre. Tant qu'aucune pression de pilotage n'est appliquée
sur X, l'huile contenue dans la chambre fond ne peut pas s'échapper — le vérin reste
en position, quelle que soit la charge.

2.3 Principe de fonctionnement [S55]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le clapet piloté fonctionne selon trois situations distinctes :

.. list-table::
   :header-rows: 1
   :widths: 25 75

   * - Situation
     - Comportement du clapet
   * - **Sens passant (A → B), sans pilotage**
     - Le fluide pousse directement l'obturateur et circule librement de A vers B.
       La pression de pilotage X n'est pas nécessaire dans ce sens.
   * - **Sens bloquant (B → A), sans pilotage**
     - L'obturateur est plaqué sur son siège par la pression en B. Le passage
       est hermétiquement fermé. Le vérin est maintenu en position.
   * - **Sens bloquant (B → A), avec pilotage X actif**
     - La pression appliquée sur X agit sur le piston de pilotage (surface Spp)
       et décolle mécaniquement l'obturateur de son siège (surface Sc). Le passage
       B → A s'ouvre et l'huile peut s'écouler — le vérin peut se déplacer.

**Condition d'ouverture par pilotage :**

La pression de pilotage minimale P(X) nécessaire pour ouvrir le clapet est donnée
par la relation entre les surfaces [S55]_ :

.. math::

   P_X \times S_{pp} \geq P_B \times S_c

soit :

.. math::

   P_X \geq P_B \times \frac{S_c}{S_{pp}}

où :

- :math:`P_X` = pression de pilotage (Pa)
- :math:`P_B` = pression en aval (chambre du vérin à maintenir) (Pa)
- :math:`S_c` = surface de l'obturateur (m²)
- :math:`S_{pp}` = surface du piston de pilotage (m²)

Le rapport Sc/Spp est caractéristique du modèle — typiquement 1/3 à 1/5,
ce qui signifie que la pression de pilotage n'a besoin d'être que 20 à 33 %
de la pression à bloquer pour ouvrir le clapet.

.. figure:: images/clapet_pilote_schema.png
   :align: center
   :width: 65%
   :alt: Schéma de fonctionnement interne du clapet piloté

   *Fig. 3 — Schéma interne du clapet piloté : surfaces Spp (pilotage), St (tige),*
   *Sc (clapet), orifices A, B et X (Source : Experts Insitu)*

2.4 Symbole normalisé ISO 1219 [S54]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le symbole du clapet piloté est identique au clapet anti-retour simple, mais avec
une **ligne tiretée** représentant la commande de pilotage arrivant sur l'orifice X.
Cette ligne tiretée indique une commande hydraulique interne au composant.

.. figure:: images/clapet_pilote_symbole.png
   :align: center
   :width: 28%
   :alt: Symbole ISO 1219 du clapet piloté

   *Fig. 4 — Symbole normalisé ISO 1219 du clapet piloté (orifices A, B et commande X)*
   *(Source : Experts Insitu)*

2.5 Connexions et câblage hydraulique [S55]_
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Le clapet piloté est monté **entre le distributeur et le vérin** afin de bloquer
la chambre du vérin que l'on souhaite maintenir :

- **Orifice A** : relié au distributeur hydraulique (ligne d'alimentation)
- **Orifice B** : relié à la chambre fond du vérin (chambre à maintenir)
- **Orifice X (pilotage)** : relié à la ligne opposée (ligne chambre tige)

**Logique de fonctionnement intégrée dans le circuit :**

Lorsque le distributeur envoie de l'huile vers la chambre tige pour rentrer le vérin,
cette même pression est automatiquement transmise à l'orifice X du clapet piloté.
La pression de pilotage ouvre le clapet et libère l'huile de la chambre fond vers
le réservoir — le vérin peut rentrer normalement. Ce déverrouillage est donc
**synchronisé mécaniquement** avec le mouvement du vérin, sans intervention
supplémentaire de l'API.

----

3. Tableau comparatif — clapet anti-retour vs clapet piloté
------------------------------------------------------------

.. list-table::
   :header-rows: 1
   :widths: 30 35 35

   * - Critère
     - Clapet anti-retour
     - Clapet piloté
   * - Sens passant
     - A → B librement
     - A → B librement
   * - Sens bloquant
     - B → A toujours bloqué
     - B → A bloqué **sauf** si X actif
   * - Orifice de pilotage
     - Absent
     - Présent (X)
   * - Maintien de charge possible
     - Non (fuite possible par le distributeur)
     - Oui (blocage hydraulique total)
   * - Déverrouillage
     - Impossible
     - Par pression sur X
   * - Application typique
     - Protection pompe, séparation circuits
     - Maintien vérin vertical sous charge

----

.. rubric:: Sources utilisées dans ce module

.. [S52] TDS DIDACTIC, *Fiche technique — Banc didactique électro-hydraulique lot 18*,
         Technology Development Systems, 2023. (fiche fournie avec le matériel)

.. [S53] Tameson, *Clapets anti-retour hydrauliques — principe, sélection et montage*,
         disponible en ligne : https://www.tameson.fr (consulté en 2024)

.. [S54] Université de Limoges, *Symboles hydrauliques ISO 1219 — organes de retenue*,
         ressource pédagogique Génie Mécanique,
         disponible en ligne : https://www.unilim.fr (consulté en 2024)

.. [S55] Experts Insitu, *Clapet piloté hydraulique — fonctionnement, calcul du rapport
         de surfaces et applications*, ressource technique,
         disponible en ligne : https://www.experts-insitu.fr (consulté en 2024)

.. [S56] ISO 1219-1:2012, *Transmissions hydrauliques et pneumatiques — Symboles
         graphiques et schémas de circuits*, Organisation internationale de normalisation,
         Genève, 2012.