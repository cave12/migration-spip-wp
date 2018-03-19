# Migration SPIP-to-WP

Ceci est une documentation concernant un processus de migration de site, du CMS [SPIP](https://www.spip.net) vers le CMS [WordPress](https://fr.wordpress.org/).

**Objectif de l'opération:** on cherche à importer le contenu d'un site sous SPIP dans un site sous WordPress.

**La méthode:** on va générer depuis SPIP un fichier XML au format accepté par WordPress. Pour produire ce fichier, on créé un modèle de page SPIP.

## Informations nécessaires:

- Inventaire des contenus du site.
- Format XML d'importation WordPress. Un peu d'étude pour comprendre le format attendu.

## Solutions à considérer:

Pour la gestion des Custom Fields:

ACF ou CMB2 ?

- https://github.com/WebDevStudios/CMB2 (a metabox, custom fields, and forms library)
- https://github.com/WebDevStudios/CMB2/wiki/Basic-Usage

