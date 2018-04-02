# Post ID et relations entre contenus

## Les Post ID

Comportement des Post ID lors de l'import par XML:

Pour chaque item (de type article, page, attachment...), une Post ID est indiquée, comme ceci: 

`<wp:post_id>26</wp:post_id>`

Comportement de WordPress: 

* Si le numéro est libre, il est effectivement attribué. 
* S'il n'est pas libre, WordPress crée de nouveaux numéros par incrémentation.
* La numérotation des ID est utilisée pour les Articles, Pages, Attachments, et autres types de contenus (tous enregistrés dans la table wp_posts). Les termes de taxonomie ont une autre numéroation (et une table: wp_terms).

Dans SPIP: la numération diffère pour les Articles et les Documents (fichiers attachés).

Pour le site SPIP Cave12:

* Les ID des Documents attachés vont de 1 à 1188.
* Les ID des Articles vont de 1 à 907.

## Relier les affiches aux articles

Pour relier les affiches aux articles, différentes stratégies sont possibles.

### Fichier uploadé sur un article

Dans WordPress, un fichier (attachment) uploadé sur un article conserve une relation avec ce dernier. Dans la base de données, le champ "post_parent" de l'attachment contient l'ID de l'article. 

Pour faire fonctionner cela lors de l'import XML, il est nécessaire que les IDs des articles soient maintenus à l'identique.

Dans le code XML, ce champ est écrit ainsi:

`<wp:post_parent>29</wp:post_parent>`

### Image à la une (Featured Image)

Un Post indique sa Featured image ainsi:

```
<wp:postmeta>
  <wp:meta_key>_thumbnail_id</wp:meta_key>
  <wp:meta_value><![CDATA[1497]]></wp:meta_value>
</wp:postmeta>
```

***

Suite: [Stratégie de migration](infos-strategie-migration.md).