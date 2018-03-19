# Importation XML dans WordPress 

Les différents modèles de pages du site http://www.cave12.org/ :

- La homepage : liste le programme (les concerts à venir).
- Concert: infos du concert.
- Page archive (par année).
- Page artiste: affiche une liste de concerts.
- Affiches: montre les affiches (3 auteurs).
- Affiche par auteur: toutes les affiches d'un auteur.

Les données qu'il faut exporter pour chaque article:

- titre
- sur-titre  = utilisé pour des infos style "La cave12 à l'Ecurie (#196)" = custom field (c12_surtitre)
- chapeau = en-tête. On va l'assigner au champ "Extrait" de WordPress.
- contenu (texte/html)
- URL
- date de début (spip: DATE DE PUBLICATION EN LIGNE)
- mots-clés (groupe Artistes)
- mots-clés (groupe Lieux)
- Fichier attaché (affiche en format PDF) => trouver solution PDF + vignette (utiliser les champs répétables ACF?)

Infos qu'on ne récupère pas:

- Composition = utilisé pour des événements-séries (Akouphène, Bains des Pâquis, MAC, Pianos).
- Date de fin (DATE DE RÉDACTION ANTÉRIEURE) = pour les événements de plusieurs jours. Sera géré au cas par cas.
