# MySQL - cours 3

## Interrogations avancées

Dans un `SELECT` : 
	* `IF`
	* `CASE`

`COUNT`


## Exemples :

**Sur la base marathon**

Afficher le nom, le prénom et la naissance  des 4 coureurs hommes les plus âgés


`SELECT CO_NOM, CO_PRENOM, CO_NAISSANCE 
FROM COUREUR 
WHERE CO_SEXE = 1 
ORDER BY CO_NAISSANCE DESC 
LIMIT 4;`

Afficher le prénom, le nom des coureurs dont le nom contient un 'o'


`SELECT CO_PRENOM, CO_NOM FROM COUREUR WHERE CO_NOM LIKE '%o%';
`

Afficher le nom, le prénom  des coureuses nées entre le 15 juin 1922 et le 18 octobre 1950

`SELECT CO_NOM, CO_PRENOM 
    -> FROM COUREUR
    -> WHERE CO_SEXE = 2 
    -> AND CO_NAISSANCE BETWEEN '1922-06-15' AND '1950-10-18';
`

Afficher (sans doublons) les villes des clubs


Pour la semaine prochaine : cinema, banque, groupement d'achat
`SELECT DISTINCT CL_VILLE FROM CLUB;
    `

Afficher l'heure des épreuves ayant eu lieu en avril 2016

`SELECT DISTINCT EP_HEURE 
FROM EPREUVE 
WHERE EP_DATE LIKE '2016-04-%';`

Afficher le nom de la catégorie d'âge des hommes âgés de 21 ans

`SELECT CA_LIBELLE 
FROM CATEGORIE_AGE 
WHERE CA_AGEDEB < 21 AND CA_AGEFIN > 21;
`

Afficher le nom et le prénom des coureurs dont le prénom commence par "s" ou "b" et dont le nom comporte un "w"

`SELECT CO_NOM, CO_PRENOM 
FROM COUREUR 
WHERE (CO_PRENOM LIKE 'S%' OR CO_PRENOM LIKE 'B%')
AND CO_NOM LIKE '%w%'`
