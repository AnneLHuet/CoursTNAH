XSLT - Branislav Mezsaros - 31/01/2018

# XML Schema

## Espace de noms : les namespaces

* Pour simplifier l'écriture des noms étendus, on y associe un **préfixe** ( un nom XML) à chaque espace de noms 

* pour pouvoir chercher les éléments, on peut garder le préfixe localement 

* pour déclarer un espace de noms : `<namespace xmlns =""></namespace>`

* En XML Schéma : 
	* on utilise le `xsd:` `xs:`
	`<xsd:element name="commande" type="CommandeType"/>`

## Les types de données 

* il y en a beaucoup, c'est à nous d'analyser ce qui est utile

* [voir : https://openclassrooms.com/courses/structurez-vos-donnees-avec-xml/schema-xml-les-types-simples ]

# Le langage XPath : une technologie XML pour le parcours de l'arbre d'un document
[voir : https://openclassrooms.com/courses/structurez-vos-donnees-avec-xml/xpath-localiser-les-donnees ]

* indique les éléments qui nous intéresse, utilisé avec XSLT. 
* XPath permet de se retrouver dans un document XML : permet de sélectionner des noeuds par navigation
* XPath, recommandation du W3C, première version en 1999. 3éme version en 2015.

## Expression des chemins en XPath 

Une **expression** d'XPath est une **succession d'étapes**

* chemin absolu : 
	* commence à la racine /étape1/étape2
* le chemin relatif : 
	* commence là où je suis (noeud courant)

## Les étapes

* Axe /directions
	* définit le **sens** de la recherche
* un noeud ou un type de noeuds
	* affiner sa recherche avec le nom d'un noeud ou le **type** d'un noeud
* un ou plusieurs prédicats (facultatifs)
	* facultatif
	* nombre n'est pas limité
	* agissent comme un filtre 

>axe::sélecteur[prédicat]

### Les axes 
* premier élément formant une étape
* définit le sens de la recherche avec un vocabulaire précis : 
	* **ancestor** (oriente la recherche vers les **ancêtres du noeud courant**)
	* **ancestor-or-self** (oriente la recherche vers **le noeud courant et ses ancêtres**)
	* **attribute** : oriente la recherche vers **les attributs du noeud courant**)
	* **child** (oriente la recherche vers **les enfants du noeud courant**)
		* axe par défaut, il n'est pas nécessaire de le préciser
	* **descendant** (oriente la recherche vers **les descendants du noeud courant**)
	* **descendant-or-self**(oriente la recherche vers **le nœud courant et ses descendants**)
	* **following** (oriente la recherche vers **les nœuds suivant le nœud courant**)
	* **following-sibling** (oriente la recherche **vers les frères suivants du nœud courant**)
	* **parent** (vers **le père du nœud courant**)
	* **preceding** (vers **les nœuds précédant le nœud courant**)
	* **preceding-sibling** (vers **les frères précédents du noeud courant**)
	* **self**(la recherche est orienté **vers le noeud courant**)
	* **namespace** oriente la recherche vers **un espace de nom**

## Les tests de noeuds

* **nom du noeud** : oriente la recherche vers un nom spécifique de noeud
* **node()** : oriente la recherche vers tous les types de noeuds
	* l'expression `self::node()` peut être simplifiée par `.`
* **\*** : oriente la recherche vers tous les noeuds
* **text()**: oriente la recherche vers les noeuds de type texte
* **processing-instruction**

## Exemples sans prédicats

* `/child::repertoire/child::personne/child::adresse/child::pays`
	* peut être résumé en  `/repertoire/personne/adresse/pays`

## Les prédicats 

* **attribute()** : affine la recherche en fonction d'un attribut
* **count()** : compte le nombre de noeuds
* **last()** : le dernier noeud de la liste
* **position()** : en fonction de la position d'un noeud
* **name()**
* **id()**
* **string-length**