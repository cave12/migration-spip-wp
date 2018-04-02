
# Stratégie de migration

Deux stratégies possibles:

### Méthode A: Documents first

1. Importer d'abord **les Documents** (leurs IDs resteront correctes).
2. Importer ensuite les Articles: leurs ID seront nouvelles, mais ils seront liés aux bons fichiers.

Cette méthode sera préférable si les attachments sont intégrés via des **galeries ACF**.

### Méthode B: Articles first

1. Importer d'abord **les Articles** (leurs IDs seront correctes).
2. Importer ensuite les Documents, en les liant aux articles via leurs champs "post_parent". 
 
Cette méthode sera préférable si les attachments sont liés via le **Post Parent**. Mais cela ne permet pas facilement de différencer les attachements "photos" des "affiches".

### PDFs et vignettes

Note concernant les **prévisualisations JPG des PDF**: dans WordPress, [depuis WP 4.7 (décembre 2016)](https://make.wordpress.org/core/2016/11/15/enhanced-pdf-support-4-7/), les prévisualisations sont **calculées automatiquement**. Il n'est plus nécessaire de les ajouter comme fichiers séparés! 

On peut donc simplifier le champ ACF des affiches: un champ "Galerie ACF" suffit.

## Champ ID originel 

Pour permettre toutes sortes de corrections post-opératoires, on va créer pour chaque item (article, attachment) un *Custom Field* qui contiendra son **ID originel**: 

* `c12_spip_doc_id` = ID originel pour les documents.
* `c12_spip_article_id` = ID originel pour les articles
* `c12_spip_linked_article` = ID de l'article lié à un document.
* `c12_spip_linked_doc` = ID du document lié à un article.

```xml
<wp:postmeta>
  <wp:meta_key>c12_spip_doc_id</wp:meta_key>
  <wp:meta_value>123</wp:meta_value>
</wp:postmeta>
```

### Champ Galerie ACF

Un champ ACF "Galerie" est créé pour les affiches. Ce champ sera enregistré sur l'article, et comportera l'ID du fichier-attachment. Pour que cela fonctionne, les IDs des fichiers attachés doivent être maintenus à l'identique.

Voici comment une galerie d'images ACF se présente dans le code:

```xml
<wp:postmeta>
  <wp:meta_key>c12_photos</wp:meta_key>
  <wp:meta_value><![CDATA[a:1:{i:0;s:4:"1497";}]]></wp:meta_value>
</wp:postmeta>
```

Galerie avec 2 éléments:

```xml
<wp:postmeta>
  <wp:meta_key>c12_photos</wp:meta_key>
  <wp:meta_value><![CDATA[a:2:{i:0;s:4:"1497";i:1;s:4:"1496";}]]></wp:meta_value>
</wp:postmeta>
```

Galerie avec 3 éléments:

```xml
<wp:postmeta>
  <wp:meta_key>c12_photos</wp:meta_key>
  <wp:meta_value><![CDATA[a:3:{i:0;s:4:"1506";i:1;s:4:"1497";i:2;s:4:"1502";}]]></wp:meta_value>
</wp:postmeta>
```

Si on désérialise ces données:

```
array
(
    [0] => 1506
    [1] => 1497
    [2] => 1502
)
```

***

Suite: [Code pour l'exportation depuis SPIP](infos-wp-xml-from-spip.md).