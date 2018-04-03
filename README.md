# Migration SPIP-to-WP

Ceci est une documentation concernant un processus de migration de site, depuis le CMS [SPIP](https://www.spip.net) vers le CMS [WordPress](https://fr.wordpress.org/).

**Objectif de l'opération:** on cherche à importer le contenu d'un site sous SPIP dans un site sous WordPress. Ce site contient 896 articles, 13 rubriques, 1220 mots-clés, 689 documents attachés.

**La méthode:** on va générer depuis SPIP un fichier XML au format accepté par WordPress. Pour produire ce fichier, on crée un modèle de page SPIP.

## Informations détaillées:

1. [Inventaire des contenus du site](infos-contenus.md).
2. [Format XML d'importation WordPress](infos-wp-xml.md) (un peu d'étude pour comprendre le format attendu).
3. [Post ID et relations entre contenus](infos-post-id-et-relations.md).
4. [Stratégie de migration](infos-strategie-migration.md).
5. [Code pour l'exportation depuis SPIP](infos-wp-xml-from-spip.md).
6. [Test final et conclusion](test-et-conclusion.md).

## Custom Fields

Pour la gestion des Custom Fields, choisir entre:

* [ACF](https://www.advancedcustomfields.com/)
* [CMB2](https://github.com/CMB2/CMB2)
* Custom Gutenberg Blocks

**Conclusion:** au final nous utilisons ACF, plus largement adopté et documenté.

ACF est utilisé pour:

- Le "sur-titre" : champ utilisé pour certains concerts.
- Les photos : champ "Galerie" attaché à un concert (c12_photos).
- Les affiches attachées aux concerts (c12_affiches). Il s'agit également d'un champ "Galerie".

***

**Suite:** [Inventaire des contenus du site](infos-contenus.md).