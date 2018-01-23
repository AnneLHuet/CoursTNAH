# Mysql - commandes

`mysql -u nom_utilisateur -p`

`mysql -u root -p`

## Commande de bases

`CREATE USER 'nom_utilisateur'@'localhost' IDENTIFIED BY 'mdp'; ` crée un utilisateur

`SHOW DATABASES;` affiche les bases de données

`USE 'nom_base';` on se met sur la base souhaité

`SOURCE 'chemin/fichier.sql';` récupére les données d'un fichier sql

`DROP DATABASE IF EXISTS 'nom_base';` supprimer la base si elle existe

`SHOW TABLES;` afficher les tables

`SELECT * FROM 'nom_table';` affiche le contenu d'une table

## Requêtes - interrogation simple avec la commande SELECT

**On commence avec la commande `SELECT` et on finit toujours par `;`**

`SELECT` requête de sélection

`SELECT * FROM table` le caractère \* affiche la totalité

`DISTINCT` eviter les doublons

`AS` renommer une colonne

`ÒRDER BY`  trier les résultats

`TOP` / `LIMIT` limiter le nombre de lignes de résultats
  * TOP pour MS SQL SERVER et MS Access
  * LIMIT fonctionne avec MYSQL et ORACLE

`WHERE` restreindre les résultats
  * `LIKE` comparaison de chaîne. Permet de chercher les éléments par rapport à leur ressemblance.
  * `IN` comparaison à une liste
    * WHERE 'ghgdhgd' IN ('camille', 'jacques'); (équivalent de OR)
  * `BETWEEN` intervalle
  * Utilisation du `AND` et du `OR`
    * <!> AND a toujours priorité sur OR

`ORDER BY` permet le tri des résultats d'une requêtes par ordre croissant (`ASC`) ou par ordre décroissant (`DESC`)

`OFFSET` permet un décalage des résultats demandés

<!> pour = utiliser **<=>** / pour. Pour signifier la différence : **!=** ou **<>**
**%** signifie n'importe quelle chaine de caractère
**_** représente un seul caractère
