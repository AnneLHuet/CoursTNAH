#MySQL Cours4

## Contraintes d'intégrité

* une expression logique devant être vraie à tout moment
	* ex : deux employées ne peuvent pas avoir le même matricules 

* nous indiquent les cardinalités

* la **contrainte de domaine** : 
	* l'ensemble des valeurs possibles d'un attributs
* **contrainte de clé** : 
	* plusieurs colonnes d'une table ne peut pas contenir les mêmes valeurs
* **contrainte obligatoire**:
	* un attribut doit toujours avoir une valeur
* **contrainte d'intégrité référentielle**
	* appelé également contrainte d'inclusion 
	* ex : l'enregistrement d'une commande par la présence du client

## Dépendance fonctionnelle (DF)

* Propriété définie sur le schéma
	* cas particulier de contrainte d'intégrité

## Liens relationnels

* liens relationnels entre les données à travers plusieurs entités: 
	* **domaine** l'ensemble des valeurs qu'un attribut peut prendre
	* **relation** 
	* **attribut** le nom de valeur d'un domaine
	* **schéma**
	* **clé**

## Normalisation

* imposer des règles de construction à sa structure afin de respecter la cohérence des données et éviter toute redondance d'informations.

* une forme normale désigne un type de relation particulier entre les entités
	* éviter la redondance des données
	* les anomalies de lecture et d'écriture
	* s’applique à toutes les entités et aux relations porteuses de propriétés

* trois sortes de dépendances permettent de normaliser les informations : 
	* les dépendances fonctionnelles
	* les dépendances multivaluées
	* les dépendances de jointures

* les bases du type OLTP
	* surtout pour le commerce en ligne 
	* tout doit être maitrisé (traitement transactionnel etc)
	* il existe 8 formes normales

* les bases du type OLAP
	* bases de données pour le traitement analytique en ligne
	* les normalisations sont moins rigides
	* NoSQL pour le big data

### La première forme normale

* une relation (ayant par définition une clé) dont les attributs possède tous une valeur sémantiquement atomique
	* un attribut est dit "atomique" si aucune subdivision de l'information initiale n'apporte une information supplémentaire ou complémentaire



