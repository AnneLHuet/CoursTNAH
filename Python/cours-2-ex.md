# Javascript Exercices - Cours 2 

## Exercice 1

- Changer le texte "Titre 2" en `"Un Joli Titre"`
- Mettre l'article 2 avec une marge de `150px`
- Remplacer l'intégralité du HTML avec un article 3

```html
<html>
 <body>
   <article id="article_1">
     <header class="sub-info">Titre</header>
     <section>Lorem Ipsum</section>
     <footer class="sub-info">Auteur</footer>
   </article>
   <article id="article_2">
     <header class="sub-info">Titre 2</header>
     <section>Lorem Ipsum 2</section>
     <footer class="sub-info">Auteur 2</footer>
   </article>
   <script type="text/javascript">
   // Votre code ici
   </script>
 </body>
</html>
```

```javascript
alert("Etape 0");
var titre = document.querySelector("#article_2 header");
titre.innerText = "Un joli titre";
alert("Etape 1");
var article = document.querySelector("#article_2");
article.style.margin = "30px";
alert("Etape 2");
var body = document.querySelector("body");
body.innerHTML = `<article id="article_3">
     <header class="sub­info">Titre 3</header>
     <section>Lorem Ipsum 3</section>
     <footer class="sub­info">Auteur 3</footer>
   </article>`;
```

## Exercice 2

* ajouter un nouvelle input dans l'interface qui permettent d'ajouter des champs 
* a quoi cela doit ressembler ? 
  * une légende de champ : variation de nom
  * un champ : nom
  * un champ : langue
  * un bouton +
  * un bouton -
* ​