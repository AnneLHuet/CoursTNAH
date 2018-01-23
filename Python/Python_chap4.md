# Chapitre 4.1 -  Les Fichiers CSV, JSON, et les requêtes.

## Le format CSV

* Un fichier de tableau simplifier au maximum
  * encodé plein texte
  * utilise un séparateur de colonne (virgule, point virgule, tabulation)
  * une ligne par ligne de tableur

* package = ensemble de modules comportant des outils tels que les fonctions.
* voir la documentation : https://docs.python.org/3.5/library/csv.html
* travailler avec le package standard pour utiliser des fichiers CSV

* **importer le module csv**
`import csv` 

* **voir le module csv**
`dir(csv)`

`csv.reader(csvfile, delimiter='', quotechar'')`

* **la fonction enumerate** renvoit un tuble sur une valeur simple
`couleurs = ["vert", "rouge", "bleu"]`
`for index, couleur in enumerate(couleurs)`
	`print(str(index)+ " = " + couleur)`

* **csv.writer**
	* prend comme argument : 
		* un fichier ouvert en mode écriture
		* un **delimiter** (délimiteur de colonne)

* `from \__ import \__`

# Chapitre 4.2 - Les fichiers CSV, JSON et les requêtes

## lire un fichier JSON

* `json.load()` : prend une instance de fichier en cours de lecture

* `json.loads()`: prend une chaîne de caractère

* la méthode **.format()** pour la concaténation de chaîne

## Ecrire

* dans une chaîne de caractère avec **json.dumps()**
* dans un fichier avec **dump**

# Chapitre 4.3

## 1. La structure du web
* lors d'une communication HTTP :
  * l'envoi de la requête
    * composée de trois types d'information :
      * l'URL
       * l'adresse dont on requiert le contenu
       * la partie *query* change suivant les utilisateurs
      * la méthode
      * les headers
  * la réponse du serveur
    * composé de trois éléments:
      * les headers
        * nous renvoie l'information sur la réponse
      * le code HTTP
        * nous renvoi le statut de la réponse
          * exemple : 404 = page non trouvée
      * le corps
        * ce que l'on voit lorsque l'on fait une requête (contenu html, contenu JSON etc...)

## 2. Faire des requêtes http en python : le module request
### 2.A Le module requests

* Les modules pour faire des requêtes WEB en python:
  * Avec PIP : gestionnaire de librairies de python
  * la commande :
  `pip install -r requirements.txt` installe chaque librairies contenues dans le fichier `requirements.txt` (parmis lesquelles `requests`)

### 2.B Faire une requête GET
* le module propose une fonction `get` qui prend une URL
 * *exemple* :

 `req = requests.get("https://...")`

 * `get()` accepte un paramètre `params`
 * accepte des headers sous la forme d'un dictionnaire
  `xml = requests.get(url, headers={"Accept": "text/xml"})`
* Les objets `Response` ont plusieurs propriétés  :
  - `.status_code` sous la forme d'un entier qui informe du succès de la requête
    * ex : 200 (succés de la requête) ou 404
  - `.headers` sous la forme d'un dictionnaire qui comporte l'ensemble des headers
  - `.encoding` qui comprend la méthode d'encodage
  - `.text` qui contient le contenu de la réponse
  - `.json()` qui, si `.headers['content-type']` est `application/json`, parse lui-même le json de la réponse.
