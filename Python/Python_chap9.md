Python - Thibault Clérice

# Chapitre 9 - Requêtes SQLAlchemy fines et petites astuces

* `.limit(Nombre Entier)` limite le nombre de résultats obtenus (à placer à la fin d'une requête)

`.first()` pour obtenir seulement le premier résultat (à placer à la fin d'une requête)

`.order_by()` résultats par ordre alphabétique (par défaut croissant)
	* `.desc` decroissant
	* `.asc` croissant

`.between` > comme en SQL, entre deux valeurs

`get_or_404(Clef Primaire)` > envoyer un message d'erreur quand la page n'existe pas

``` 
python
noms_lieux_2 = [lieu.place_nom for lieu in data]
print(noms_lieux_2)
```
! boucle en une ligne!

## Faire une pagination

* a la place de `.all` qui affichait tous les résultats, on met `.paginate`

* `.iter_pages()` génére automatiquement le numéro des pages à afficher

>faire exercice chapitre 9