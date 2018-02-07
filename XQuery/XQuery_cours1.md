XQuery - Cours 1 - Rémy Delmotte

# Panorama des solutions de stockage
## Introduction aux bases de données XML natives

### Les bases de données Relationnelles
### No SQL
### Les bases orientées Graph
### Les bases clés-valeurs
### Les bases orientées documents

Stocke des documents et non des données, en préservant leur contenu. Dans d'autre bases, on extrait les données, pour une autre structure, ici la structure et préservée.

Voir Json.org pour la description de la grammaire par schèma : vocabulaire très simple. Quel que soit mon format, on utilise 
pour un objet{ chainedecaractere : valeur, chaine de caractere : valeur }

qu'est ce qu'une valeur ? une chaine de caractère, un objet, un tableau, un booléen... Qu'est ce qu'une chaine de caractère ? tous caractère unicode sauf les caractères propres au langage à échapper avec \. Qu'est ce qu'un nombre ? un nombre, 0 ou un négatif, un exposant... 

JSON est un format très utilisé pour acheminer les données. XML s'est imposé pour stocker de la donnée en format document. Réflexions pour faire un pont entre les deux (XSLT). Les spécifications XSLT propose une interprétation XML dde fichiers JSON. Le format XML décrit le schéma en même temps qu'il décrit les données.

#### Pourquoi une solution de stockage spécifique pour XML ?
* Dans les SGBDR : 
	* Stockage des documents sous forme d'objets binaires (BLOB, BTree)
	* Permet de stocker les documents , mais pas d'accéder aux données
* Quelques innovations dans les bases de données relationnelles:
	* type XML dans certaines bases avec un support partiel xpath. Accés aux données, mais avec des requêtes xpath. accés aux données restrictives. 
* BDXN et SGDB
	* voir tableau PPT (p.15)

#### Caractéristiques

* Selon les bases : 
	* stockage hiérarchique (collection et documents). Permet une organisation complète
	*  Documents, fragments de documents et objets binaires
	* langages d'adressage (Xpath) et de requête (Xquery) normalisés
	* connectivité large (xmlrpc, rest, webdav, soap, API,...)
		* data.gouv
		* data.bnf.fr (notice d'autorité)
		* VIAF (authorité internationale)
* une base de donnée XML est très riche fonctionnellement. 
	* facilite la gestion et le dev d'application 
	* accés à la structure facilité par Xpath et XQuery
	* s'inscrivent dans le respect des normes et l'implémentation des standards

#### Quels usages ? 

* Un espace de travail:
	* Environnement d'exécution (XQuery, XSLT, XPath, Xinclude)
	* Editeur et navigateur de fichier intégré
	* Gestion des accés 
* Dépôt XML / base de donnée applicative
	* Communication depuis une application (REST, XMLRPC)
	* Communication depuis un poste de travail (Webdav, clien léger ou riche). Serveur de partage : base peut servir de dépôts distants.
* Moteur de recherche : 
	* intégré dans la base de donnée XML via Xpath
	* la théorie des moteurs de recherche : 
		* pour une recherche dans un corpus, on constitue un index au lieu de chercher dans chaque documents. Index prégénéré et définis apr l'utilisateur
		* Fonctions de recherche intégrées à XQuery

#### L'offre de bdd XML

* Marklogic
* solutions open source : 
	* eXist
	* basics
* **markmail.org** : 
	* permet de recenser l'ensemble des listes de diffusion des outils libre ou non et d'en connaitre l'influence. Possibilité de vérifier l'activité de la communauté.
	* la base de donnée eXist est présente depuis 2006, produits relativement stable 

* history.state.gov
	* fait avec une base xml

* XPath : un langage d'adressage
	* ressemble à uns système de fichier
	* XML Path Language
		* désigner des portions et des chemins d'un fichier XML
	* pointer un endreoit du document XML 
* XSLT : Langage de Transformation
	* réaliser des transformations de documents XML
	* ensemble de régles de transformation
	* XSLT : rédiger des "templates" qui vont réagir uniquement quand on trouve un élément dans le document XML. Un processeur XML parcours le document. EX : dans mon XSLT j'ai réalisé un template title. Processeur XML va chercher dans mon fichier XML les balises Title
	* peut être stocké dans les bases XML

#### XQuery
* en XQuery on va directement chercher les données dans le documents, on peut se passer de parcourir l'entiéreté du document
* XML Query Language
	* définit un langage pour interroger des dépôts de documents XML
	* Orienté données et documents
	* XPath 2, et types XML Schema
	* une requête XQuery n'est pas un document XML (donc on ne peut pas générer des XQuery en XML)
* Quels usages : 
	* interroger des corpus
	* lire des données
	* modifier les données
		* langage de transformationl : on peut faire les mêmes choses qu'avec XSLT
		* intégration de XML dans la syntaxe des requêtes
		* Génération d'élémenets et d'attributs
		* parcours explicite de la ressource
* langage de programmation
	* Types de données imples et avancés
	* structure de contrôles variées
	* déclaration de fonctions
	* Biblithèque de modules riches
* Procédures stockées : 
	* directement sur mon serveur, appelé par mon application 
* Indexation : 
	* repose sur l'indexation pour une question de performance
	* index plein texte





