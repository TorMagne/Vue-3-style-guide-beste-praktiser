## Disse reglene hjelper til med å forhindre feil, så lær og følg dem til enhver tid. Unntak kan eksistere, men bør være svært sjeldne.

Table of Contents:
- [Prettier code formatering](#Prettier-code-formatering)
- [HTML sematics og accessibility](#HTML-sematics-og-accessibility)
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



## Prettier code formatering

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

[Les mer om accessibility ](https://developer.mozilla.org/en-US/docs/Learn/Accessibility)

[Les mer om HTML semantics ](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

- Alle skal skrive riktig HTML semantics og implementere god accessibility. Som forbedrer tilgjengeligheten, forbedrer også SEO, noe som gjør nettstedet ditt mer søkbar.
- Å bygge tilgjengelige nettsteder er til fordel for alle.
- Å bry seg om tilgjengelighet viser god etikk og moral, noe som forbedrer ditt/bedriftens offentlige bilde.
- Andre gode fremgangsmåter som forbedrer tilgjengeligheten gjør også nettstedet ditt mer brukbart for andre grupper, for eksempel mobiltelefonbrukere, synshemede etc, eller de med lav nettverkshastighet. Faktisk kan alle dra nytte av mange slike forbedringer.
- Quote fra The Web Accessibility Directive "The 15-page directive requires all public sector websites and applications in EU member states to implement, enforce, and maintain a uniform set of accessibility standards."

Mann skal for eks ikke bruke ```<div></div>``` for en navigasjon. Mann skal da istede bruke riktig HTML semantics for en navigasjon som er ```<nav></nav>```

### ❌ Dårlig
```html
<!-- Navigation eksempel -->
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
<nav>
  <ul>
    <li><
      a href="#">Home</a>
    </li>
    <li>
      <a href="#">Blog</a>
    </li>
  </ul>
</nav>
```

---

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
