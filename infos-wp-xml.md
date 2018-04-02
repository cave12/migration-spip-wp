# Importation XML dans WordPress 


Un peu d'étude pour comprendre le format attendu:

http://wordpress.stackexchange.com/questions/82399/what-is-the-required-format-for-importing-posts-into-wordpress

## Structure du XML WordPress

Voici comment est structuré le code XML exporté depuis WordPress:

Ordre des éléments dans le fichier XML exporté depuis WP:

- authors
- wp:category
- wp:tag
- wp:term
- contenus: pages, articles, ...

### Les auteurs

Le fichier contient une liste des auteurs, sous cette forme:

```
<wp:author>
  <wp:author_id>6</wp:author_id>
  <wp:author_login><![CDATA[loginname]]></wp:author_login>
  <wp:author_email><![CDATA[email@example.com]]></wp:author_email>
  <wp:author_display_name><![CDATA[Display Name]]></wp:author_display_name>
  <wp:author_first_name><![CDATA[First]]></wp:author_first_name>
  <wp:author_last_name><![CDATA[Last]]></wp:author_last_name>
</wp:author>
```

### Les catégories

Le ficher contient une liste des catégories:

```
<wp:category>
  <wp:term_id>1</wp:term_id>
  <wp:category_nicename>concerts</wp:category_nicename>
  <wp:category_parent></wp:category_parent>
  <wp:cat_name><![CDATA[Concerts]]></wp:cat_name>
</wp:category>
```

### Les tags (étiquettes)

```
<wp:tag>
  <wp:term_id>47</wp:term_id>
  <wp:tag_slug>acid-mothers-temple</wp:tag_slug>
  <wp:tag_name><![CDATA[Acid Mothers Temple]]></wp:tag_name>
</wp:tag>
```

### Les taxonomies

Si le site contient des taxonomies custom, le XML contient une liste sous cette forme:

```
<wp:term>
  <wp:term_id><![CDATA[19]]></wp:term_id>
  <wp:term_taxonomy><![CDATA[type_de_projet]]></wp:term_taxonomy>
  <wp:term_slug><![CDATA[photographie]]></wp:term_slug>
  <wp:term_parent><![CDATA[]]></wp:term_parent>
  <wp:term_name><![CDATA[Photographie]]></wp:term_name>
</wp:term>
```

Il n'est cependant pas nécessaire de créer les catégories/tags/taxonomies de cette manière. En effet, elles sont également déclarées dans le code XML des contenus, et WordPress va les créer à la volée durant l'importation.

Dans un article, les taxonomies sont déclarées de manière simplifiée (pour une Catégorie, un Tag, une taxonomie "Lieux"):

```
<category domain="category" nicename="concerts"><![CDATA[Concerts]]></category>
<category domain="post_tag" nicename="Joke-Lanz"><![CDATA[Joke Lanz]]></category>
<category domain="lieux" nicename="ilot-13"><![CDATA[Ilôt 13]]></category>
```

## Les contenus:

Le fichier XML contient tout type de contenus WordPress: Posts, Pages, Champs ACF (acf-field), fichiers attachés (attachment)...

### Article

```
<item>
	<title>THE AMES ROOM</title>
	<link>http://cave12.org/the-ames-room/</link>
	<pubDate>Tue, 31 Jan 2012 20:00:00 +0000</pubDate>
	<dc:creator><![CDATA[manu-s]]></dc:creator>
	<guid isPermaLink="false">http://www.cave12.org/THE-AMES-ROOM/</guid>
	<description></description>
	<content:encoded><![CDATA[<p>Concert de jazz free</p>]]></content:encoded>
	<excerpt:encoded><![CDATA[<p>MARDI 31 JANVIER</p>]]></excerpt:encoded>
	<wp:post_id>1492</wp:post_id>
	<wp:post_date>2012-01-31 21:00:00</wp:post_date>
	<wp:post_date_gmt>2012-01-31 20:00:00</wp:post_date_gmt>
	<wp:comment_status>closed</wp:comment_status>
	<wp:ping_status>closed</wp:ping_status>
	<wp:post_name>the-ames-room</wp:post_name>
	<wp:status>publish</wp:status>
	<wp:post_parent>0</wp:post_parent>
	<wp:menu_order>0</wp:menu_order>
	<wp:post_type>post</wp:post_type>
	<wp:post_password></wp:post_password>
	<wp:is_sticky>0</wp:is_sticky>
	<category domain="category" nicename="concerts"><![CDATA[Concerts]]></category>
	<wp:postmeta>
		<wp:meta_key>_mem_start_date</wp:meta_key>
		<wp:meta_value><![CDATA[2012-01-31 21:00]]></wp:meta_value>
	</wp:postmeta>
</item>
```

### Attachement

Code d'un attachment (fichier SVG):

```
<item>
  <title>example attachment</title>
  <link>https://example.com/page/attachment/example/</link>
  <pubDate>Fri, 25 Aug 2017 19:29:14 +0000</pubDate>
  <dc:creator><![CDATA[mschmalstieg]]></dc:creator>
  <guid isPermaLink="false">http://example.com/wp-content/uploads/2017/08/example.svg</guid>
  <description></description>
  <content:encoded><![CDATA[]]></content:encoded>
  <excerpt:encoded><![CDATA[]]></excerpt:encoded>
  <wp:post_id>31</wp:post_id>
  <wp:post_date><![CDATA[2017-08-25 21:29:14]]></wp:post_date>
  <wp:post_date_gmt><![CDATA[2017-08-25 19:29:14]]></wp:post_date_gmt>
  <wp:comment_status><![CDATA[open]]></wp:comment_status>
  <wp:ping_status><![CDATA[closed]]></wp:ping_status>
  <wp:post_name><![CDATA[75e_]]></wp:post_name>
  <wp:status><![CDATA[inherit]]></wp:status>
  <wp:post_parent>29</wp:post_parent>
  <wp:menu_order>0</wp:menu_order>
  <wp:post_type><![CDATA[attachment]]></wp:post_type>
  <wp:post_password><![CDATA[]]></wp:post_password>
  <wp:is_sticky>0</wp:is_sticky>
  <wp:attachment_url><![CDATA[http://example.com/wp-content/uploads/2017/08/example.svg]]></wp:attachment_url>
  <wp:postmeta>
    <wp:meta_key><![CDATA[_wp_attached_file]]></wp:meta_key>
    <wp:meta_value><![CDATA[2017/08/75e_.svg]]></wp:meta_value>
  </wp:postmeta>
</item>
```

