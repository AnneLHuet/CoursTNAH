XQuery - cours 3 du 12 février 2018


# TP 

A partir de mondial.xml

## Les expressions FLOWR

**Afficher une liste des noms de pays triés par nom de pays**

``

**Afficher pour chaque pays une phrase de description : Population of « Nom_du_pays » is « Population_du_Pays »**

```
for $pays in doc("db/tp/mondial.xml")//country
  return ("Population of "|| $pays/name/text() || " is " || $pays/population/text())
```

ou

```
for $pays in doc("db/tp/mondial.xml")//country
  return concat("Population of ", $pays/name/text() , " is " , $pays/population/text())
```

**Trier par grandeur de population la requête précédente**

```
for $pays in doc("db/tp/mondial.xml")//country
  order by number($pays/population/text()) descending
  return ("Population of "|| $pays/name/text() || " is " || $pays/population/text())
```

**Afficher une liste des pays dans lesquels le français est utilisé (languages)**

```
for $pays in doc("db/tp/mondial.xml")//country
  where $pays/language/text() = "French"
  return $pays/name/text()

```

**Afficher uniquement le nom des villes françaises**

```
for $ville in doc("db/tp/mondial.xml")//city
  where $ville/@country = 'F'
  order by$ville/name/text() ascending
  return $ville/name/text()

```

**Afficher les villes qui sont des capitales (is_country_cap="yes") et les trier par nom**
```
for $capitale in doc("db/tp/mondial.xml")//city
  where $capitale/@is_country_cap="yes"
  order by$capitale/name/text() ascending
  return $capitale/name/text()
```
si l'on souhaite en plus afficher les nomes des pays concernés : 

```
for $capitale in doc("db/tp/mondial.xml")//city
  where $capitale/@is_country_cap="yes"
  order by$capitale/name/text() ascending
  return $capitale/name/text()||" : "|| $capitale/ancestor::country/name/text()
```


**Afficher une liste des villes les trier par pays, puis par nom**
```
for $ville in doc("db/tp/mondial.xml")//city
  order by $ville/@country ascending, $ville/name/text() ascending
  return $ville/name/text() || " : " || $ville/ancestor::country/name/text()
```

**Sur la base de la requête précédente générer une réponse permettant d'indiquer entre parenthèses
l'indicatif du pays (@country)**

```
for $ville in doc("db/tp/mondial.xml")//city
  order by $ville/@country ascending, $ville/name/text() ascending
  return $ville/name/text() || " ( " || $ville/@country || " ) "

```

**Afficher une liste des types de gouvernement représentés (government) triés par ordre
alphabétique, sans redondance.**

```
for $gov in distinct-values (doc("db/tp/mondial.xml")//government/text())
  order by $gov ascending
  return "Gouv : " || $gov

```

## notes de TP : 

**explorer le document**
```
doc("db/tp/mondial.xml")
```

**ressources pour XPath**

http://zvon.org/

**Ressources pour XQuery et XSLT**

http://www.xqueryfunctions.com/

donne des exemples de requêtes pour un but précis. Répertoire de snippets (c'est à dire d'extraits de code réutilisable)
