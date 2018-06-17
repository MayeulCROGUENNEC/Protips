# Documentation

## Convention BEM

- B -> Block
- E -> Element
- M -> Modifier

```html

<!-- mainList = Block -->
<ul class="mainList mainList--xmas">
   <!-- __item = Element -->
   <li class="mainList__item">
      <!-- __itemList = Element -->
      <a class="mainList__itemLink mainList__itemLink--isActive" href="/home">Accueil</a>
   </li>
   <li class="mainList__item">
      <!-- __itemList = Element -->
      <a class="mainList__itemLink" href="/about">About</a>
   </li>
   <li class="mainList__item">
      <!-- __itemList = Element -->
      <a class="mainList__itemLink" href="/works">Works</a>
   </li>
</ul>
```

```css
.mainList {
   display: flex;
   justify-content: space-between;
   &--xmas {
      background: green;
   }
   &__item {
      list-style: none;
   }
   &__itemLink {
      color: red;
      &--isActive {
         color: white;
      }
   }
}
```

Exemple en CSS du rendu :

```css
.mainList{
   display: flex;
   justify-content: space-between;
}
.mainList--xmas{
   background: green;
}
.mainList__item {
   list-style: none;
}
.mainList__itemLink {
   color: red;
}
.mainList__itemLink--isActive {
   color: white;
}
```

### Pseudo attributs

Les pseudo attributs `before` et `after` permettent de créer des noeuds HTML en CSS. Ils sont essentiellement utilisés pour ajouter des ornements, des décorations... On peut bien entendu faire des animations avec, les positionner par rapport à leur parent (relative / absolute). **Ils doivent obligatoirement avoir un `content: ''`** afin de s'afficher.

```html

<section class="cover">
   <h1 class="cover__mainTitle">Présentation des pseudo-attributs</h1>
</section>
```

```css

.cover {
   background: #FDFDFD;
   padding: 20px;
   &__mainTitle {
      text-align: center;
      font-size: 24px;
      color: green;
      position: relative;
      &::before,
      &::after {
         content: '';
         position: absolute;
         display: block;
         width: 50px;
         height: 50px;
         background: green;
      }
      &::before {
         left: 0;
      }
      &::after {
         right: 0;
      }
   }
}
```

---

## REM, EM, %, VW Sizing (unités)

### %

- Taille par rapport au parent.

### EM

- Relative à la taille de son parent direct.

```css
.cover {
   font-size: 100%;
   &__mainTitle {
      /*1em=16px / 0.8em !== 16px*/
      font-size: .8em;
   }
}
```

### REM

- Le REM est basé sur la taille de la racine (soit la balise ) qui, par défaut a une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire de l'écraser en donnant une base de 10px soit 62.5%.

- Le REM est intéressant à utiliser si les media-queries employées sont en rem également. Cela vous permettra de garder des proportions égales lorsqu'on va redimensionner la page.

- Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.

```css
html {
   /* taille de typo à 10px */
   font-size:62.5%;
}
.mainTitle {
   /* 1.6rem === 16px */
   font-size: 1.6rem;
   /* 32rem === 320px */
   width: 32rem;
}
```

### VW(idth)/VH(eigth) Sizing

- Unités relatives à la taille de votre écran (peu importe le device).

- Attention au VH et à son contenu. 100vh === 100vh quoi qu'il arrive.

- VW : très utile pour les interfaces fluides.

--------------------------------------------------------------------------------

## SCSS

```
node-sass -w scss -o CSS
```

```html
<body>
   <section class="firstSection">
      <h2 class="firstSection_title">Titre</h2>
      <ul class="firstSection_list">
         <li class="firstSection_listItem is-active">Item 1</li>
         <li class="firstSection_listItem">Item 2</li>
         <li class="firstSection_listItem">Item 3</li>
      </ul>
   </section>
</body>
```

```css

/* variable pour la police */
$mainFont: "Open Sans", helvetica, arial, sans-serif;

/* variable pour la mediaqueries tablet */
$tablet-width: 768px;

/* media queries tablet */
@mixin tablet {
   @media (min-width: #{$tablet-width}) {
      @content;
   }
}

body {
   font-family: $mainFont;
}

.firstSection {
   background: rgba(0,255,0,0.5);

   /* pour la classe .firstSection__title */
   &__title {
      font-size:64px;
   }

   /* pour la classe .firstSection__list */
   &__list{

      /* pour la classe .firstSection__listItem */
      &Item {
         color: rgba(255,0,0,0.5);

         /* pour la classe .firstSection__listItem avec la classe .is-active */
         &.is-active {
            color: rgba(0,0,255,0.5);
         }
      }
   }

   /* pour la media-queries tablet*/
   @include tablet {
      background-color: rgba(255,255,0,0.5);
   }
}
```

--------------------------------------------------------------------------------

## CSS

### Responsive :

```HTML

<head>
   <meta name="viewport" content="width=device-width, initial-scale=1"/>
</head>

```


### Keyframes animation :

```css
.blinking {
   color: #93B7BE;
   -webkit-animation: blinkAnimation 1s infinite;
}

@-webkit-keyframes blinkAnimation {
   0% {
      color: #93B7BE;
   }
   50% {
      color: #000;
   }
   100% {
      color: #93B7BE;
   }
}
```

### Font-face

Les font-face permettent de fournir les fonts du site.

```css
@font-face {
   font-family: "Open Sans Regular";
   src: url("../fonts/OpenSans-Regular.ttf");
}

.message {
   font-family: "Open Sans";
}
```


### Media-queries

```css
.class {
  background:red;
}

@media (min-width: 768px) {
  .class{
    background:blue;
  }
}

@media (min-width: 1024px) {
  .class{
    background:yellow;
  }
}
```

---

## Liens utiles :

- [Caniuse](https://caniuse.com/) : c'est compatible partout ou pas ?
- [Front-end Developers Interview Questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions) : questions récurrentes sur le front-end
