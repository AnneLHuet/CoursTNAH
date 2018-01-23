# Introduction à Git - Thibault Clérice
## 1 - Exemple simple

### Créer un repository git

* **mkdir** notes-de-cours (je crée un répertoire intitulé "notes-de-cours")
* **cd** notes-de-cours
* **git init** (le dossier dans lequel je suis devient repository git)

### Ajouter un fichier à la stagin area et effectuer un commit
Créer un fichier dans notre repository
* **git status** (à ce stade, notre fichier est affiché non suivi)
* **git add** cours1.txt (on ajoute le fichier créer à la staging area)
* **git commit -m** "Notes du cours 1" (on commit le fichier en n'oublient pas d'ajouter un commentaire avec -m)

Désormais, si l'on fait un **git status**,il n'y aura aucune modification.
On a enregistré le premier fichier. On ajoute maintenant des notes de cours
* **git diff** (?)
* **git status** (cours1.txt a des changements qui ne sont pas en staging area)
* **gitt add** cours1.txt
* **git commit -m** "ajouter des commandes" (on fait un commit en précisant le type de modification effectuées)

## 2 - Les branches
* **git checkout master** (m'indique sur quelle branche je suis)
* **git merge** (fusionne les branches)

### Les bonnes pratiques
Une tâche doit correspondre à une branche. Quand on commence à travailler sur un repository, il est nécessaire de savoir de quelle branche on travaille, pour être sur la bonne version des fichiers.
#### Les conflits d'historiques
Il y a conflit d'historiques lorsque des modifications ont été effectuées sur les mêmes lignes de textes dans un fichier mais sur deux branches différentes.

Il est important de travailler sur d'autres branches que master = moins de risques.

## 3 - Les serveurs

Git peut être utilisé avec des serveurs distants. Il y a deux grands concurrents:
* Github (le plus ancien des deux et celui que l’on va utiliser)
* Gitlab, son concurrent le plus sérieux car *Opensource* et donc intéressant.
* Egalement *Bitbucket* et *Forge* (pour le CNRS).
Dépend des besoins des institutions pour lesquelles on travaille.

### Comment fonctionne les serveurs de Git ?
### Remote
Correspond à des versions d’un repository donné : version principale vs version à synchroniser. Un repository GIT peut être synchronisé avec différents serveurs. Par convention, la première remote déclarée s’appelle **origin** et la deuxième s’appelle **upstream** (ce sont plus des conventions).

Contrairement à dropbox, git ne se synchonisre pas automatiquement. Pour mettre à jour une remote, il va falloir le faire volontairement.

* **git push** (pour faire une synchronisation)
* **git pull** (pour faire une synchronisation du serveur vers le PC. Par exemple si l’on travaille sur différents PC)

#### Exemple

Imaginons qu'une institution / entreprise a fait un morceau de logiciel intéressant que l'on souhaite utiliser. Dans notre exemple, il s'agit de l'ENC :  

* **Etape 1** : Copier l’ensemble d’un repository sous git avec **git clone**. Dans notre exemple,  ENC est *origin*. Pour cette étape, il est possible de passer par le serveur github (on effectue un *fork*)
* **Etape 2** : push / pull
* **Etape 3** : upstream


Si l'on a prévu de modifier le dossier, on le *Fork*. Si l'on a prévu de le consulet seulement, on peut simplement le cloner.

Ces trois commandes sont les seules interactions avec github :
* **clone**
* **pull**
* **push**

Github n’est pas open-source mais est l’outil le plus moderne pour de la gestion de code versionné en équipe. Il propose un environnement complet.

### Bonnes pratiques
* Toujours faire un **git status** en se connectant sur son dossier
* Suivi d’un **git pull** si on a travaillé depuis un autre pc.
* Essayer le plus possible de **ne pas travailler sur la branche master**

## 4 - Les applications et serveurs web pour Git : l'exemple Github
### Github, Gitlab etc... : pourquoi ?

* Serveur distant
* Pour la gestion d'équipe et de projet :
  * comptes utilisateurs
  * compte d’organisation : possibilité de créer des groupes avec plusieurs comptes pour avoir ses propres repository communs.
* Gestion de bug est de tickets (Issues) : permet d’informer les autres facilement
* Gestion de fusion de branche et de « review »

### Github : les issues
* un bug : on donne alors un titre au bug
  * on donne la démarche pour le reproduire
  * on pense à donner les fichiers concernés par ce bug
  * on essaye de décrire au mieux le problème. Même si c’est sur notre propre dépôt
  * Démarche nécessaire, sinon on oublie le bug, on revient deux mois plus tard, on ne sait plus ce que c’est.
* si l'on souhaite une nouvelle fonctionnalité :
  * permet de décrire ce que l'on souhaite de manière à transférer la charge ou bien s'en occuper plus tard
* une discussion :
  * lorsque l'on essaye de comprendre un morceau de code par exemple

Les issues peuvent être attribuées à des membres du dépôt. Elles peuvent également avoir des labels Elles peuvent faire l'objet de regroupement dans les **projects**(sans deadline), des **milestones** (objectif de sortie d'une nouvelle version)

#### Les dépôts dérivés (forks)
Si l'on souhaite récupérer / modifier une partie des données :
* on réalise un **fork** du repository sur son compte
  * on obtient de cette manière les droits d'écritures, tout en gardant l'ensemble de l'historique
  * on travaille sur ce repository localement
* lorsque l'on fait des modifications sur un dépôt d'une autre personnes, il est plus respectueux de faire un fork que de télécharger et de créer un nouveau dépôt.

#### Collaborer avec des pull requests
Une **pull request**  est une demande d'autorisation de contribution à un dépôt. Comme un **merge**, elle se fait **entre deux branches**.  (Cela peut être deux branches de deux forks)

Contribuer à un repository permet d'aider la personne et les utilisateurs du repsitory.

##### La bonne démarche

* je remarque une erreur :
  * j'ouvre une **issue** qui doit **expliquer** le problème
  * je propose de faire la modification moi-même
  * je fork le dépôt concerné
  * je crée une branche spécifique et je rentre dessus
    * appeler la branche du nom de l'issue pour se souvenir de pourquoi on a crée cette branches
  * je fais la modification et je la **commit**
  * je **push**
  * je fais une **pull request** sur le repository d'origine
