# Publication des releases

A partir de ce depot (central), on va publier sur **npm** ainsi que sur **bower**,
les **binaires** et les **sources** pour **OpenLayers** et **Leaflet**.

Les publications sont déposées dans des dépôts séparés. Et ils contiennent les
fichiers binaires, les sources ainsi que des fichiers d'information (LICENCE, README, ...)

La publication est gérée par un script (bash ou node).

Ce script consiste à *construire* les binaires, *copier* les fichiers utiles dans le depot,
*tagger* la publication et enfin, *publier*...

## Publication via bower

**Liens utiles**

    project/howto - http://www.mimiz.fr/blog/publier-package-sur-bower/
    spec/json - https://github.com/bower/spec/blob/master/json.md
    register/unregister - https://bower.io/docs/creating-packages/

> **Commande**
bower register geoportal-extensions-openlayers http://github.com/IGNF/geoportal-extensions-openlayers.git

## Publication via npm

**Liens utiles**

https://docs.npmjs.com/getting-started/publishing-npm-packages

> **Commande**
npm publish

avec la configuration dans le **package.json**

    "name": "geoportal-extensions-openlayers",
    "repository": {
      "type": "git",
      "url": "https://github.com/IGNF/geoportal-extensions-openlayers.git"
    },

## Depot de publication

Les publications sont déposées dans des dépôts séparés :

    geoportal-extensions-openlayers
    geoportal-extensions-leaflet

Ces depots contiennent les fichiers suivants :

    bower.json
    dist/.js
    dist/.css
    dist/images
    CHANGELOG.md
    LICENCE.md
    package.json
    README.md
    [ src/.js ]
    summary.json <!-- meta information de la publication -->

> **TODO**
Le dépôt est à initialiser manuellement pour une 1ere utilisation !


## Scripts de construction des releases (+ publication)

**Liens utiles**

    https://gist.github.com/bclinkinbeard/1331790
    https://gist.github.com/foca/38d82e93e32610f5241709f8d5720156
    https://github.com/aktau/github-release
    https://kaspars.net/blog/web-development/create-release-zip-git-tags

**Synopsys**

> release.sh -h
Usage :
    release.sh -h    Affiche cette aide.
    l (--leaflet)     Execution de la publication Leaflet (par defaut),
    o (--ol3)         Execution de la publication Openlayers,
    b (--run-build)   Execution de la tache de compilation,
    d (--run-data)    Execution de la tache de git-clone,
    j (--run-json)    Execution de la tache de creation des json,
    i (--run-info)    Execution de la tache de creation du fichier d'info,
    c (--run-commit)  Execution de la tache de git-push,
    p (--run-publish) Execution de la tache de publication npm et bower,
    C (--run-clean)   Execution de la tache de nettoyage.
Ex. release.sh -bdjicpC


Ce script consiste à executer les étapes suivantes :

* build - construction des binaires dans le répertoire *dist*
avec la commande *gulp*.

* json - création des fichiers de configuration json (package et bower)

* data - copie des fichiers utiles dans le dépôt de publication avec *git*.
  * copie des sources,
  * copie des binaires,
  * copie des README, COMPILE, LICENCE
  * copie du CHANGELOG_DRAFT mais ne pas oublier de le mettre à jour au préalable

* commit - *commit* des modifications de la publication avec *git*.
  * **TODO** : tag - mise en place du *tag* de publication avec *git*.

* info - création d'un fichier d'information

* publish - publication via *npm* et *bower*

* clean - nettoyage du répertoire

## Scripts de publication des releases sur le gitHub

> Ex. release-github.sh

Ce script sert à mettre en place les releases dans le dépôt central.

Les étapes consistent à :

* build - construction des binaires dans le répertoire *dist*
avec la commande *gulp*.

* tag - mise en place du *tag* de publication avec *git*.

* publish/upload - via l'API **Github** (https://developer.github.com/v3/repos/releases/),
on dépose l'archive et le changelog sur le gitHub.
  * create - creation du répertoire temporaire de publication.
  * zip - construire les archives au format zip.
  * data - copie du CHANGELOG_DRAFT mais ne pas oublier de le mettre à jour au préalable

> **Note**
Le contenu du changelog est extrait du fichier *CHANGELOG.md* ou *CHANGELOG_DRAFT.md*.
Il faut donc au préalable le mettre à jour...

## Authentification sur le GitHub

On utilise l'authentification via Token Personal Access.
Comment creer un token :
    https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/

Ensuite, ce token est stocké dans une variable d'environnement du systeme :
> export RELEASE_GITHUB_TOKEN="grsgz5r4gzr5g4er654er54er4tyer5646y"