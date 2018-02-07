XSLT - Branislav Mezsaros - 07/02/2018

## Les espaces de noms

* permet la réutilisation d'un vocabulaire particulier
	* le vocabulaire permettant décrire une page xHTML
	* le vocabulaire permettant de décrire un schéma XML

* la déclaration se fait dans le premier élément
	* mon espace de nom défini, tout ce qui est dans ce fichier est définit par celui-ci

* identifié par une URI (Uniform Resource Identifier)
	* On distingue les URL (Uniform Resource Locator) et les URN (Uniform Resource Name)

* On déclare un espace de nom avec l'attribut `xmlns=""` 
	`xmlns="mon_uri"`

* Quand il y en a plusieurs, il est parfois nécessaires de les préciser : 
`xmlns:prefixe="mon_uri"`

* exemple : `<html xmlns="http://www.w3.org/1999/xhtml">`
	* tous les éléments utilisés dans ce document XML font partie du vocabulaire d'une page xHTML

* Lorsqu'un espace de noms est déclaré avec un préfixe, tous les éléments qui appartiennent au vocabulaire, et donc à l'espace de noms, doivent être précédés par ce préfixe

```
<http:html xmlns:http="http://www.w3.org/1999/xhtml">

    <http:head>

        <http:title>Titre du document</http:title>

    </http:head>

    <http:body>
    	<http:p>
    	</http:p>
    </http:body>
```

* on peut également imbriquer les espaces de noms

``` XML
<!-- il est possible d'utiliser l'espace de noms http -->
<http:html xmlns:http="http://www.w3.org/1999/xhtml">
    <http:head>
        <http:title>Titre du document</http:title>
    </http:head>
    <http:body>
        <http:p>
           <!-- il est possible d'utiliser l'espace de noms ml -->
           <ml:math xmlns:ml="http://www.w3.org/1998/Math/MathML">
               <ml:matrix>
                   <ml:matrixrow>
                       <ml:cn>0</ml:cn>
                       <ml:cn>1</ml:cn>
                       <ml:cn>0</ml:cn>
                   </ml:matrixrow>
                   <ml:matrixrow>
                       <ml:cn>0</ml:cn>
                       <ml:cn>0</ml:cn>
                       <ml:cn>1</ml:cn>
                   </ml:matrixrow>
               </ml:matrix>
           </ml:math>
           <!-- il n'est plus possible d'utiliser l'espace de noms ml -->
        </http:p>
    </http:body>
</http:html>
<!-- il n'est plus possible d'utiliser l'espace de noms http -->

```

* La règle qui régit la portée d'un espace de noms est assez simple : **un espace de noms est utilisable tant que l'élément qui le déclare n'est pas refermé.**

* quelques exemples d'espace de noms : 
	* **DocBook** : décrit des documents techniques (livre article etc...) (http://docbook.org/ns/docbook)
	* **MathML** : afficher des éléments mathématiques divers et variés comme des additions, des soustractions, des matrices, etc... (http://www.w3.org/1998/Math/MathML)
	* **SchémaXML** : décrire des Schémas XML http://www.w3.org/2001/XMLSchema
	* **XSLT** : décrire des transformations à appliquer à un document XML http://www.w3.org/1999/XSL/Transform

* Voir avec XPath

## En résumé 

* un espace de nom a un identifiant unique par une URI
* se déclare dans le premier élément avec l'attribut `xmlns=""`
