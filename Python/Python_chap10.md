Python chapitre 10 - Thibault Clérice

# Chapitre 10 - Session utilisations et Insertions SQL 

## Bibliographie
* https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iii-web-forms

* https://www.youtube.com/watch?v=8ZtInClXe1Q

## Sécurisé une base 

* les attaques "Man in the middle"
	* https://
	* encrypter les formulaires / les données de session / les cookies
	* le but étant que le "man in the middle" ne soit pas en mesure de comprendre ce qu'il se passe.

* Flask ne peut pas fonctionner sans secret

* `@staticmethod`
	* ne porte pas sur un utilisateur particulier mais concerne tous les utilisateurs
	* précéder de `utilisateur = User.identification(login,motdepasse)`

## La création utilisateur

* tous les champs doivent être remplis
* mon email doit être une adresse email etc...
* vérifier qu'un utilisateur est unique

## Formulaire d'inscription

* `flask.request.method`
* `@app.route("/register", methods=["GET", "POST"])`
	* je signifie à Flask que ma page ne fonctionne qu'avec POST et GET

	* get > request.args (se comporte comme un dictionnaire)
	* post > request.form (se comporte comme un dictionnaire)

## Flash

* **spécifique à flask**
* permet de stocker un ensemble de message d'une page à une autre. 
* utiliser la barre url pour les messages = interdit ! c'est une faille de sécurité qui laisse la possibilité de changer le contenu (faille XSS)

## La gestion des sessions 

* mieux vaut utiliser des library qui sont prévues pour
* dans notre cas on utilise l'extension **flask-login**
	* import de LoginManager

## La programmation orientée objet 

* en dehors du cours mais regarder !