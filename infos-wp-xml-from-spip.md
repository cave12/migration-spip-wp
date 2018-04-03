# Production du XML depuis SPIP

Dans SPIP, un modèle ("squelette") spécial est créé pour produire le code XML nécessaire à l'importation dans WordPress. Pour appliquer le squelette:

- Créer dans l'admin de SPIP une rubrique "Export", et un Article "Export-WP". Relever l'ID de la rubrique.
- Nommer le squelette pour qu'il corresponde à la rubrique, p.ex. article-42.html (si l'ID de la rubrique est 42).
- Visiter l'article Export-WP, copier-coller le code source, et l'enregistrer dans un `fichier.xml`.
- Importer le fichier XML dans WordPress, via *Outils > Importer*.

## Les mots-clés

Le code pour exporter les mots-clés: [export-mots.html](https://github.com/cave12/migration-spip-wp/blob/master/code-spip/export-mots.html)

```
<BOUCLE_mots(MOTS){id_groupe=3}{par titre}>
<wp:tag>
  <wp:term_id>#ID_MOT</wp:term_id>
  <wp:tag_slug>#URL_MOT</wp:tag_slug>
  <wp:tag_name><![CDATA[#TITRE]]></wp:tag_name>
</wp:tag></BOUCLE_mots>
```

## Articles

Le code pour exporter les articles:

[export-articles.html](https://github.com/cave12/migration-spip-wp/blob/master/code-spip/export-articles.html)

Le code inclut des boucles spéciales:

Une boucle pour obtenir le mot-clé "Artiste":

```
<BOUCLE_artistes(MOTS){id_article}{id_groupe=3}>
  <category domain="post_tag" nicename="[(#URL_MOT)]"><![CDATA[[(#TITRE)]]]></category></BOUCLE_artistes>
```

Une boucle pour obtenir les documents liés (dans le groupe 3, donc des affiches). **Complexité:** le code sera différent selon le nombre d'affiches... Il faut produire un Array() PHP, et le sérialiser.

Quelques infos sur la manière de faire ça avec SPIP: 

* [https://www.spip.net/fr_article4009.html](https://www.spip.net/fr_article4009.html)
* [|table_valeur](https://www.spip.net/fr_article4572.html)


```
<B_docs>
#SET{c12_affiches,array(}
<BOUCLE_docs(DOCUMENTS){id_document}{id_article}{id_groupe=3}>
#SET{c12_affiches,|concat{#GET{c12_affiches},#ID_DOCUMENT}
</BOUCLE_docs>
</B_docs>
```


## Documents

Voir le code : [export-documents.html](https://github.com/cave12/migration-spip-wp/blob/master/code-spip/export-documents.html)

### Boucle principale DOCUMENTS:

Si on écrit la boucle ainsi...

```
<BOUCLE_docs(DOCUMENTS){0,1999}{par id_document}>
```

...seulement 620 documents sont retournés sur 689.

La raison: il y a 69 documents **non publiés** (ils ne sont attachés à aucun article).

On peut les inclure, en écrivant la boucle ainsi:

```
<BOUCLE_docs(DOCUMENTS){tout}{0,1999}{par id_document}>
```

Mais on a alors 1149 documents, y compris les *thumbnails* des PDFs (le mode vignette)! Pour les exclure, il faut ajouter: {mode != vignette}. 

Le code final:

```
<BOUCLE_docs(DOCUMENTS){tout}{mode != vignette}{0,1999}{par id_document}>
```

Le code inclut des boucles spéciales pour des données supplémentaires:

Une boucle pour obtenir **la taxonomie "Affiche par"**:

```xml
<BOUCLE_mots(MOTS){id_document}>
  <category domain="affiches" nicename="#URL_MOT">[par (#TITRE)]</category>
</BOUCLE_mots>
```

Une boucle pour obtenir **le concert lié au document**:

```xml
<BOUCLE_article_lie(ARTICLES) {id_document}><wp:postmeta>
  <wp:meta_key>c12_spip_linked_article</wp:meta_key>
  <wp:meta_value>#ID_ARTICLE</wp:meta_value>
</wp:postmeta></BOUCLE_article_lie>
```

***