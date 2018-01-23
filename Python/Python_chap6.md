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

>`import MySQLdb #
db = MySQLdb.connect(
    user="gazetteer_user",
    passwd="password",
    db="gazetteer"
)
cursor = db.cursor() # .cursor permet d'effectuer une requête
cursor.execute("SELECT * FROM place")
for result in cursor.fetchall(): #pour chaque résultat dans cursor
    print(result) #j'affiche le résultat
print(type(result))
db.close()# je ferme la connexion avec ma bdd`


* Affiche les résultats sous forme de tuples, dans l'ordre des entrées

## SQLAlchemy et Flask_sqlalchemy

SQLAlchemy traduit les variations entre :

* **SQLite**
* **MariaDB**
* **PostgreSQL**
	* très présente sur le marché

Quoi qu'il arrive, la syntaxe est quasiment identique

* on importe les deux pour connecter notre application : 

> `from flask import Flask
from flask_sqlalchemy import SQLAlchemy
>
app = Flask("Nom")
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://gazetteer_user:password@localhost/gazetteer'
db = SQLAlchemy(app)`