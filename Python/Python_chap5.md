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

* système de templates de flask = jinja

#### les conditions dans les templates 

exemple : 

```
<body>
        <h1>Bienvenue !</h1>
        <p>
            Il y a {{lieux|length}} enregistrés
            {% if lieux %}
            , voici le premier : {{lieux[0]}}
            {% endif %}
    </p>
    </body>
</html>

```

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
    * en JINJA : on définit des blocs
 
* **avec un seul bloc d'import** : 

Exemple : 

*templates/conteneur.html*

```
   	<html>
    <head>
        <title>Gazetteer</title>
    </head>
    <body>
        <div><h1>Bienvenue sur le Gazetteer</h1></div>
        <div>{% block corps%}{%endblock%}</div>
    </body>
</html>
```

*templates/accueil.html*

```
{% extends "conteneur.html" %}
{% block corps %}
Il y a {{lieux|length}} enregistrés :
<ul>
    {% for lieu_id, lieu in lieux.items() %}
        <li><a href="{{url_for('lieu', place_id=lieu_id)}}">{{lieu.nom}}</a></li>
    {% endfor %}
</ul>
{% endblock %}

```

* **avec plusieurs blocs d'import**

*templates/conteneur.html*

```
<html>
    <head>
        <title>Gazetteer {%block titre %}{%endblock%}</title>
    </head>
    <body>
        <div><h1>Bienvenue sur le Gazetteer</h1></div>
        <div>{% block corps%}{%endblock%}</div>
    </body>
</html>

templates/pages/accueil.html

Pour plus de lisibilité, il est commun de regrouper les éléments semblables dans des sous-dossiers de templates.

{% extends "conteneur.html" %}
{% block corps %}
Il y a {{lieux|length}} enregistrés :
<ul>
    {% for lieu_id, lieu in lieux.items() %}
        <li><a href="{{url_for('lieu', place_id=lieu_id)}}">{{lieu.nom}}</a></li>
    {% endfor %}
</ul>
{% endblock %}
```

*templates/pages/places.html*

```
{% extends "conteneur.html" %}
{% block titre %}
    {%if lieu %}| Lieu : {{lieu.nom}} {% endif %}
{% endblock %}

{% block corps %}
    {% if lieu %}
        <h1>{{lieu.nom}}</h1>
        <h2>{{lieu.moderne}}</h2>
        <dl>
            <dt>Longitude</dt><dd>{{lieu.latlong[1]}}</dd>
            <dt>Latitude</dt><dd>{{lieu.latlong[0]}}</dd>
            <dt>Description</dt><dd>{{lieu.description}}</dd>
            <dt>Type</dt><dd>{{lieu.type}}</dd>
        </dl>
    {% else %}
        <p>La base de données est en cours de constitution</p>
    {% endif %}
    <p><a href="{{url_for('accueil')}}">Retour à l'accueil</a></p>
{% endblock %}
```


`extends`  permet d'importer le corps dans le conteneur. (Attention, pas de `{%endextends%}` ici !

* on peut étendre plusieurs blocs avec un seul conteneur : déclarer l'ensemble des blocs
* on peut avoir des blocs avec des conteneurs
* **includes** intègre le HTML d'un autre template sans le modifier
	* Cette inclusion se fait via `{% include "chemin/vers/inclusion/html" %}` et ne possède pas de fin `{% endincludes %}`.

#### Les assets
Pour faire des trucs jolis
* Javascript
* CSS
* Peut être étendu à des polices de caractère (mauvaise idée en python)
* Des images (mauvaise idée en python)

* Font partie des "statics" : ne bouge pas
	* pour réaliser un lien vers un fichier static : 
		 

