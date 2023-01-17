## Disse reglene hjelper til med å forhindre feil, så lær og følg dem til enhver tid. Unntak kan eksistere, men bør være svært sjeldne.

Table of Contents:
- [Beste praksiser for Vue 3](#Beste-praksiser-for-Vue-3)
  - [Komponentnavn skal alltid være flerordige](#Komponentnavn-skal-alltid-være-flerordige)
  - [Bruk detaljerte prop-definisjoner](#Bruk-detaljerte-prop-definisjoner)
  - [Bruk nøkkel med v-for](#Bruk-nøkkel-med-v-for)
  - [Unngå v-if med v-for](#Unngå-v-if-med-v-for)
  - [Komponent navn på views](#Komponent-navn-på-views)
  - [Komponentfilnavn for enkel-filkomponenter](#Komponentfilnavn-for-enkel-filkomponenter)
  - [Tett sammenkoblede komponentnavn](#Tett-sammenkoblede-komponentnavn)
  - [Navn på fullordskomponenter](#Navn-på-fullordskomponenter)
  - [Prop navn casing](#Prop-navn-casing)
  - [Enkeltfilkomponent på toppnivå elementrekkefølge](#Enkeltfilkomponent-på-toppnivå-elementrekkefølge)
- [Beste praksiser for Pinia](#Beste-praksiser-for-Pinia)
  - [Definer en Pinia store](#Definer-en-Pinia-store)
  - [Navngivning på Pinia store filer](#Navngivning-på-Pinia-store-filer)
  - [Pinia store importering eksempel](#Pinia-store-importering-eksempel)

---



## Beste praksiser for Vue 3

### Komponentnavn skal alltid være flerordige

Navn på komponenter skal alltid være flerordige, med unntak av rot-App-komponenter. Dette hindrer konflikter med eksisterende og fremtidige HTML-elementer, siden alle HTML-elementer er et enkelt ord.

### ❌ Dårlig 

```html
<Item />
```

### ✅ Bra

```html
<TodoItem />
```
---

### Bruk detaljerte prop-definisjoner

I kode som er commited bør prop-definisjoner alltid være så detaljerte som mulig, med å angi minst type(r).

### ❌ Dårlig
```js
// Dette er bare OK når man prototyping
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

### Bruk nøkkel med v-for

Nøkkel med v-for er alltid nødvendig på komponenter for å opprettholde intern komponenttilstand nedover undertrær. Selv for elementer er det en god praksis å opprettholde forutsigbart oppførsel.

### ❌ Dårlig
```html
<ul>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ul>
```

### ✅ Bra
```html
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

### Unngå v-if med v-for

Bruk aldri v-if på samme element som v-for.

Det er to vanlige tilfeller hvor dette kan være fristende:

- For å filtrere elementer i en liste (f.eks. v-for = "user in users" v-if = "user.isActive"). I disse tilfellene, erstatt users med en ny computed property som returnerer den filtrerte listen (f.eks. activeUsers).
- For å unngå å rendre en liste hvis den skal skjules (f.eks. v-for = "user in unsers" v-if = "shouldShowUsers"). I disse tilfellene flytter du v-if til et container-element (f.eks. ul, ol).

### ❌ Dårlig
```html
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
```html
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

### Komponent navn på views

Navn på views komponenter skal være PascalCase og skal ha et forklarendre navn med en (View) prefiks

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
```html
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
```html
<!-- template / HTML -->
<WelcomeMessage greeting-text="hi"/>
```
---

### Enkeltfilkomponent på toppnivå elementrekkefølge

Enkeltfilkomponenter bør alltid være i denne rekkefølgen <template>-, <script>- og <style>-tagger konsekvent, med <style> sist, fordi minst en av de to andre alltid er nødvendig.
  
### ❌ Dårlig
```html
<style>/* ... */</style>
<script>/* ... */</script>
<template>...</template>

<script>/* ... */</script>
<template>...</template>
<style>/* ... */</style>
  ```
  
### ✅ Bra
```html
<template>...</template>
<script>/* ... */</script>
<style>/* ... */</style>
```
---
  
## Beste praksiser for Pinia
  
### Definer en Pinia store
- Du kan navngi returverdien til `defineStore()` alt du vil,
- men det er best å bruke navnet på Pinia store og omgi den med `use`
- og `Store` (f.eks. `useUserStore`, `useCartStore`, `useProductStore`)
- det første argumentet er en unik ID for store på tvers av applikasjonen din
  
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
store/
|- myuserstore.vue

store/
|- myUserStore.vue
```
  
### ✅ Bra
```
store/
|- MyUserStore.vue
```
  
### Pinia store importering eksempel
```js
<script setup>
```js
// importing the store
import { useTaskStore } from '../stores/TaskStore';
  
// setting the store
const taskStore = useTaskStore();
<script>
```
```
---
  

