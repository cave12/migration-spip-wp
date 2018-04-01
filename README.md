# Migration SPIP-to-WP

Ceci est une documentation concernant un processus de migration de site, depuis le CMS [SPIP](https://www.spip.net) vers le CMS [WordPress](https://fr.wordpress.org/).

**Objectif de l'opération:** on cherche à importer le contenu d'un site sous SPIP dans un site sous WordPress.

**La méthode:** on va générer depuis SPIP un fichier XML au format accepté par WordPress. Pour produire ce fichier, on crée un modèle de page SPIP.

## Informations nécessaires:

1. [Inventaire des contenus du site](infos-contenus.md).
2. [Format XML d'importation WordPress](infos-wp-xml.md). Un peu d'étude pour comprendre le format attendu.

## Solutions à considérer:

Pour la gestion des Custom Fields:

ACF ou CMB2 ?

- https://github.com/WebDevStudios/CMB2 (a metabox, custom fields, and forms library)
- https://github.com/WebDevStudios/CMB2/wiki/Basic-Usage

**Conclusion:** au final nous utilisons ACF, plus largement adopté et documenté.