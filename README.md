> _Fork_ deze leertaak en ga aan de slag. 
Onderstaande outline ga je gedurende deze taak in jouw eigen GitHub omgeving uitwerken. 
De instructie vind je in: [docs/INSTRUCTIONS.md](docs/INSTRUCTIONS.md)

# 🍔 menu

Micro-interactie die mobiele navigatie mogelijk maakt, door middel van een hamburger-menu.

## Gebruiker

Aangezien het hamburger-menu niet word getoond op de desktop versie, word de gebruiker specifieker dan de overkoepelende doelgroep.
Deze micro-interactie is namelijk gericht op de mobiele gebruiker.

## User Story

Als mobiele gebruiker wil ik door middel van een hamburger-menu, alsnog toegang hebben tot de volledige navigatie van de website.

## Wireflow

![20221214_112206](https://user-images.githubusercontent.com/112861614/207584480-b240a354-7bef-414b-9e39-14bffe3b63bd.jpg)

## Beschrijving
Door de links en instellingen van de desktop versie ook op mobiel mogelijk te maken, heb ik een hamburger-menu toegepast.
Deze wordt pas weergegeven als de resolutie breedte kleiner of gelijk is aan 550px.
Door op het hamburger icoontje rechtsboven in de navigatie balk te klikken, verschijnt er een menu van boven, die het scherm vult.
Dit icoontje bestaat uit drie streepjes, waardoor ik ze door middel van een animatie in een kruis kan vormen. Hiermee kan de gebruiker het menu ook weer sluiten.

Hamburger menu in actie!

<img src="https://user-images.githubusercontent.com/112861614/212547721-f65b7d63-a5f3-4bad-9d21-285417c0a9a9.gif" width="400px">

Hamburger menu is INGEKLAPT.

![image](https://user-images.githubusercontent.com/112861614/212546900-bbeca4d0-0b90-4f25-a6eb-a19ad9c5d899.png)

Hamburger menu is UITGEKLAPT.

![image](https://user-images.githubusercontent.com/112861614/212546963-89f8f34b-6794-4290-9e6a-34b861c90a72.png)

https://tom-toolgankelijk.student.fdnd.nl/

## Kenmerken

### Hamburger menu

Door middel van een eventListener wacht ik voor een click event op de hamburger menu button. Deze bevat een aria-expanded attribuut.
Als blijkt dat deze false is, betekent het dat het hamburger icoontje in een kruisje moet veranderen en visa versa wat door CSS wordt afgehandeld.
Daarnaast toggled dit event een "open" class op de navigatie, die overigens hetzelfde element is als op de desktop versie.

```js
const hamburgerButton = document.querySelector("#navigation button");

hamburgerButton.addEventListener("click", function() {
    const isOpened = hamburgerButton.getAttribute('aria-expanded');
    if (isOpened === "false") {
        hamburgerButton.setAttribute("aria-expanded", "true");
    } else {
        hamburgerButton.setAttribute("aria-expanded", "false");
    }

    document.querySelector("#navigation #top-nav").classList.toggle("open");
    document.body.classList.toggle("stop-scroll");
});
```

```css
#hamburger-icon .line {
    transition: 
    y 200ms ease-in 200ms,
    rotate 200ms ease-in,
    opacity 0ms 200ms,
    fill 200ms;
    transform-origin: center;
}

#hamburger-icon[aria-expanded="true"] .line {
    transition: 
    y 200ms ease-in,
    rotate 200ms ease-in 200ms,
    opacity 0ms 200ms,
    fill 200ms;
    fill: var(--c-huisstijl-magenta-plain);
}

#hamburger-icon[aria-expanded="true"] :is(.top, .bottom) {
    y: 45px;
}

#hamburger-icon[aria-expanded="true"] .top {
    rotate: 45deg;
}

#hamburger-icon[aria-expanded="true"] .middle {
    opacity: 0;
}

#hamburger-icon[aria-expanded="true"] .bottom {
    rotate: -45deg;
}
```

### Progressie per principe

Een voorbeeld van de code voor het eerste principe: Waarneembaar.
Met daarbij comments ter verheldering.

```js
checkboxesWaarneembaar.forEach(function (checkbox) {
    //vul de Array met de huidige checkbox vanuit de DOM
    waarneembaarChecklistCheckboxes.push(checkbox);
    //verander de checked waarde van de checkboxes aan de hand van de bijbehorende value (uit de localStorage of standaard false)
    checkboxesWaarneembaar[waarneembaarChecklistCheckboxes.indexOf(checkbox)].checked = waarneembaarChecklistValues[waarneembaarChecklistCheckboxes.indexOf(checkbox)];
    checkbox.addEventListener("change", function () {
        //verander de progressie van het principe aan de hand van de (handmatig) aangevinkte checkboxes
        changeProgression(checkbox, this.closest(".richtlijnen").parentElement.id);
        //pas de bijbehorende value aan aan de hand van de huidige checkox value
        waarneembaarChecklistValues[waarneembaarChecklistCheckboxes.indexOf(checkbox)] = checkbox.checked;
        //maak of verander de localStorage met de actuele values
        localStorage.setItem("waarneembaarProgression", JSON.stringify(waarneembaarChecklistValues));
    });
    //verander de progressie van het principe aan de hand van de (automatisch) aangevinkte checkboxes
    changeProgression(checkbox, checkbox.closest(".richtlijnen").parentElement.id);
});
```

## Licentie

![GNU GPL V3](https://www.gnu.org/graphics/gplv3-127x51.png)

This work is licensed under [GNU GPLv3](./LICENSE).
