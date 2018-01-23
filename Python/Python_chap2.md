# Chapitre 2 :Les fonctions et les fichiers

## Lire des fichiers
* **ouvrir un fichier** 
	`fichier_ouvert = open('chemindufichier')`

* **modifier le modèle d'encodage d'un fichier_ouvert** 
	`encodage_latin = open('chemin', encoding='latin')`

* **lire le contenu d'un fichier (la fonction .read fonctionne sur les objets TextWrapper)** 
	`print(fichier_ouvert.read())`

* **assigner à une variable le contenu d'un fichier**

>`fichier_ouvert = open('chemin')`
`texte = fichier_ouvert.read()`

* **toujours penser à fermer un fichier que l'on a ouvert une fois lu**
`fichier_ouvert.close`

* **il existe une autre syntaxe pour gérer un fichier à ouvrir et lire**
	* dans cette méthode, le fichier se ferme de lui même
	* les variables modifiées dans cet ensemble sont encore disponible à la fin. Mais le fichier sera clos

`with open("chemin") as fichier_cid: `
`texte = fichier_cid.read()`


## Ecrire une fonction

* La méthode **count**
>`nombre_de_e = texte.count("e")`
`print(nombre_de_e)`

* **split()** divise une chaine de caractère sur ses espaces
`print(texte.split())`
	* on peut diviser la chaine texte en une liste de mots
	`mots = texte.split()`

* On définit une fonction et ses paramètres 
	* ici ma fonction = compter_dans_une_autre_chaine et mes paramètres sont `aiguille` et botte_de_foin

>`def compter_dans_une_autre_chaine(aiguille, botte_de_foin):`
    `mots_de_foin = botte_de_foin.split()`
    `nombre_daiguilles = mots_de_foin.count(aiguille)`
    `return nombre_daiguilles`

* on peut ensuite appeler la fonction, dans ce cas précis pour par exemple compter le nombre de 'à' dans notre texte
`print(compter_dans_une_autre_chaine("à", texte))`

## éviter les doublons avec set

* on peut ajouter une valeur à **set()** avec **.add**
`unique_x.add("test")`

* permet de simplifier nos fonctions :

>`def comptage2(mots):`
    `sans_doublon = set(mots)`
    `compteur = {}`
    `for mot in sans_doublon:`
        `compteur[mot] = mots.count(mot)`
        `print(mot)`
    `return compteur`

## documenter une fonction : méthode sphinx RestrucTuredText (RST)

`def comptage2(mots):`
    `""" Compte et stocke le décompte de chaque mot dans une liste de mots`

    `:param mots: Liste de mosts`
    `:type mots: list`
    `:returns: Dictionnaire où les clefs sont les mots et les valeurs le nombre d'occurrences`
    `:rtype: dict`
    `"""`
    `sans_doublon = set(mots)`
    `compteur = {}`
    `for mot in sans_doublon:`
        `compteur[mot] = mots.count(mot)`
    `return compteur`

## Nettoyer des données textuelles

* la méthode **lower** pour les majuscules

`x = 'E'`
`x_lower = x.lower()`
`print(x_lower)`

* La méthode **replace** qui prend deux arguments

`phrase = 'Mais. Arrêtez. De. Me. Couper. Dans. Mon. Élocution. S\'il. Vous. Plait'`
`sans_points = phrase.replace(".", "")`

## On peut vérifier qu'une ligne commence par une chaîne de caractère en utilisant .startswith(chaine) :
`print("Pour le desir que j’ay de vous veoir.".startswith("Pour"))`
`print("Pour le desir que j’ay de vous veoir.".startswith("POUR"))`
`print("Pour le desir que j’ay de vous veoir.".startswith("le desir"))`

