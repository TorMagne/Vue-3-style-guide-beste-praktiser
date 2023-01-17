# StyleGuide og beste praksis for Vue.js

## Disse reglene hjelper til med å forhindre feil, så lær og følg dem til enhver tid. Unntak kan eksistere, men bør være svært sjeldne.

## Table of Contents

- [Komponentnavn skal alltid være flerordige](#Komponentnavn-skal-alltid-være-flerordige)
- [Bruk detaljerte prop-definisjoner](#Bruk-detaljerte-prop-definisjoner)
- [Bruk nøkkel med v-for](#Bruk-nøkkel-med-v-for)
- [Unngå v-if med v-for](#Unngå-v-if-med-v-for)
- [Komponentfilnavn for enkel-filkomponenter](#Komponentfilnavn-for-enkel-filkomponenter)

## Komponentnavn skal alltid være flerordige

Brukernavn for komponenter skal alltid være flerordige, med unntak av rot-App-komponenter. Dette hindrer konflikter med eksisterende og fremtidige HTML-elementer, siden alle HTML-elementer er et enkelt ord.

### ❌ Dårlig 

```html
<!-- Dårlig -->
<Item />
```

### ✅ Bra

```html
<!-- Bra-->
<TodoItem />
```

## Bruk detaljerte prop-definisjoner

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

## Bruk nøkkel med v-for

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

## Unngå v-if med v-for

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

## Komponentfilnavn for enkel-filkomponenter

Filnavnene til Single-File Components skal være PascalCase.

PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og maler, så langt det er mulig.

### ❌ Dårlig
```html
components/
|- mycomponent.vue

components/
|- myComponent.vue
```
### ✅ Bra
```html
components/
|- MyComponent.vue
```
