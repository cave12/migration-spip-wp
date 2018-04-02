# Production du XML depuis SPIP

Dans SPIP, un modèle spécial est créé pour produire le code XML nécessaire à l'importation dans WordPress.

Le code pour exporter les mots-clés:

```
<BOUCLE_mots(MOTS){id_groupe=3}{par titre}>
<wp:tag>
  <wp:term_id>#ID_MOT</wp:term_id>
  <wp:tag_slug>#URL_MOT</wp:tag_slug>
  <wp:tag_name><![CDATA[#TITRE]]></wp:tag_name>
</wp:tag></BOUCLE_mots>
```

Le code pour exporter les articles:

```
<B_articles>
[(#REM) - Si plusieurs articles, affiche la liste des articles ]
<BOUCLE_articles(ARTICLES){id_rubrique=1}{annee=2016}{par date}{0, 5}>
  <item>
    <title>[(#TITRE)]</title>
    <link>#URL_SITE_SPIP/#URL_ARTICLE/</link>
    <pubDate>[(#DATE|affdate{'D, d M Y H:i:s +0000'})]</pubDate>
    <dc:creator><![CDATA[manu-s]]></dc:creator>
    <guid isPermaLink="false">#URL_SITE_SPIP/#URL_ARTICLE/</guid>
    <description/>
    <content:encoded><![CDATA[[(#TEXTE|image_reduire{500,0})]
  ]]></content:encoded>
    <excerpt:encoded><![CDATA[[(#CHAPO)]]]></excerpt:encoded>
    <wp:post_date>[(#DATE|affdate{'Y-m-d H:i:s'})]</wp:post_date>
    <wp:post_name>#URL_ARTICLE</wp:post_name>
    <wp:status>publish</wp:status>
    <wp:post_parent>0</wp:post_parent>
    <wp:post_type>post</wp:post_type>
    <category domain="category" nicename="concerts"><![CDATA[Concerts]]></category>
    <B_artistes><BOUCLE_artistes(MOTS) {id_article} {id_groupe=3}>
    <category domain="post_tag" nicename="[(#URL_MOT)]"><![CDATA[[(#TITRE)]]]></category></BOUCLE_artistes></B_artistes>
    <wp:postmeta>
      <wp:meta_key>_mem_start_date</wp:meta_key>
      <wp:meta_value><![CDATA[[(#DATE|affdate{'Y-m-d H:i'})]]]></wp:meta_value>
    </wp:postmeta>
  </item>
</BOUCLE_articles>
</B_articles>
[(#REM) AUCUN RESULTAT]
<//B_articles>
```

