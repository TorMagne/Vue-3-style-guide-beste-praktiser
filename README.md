# StyleGuide

# Beste praksis for Vue.js

## Komponentnavn skal alltid være flerordige

Brukernavn for komponenter skal alltid være flerordige, med unntak av rot-App-komponenter. Dette hindrer konflikter med eksisterende og fremtidige HTML-elementer, siden alle HTML-elementer er et enkelt ord.

### <span class="text-danger">Dårlig</span>

```html
<!-- Dårlig -->
<Item />
```

### Bra

```html
<!-- Bra-->
<TodoItem />
```
