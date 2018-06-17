# JavaScript mémo

Le HTML

```html
<section id="sectionId" class="firstSection">
   <h2 class="firstSection_title">Le titre</h2>
   <img class="firstSection_Img" src="" alt="">
   <div class="firstSection_container">
      <p class="firstSection_containerText">Coucou</p>
      <p class="firstSection_containerText">Toi</p>
   </div>

   <button data-number="1" type="button" name="button">Bouyah</button>
   <button data-number="2" type="button" name="button">Hola</button>
   <button data-number="3" type="button" name="button">Hey</button>
   <article class="firstSection_article">
      <img src="" alt="">
   </article>
</section>
```

## 1. Sélecteur

### querySelector

Pour sélectionner une balise, on peut utiliser le querySelector en visant le nom de la balise, l'id ou la classe.

Pour mettre la section dans la variable theFirstSection, on peut utiliser :

```javascript
// avec le nom de balise
var theFirstSection=document.querySelector('section');

// avec la classe
var theFirstSection=document.querySelector('.firstSection');

// avec l'id
var theFirstSection=document.querySelector('#sectionId');

// la balise et la classe
var theFirstSection=document.querySelector('section.firstSection');

// pour sélectionner la balise img dans le .firstSection_article
var myImg=document.querySelector('.firstSection_article img');

// avec le dataset
var bouton=document.querySelector('[data-number="2"]')
```

**IMPORTANT!**

Le **querySelector** renvoie le **premier** élément qu'il trouve dans le HTML.

```javascript
var bouton=document.querySelector('button');
```

ça renvoie le **PREMIER BUTTON**

* * *

### querySelectorAll

Pour sélectionner plusieurs éléments, on utilise querySelectorAll qui renvoie un **TABLEAU**

```javascript
var boutons=document.querySelectorAll('button')
```

La variable **boutons** est un **TABLEAU**. Les éléments du tableau sont utilisables avec boutons[0], boutons[1], ...

* * *

## 2. Quelques fonctions utiles

_Valeur/contenu_:

```javascript
element.innerHTML //renvoie le contenu d'une element
element.textContent //renvoie le texte d'une element
input.value //renvoie le contenu d'un input
checkbox.checked // renvoie true si la checkbox est cochée, sinon false
```

_Styles_:

```javascript
element.style.color='red'; // change le style couleur d'un element en 'red'
element.style.backgroundColor='blue'; //change le style background-color d'un element
element.style.transform='translateX(10px)';
element.style.src='img/imgopif.jpg';
element.style.display='none';
...
```

_Classes_:

```javascript
element.classList //renvoie la liste des classe d'un element
element.classList.add('nomdeclasse'); //ajoute la classe "nomdeclasse" à un élément
element.classList.remove('nomdeclasse'); //supprime la classe "nomdeclasse" à un élément
element.classList.toggle('nomdeclasse'); //ajoute la classe "nomdelaclasse" si elle est absente, supprime la classe si elle est présente
element.dataset.exemple="ex"; //Donne la valeur "ex" au "data-exemple" de la balise
```

_Tableaux_:

```javascript
var tableau=[]; // déclare un tableau
tableau.length // renvoie la taille du tableau
tableau.length-1 // indice du dernier élément du tableau
tableau.push(element); // place un "element" à la fin du "tableau"
tableau.splice(2, 3); //supprime 2 elements à partir de l'index 3 du tableau
```

Trucs:

```javascript
window.pageYOffset; //renvoie la valeur du scroll actuel de la page
```

```js
var a = chaineDeCaractere.trim();   //retire tous les espaces de la chaine de caractères
```

### - Créer un élément:

```javascript
var newSpan=document.createElement('SPAN'); //Crée un élément <span></span>
newSpan.className="exempleClass" // donne la classe "exempleClass" à l'élément span
var newText=document.createTextNode('exemple'); //Crée un texte "exemple"
newSpan.appendChild(newText); //place le texte "exemple" dans l'élément span

var article=document.querySelector('.firstSection_article');
article.appendChild(newSpan); //place l'élément span dans l'aticle dans le HTML
```

### - Evenement par défaut

Pour empecher un evenement par défaut

```javascript
// empeche les evenement par defaut (le submit du formulaire par ex)
form.addEventListener('submit', function(event) {
      event.preventDefault();
});
```

## 3. addEventListener

Pour mettre de l'intéraction, on peut placer un addEventListener sur un élément pour qu'il exécute une fonction (**function**).

```javascript
var bouton=document.querySelector('button')

var bouton.addEventListener('click', function(){
   console.log('coucou')
})
```

Lorsqu'on **clique** `'click'` sur le **premier bouton**, on affiche "coucou" dans la console.

### Des trucs :

```javascript
var window.addEventListener('keyup', function(event){
   console.log(event.which);  //renvoie le keycode de la touche du clavier qu'on relache
})
```

## 4. Timeout, Interval

```javascript
//Affiche 'coucou' dans la console après 1000ms (1s)
var timoute = setTimeout(function () {
   console.log('coucou');  
}, 1000);

clearTimeout(timoute); //supprime le setTimeout
```

```javascript
//Affiche 'bouh' dans la console toute les 2000ms (2s)
var intervalle = setInterval(function () {
   console.log('bouh');  
}, 2000);

clearInterval(intervalle); //supprime le setInterval
```

## 5. Parse

```js
var a=[{name:"Kantin"},{name:"Vlontin"},{name:"M00N"}];
var b=JSON.stringify(a);
```

```js
var a='[{"name":"Kantin"},{"name":"Vlontin"},{"name":"M00N"}]'
var b=JSON.parse(a);
```


## Local storage

Pour sauvegarder dans le local storage la variable item :
```js
window.localStorage.setItem("itemName", item)
```

Pour mettre dans la variable item la sauvegarde du local storage :
```js
var item = window.localStorage.getItem("itemName")
```


## Smooth scroll to top


```js
window.scroll({
      top: 0, 
      left: 0, 
      behavior: 'smooth' 
});
```