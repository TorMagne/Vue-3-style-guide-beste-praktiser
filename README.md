## Disse reglene hjelper til med å forhindre feil, så lær og følg dem til enhver tid. Unntak kan eksistere, men bør være svært sjeldne.

Table of Contents:
- [Prettier kode formatering](#Prettier-kode-formatering)
- [HTML sematics og accessibility](#HTML-sematics-og-accessibility)
  - [aria-label](#aria-label)
- [Tailwind](#Tailwind)
  - [Tailwind extension](#Tailwind-extension)
  - [Tailwind apply](#Tailwind-apply)
  - [Tailwind custom fonts](#Tailwind-custom-fonts)
  - [one-off custom value i Tailwind](#one-off-custom-value-i-Tailwind)
- [Best praksis for Vue 3](#Best-praksis-for-Vue-3)
  - [v-for og v-if](#v-for-og-v-if)
    - [Bruk nøkkel med v-for](#Bruk-nøkkel-med-v-for)
    - [Bruk en unik id på nøkkel i v-for](#Bruk-en-unik-id-på-nøkkel-i-v-for)
    - [Unngå v-if med v-for](#Unngå-v-if-med-v-for)
  - [Komponenter](#Komponenter)
    - [Komponentnavn skal alltid være flerordige](#Komponentnavn-skal-alltid-være-flerordige)
    - [Importering av komponenter](#Importering-av-komponenter)
    - [Komponent navn på views](#Komponent-navn-på-views)
    - [Komponentfilnavn for enkel-filkomponenter](#Komponentfilnavn-for-enkel-filkomponenter)
    - [Tett sammenkoblede komponentnavn](#Tett-sammenkoblede-komponentnavn)
    - [Navn på fullordskomponenter](#Navn-på-fullordskomponenter)
    - [Enkeltfilkomponent på toppnivå elementrekkefølge](#Enkeltfilkomponent-på-toppnivå-elementrekkefølge)
  - [Props](#Props)
    - [Bruk detaljerte prop-definisjoner](#Bruk-detaljerte-prop-definisjoner)
    - [Prop navn casing](#Prop-navn-casing)
- [Best praksis for Pinia](#Best-praksis-for-Pinia)
  - [Definer en Pinia store](#Definer-en-Pinia-store)
  - [Navngivning på Pinia store filer](#Navngivning-på-Pinia-store-filer)
  - [Pinia store importering eksempel](#Pinia-store-importering-eksempel)
  - [Basic eksempel på en Pinia store](#Basic-eksempel-på-en-Pinia-store)

---



## Prettier kode formatering

:bangbang: Disse reglene for Prettier er noe alle skal bruke. :bangbang:

:bangbang: Det kommer til og være en ```.prettierrc``` fil i alle Vue 3 prosjekter.
Denne filen innholder regler for Prettier som alle skal følge. :bangbang:

Prettier extension skal være installert i VS Code for alle prosjekter som bruker Vue 3.

Dette er den rette extension å installere.

![Prettier](https://user-images.githubusercontent.com/61709493/213147526-92ad0894-6ca2-4a2e-9d10-e0fa87b30459.png)

Sørg for at Prettier er valg som default formatter i VS Code setting.

![Prettier setting](https://user-images.githubusercontent.com/61709493/213150743-73e72f53-0286-4ddf-a560-cf8e82486d81.png)


Sørg også for at Prettier: Use Editor Config er på.

![Prettier Editor Config](https://user-images.githubusercontent.com/61709493/213149028-3a95b2ae-126b-40e8-9fb3-8683e4bb3415.png)

---

## HTML sematics og accessibility

:bangbang: Alle skal skrive riktig HTML semantics og implementere god accessibility. Som forbedrer tilgjengeligheten, forbedrer også SEO, noe som gjør nettstedet ditt mer søkbar. :bangbang:
- Å bygge tilgjengelige nettsteder er til fordel for alle.
- Å bry seg om tilgjengelighet viser god etikk og moral, noe som forbedrer ditt/bedriftens offentlige bilde.
- Andre gode fremgangsmåter som forbedrer tilgjengeligheten gjør også nettstedet ditt mer brukbart for andre grupper, for eksempel mobiltelefonbrukere, synshemede etc, eller de med lav nettverkshastighet. Faktisk kan alle dra nytte av mange slike forbedringer.
- Quote fra The Web Accessibility Directive "The 15-page directive requires all public sector websites and applications in EU member states to implement, enforce, and maintain a uniform set of accessibility standards."

Mann skal for eks ikke bruke ```<div></div>``` for en navigasjon. Mann skal da istede bruke riktig HTML semantics for en navigasjon som er ```<nav></nav>```

Er du i tvil om hva som er riktig semantic i forhold til hva du holder på og lage kan du se på linkene nedenfor.

[Les mer om accessibility ](https://developer.mozilla.org/en-US/docs/Learn/Accessibility)

[Les mer om HTML semantics ](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

[Les mer om HTML elementer](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

### ❌ Dårlig
```html
<!-- Navigasjon eksempel -->
<div>
    <li>
      <a href="#">Home</a>
    </li>
    <li>
      <a href="#">Blog</a>
    </li>
</div>
```


### ✅ Bra
```html
<!-- Navigasjon eksempel -->
<nav>
  <ul>
    <li>
      <a href="#">Home</a>
    </li>
    <li>
      <a href="#">Blog</a>
    </li>
  </ul>
</nav>
```

---

## aria-label

:bangbang: aria-label er noe alle skal bruk hvis det mangler standard tilgjengelige navn på et element, eller innholde ikke er beskrevet nøyaktig, og det ikke er noe synlig innhold i DOM-en som kan assosieres med objektet for å gi det mening. :bangbang:

- Det meste av innholdet har et tilgjengelig navn generert fra tekstinnholdet i det umiddelbare innpakningselementet. Tilgjengelige navn kan også opprettes av visse attributter eller tilknyttede elementer.

- Som standard er en knapps tilgjengelige navn innholdet mellom den åpne og avsluttende ```<button>``` taggen, et bilde tilgjengelige navn er innholdet i alt-attributtet, og et ```<form></form>``` tilgjengelige navn er innholdet i det tilknyttede ```<label>``` elementet.

- Hvis ingen av disse alternativene er tilgjengelige, eller hvis standard tilgjengelig navn ikke er passende, bruk aria-label-attributtet for å definere det tilgjengelige navnet på et element.

Et vanlig eksempel er en knapp som inneholder en SVG.

aria-label-attributtet kan brukes til å definere en string som merker det interaktive elementet det er satt på. Dette gir elementet dets tilgjengelige navn.

Er du i tvil så kan du finne mer informasjon om aria-label i linken nedenfor

[Les mer om aria-label](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label)

### ✅ Eksempel
```html
<button aria-label="Close" onclick="myDialog.close()">
  <svg
    aria-hidden="true"
    focusable="false"
    width="17"
    height="17"
    xmlns="http://www.w3.org/2000/svg">
    <path
      d="m.967 14.217 5.8-5.906-5.765-5.89L3.094.26l5.783 5.888L14.66.26l2.092 2.162-5.766 5.889 5.801 5.906-2.092 2.162-5.818-5.924-5.818        5.924-2.092-2.162Z"
      fill="#000" />
  </svg>
</button>
```
---

## Tailwind

## Tailwind extension

Anbefaler alle og laste ned Tailwind CSS IntelliSense extension. Sånn at mann får intellisense på alle Tailwind klassene.

Får også egenskapen til og hover en klasse fra Tailwind får og se den faktise CSS til den klassen.

Den rette extension og installere vises på bildet nedenfor.

![Tailwind IntelliSense](https://user-images.githubusercontent.com/61709493/213677701-5c5b4d48-62aa-4774-9e96-c813f69d0296.png)


## Tailwind apply

Tailwind CSS er utiliti først og bruker et klasse basert system. Derfor kan det ofte bli veldig mye klasser på HTML elementer.

:bangbang: Anbefaler på det sterkeste å se den youtube videoen i linken nedenfor. Får en bedre forståelse av @apply og hvordan du får mest ut av Tailwind CSS :bangbang:

[Youtube video Composing Utilities with @apply](https://www.youtube.com/watch?v=TrftauE2Vyk&ab_channel=TailwindLabs)

[Les mer om extracting classes with apply](https://tailwindcss.com/docs/reusing-styles#extracting-classes-with-apply)

```html
<!-- eksempel på mye klasser på et HTML element -->
<a href="#" class="inline-block px-5 py-3 rounde-lg shadow-lg bg-indigo-500 hover:bg-indigo-400 hover:-translate-y-0.5 focus:outline-none focus:ring focus:ring-offset-2 focus:ring-indigo-500 focus:ring-opacity-50 active:bg-indigo-600 transform transition text-white uppercase tracking-wider font-semibold text-sm sm:text-base">
  Book your escape
</a>

<a href="#" class="inline-block px-5 py-3 rounde-lg shadow-lg bg-indigo-500 hover:bg-indigo-400 hover:-translate-y-0.5 focus:outline-none focus:ring focus:ring-offset-2 focus:ring-indigo-500 focus:ring-opacity-50 active:bg-indigo-600 transform transition text-white uppercase tracking-wider font-semibold text-sm sm:text-base">
  Traveling
</a>
```

Hvis du finner deg selv i en lignende situasjon som det eksempelet ovenfår kan du bruke @apply.

Med @apply kan du ta alle klassene fra en HTML element og lage en ny tilpassede klasse med de valgte klassene.

Dette vil da skje i den CSS filen der tailwind er importert.

```css
<!-- Tailwind CSS fil -->
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer components {
  .custom-button {
    @apply inline-block px-5 py-3 rounde-lg shadow-lg bg-indigo-500 hover:bg-indigo-400 hover:-translate-y-0.5 focus:outline-none focus:ring focus:ring-  offset-2 focus:ring-indigo-500 focus:ring-opacity-50 active:bg-indigo-600 transform transition text-white uppercase tracking-wider font-semibold text-sm sm:text-base;
  }
}
```

Grunnen til at mann skal bruk ```@layer components``` er at disse klassene må komme før Tailwind sine utility klasser, Hvis mann setter de etter utilities eller bruker ```@apply utilites``` Så vil alle klassen som vi har i denne tilpassede klassen bli overkjørt av utiliti klassene. 

```html
<!-- eksempel på HTML etter flytting av klasser -->
<a href="#" class="custom-button">
  Book you escape
</a>

<a href="#" class="custom-button">
  Traveling
</a>
```

Flere gode kilder for og lære mer om Tailwind CSS i linkene nedenfor.

- [Tailwind CSS youtube kanal](https://www.youtube.com/@TailwindLabs/videos)
- [Tailwind dokumentasjon](https://tailwindcss.com/)
- [Weather App Build (Vue 3 & Tailwind) - THe Net Ninja](https://www.youtube.com/watch?v=gUsBaB5ViAo&list=PL4cUxeGkcC9hfoy8vFQ5tbXO3vY0xhhUZ&ab_channel=TheNetNinja)

---

## Tailwind custom fonts

Får og bruke custom fonts/legge til ekstra fonter som for eks google fonts i Tailwind CSS må du extende Tailwind CSS sin font familie.

Dette gjøres da i ```tailwind.config.js``` filen.

[Les mer om Tailwind CSS font family](https://tailwindcss.com/docs/font-family)

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./public/**/*.html', './src/**/*.{vue,js,ts,jsx,tsx}'],
  theme: {
    extend: {
      fontFamily: {
        sora: "'Sora', sans-serif",
      },
    },
  },
  plugins: [],
};
```

Grunnen til at vi gjør det på denne måten er at vi da får alle utilities fra Tailwind CSS får denne font familien. Som for eksempel ```lg:font-sora``` som da bare vil vise fonten Sora på stor skjerm og oppover.

Dette vil da gjelde alle varianter i Tailwind CSS ```hover:font-sora```, ```lg:font-sora"```, ```md:font-sora``` osv.

```html
<!-- eksempel -->
<h1 class="lg:font-sora">Eksempel heading</h1>
```

Importering av fonter vil skje på den vanlige måten med og importere de i ```ìndex.html``` filen i Vue

```html
<!-- Eksempel på importering av fonter-->
  <head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width,initial-scale=1.0" />
    <link rel="icon" href="<%= BASE_URL %>favicon.ico" />
    <title><%= htmlWebpackPlugin.options.title %></title>
    <!-- google fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Raleway:wght@300;500;700&family=Sora:wght@300;400;600;700;800&display=swap" rel="stylesheet" />
  </head>
```

---

## one-off custom value i Tailwind

Hvis mann har bruk for eks en height verdi på ```60px``` som ikke eksisterer i Tailwdind så kan mann bruke en one-off custom value.

Det nermeste vi kommer til ```60px```i Tailwind er ```64px``` som vi da ville brukt klassen ```h-16``` til.

For og bruke en vilkårlige verdi vil vi da bruke en postfix med square brackets som vist i eksempelet nedenfor.

```html
<nav class="h-[60px]">
  <ul>
    <li>
      <a href="#">Home</a>
    </li>
  </ul>
</nav>
```

Flere eksempler.

```html
<button class="bg-[#1da1f2]">...</button>
<div class="ease-[cubic-bezier(0.95,0.05,0.795,0.035)]">...</div>
<p class="underline-offset-[3px]">...</p>
<p class="font-[1100]">...</p>
```

## Best praksis for Vue 3

## v-for og v-if

### Bruk nøkkel med v-for

Nøkkel med v-for er alltid nødvendig på komponenter for å opprettholde intern komponenttilstand nedover undertrær. Selv for elementer er det en god praksis å opprettholde forutsigbart oppførsel.

### ❌ Dårlig
```vue
<ul>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ul>
```

### ✅ Bra
```vue
<ul>
  <li
    v-for="todo in todos"
    :key="todo.id"
  >
    {{ todo.text }}
  </li>
</ul>
```
---

### Bruk en unik id på nøkkel i v-for

En v-for-loop skal bruke en unik id for en nøkkel hvis en er tilgjengelig.

En v-for-loop som bruker den unike id-egenskapen til hvert element som en måte å spore unikheten til hvert av listeelementene - som vanligvis foreslått av kompilatoren, og for å øke DOM-ytelsen.

### ❌ Dårlig
```vue
<!-- Kan brukes hvis en unik id ikke er tilgjengelig eller for prototyping -->
<div v-for="(task, taskIndex) in taskStore.favs" :key="taskIndex">
  <div class="card-body">
    <TaskDetails :task="task" />
  </div>
</div>
```

### ✅ Bra
```vue
<div v-for="task in taskStore.favs" :key="task.id">
  <div class="card-body">
    <TaskDetails :task="task" />
  </div>
</div>
```
---

### Unngå v-if med v-for

Bruk aldri v-if på samme element som v-for.

Det er to vanlige tilfeller hvor dette kan være fristende:

- For å filtrere elementer i en liste (f.eks. v-for = "user in users" v-if = "user.isActive"). I disse tilfellene, erstatt users med en ny computed property som returnerer den filtrerte listen (f.eks. activeUsers).
- For å unngå å rendre en liste hvis den skal skjules (f.eks. v-for = "user in unsers" v-if = "shouldShowUsers"). I disse tilfellene flytter du v-if til et container-element (f.eks. ul, ol).

### ❌ Dårlig
```vue
<ul>
  <li
    v-for="user in users"
    v-if="user.isActive"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>
```
---

### ✅ Bra
```vue
<ul>
  <li
    v-for="user in activeUsers"
    :key="user.id"
  >
    {{ user.name }}
  </li>
</ul>

<ul>
  <template v-for="user in users" :key="user.id">
    <li v-if="user.isActive">
      {{ user.name }}
    </li>
   </template>
</ul>
```
---

## Komponenter

### Komponentnavn skal alltid være flerordige

Navn på komponenter skal alltid være flerordige, med unntak av rot-App-komponenter. Dette hindrer konflikter med eksisterende og fremtidige HTML-elementer, siden alle HTML-elementer er et enkelt ord.

### ❌ Dårlig 

```vue
<Item />
```

### ✅ Bra

```vue
<TodoItem />
```
---

### Importering av komponenter

Imortering av komponenter skal vær PascalCase.

PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template.

### ❌ Dårlig
```vue
<todo-item><todo-item/>

<toDoItem><toDoItem/>
```

### ✅ Bra
```vue
<TodoItem />
```
---

### Komponent navn på views

Navn på views komponenter skal være PascalCase og skal ha et forklarendre navn med en (View) postfiks.

PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template.


### ❌ Dårlig
```
views/
|- myview.vue

views/
|- myView.vue
```
### ✅ Bra
```
views/
|- HomeView.vue

views/
|- LoginView.vue
```
---

### Komponentfilnavn for enkel-filkomponenter

Filnavnene til Single-File komponenter skal være PascalCase.

PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template.

### ❌ Dårlig
```
components/
|- mycomponent.vue

components/
|- myComponent.vue
```
### ✅ Bra
```
components/
|- MyComponent.vue
```
---

### Tett sammenkoblede komponentnavn

Child komponenter som er tett koblet til deres parent komponent, bør inkludere navnet på den overordnede komponenten som et prefiks.

Hvis en komponent bare gir mening i sammenheng med en enslig parent komponent, bør forholdet være tydelig i navnet. Siden editoren vanligvis organiserer filer alfabetisk, holder dette også disse relaterte filene ved siden av hverandre.

### ❌ Dårlig
```
components/
|- TodoList.vue
|- TodoItem.vue
|- TodoButton.vue

components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue
```

### ✅ Bra
```
components/
|- TodoList.vue
|- TodoListItem.vue
|- TodoListItemButton.vue

components/
|- SearchSidebar.vue
|- SearchSidebarNavigation.vue
```
---

### Navn på fullordskomponenter

Komponentnavn skal ha hele ord fremfor forkortelser.

Autofullføringen i editoren gjør kostnadene ved å skrive lengre navn svært lave, mens klarheten de gir er uvurderlig. Spesielt uvanlige forkortelser bør alltid unngås.

### ❌ Dårlig
```
components/
|- SdSettings.vue
|- UProfOpts.vue
```

### ✅ Bra
```
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```
---

### Enkeltfilkomponent på toppnivå elementrekkefølge

Enkeltfilkomponenter bør alltid være i denne rekkefølgen ``` <template> <script> <style> ``` tagger konsekvent, med <style> sist, fordi minst en av de to andre alltid er nødvendig.
  
### ❌ Dårlig
```vue
<style>/* ... */</style>
<script>/* ... */</script>
<template>...</template>

<script>/* ... */</script>
<template>...</template>
<style>/* ... */</style>
  ```
  
### ✅ Bra
```vue
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>
```
---

## Props

### Bruk detaljerte prop-definisjoner

I kode som er commited bør prop-definisjoner alltid være så detaljerte som mulig, med å angi minst type(r).

### ❌ Dårlig
```js
// Dette er bare OK når man prototyper
const props = defineProps(['status'])
```

### ✅ Bra
```js
const props = defineProps({
  status: String,
  required: true
})
```
---

### Prop navn casing

Propnavn skal alltid bruke camelCase under deklarering, men kebab-case i templates og JSX.

Vi følger ganske enkelt konvensjonene for hvert språk. Innen JavaScript er camelCase mer naturlig. Innen HTML er kebab-case.

### ❌ Dårlig
```js
<!-- Javascript -->
props: {
  'greeting-text': String
}
```
```vue
<!-- template / HTML -->
<WelcomeMessage greetingText="hi"/>
```

### ✅ Bra
```js
<!-- Javascript -->
props: {
  greetingText: String
}
```
```vue
<!-- template / HTML -->
<WelcomeMessage greeting-text="hi"/>
```
---
  
## Best praksis for Pinia
  
### Definer en Pinia store
- Du kan navngi returverdien til `defineStore()` alt du vil,
- men det er best å bruke navnet på Pinia store og omgi den med `use`
- og `Store` (f.eks. `useUserStore`, `useCartStore`, `useProductStore`)
- det første argumentet er en unik ID for store på tvers av applikasjonen din
  
[Flere detaljer om Pinia define store](https://pinia.vuejs.org/core-concepts/)
  
### ❌ Dårlig
```js
import { defineStore } from 'pinia';

export const taskStore = defineStore('useTaskStore', {
  state: () => ({}),
});

import { defineStore } from 'pinia';

export const taskStore = defineStore('TaskStore', {
  state: () => ({}),
});
```
  
### ✅ Bra
```js
import { defineStore } from 'pinia';

export const useTaskStore = defineStore('taskStore', {
  state: () => ({}),
});
```
---
  
### Navngivning på Pinia store filer
  
Filnavnene til Pinia store skal være PascalCase.
  
PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template.
  
### ❌ Dårlig
```
stores/
|- myuserstore.vue

stores/
|- myUserStore.vue
```
  
### ✅ Bra
```
stores/
|- MyUserStore.vue
```
---
  
### Pinia store importering eksempel

```vue
<script setup>
import { useTaskStore } from '../stores/TaskStore';
  
const taskStore = useTaskStore();
</script>
```
---

### Basic eksempel på en Pinia store

```js
import { defineStore } from 'pinia';

export const useTaskStore = defineStore('taskStore', {
  state: () => ({
    // store state(s)
    tasks: [
      {id: 1, title: "buy some milk", isFav: false},
      {id: 2, title: "play Gloomhaven", isFav: true}
      ],
  }),
  getters: {
    // returning true or false depending on the isFave
    favs() {
      return this.tasks.filter((task) => task.isFav);
    },
  },
  actions: {
    // push to tasks array
    addTask(task) {
      this.tasks.push(task);
    },
    // deleting a task depending if true or not
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => {
        return task.id !== id;
      });
    },
    // setting a task to fav if the id matches
    toggleFav(id) {
      const task = this.tasks.find((task) => task.id === id);
      task.isFav = !task.isFav;
    },
  },
});
```
---
