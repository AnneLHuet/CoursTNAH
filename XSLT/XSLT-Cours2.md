XSLT - Branislav Mezsaros - 24/01/2018

## Pour le cours d'aujourd'hui

* Transformer des fichiers XML en DTD et inversement
* XML Schéma XSD
* Relax NG : fonctionnement

## Exercices 
### Exercice 1

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE compositions
[
<!ELEMENT compositions (composition*)>
<!ELEMENT composition (auteur, date_de_creation, fleuriste?, composants)>

<!ELEMENT auteur (#PCDATA)>
<!ELEMENT date_de_creation (#PCDATA)>
<!ELEMENT fleuriste (ville|lieu)*>
<!ELEMENT composants (vase, fleurs)>

<!ELEMENT ville (#PCDATA)>
<!ELEMENT lieu (#PCDATA)>

<!ELEMENT vase (matiere, taille)>
<!ELEMENT matiere (#PCDATA)>
<!ELEMENT taille (#PCDATA)>

<!ELEMENT fleurs (nature, item)>
<!ELEMENT nature (#PCDATA)>
<!ELEMENT item (#PCDATA)>
]
```

### Exercice 2
```

<aa>
	<aa1></aa1>
</aa>


```

### Exercice 4

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE compactdiscs[

<!ELEMENT compactdiscs (compactdisc*)>
<!ELEMENT compactdisc (artist, title, tracks, price)>
<!ENTITY % Type "individuel | groupe">

<!ELEMENT artist (#PCDATA)>
<!ATTLIST artist type (%Type;) #REQUIRED>

<!ELEMENT title (#PCDATA)>
<!ATTLIST title numberoftracks CDATA #REQUIRED>

<!ELEMENT tracks (track*)>
<!ELEMENT price (#PCDATA)>
<!ELEMENT track (#PCDATA)
]
```

### Exercice 6

```
<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE bibliographie[

<!ELEMENT bibliographie (livre+, article+, avis*)>

<!ELEMENT livre (titre, auteurs+, tome*, edition)>
<!ELEMENT titre (#PCDATA)>
<!ELEMENT auteurs (prenom,nom)>
<!ELEMENT prenom (#PCDATA)>
<!ELEMENT nom (#PCDATA)>
<!ELEMENT tome (nombre_de_pages+)>
<!ELEMENT nombre_de_pages (#PCDATA)>
<!ELEMENT edition (editeur, lieu_edition, lieu_impression?, ISBN)

<!ELEMENT article (titre, auteur, publication)
<!ELEMENT titre (#PCDATA)>
<!ELEMENT auteurs (prenom,nom)>
<!ELEMENT prenom (#PCDATA)>
<!ELEMENT nom (#PCDATA)>
<!ELEMENT publication (nom_journal, pages, année, numero_journal)
<!ELEMENT nom_journal (#PCDATA)>
<!ELEMENT pages (#PCDATA)>
<!ELEMENT année (#PCDATA)>
<!ELEMENT numero_journal (#PCDATA)>
]

```

**correction** (à ajouter)

```
<!ELEMENT bibliographie (livre|article)*>

	<!ELEMENT livre (titre, auteur+, tome*, edition, avis?)>
		<ATTLIST titre soustitre CDATA #IMPLIED>
			<!ELEMENT titre (#PCDATA)>
			<!ELEMENT auteur (#PCDATA)>
			<!ELEMENT tome EMPTY>
					<!ATTLIST tome
							nb-pages CDATA #REQUIRED
							soustitre CDATA #IMPLIED>


		<!ELEMENT edition (editeur, lieu_edition, lieu_impression, ISBN)
			<!ELEMENT editeur (#PCDATA)>
			<!ELEMENT lieu_edition (#PCDATA)>
			<!ELEMENT lieu_impression (#PCDATA)>
			<!ELEMENT ISBN (#PCDATA)>
		<!ELEMENT avis (#PCDATA)
	<!ELEMENT article (titre, auteur+, journal)
		<!ELEMENT journal (page,num_journal)
				<!ATTLIST journal
					nom_journal CDATA "Feuille de Chou"
					annee (2000 | 2001 | 2002 | avant_2000 | inconnue)"inconnue">
]

```

#### Pour la semaine prochaine 

Faire un fichier XML à partir du fichier DTD (voir mail)
