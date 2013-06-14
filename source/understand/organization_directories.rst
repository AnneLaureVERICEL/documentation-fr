Organisation des répertoires
############################

De Novius OS
************

Repertoires à la racine
=======================

* :file:`~/novius-os/` : Le ``core`` de Novius OS
* :file:`~/local/` : Votre site
* :file:`~/public/` : Le ``DOCUMENT_ROOT`` du site
* :file:`~/logs/` : Un répertoire de logs

Le répertoire ``public``
========================

Un fichier peut être :

* Exécutable ou non exécutable
* Fourni par le developpeur ou le logiciel, ou généré par le logiciel

Cela donne 4 usages possibles. Chacun d'eux a un répertoire dans :file:`~/public/` :

* :file:`~/public/static/` : Équivalent des ``assets``. Des fichiers non exécutables fournis par le développeur ou Novius OS.
* :file:`~/public/data/` : Fichiers non exécutables générés par Novius OS.
* :file:`~/public/htdocs/` : Fichiers exécutables fournis par par le développeur ou Novius OS.
* :file:`~/public/cache/` : Fichiers exécutables générés par Novius OS

.. note:: Ici, Novius OS fait référence au core, ou toute application de votre site web.

Il y a un 5ème répertoire :file:`~/public/media/` utilisé par la :doc:`media_centre`.

Là où Novius OS peut écrire, le développeur ne le peut pas et vice et versa.

:file:`~/public/static/` et :file:`~/public/htdocs/` ont la même structure de sous-répertoire :

* :file:`~/novius-os/` : Pour les fichiers venant du logiciel
* :file:`~/apps/<application_name>/` : Pour les fichiers venant des developpeurs d':doc:`applications <applications>`.

| Ces sous-répertoires sont des liens symboliques, créés à l'installation du logiciel ou à l'activation des :doc:`applications <applications>`.
| Ces liens symboliques pointant respectivement vers le :file:`htdocs` et le :file:`static` du repertoire du logiciel ou de l'application.
| Voir ci-dessous l':ref:`organisation des répertoires d'une application <understand/organization_directories/application>`.

Le répertoire du ``core``
=========================

* :file:`~/novius-os/framework/` : Le framework de Novius OS
* :file:`~/novius-os/fuel-core/` : Le framework FuelPHP
* :file:`~/novius-os/packages/` : Les packages FuelPHP


Le répertoire ``local``
=======================

* :file:`~/local/applications/` : Les :doc:`applications <applications>` Novius OS.
* :file:`~/local/cache/` : Contient des médias redimensionnés.
* :file:`~/local/classes/` : Classes PHP de vos développements.
* :file:`~/local/config/` : Vos fichiers de configuration de Novius OS
* :file:`~/local/data/` : Fichiers générés par Novius OS
* :file:`~/local/metadata/` : Des fichiers de metadata de votre site, générés par Novius OS.
* :file:`~/local/migrations/` : Des classes de migration.
* :file:`~/local/views/` : Vos fichiers PHP de ``Views`` de vos développements.

.. note::

	Les répertoires :file:`classes` et :file:`views` ne devrait pas contenir beaucoup de fichiers, la plupart de vos développements devrait être des :doc:`applications <applications>`..

.. _understand/organization_directories/application:

D'une application
*****************

Tout Novius OS reprend les principes de segmentation issus de l’architecture MVC. Ils s'appliquent aussi bien au core qu'aux applications.

.. image:: images/files_organisation.png
	:alt: Organisation des fichiers
	:align: center

On distingue 6 dossiers principaux :

:file:`classes`
	Ce dossier regroupe la partie logique, c'est-à-dire les classes PHP qui définissent et manipulent les données.
	Il s'agit a minima des contrôleurs et modèles de l’application. On y retrouve également des outils utilisés par les vues ou directement par les contrôleurs.

:file:`config`
	| Ce dossier rassemble l’ensemble des informations permettant de représenter vos modèles.
	  Les contrôleurs effectuent les opérations logiques sur vos données, mais auront besoin d’informations complémentaires à transmettre aux vues pour leur représentation.
	  Ces informations sont ainsi séparées des contrôleurs, n’ayant pas de valeur logique, et des vues, car celles-ci reçoivent les données en paramètres et ne les recherchent jamais.
	| Le fichie de configuration du contrôleur :file:`controller/admin/monkey.ctrl.php` se situe à :file:`config/controller/admin/monkey.ctrl.php`
	  Une classe et son fichier de configuration partagent une convention de nommage symétrique.

:file:`lang`
	Ce dossier contient les fichiers de traduction, organisés en sous-dossiers par langue.

:file:`migrations`
	Ce dossier contient les fichiers de migration.

:file:`static`
	Ce dossier contient l’ensemble des scripts (JS et CSS) et ressources publiques (comme les images) chargées en front office.

:file:`views`
	Ce dossier contient les fichiers responsables de l’affichage et de la représentation des données.

