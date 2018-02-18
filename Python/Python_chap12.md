Python chapitre 12 - Thibault Clérice

# Chapitre 12 - Créer une API

## API (Application Programming Interface)

* système informatique prévue pour la communication de **données** ou de **fonctions**

* Exemple : les services d'autocomplétion pour les fromaulaires de recherche

* simplifier les données pour avoir une réutilisation simple (html n'est pas un format d'API)
	* recommandé de passer par du JSON : pour le poids, simplifier le parsage etc..
		* quand nos données ressemble à des objets
	* également XML (débat éternel entre les deux)
		*  préférable quand on a un texte avec de nombreuses variations (alternance de texte et de balises)
	* **Voir articles mentionnés dans le cours sur la question**

## Jsonify

* permet de transformer nos variables en format JSON
* la fonction `render_templates` génére un objet Response (corps, en-tête, status)
	* il va être nécessaire de préciser que le renvoi = en JSON

* sérialiser : prendre un objetx et l'exposrter dans un autre format
	* seuls les listes, les booléens, les dictionnaires sont sérialisables en JSON
	* solutions étant de transformé nos objets qui ne sont pas sérialisables en liste ou dictionnaire
