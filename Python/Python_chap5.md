# Chapitre 5 - Flask, un framework d'application web

## Les objets
* Les classes d'objets : catégorie de valeurs
  * `str` et `list`
  * `print(type("Hello"))` (objet de la classe `str`)

### Les méthodes
* Fonctions propres à des classes et à leurs objets
  * syntaxe différente : `.`
    `print("Bonjour le monde".replace("monde","Mickey"))`
  * accessible pour les classes qui la possède : on ne peut pas utiliser `.replace` avec des entiers

### Les attributs
* propriétés des classes : fonctionnent comme des variables ou des clés de dictionnaire

### Instancier un objet
* créer un objet qui ne fait pas partie des types principaux

## Flask
* Framework pour le développement d'application web en python
    * utilisé pour de petits projets / projet simple
    * *voir également Django*
* Package python
  * s'installe via la cmd : `pip install flask`

### Travailler sur son propre projet
* procéder avec un environnement virtuel
* quand l'environnement virtuel est chargé , le terminal affiche son nom entre parenthèse
* pour savoir quels packages sont installés :
  * taper `pip freeze` dans terminal sous l'environnement virtuel.

> Exemple :
- `cd ~` *vous met dans votre dossier utilisateur*
- `mkdir veille-micro-blog` *crée un dossier appelé veille-micro-blog* (**A exécuter une fois seulement**)
- `cd veille-micro-blog` *vous déplace dans ce dossier*
- `python3 -m venv env` *crée un environnement virtuel dans un sous-dossier. Alternative à `virtualenv -p python3 env` (**A exécuter une fois seulement**)
- `source env/bin/activate` *remplace dans votre session de terminal le lien vers le python 3 global par un lien vers le python 3 de votre environnement virtuel*
- `pip install flask` *installe flask dans votre environnement virtuel* (**A exécuter une fois seulement**)

### Une application simple

Exemple :
> ```python
from flask import Flask  # J'importe le module et dans ce module j'importe
#la classe flask
#je crée une application en donnant un nom à mon application
app = Flask("Nom de l'application")
#
@app.route("/")
# je définis une fonction qui retourne une chaîne de caractère Hello World
def index():
    return "Hello world !"```

* `.run` : lance le serveur

### Les templates

* fichier HTML, XML ou équivalent qui sera lu par votre framework et complété le cas échéant par des informations que vous fournirez.
* Dans flask : sous-dossier "templates"

* la fonction `render_template`
  * prend en premier argument le chemin du template
  * des arguments nommés

#### Les dictionnaires dans les templates

* A partir du dictionnaire, on pourra appelé au choix:
  * `{{lieux[0]["nom"]}}`
  * `{{lieux[0].nom}}`

#### Boucles dans les templates et liens

* tout comme pour les if s'exprime entre `{% %}`:
> ```
Il y a {{lieux|length}} enregistrés :
<ul>
    {% for lieu in lieux %}
        <li>{{lieu.nom}}</li>
    {% endfor %}
</ul>```

* si je veux rajouter un lien :
  * <li><a href ="/place/{{lieu.id}}"> {{lieu.nom}}</a></li>

#### Héritage dans les templates
* La composition d'un site web : répétitivité des pages (toutes les pages sont à modifier)
  * problématique traiter en programmation
    * en HTML `iframe` permet d'intégrer une partie d'une page (Mais c'est moche!)
    * inclusion : on intègre un contenu dans une page déjà faite. Permet d'être plus souple dans la gestion de l'HTML
    * en JINJA : on définit des blocs : {% block corps %} {%endblock%}

> Exemple :
{% extends "conteneur.html" %}
{% block corps %}

`extends`  permet d'importer le corps dans le conteneur. (Attention, pas de `{%endextends%}` ici !

* on peut étendre plusieurs blocs avec un seul conteneur : déclarer l'ensemble des blocs
* pn peut avoir des blocs avec des conteneurs et enfin des **includes** (intègre le HTML d'un autre template sans le modifier)

#### Les assets
Pour faire des trucs jolis
* Javascript
* CSS
* Peut être étendu à des polices de caractère (mauvaise idée en python)
* Des images (mauvaise idée en python)

Font partie des "statiques"
