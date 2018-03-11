# CSS en 2018

Ejercicios a partir del repo de Paqui Calabria [CSS en 2018](https://github.com/FCalabria/css-en-2018). Se traen todos las ramas a master para publicar todos los ejercicios con GitHub Pages.

[Slides](http://slides.com/paquicalabria/t3chfest/fullscreen)

Preview:

![](./result.jpg)

## Paso 1

https://cristinafsanz.github.io/css-en-2018/step1

Sin Flexbox ni CSS Grid Layout.

## Paso 2

https://cristinafsanz.github.io/css-en-2018/step2

Se añade:

En el html se añade en el from dentro del header la clase "flex-right".

En el css:

```
/* Generic classes */
.flex-right {
  margin-left: auto;
}

header {
  align-items: flex-end;
  display: flex;
}

header a {
  margin-left: var(--spacer);
  white-space: nowrap;
}

main {
  display: flex;
  flex-wrap: wrap;
}
main div {
  position: relative;
}

main span {
  top: 1rem;
  display: none;
  position: absolute;
  width: 100%;
}
main div:hover span, main div:focus span {
  background-color: var(--c-background);
  display: inline;
}

footer {
  display: flex;
  flex-direction: column;
  text-align: center;
}

.social-logos {
  display: flex;
  justify-content: space-evenly;
}
```

## Paso 3

https://cristinafsanz.github.io/css-en-2018/step3

Se añade:

En el css:

```
header input:placeholder-shown {
  border: var(--c-accent) 2px solid;
}
```

## Paso 4

https://cristinafsanz.github.io/css-en-2018/step4

Se añade:

En el html la clase landscape o portrait a todos los divs que contienen las imágenes. 

En el css:

```
.landscape {
  grid-column: span 2;
}
.portrait {
  grid-row: span 2;
}

@supports (display: grid) {
  main {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    grid-auto-flow: dense;
    grid-gap: var(--spacer);
  }
  main img {
    height: 100%;
    max-width: none;
    object-fit: cover;
    width: 100%;
  }
}
```


## Paso 5

https://cristinafsanz.github.io/css-en-2018/step5

Se añade: 

En el css:

```
@supports (display: grid) {

  main {
    /* Chrome grid in grid fix */
    grid-auto-rows: 200px;
  }

  main div {
    align-items: end;
    display: grid;
  }

  main span {
    position: relative;
    top: 0;
  }
  main img, main span {
    grid-column: 1;
    grid-row: 1;
  }
}
```

## Paso 6

https://cristinafsanz.github.io/css-en-2018/step6

Se añade: 

En el css:

```
main img {
  filter: contrast(0.9) sepia(0.2);
  position: relative;
}

@supports (filter: grayscale(1)) {
  main div:hover img, main div:focus img {
    filter: grayscale(.3) blur(2px) brightness(.5);
  }
  main div:hover span, main div:focus span {
    background-color: transparent;
  }
}

@supports (mix-blend-mode: overlay) {
  /* Filter idea from cssgram */
  main div:after {
    content: '';
    display: block;
    height: 100%;
    width: 100%;
    top: 0;
    left: 0;
    position: absolute;
    pointer-events: none;
    z-index: 3;
  }
  main div::after {
    background-image: radial-gradient(circle, #ecc798 20%, #d35435 75%, #634c03 100%);
    mix-blend-mode: overlay;
    opacity: 0.4;
  }
}
```

## Paso 7

https://cristinafsanz.github.io/css-en-2018/step7   

Se añade: 

En el html se añade la clase "urban-layout" en main y la clase "central-image" en la imagen 11.

En el css:

```
@supports (mix-blend-mode: hard-light) {
  .logo {
    position: relative;
  }
  .logo:after {
    content: '';
    display: block;
    height: 20%;
    width: 20%;
    opacity: 0;
    top: 42%;
    right: 9%;
    position: absolute;
    pointer-events: none;
    z-index: 3;
  }
  .logo::after {
    background: radial-gradient(circle, #fff 0%, #dcdd8b 20%, #000 100%);
    mix-blend-mode: hard-light;
  }
  .logo:hover::after {
    opacity: 0.5;
    transition: opacity .2s ease-in .5s;
  }
}

@supports (display: grid) {
  .urban-layout {
    grid-template-columns: repeat(4, 1fr);
    grid-template-areas: ". . . ." ". central central . " " . central central ."
  }
  .urban-layout .central-image {
    grid-area: central;
  }
}
```