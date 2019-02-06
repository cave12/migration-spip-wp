# Exécution de l'exportation

Les différents modèles étant prêts, il est temps de procéder à l'exportation. Voici les étapes:

1. Exportation d'un XML avec tous les fichiers Documents.
2. Importation dans WP.
3. Exportation d'un XML avec tous les articles.
4. Importation dans WP.

## Etape 1 : exportation des Documents

Constat après le processus 1: le fichier XML contenant les 689 documents (poids du XML: 680 KB) passe sans problème. Tous les fichiers sont importés. Le temps de traitement est d'environ 4 minutes sur une installation MAMP locale. Sur un hébergement professionnel, le temps d'importation est de 1:55 min.

- Comme prévu, les ID des documents sont respectés.

Attention: bien régler les formats des médias de WordPress, car c'est pendant cette importation que les images sont redimensionnées.

Note: il est possible que les limites d'exécution de votre hébergeur ne permettent pas à l'importation de s'effectuer entièrement.

## Etape 2 : exportation des Articles

Le fichier XML exporté contient 851 articles. Ils sont plus riches en texte, on a donc un XML pesant 4.5 Mb.

Le processus d'importation prend environ 1 minute - la vitesse d'insertion dans la base de données est donc de 14 articles / seconde.

**Conclusion:** la technique fonctionne à merveille!

***