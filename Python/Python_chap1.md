# Chapitre 1 : les variables 

* valeur 
* assignation de valeur (**assignment**)
* différence entre variables et valeurs 
* chaînes (**string**) 
* nombre entiers (**integer**) 
* faire évoluer des variables 

## Manipulation de chaîne

* **Concaténation** : ajouter une chaîne de caractère à une chaîne de caractère
* **Indexation**: permet d’accéder à chacun des caractères d’une chaîne. En python l’index démarre toujours à 0.
* pour accéder à une chaîne depuis l’arrière : `chaîne = [-1]`
* la fonction `len()` retourne la longueur de la chaîne
* Index de tranches (slices). 
	* Ex : `chaîne = variablex[0:2]`

## Les listes

* `split()` transforme une phrase en une liste de mots. Ex : `mots = phrase.split()`
* liste : permet d’enregistrer plusieurs valeurs. On accède à ces valeurs en utilisant les index et tranches.
* **append**: ajouter des objets à une liste
* remplacer la valeur d’une liste : 
	* ex : `bonnes_lectures[0] = ‘Dracula’` (il n’est pas possible de le faire pour une chaîne de caractères.) 
* **remove()** : supprimer un élément d’une liste
* **sort()** : permet de trier une liste

### Les listes imbriquées (*nested list*)

Liste contenant des listes 

## Les dictionnaires

* Se composent d’entrées (*keys*) qui contiennent des valeurs `dictionnaire = {‘key1’ : ‘valeur1 ‘,’key2’: ‘valeur2’}`
* on parle également d’indexation
	* `.keys` permet de retrouver la liste des **index** 
	* `.values` permet de retrouver la liste des **valeurs**
	* `.items` permet de demander les paires **(clé,valeur)**

## Générateurs

* Ne supportent pas l’indexation
* même propriétés globales que les listes

## Tuples

* Listes simplifiées et immutables
	* ex : `titre, note = bonne_lecture_tuple[0]`
* on peut « dézipper » un tuple
	* ex : `x,y =(1,2)`

## Les conditions
**faire très attention à l’indentation (conventionnellement : 4 espaces)**

## Les conditions simples
* si, ou si et sinon ( **if, elif and else**)
* et, ou, non (**and, or, not**)
* **and** permet de juxtaposer deux expressions qui doivent être vraies
* **not** teste les conditions qui ne sont pas vraies

## Les boucles

* **for** permet d'itérer à travers n'importe quel objet itératif et effectuer des actions sur ses éléments
* **for x in iterable**

## Chapitre 2 : Les fonctions et les fichiers

### Lire des fichiers
Ouvrir un fichier :
open(‘emplcement/nomdufcihier)
TextIOWrapper 
s’affiche après l’ouverture d’un fichier avec print(nom_du_fichier_ouvert)
indique que python a ouvert une connexion au fichier
donne des informations concernant l’encodage d’un fichier ouvert
lire un fichier :
nom_du_fichier.read()
fermer un fichier :
nom_du_fichier.close
with... as ...: concerne l’ensemble du bloc ouvert en dessous :
ex : with open (‘emplacement_du_fichier ‘) as (en tant que) nom_variable
avec le fichier ouvert … en tant que variable nom_variable
assert …, …
permet une vérification : 
ex : assert nom_variable_a_verifier == x, ‘le bon résultat est x’
Ecrire une fonction
Count
prend comme argument l’élément que l’on veut compter
ex : texte.count(‘e’)
attention : diffèrence entre chaine et mot !
La chaine ‘et’ peut être trouver plus de fois que le mot ‘et’. Pour rechercher la récurrence du mot ‘et’texte.count(‘et’)
split()
divise une chaîne sur les espaces et retourne une liste de plus petites chaînes
ex mots = texte.split()
arguments ou paramètres : sont les éléments dont la fonction a besoin
arguments/args ou parameters/param
valeur de return (return value) : est la résultat de la fonction
Une méthode est une fonction particulière mais régie par le même vocabulaire
définition d’une fonction :
def nom_de_la_fonction (param1, param2, param3) :
def fonction_sans_parametre () :
fonctions peuvent avoir une valeur de retour permettant d’accéder aux résultats calculés dans la fonction : 
return
scope
capacité à accéder à des variables à différents endroits du code.
Les variables dans les fonctions ont une portée limitées à la fonction. C’est pourquoi on utilise la déclaration return
fonction de décompte plus générale

set = permet d’éviter les doublons
ex : unique_x = set(x)
un set n’est pas ordonné et ne s’utilise donc pas comme un index
on ajoute des valeurs avec add()
documenter une fonction : 
méthode shpinx entre ‘’’ :
description de la fonction
:param mots: Liste de mots
:type mots: list
:returns: Dictionnaire où les clefs sont les mots et les valeurs le nombre d'occurrences
:rtype: dict
Nettoyer des données textuelles : 
tâches importantes du métier
méthodes et fonctions permettent de nettoyer un texte
expressions régulières sont cependant beaucoup plus efficaces
replace
sans_point = phrase.replace(‘.’,’’)
possible de faire des replace à la suit
sans_point = phrase.replace(‘.’,’’).replace(‘u’,’’)
lower() : pour les majuscules
Ecrire dans un fichier : 
mode = ‘r’ : on est en mode lectures
mode = ‘w’ : on est en mode écriture
Les arguments optionnels ou défaut de python
possible de définir des paramètres par défaut en python :
= ‘valeur_par_defaut’
en python, on peut utiliser des paramètres nommés : 
keyword argument (kwargs)