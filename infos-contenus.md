# Inventaire des contenus du site

## Modèles de page

Les différents modèles de pages du site http://www.cave12.org/ :

- La homepage : liste le programme (les concerts à venir).
- Concert: infos du concert.
- Page archive (par année). http://www.cave12.org/2001 etc.
- http://www.cave12.org/artistes = liste des mots-clés
- Page artiste: affiche une liste de concerts.
- Affiches: montre les affiches (3 auteurs).
- Affiche par auteur: toutes les affiches d'un auteur.

## Les contenus à exporter

- Concerts
- Affiches - Fichiers attachés
- Artistes (mots-clés)

## Les champs de données

Les données qu'il faut exporter pour chaque Concert:

- Titre = champ titre, identique dans SPIP et WP.
- Sur-titre  = utilisé parfois pour des infos style "La cave12 à l'Ecurie (#196)". Dans WP: custom field ACF (c12_surtitre)
- Chapeau = en-tête. Contient le line-up du concert. On va l'assigner au champ "Extrait" de WordPress.
- Contenu = contenu principal.
- URL
- Date de début (spip: DATE DE PUBLICATION EN LIGNE)
- Mots-clés (groupe Artistes)
- Mots-clés (groupe Lieux)
- Fichier attaché (affiche en format PDF) => trouver solution PDF + vignette (utiliser les champs répétables ACF?)

Infos qu'on ne récupère pas:

- Composition = utilisé pour des événements-séries (Akouphène, Bains des Pâquis, MAC, Pianos).
- Date de fin (DATE DE RÉDACTION ANTÉRIEURE) = pour les événements de plusieurs jours. Sera géré au cas par cas.

## Modèles de page en détail:

### La homepage

Cette page est créée dans SPIP par le modèle **[sommaire.html](https://github.com/cave12/cave12-spip/blob/master/c12-2013/sommaire.html)**.

La `BOUCLE_articles_recents` récupère tous les articles dont la date est dans le futur proche `(age<1)`.

On affiche ces données:
* La date
* Le champ #SURTITRE
* Le champ #CHAPO

### Page concert

La page de chaque concert est produite avec le modèle SPIP **[article-1.html](https://github.com/cave12/cave12-spip/blob/master/c12-2013/article-1.html)** (articles de la rubrique 1).

Ce modèle affiche:

* La date
* Le champ #SURTITRE
* Le champ #CHAPO
* Le contenu - #TEXTE

### [Page affiches](http://www.cave12.org/affiches)

Cette page est produite par le modèle **[rubrique=22.html](https://github.com/cave12/cave12-spip/blob/master/c12-2013/rubrique%3D22.html)**.

Elle inclut plusieurs boucles:

* Boucle affichant les 5 derniers documents PDF liés au mot-clé Xavier Robel.
* Idem pour Harrisson.
* Idem pour Thomas Perrodin.

### Liste des affiches par auteur

Ces pages (une pour Xavier Robel, Harrisson, Thomas Perrodin...) sont créées par le modèle **[mot.html](https://github.com/cave12/cave12-spip/blob/master/c12-2013/mot.html)**.

Le même modèle crée les pages "concerts par artiste". 

***

Suite: [Format XML d'importation WordPress](infos-wp-xml.md) (un peu d'étude pour comprendre le format attendu).