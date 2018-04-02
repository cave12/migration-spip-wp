# Migration SPIP-to-WP

Ceci est une documentation concernant un processus de migration de site, depuis le CMS [SPIP](https://www.spip.net) vers le CMS [WordPress](https://fr.wordpress.org/).

**Objectif de l'opération:** on cherche à importer le contenu d'un site sous SPIP dans un site sous WordPress. Ce site contient 896 articles, 13 rubriques, 1220 mots-clés, 689 documents attachés.

**La méthode:** on va générer depuis SPIP un fichier XML au format accepté par WordPress. Pour produire ce fichier, on crée un modèle de page SPIP.

## Informations nécessaires:

1. [Inventaire des contenus du site](infos-contenus.md).
2. [Format XML d'importation WordPress](infos-wp-xml.md). Un peu d'étude pour comprendre le format attendu.
3. [Post ID et relations entre contenus](infos-post-id-et-relations.md)

## Custom Fields

Pour la gestion des Custom Fields:

[ACF](https://www.advancedcustomfields.com/) ou CMB2 ?

- https://github.com/WebDevStudios/CMB2 (a metabox, custom fields, and forms library)
- https://github.com/WebDevStudios/CMB2/wiki/Basic-Usage

**Conclusion:** au final nous utilisons ACF, plus largement adopté et documenté.

ACF est utilisé pour:

- Le "Sur-titre" utilisé pour certains concerts.
- Les photos: champ "Galerie" attaché à un concert (c12_photos).
- Les affiches attachées aux concerts (c12_affiches). Il s'agit également d'un champ "Galerie".

***

Voici d'autres Custom Fields:

Champ surtitre:

```
<wp:postmeta>
  <wp:meta_key>c12_surtitre</wp:meta_key>
  <wp:meta_value><![CDATA[Je suis un surtitre]]></wp:meta_value>
</wp:postmeta>
```


