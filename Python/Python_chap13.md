# Chapitre 13 - Ecrire des tests

* vérifier : 
	* le fonctionnement des blocs programmés séparément
	* l'interraction des différents blocs
	* la partie graphique de l'application
	* les modifications futures

## Les tests en python 

* existe plusieurs librairies en python : 
	* `unittest`
	* `nosetest` installable via `pypi` (rétrocompatible avec `ùnittest`)
	* `py.test` qui utilise beaucoup `assert`

## Concepts fondamentaux de la rédaction de test 

### test unitaire et test d'intégration 

### `setÙp` et `tearDown`

### les `fixtures`

* données temporaires permettant de vérifier la validité des tests.
* soit on les installe au niveau du set-up soit on les insére au fur et à mesure.

### les `Mocks`

* fonction qui va venir remplacer une autre fonction capable d'échouer
* n'est pas développé dans le cours mais liens vers tuto en ligne

sqlite : moteur de bases de données 



# Utilisation de Pycharm 

* Pycharm peut fonctionner avec l'environnement virtuel que l'on a crée. Il vérifie le requirements

* création du dossier
* cloner le repository

* création de l'environnement virtuel dans pycharm (une fenêtre qui correspond au terminal)
	* paramètre / projet / interpreter > l'env virtuel crée

* très pratique au niveau des tests. 
	