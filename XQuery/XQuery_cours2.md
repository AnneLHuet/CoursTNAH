XQuery -  Cours 2 du 5 février

# BaseX

## Exercices

Je cherche toutes les villes ayant une capitale (tous les éléments city ayant l'attribut (ciblé par @) is_country_cap="yes"
//city[@is_country_cap="yes"]

## Le protocole Web dav 

Protocole (deux services communicant entre eux). Web dav : communique avec un serveur distant qui apparaît comme un dossier. Si l'on souhaite faire de la base "mondial" un répertoire commun par exemple. BaseX permet d'avoir un serveur de fichier que l'on peut utiliser.

## API Rest

Permet l'accés aux documents dans une ressource XML

# XQuery

Conçu comme une extension d'XPath, qui permer d'interroger un fichier XML. Notion de chemin, de filtres et de prédicat. XQuery se positionne plus comme un langage d'adressage, interroger des collections de documents.

## XPath
 Les axes (ancestor, namespace...), les filtres ( \*, node(), text(), comment(), processing-instruction()...)
 Les noeuds texte : est induit en XSLT, là où il faut le préciser en XQuery

 En XPath : les fonctions 
 	* (par exemple concat()) `concat("le","petit","chat")` en XQuery `"le"||"petit"||"chat"`
 	* count(/book/*) (compter le contenu d'une séquence)
 	* `/book/*[starts-with(text(),'la')`

## XQuery
En XQuery, quand on cherche un élément on précise tooujours le noeud text(). 
XQuery est un langage typé:
	* element(), attribute(), text(), comment()
	* xs: string, xs: integer
Il est parfois nécessaire de réaliser des conversions
	* Afficher les valeurs d'attributs
L'environnement XQuery est entre choses, une calculatrice : il accepte les opérations arithmétiques. La fonction number permet une conversion en chiffre

Quand on souhaite afficher un attribut, il faut le convertir en chaîne de caractère. Ne considère pas les attribut d'un élément comme un noeud text()

XQuery est composé de plusieurs expressions, qu'il est possible de combiner dans une requête (expressions de chemins, expression FLOWR, expression booléenne, expression de séquence)
pur écrire un commentaire `(: écrire un commentaire :)`

### Les expressions FLOWR
* **For**
```
for $city in doc("db/tp/mondial.xml")//city
	return $city
```
	* on peut également écrire par exemple ```return "ville "||$city```
	* on peut ajouter une deuxième variables dans la séquence
* **Let**
	* définir une constante avec :=
	* permet de réccourcir le code en évitant de répéter les chemins
	* on peut faire plusieurs déclarations de varibales en répétant let ou en séparant par des virgules
```
let $doc := doc("db/tp/mondial.xml")
  return $doc//city/name/text()
```

* **Order by**
	* ascending / descending
	* permet de trier une séquence selon un ou plusieurs critères et s'utilise nécessairement dans une expression for

* **Where**
	* filtrer une séquence
	* se situe entre un for et un return
	* on peut se passer des prédicats XPath et mettre un Where à la place. Permet de mieux lire la requête
Return

## TP
`collection("db/tp/notices")`

`doc("db/tp/mondial.xml")//country` afficher l'ensemble des éléments pays du document mondial.xml

`doc("db/tp/mondial.xml")//country/name/text()`

`string (doc("db/tp/mondial.xml")//country[name='France']/@capital)`

```
for $theme in distinct-values(collection("db/tp/notices")//THEME/text())
	return $theme
```

(distinct-values permet d'éviter la redondance des informations)

