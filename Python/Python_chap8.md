Python - Thibault Clérice

# Chapitre 8 - Mon premier formulaire et la recherche

## Les méthodes POST ou GET

* on recommande la méthode **GET** pour les formulaires de recherche

* Utiliser **POST** pour les données sensibles ! (mdp, coordonnées etc...)

## Formulaires

* recherche à facette : recherche avec filtre

## la récupération de l'information

* simple avec flask : 
```python
from flask import Flask, request

request.arg == {
	"une_page": "0",
    "recherche": "quelque chose" # %20 remplace un espace dans les URLs
}
```

* on crée une route qui récupére l'information

* 
