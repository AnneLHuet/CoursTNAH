XSLT - Branislav Mezsaros - 17/01/2018

# XML - DTD - XSD - XPath - XSLT

Deux séances tournées vers XPath pour comprendre XSLT

## XML

### Qu'est-ce que XML ?

* **eXtensible Markup Language**
* Extensible
* Langage de balisage

Permet principalement de créer d'autre langage de manipulation des données : 
* SOAP = un protocole d'échange au format XML qui décrit la manière dont les applications doivent communiquer entre elles
* Principalement pour stocker, ranger les données, en leur ajoutant un aspect **sémantique**. On peut même utiliser les fichiers XML pour alimenter les bases de données. 

Certains documents posent des problèmes d'interopérabilité. On peut parfaitement créer des bdd en XML, (même si ce n'est pas des BDD relationnelle). Principe de stockage.



On peut intégrer des données Mysql en XML (pour l'intégrer à un site par exemple.). Aujourd'hui, sous windows, pour améliorer le système, le format XML constitue la base.

XHTML : grand débat depuis l'apparition d'HTML 5 sur sa pertinence. 

### Un document XML

Commence par `<?xml` pour indiquer le format `?>` permet d'indiquer l'encodage. 
**Toujours préciser l'encodage d'un fichier**

Dans ce cours : comment traduire un fichier XML en DTD.

Un fichier valide respecte "la grammaire". Un fichier valide n'est pas forcément bien formé et inversement.

### Un document XML bien formé

Il ne doit exister qu'une seule balise racine. Toutes les balises doivent être fermées. Les noms de balises doivent impérativement commencé par une **lettre ou "\_"** ne pas contenir **"** ou **-** etc.

Eviter au maximum les accents dans les noms de balises (mais cependant reste correct dans l'encodage du fichier lui même). (ASCII American Standard Code for Information Interchange)
Avec **unicode**, on est confronté à un autre problème : on peut l'utiliser mais pose des problématique dans son utilisation d'une application à l'autre.

Certains éléments ne peuvent pas faire parti d'un fichier XML : 
	* & devient `&amp`
	* < devient `&lt`
	* > devient `&gt`
	* ' devient `&apos`
	* " devient `&quot`
 Faire attention aux noms de variables et aux noms d'attributs.

Exercice : 
```XML

<t> (<!--élément racine-->
	Hello
	<a> </a>
	<l5/>
	<b x="5" x="7"/>
	<p>
		<r></r>
	</p>
	<e>x &lt; <3</e>
	<t> M &amp; M</t>
	<x t="\"\""/>
</t>

```

## DTD et XSD
### Un document valide

Un document qui peut être reproduit, modifié et mis à jour par une personne qui ne l'a pas crée. 

Correspond à une "gramaire" : comment manipuler, refaire, réaliser un fichier XML selon certaines règles de construction.

Un document valide doit comporté le contenu recommandé par la DTD ex : un fichier sans `<body>` est un fichier non valide. 

Le probléme avec la validation : fonctionne avec les petits fichiers. 

Il existe deux normes de documents de validation : DTD et XML Schema. (Egalement : Relax NG évolution de la DTD mais pas aussi puissant que XML shéma, même s'il a été simplifier. Schematron par liste d'assertion)

Une DTD peut être définie : soit à l'intérieur d'une document XML soit d'un fichier à part. Cette dernière solution est la plus fréquent et la plus pratique. L'intérêt d'avoir un fichier externe : il est réutilisable. Simplifie les changements, puisque l'on modifie un seul fichier pour modifier la DTD. 

Pour définir une DTD externe il suffit d'écrire : 
`<!DOCTYPE élément-racine SYSTEME "nom_du_fichier.dtd">`

**Exemple**

```
<?xml version="1.0"?>
<!ELEMENT encyclopedie (personne*)> 
<!ELEMENT personne (nom,prenom,publication+)>
<!ATTLIST personne sexe (H|F)"H">
<!ELEMENT nom (#PCDATA)>
<!ELEMENT prenom (#PCDATA)>
<!ELEMENT publication (#PCDATA)>
```


Pour chacun des éléments, on définit sa composition, son nom et sa structure
* on définit également les attributs si besoin avec `<!ATTlIST>`
* **\*** signifie 0 à plusieurs
* **+** signifie plusieurs
* **?** non obligatoire
* si rien n'est mentionné (ex : nom) signifie qu'il ne doit apparaître qu'une seule fois
* **(#PCDATA)** signifie que l'élément contient du texte
* dans cet exemple "H" est par défaut

#### La syntaxe de la DTD

* Les différents connecteurs possibles : 
	* séparés par une , et doivent apparaître dans l'ordre
	* | un seul des deux éléments doit apparaître
* Les attributs déclarés par ATTLIST: 
	* CDATA chaîne quelconque de caractère¹
	* ID pour indiquer que la valeur de l'attribut est unique (identifiant)
	* IDREF pour un numéri d'identifiant du document (création d'un lien dans le document) (un élément peut dépendre de plusieurs éléments uniques)
	* ENTITY entité externe
	* ENTITIES Liste d'ENTITY séparées par des espaces
	* REQUIRED pour indiquer d'un attribut est obligatoire
	* IMPLIED non obligatoire


#### Bilan sur les DTD

Il y a de nombreuses données types que l'on peut ajouter avec XML, mais qui ne sont pas prise en charge par la DTD. Dans XML shema, on peut bien définir le nombre exacte d'apparition d'un èlèment ( à la différence de DTD et Relax NG). 

Il n'y a pas vraiment de gestion des types de données avec DTD. On peut créer notre propre type de données avec XML shema, pas en DTD. 

XML schema a été développé pour contourner ces limitations. La différence dans son principe de fonctionnement avec la DTD est que Relax NG est basé sur XML

#### Exercices 

**Exercice 1**

```
<?xml version="1.0" encoding="UTF-8"?>
<!ELEMENT bibliotheque (livre*)>
<!ELEMENT livre (titre, auteur*)>
<!ATTLIST livre genre (fiction|drame|aventure|policier)#REQUIRED>
<!ELEMENT titre (#PCDATA)>
<!ELEMENT auteur (#PCDATA)>
```

<!> Respecter l'ordre 

Ici #REQUIRED = on ne peut pas laisser ce champs vide. La liste (fiction | drame | ...) remplace (#PCDATA) qui indique qu'il s'agit d'une chaine de caractères.

Peut être aprfois intéressant de commencer le fichier XML avant le shéma, selon ses besoins et sa mnière de travailler/réfléchir.

**Exercice 2**

```
<?xml version="1.0" encoding="UTF-8"?>

```

En XSD les éléments dont on a besoin pour définir la galerie sont définit en premier. On définit en profondeur les éléments pour les récupérer par la suite. 

Dans l'exemple, on a définit un type "Bibliography". 

### XSD

Beaucoup plus complexe que DTD, Relax NG a simplifié son schéma. 

Il s'agit d'une alternative aux DTD. Spécifier les types de données dans chaque éléments, gérer l'ordre, le nombres d'occurences d'un élément.

En XSD, on définit auparavant, les éléments obkigatoire de l'élément racine. (voir l'exemple PP Galeries). Beaucoup plus complexe et long que la DTD.

