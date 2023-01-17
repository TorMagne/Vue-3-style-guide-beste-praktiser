# StyleGuide

# Beste praksis for Vue.js

## Komponentnavn skal alltid være flerordige

### Brukernavn for komponenter skal alltid være flerordige, med unntak av rot-App-komponenter. Dette hindrer konflikter med eksisterende og fremtidige HTML-elementer, siden alle HTML-elementer er et enkelt ord.

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

### I kode som er commited bør prop-definisjoner alltid være så detaljerte som mulig, med å angi minst type(r).

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
