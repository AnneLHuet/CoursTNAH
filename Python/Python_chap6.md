# Chapitre 6 - Flask et introduction au SQL en Python

## Travailler avec MySQL
* Lorsque l'on travaille avec des bdd : 
	* On ne travaille **jamais** directement sur la base de donnée publique
	* Travaille sur des copies
	* Privilégiez le lancement de toutes vos requêtes sur des machines hors production

## installer 
* **Dans son environement virtuel**
	* `pip install mysqlclient`
	* `sudo apt-get install python3-dev libmysqlclient-dev`

## Ecrire une requête avec python 

```python

# j'importe le module MySQLdb
import MySQLdb 
# je me connecte à mysql avec la fonction connect(). Je stocke
# ma connection dans la variable db
db = MySQLdb.connect(
    user="gazetteer_user",
    passwd="password",
    db="gazetteer"
)
# je crée un curseur (objet d'accés aux données) avec .cursor. 
# je stocke ce curseur dans la variable cursor
cursor = db.cursor()
#j'exécute cette requête avec .execute. Le résultat n'est pas stocké.
cursor.execute("SELECT * FROM place")

#je boucle sur les résultats de cursor avec .fetchall
for result in cursor.fetchall(): #pour chaque résultat dans cursor
    print(result) #j'affiche le résultat
#result = renvoi un tuple
print(type(result)) 
# je ferme la connexion avec ma bdd
db.close()
```

* Affiche les résultats sous forme de tuples, dans l'ordre des entrées

## SQLAlchemy et Flask_sqlalchemy

Recommandé, moins complexe

SQLAlchemy traduit les variations entre :

* **SQLite**
* **MariaDB**
* **PostgreSQL**
	* très présente sur le marché

Quoi qu'il arrive, la syntaxe est quasiment identique

* on importe les deux pour connecter notre application : 

```python
#j'importe le module flask et le module SQLAlchemy
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

# je crée une application flas qui porte le nome de "Nom"
app = Flask("Nom")
#je configure l'application avec les informations de connexion
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://gazetteer_user:password@localhost/gazetteer'
#j'initie l'objet SQLAlchemy en le stockant dans une variable db
db = SQLAlchemy(app)
```

### Requêtes manuelles

```python
# sous méthode engine.execute pour lancer une requête
query = db.engine.execute("SELECT * FROM place")
print(query)
# Vous pouvez remplacer fetchmany par fetchall ou fetchone en supprimant le 2
# on peut faire une boucle sur le résultat d'une méthode .fetch___()
for x in query.fetchmany(2):
    print(x["place_nom"])
    print(type(x))```

### générer des requêtes automatiquement

* `class` permet de déclarer un modèl

```python
# nom de table (ici Place) prend une maj, pour être identifiable 
class Place(db.Model):
	# ne pas oublier que ce qui suit doit être indenté (sinon la #colère de dieu s'abat sur ton code)
	# on enregistre ensuite les différents chmp du modèle : 
	place_id = db.Column(db.Integer, unique=True, nullable=False, primary_key=True, autoincrement=True)

```
useful memo pour les types : 

```

| Type         | Exemple         | Définition                                                                    |
| ------------ | --------------- | ------------------------------------------------------------------------------|
| Entier       | db.Integer      | Stocke un entier                                                              |
| Chaîne       | db.String(42)   | Stocke une chaîne à taille maximale ( ici 42)                                 |
| Texte        | db.Text         | Un texte sans taille maximale                                                 |
| DateTime     | db.DateTime     | Date et Heure suivant un objet [`datetime`](https://docs.python.org/3.5/library/datetime.html) en python                           |
| Float        | db.Float        | Stocke un décimal                                                             |
| Boolean      | db.Boolean      | Stocke un booléen                                                             |
```

**on ne peut faire de requêtes avant d'avoir mis le modèle en place**

`variable = Nom_table.query.all()`

* pour afficher les éléments souhaités, on utilise les noms de colonnes comme attributs : 

```
 for x in variable:
 	print(x.nom_colonne1, x.nom_colonne2)
```

* Select * From Places where place_id = 1 (pour la clé primaire)
	* `.query.get(cle)`

* Select * From Places where place_type="settlement"

```python
settlements = Place.query.filter(Place.place_type=="settlement").all()
print(settlements)
```

* **.count()** = compter le nombre de résultat
