# StyleGuide

# Beste praksis for Vue.js

## Komponentnavn skal alltid være flerordige

Brukernavn for komponenter skal alltid være flerordige, med unntak av rot-App-komponenter. Dette hindrer konflikter med eksisterende og fremtidige HTML-elementer, siden alle HTML-elementer er et enkelt ord.

### Dårlig
```html
<!-- i forhåndskompilerte maler -->
<Item />

<!-- i i-DOM-maler -->
<item></item>

### Bra

```html<!-- i forhåndskompilerte maler -->
<TodoItem />

<!-- i i-DOM-maler -->
<todo-item></todo-item>
