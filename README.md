## Disse reglene vil hjelpe deg med å unngå feil, så følg dem så godt som mulig til enhver tid.

Table of Contents:

- [Prettier kode formatering](#Prettier-kode-formatering)
- [HTML sematics og accessibility](#HTML-sematics-og-accessibility)
  - [aria-label](#aria-label)
  - [max width for paragrafer](#max-width-for-paragrafer)
- [Tailwind](#Tailwind)
  - [Tailwind extension](#Tailwind-extension)
  - [Tailwind apply](#Tailwind-apply)
  - [Tailwind custom fonts](#Tailwind-custom-fonts)
  - [one-off custom value i Tailwind](#one-off-custom-value-i-Tailwind)
- [Best praksis for Javacript](#Best-praksis-for-Javacript)
  - [Bruk samme ordforråd for samme type variabel](#Bruk-samme-ordforråd-for-samme-type-variabel)
  - [Bruk søkbare navn](#Bruk-søkbare-navn)
  - [Bruk variabler for å forklare](#Bruk-variabler-for-å-forklare)
  - [Ingen mental kartlegging](#Ingen-mental-kartlegging)
  - [Ingen unødvendig kontekst](#Ingen-unødvendig-kontekst)
  - [Navngi funksjoner etter hva de gjør](#Navngi-funksjoner-etter-hva-de-gjør)
  - [Funksjons parameter](#Funksjons-parameter)
- [Best praksis for Vue 3](#Best-praksis-for-Vue-3)
  - [Axios config i main js](#Axios-config-i-main-js)
  - [Async Await med Axios i Vue 3](#Async-Await-med-Axios-i-Vue-3)
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

:bangbang: Alle skal følge disse reglene for Prettier :bangbang:

:bangbang: Det kommer til å være en `.prettierrc` fil i alle Vue 3 prosjekter.
Denne filen inneholder regler for Prettier som alle skal følge. :bangbang:

### Innhold for prettierrc fil

```js
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true,
  "bracketSpacing": true,
  "vueIndentScriptAndStyle": true,
  "printWidth": 100,
  "singleAttributePerLine": false
}
```

Prettier extension (utvidelse) skal være installert i VS Code for alle prosjekter som bruker Vue 3.

Dette er den korrekte utvidelsen.

![Prettier](https://user-images.githubusercontent.com/61709493/213147526-92ad0894-6ca2-4a2e-9d10-e0fa87b30459.png)

Sørg for at Prettier er satt til default formatter i VS Code setting.

![Prettier setting](https://user-images.githubusercontent.com/61709493/213150743-73e72f53-0286-4ddf-a560-cf8e82486d81.png)

Pass på at Prettier: Use Editor Config er også på.

![Prettier Editor Config](https://user-images.githubusercontent.com/61709493/213149028-3a95b2ae-126b-40e8-9fb3-8683e4bb3415.png)

---

## HTML Sematics og Accessibility

:bangbang: Det påkreves at man skriver HTML semantics på riktig måte, og at man legger opp til god tilgjengelighet for alle endebrukere. Dette vil forbedre din SEO, som da gjør nettstedet ditt mer navigeringsvennlig og søkbart. :bangbang:

- Nettsteder med god tilgjengelighet er til fordel for absolutt alle.
- Å bry seg om tilgjengelighet viser god etikk og moral, noe som forbedrer ditt/bedriftens offentlige bilde.
- Andre gode fremgangsmåter som forbedrer tilgjengeligheten gjør også nettstedet ditt mer brukbart er å legge til rette for andre grupper, som for eksempel mobiltelefonbrukere, synshemmede etc, eller de med lav nettverkshastighet. Faktisk så kan alle dra nytte av mange slike forbedringer.
- Sitat fra The Web Accessibility Directive: "The 15-page directive requires all public sector websites and applications in EU member states to implement, enforce, and maintain a uniform set of accessibility standards."

Ett godt eksempel er at man skal ikke bruke `<div></div>` for navigasjon, men istedet bruke `<nav></nav>`, for da blir i dette tilfellet korrekt HTML semantics.

Om du blir usikker på hva som blir korrekt semantics i sammenheng med hva du holder på med, så kan du referere til linkene nedenfor.

[Les mer om accessibility (tilgjengelighet) ](https://developer.mozilla.org/en-US/docs/Learn/Accessibility)

[Les mer om HTML semantics ](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

[Les mer om HTML elementer](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

### ✅ Korrekt

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

### ❌ Ikke Korrekt

```
html
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

---

## aria-label

:bangbang: Om det mangler standard navn på et element du jobber med, eller det ikke lar seg gjøre å beskrive innholdet nøyaktig med elementet som blir brukt, så skal du bruke aria-label for å gi det en klar og tydelig beskrivelse. Dette er for å gjøre elementet mer tydelig i DOM'en. :bangbang:

- Det meste av alt innehold vil ha et navn allerede tilgjengelig i HTML taggen. Du kan også opprette navn via enkelte attributter eller tilknyttede elementer.

- Som standard vil navnet på feks knapper være tilgjengelig i '<button>aria label navnet</button>' taggen, mens et bilde vil ha navnet tilgjengelig i alt-attributtet, mens '<form></form>' vil ha navnet tilgjengelig fra et tilknyttet '<label>' element.

- Hvis ingen av disse alternativene er tilgjengelige, eller hvis standard tilgjengelig navn ikke er passende, så skal du bruke aria-label-attributtet for å definere det tilgjengelige navnet på elementet.

Et vanlig eksempel er en knapp som inneholder en SVG, for en SVG vil ikke få navn tildelt fra HTML-taggen den er satt i.

Aria-label-attributtet kan brukes til å definere en string som merker det interaktive elementet det er satt på. Dette gir elementet dets tilgjengelige navn.

Er du i tvil så kan du finne mer informasjon om aria-label i linken nedenfor

[Les mer om aria-label](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label)

### ✅ Eksempel

```
html
<button aria-label="Close" onclick="myDialog.close()">
  <svg
    aria-hidden="true"
    focusable="false"
    width="17"
    height="17"
    xmlns="http://www.w3.org/2000/svg"
  >
    <path
      d="m.967 14.217 5.8-5.906-5.765-5.89L3.094.26l5.783 5.888L14.66.26l2.092 2.162-5.766 5.889 5.801 5.906-2.092 2.162-5.818-5.924-5.818        5.924-2.092-2.162Z"
      fill="#000"
    />
  </svg>
</button>
```

---

## max width for paragrafer

<!-- Paragrafer skal ha en max-width. Dette skal vi gjøre sånn at tekst på nettsider blir lettere å lese. -->

Alle paragrafer skal ha en max-width. Dette er for at nettsidene skal ha god leservennlighet.

Hvis ikke så vil paragrafene strekke seg over hele skjermen, noe som da vil gjøre brukeropplevelsen mye dårligere.

Tailwind har klasser hvor dette er allerede innebygd, nedenfor er det et eksempel på dette.

Max-w-prose er en klasse som gir et element en maksimal bredde som er optimalisert for lesbarhet, og som tilpasser seg i forhold til skriftstørrelsen som blir satt.

### ✅ Eksempel 1

```
html
<div class="text-sm max-w-prose ...">
  <p>
    Oh yeah. It's the best part. It's crunchy, it's explosive, it's where the
    muffin breaks free of the pan and sort of does it's own thing. I'll tell
    you. That's a million dollar idea right there. Just sell the tops.
  </p>
</div>

<div class="text-base max-w-prose ...">
  <p>
    Oh yeah. It's the best part. It's crunchy, it's explosive, it's where the
    muffin breaks free of the pan and sort of does it's own thing. I'll tell
    you. That's a million dollar idea right there. Just sell the tops.
  </p>
</div>

<div class="text-xl max-w-prose ...">
  <p>
    Oh yeah. It's the best part. It's crunchy, it's explosive, it's where the
    muffin breaks free of the pan and sort of does it's own thing. I'll tell
    you. That's a million dollar idea right there. Just sell the tops.
  </p>
</div>
```

[Les mer om max-w-prose for tekst i tailwind her](https://tailwindcss.com/docs/max-width#reading-width)

---

## Tailwind

## Tailwind extension

Det anbefales at alle laster ned utvidelsen 'Tailwind CSS IntelliSense' for å få intellisense på alle Tailwind klassene.

Man får også funksjonaliteten til å kunne holde musepekeren over klassene i tailwind for å kunne se alle CSS funksjonaliteten brukt i den klassen.

I bildet nedenfor vil du kunne se den korrekte utvidelsen, og hvordan du installerer den.

![Tailwind IntelliSense](https://user-images.githubusercontent.com/61709493/213677701-5c5b4d48-62aa-4774-9e96-c813f69d0296.png)

## Tailwind apply

<!-- Tailwind CSS er utiliti først og bruker et klasse basert system. Derfor kan det ofte bli veldig mye klasser på HTML elementer. -->

Tailwind CSS er 'utility first' og derfor bruker et klasse-basert system. Det er derfor det kan bli store mengder med klasser i et HTML element.

<!-- :bangbang: Anbefaler på det sterkeste å se den youtube videoen i linken nedenfor. Får en bedre forståelse av @apply og hvordan du får mest ut av Tailwind CSS :bangbang: -->

:bangbang: Det anbefales å se videoen som er lenket til nedenfor. Du vil få en bedre forståelse av @apply, og hvordan du får mest mulig ut av å bruke Tailwind CSS :bangbang:

[Youtube video Composing Utilities with @apply](https://www.youtube.com/watch?v=TrftauE2Vyk&ab_channel=TailwindLabs)

[Les mer om extracting classes with apply](https://tailwindcss.com/docs/reusing-styles#extracting-classes-with-apply)

```
html
<!-- her er noen eksempler på HTML elementer som har mange klasser -->

<a
  href="#"
  class="inline-block px-5 py-3 rounded-lg shadow-lg bg-indigo-500 hover:bg-indigo-400 hover:-translate-y-0.5 focus:outline-none focus:ring focus:ring-offset-2 focus:ring-indigo-500 focus:ring-opacity-50 active:bg-indigo-600 transform transition text-white uppercase tracking-wider font-semibold text-sm sm:text-base"
>
  Book your escape
</a>

<a
  href="#"
  class="inline-block px-5 py-3 rounded-lg shadow-lg bg-indigo-500 hover:bg-indigo-400 hover:-translate-y-0.5 focus:outline-none focus:ring focus:ring-offset-2 focus:ring-indigo-500 focus:ring-opacity-50 active:bg-indigo-600 transform transition text-white uppercase tracking-wider font-semibold text-sm sm:text-base"
>
  Traveling
</a>
```

<!-- Hvis du finner deg selv i en lignende situasjon som det eksempelet ovenfår kan du bruke @apply. -->

Om du befinner deg i en situasjon hvor du har gjort lignende som eksemplet ovenfor, så kan du bruke @apply.

<!-- Med @apply kan du ta alle klassene fra en HTML element og lage en ny tilpassede klasse med de valgte klassene. -->

Med @apply kan du lage en egen klasse med alle klassene i HTML elementet slik at du slipper å skrive alle inn i hvert element.

<!-- Dette vil da skje i den CSS filen der tailwind er importert. -->

Dette gjøres i CSS filen hvor tailwind har blitt importert.

```
css
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

Grunnen til at man skal bruke '@layer components' er at disse klassene må komme før Tailwind sine utility klasser. Hvis man ikke gjør dette, eller bruker '@apply utilities', så vil tailwind sine utility klasser overkjøre de nye klassene vi har lagd.

```
html
<!-- eksempel på HTML etter flytting av klasser til en egen CSS klasse -->
<a href="#" class="custom-button"> Book you escape </a>

<a href="#" class="custom-button"> Traveling </a>
```

Flere gode kilder om Tailwind CSS i linkene nedenfor.

- [Tailwind CSS youtube kanal](https://www.youtube.com/@TailwindLabs/videos)
- [Tailwind dokumentasjon](https://tailwindcss.com/)
- [Weather App Build (Vue 3 & Tailwind) - THe Net Ninja](https://www.youtube.com/watch?v=gUsBaB5ViAo&list=PL4cUxeGkcC9hfoy8vFQ5tbXO3vY0xhhUZ&ab_channel=TheNetNinja)

---

## Tailwind custom fonts

For å kunne bruke custom fonts eller legge til ekstra fonter, som feks fonter fra Google, så må du legge det til i Tailwind CSS sin font familie.

Dette gjøres i `tailwind.config.js` filen.

[Les mer om Tailwind CSS font family](https://tailwindcss.com/docs/font-family)

```
js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./public/**/*.html", "./src/**/*.{vue,js,ts,jsx,tsx}"],
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

Grunnen til at vi gjør det på denne måten er at vi da får alle utilities fra Tailwind CSS får denne font familien. Som for eksempel `lg:font-sora` som da bare vil vise fonten Sora på stor skjerm og oppover.

Dette vil da gjelde alle varianter i Tailwind CSS `hover:font-sora`, `lg:font-sora"`, `md:font-sora` osv.

```
html
<!-- eksempel -->
<h1 class="lg:font-sora">Eksempel heading</h1>
```

Importering av fonter vil skje på den vanlige måten med og importere de i `ìndex.html` filen i Vue

```
html
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
  <link
    href="https://fonts.googleapis.com/css2?family=Raleway:wght@300;500;700&family=Sora:wght@300;400;600;700;800&display=swap"
    rel="stylesheet"
  />
</head>
```

---

## one-off custom value i Tailwind

<!-- Hvis mann har bruk for eks en height verdi på `60px` som ikke eksisterer i Tailwdind så kan mann bruke en one-off custom value. -->

Hvis man skal bruke feks en height verdi på '60px' som ikke vanligvis er tilgjengelig i Tailwind, så kan man bruke en one-off custom value.

<!-- Det nermeste vi kommer til `60px`i Tailwind er `64px` som vi da ville brukt klassen `h-16` til. -->

Det nermeste vi kommer til `60px`i Tailwind er `64px` som vi da ville brukt klassen `h-16` til.

<!-- For og bruke en vilkårlige verdi vil vi da bruke en postfix med square brackets som vist i eksempelet nedenfor. -->

For å bruke en verdi som ikke er standard i Tailwind, så skal man bruke en postfix med square brackets, som vist i eksempelet nedenfor.

```
html
<nav class="h-[60px]">
  <ul>
    <li>
      <a href="#">Home</a>
    </li>
  </ul>
</nav>
```

Flere eksempler.

```
html
<button class="bg-[#1da1f2]">...</button>
<div class="ease-[cubic-bezier(0.95,0.05,0.795,0.035)]">...</div>
<p class="underline-offset-[3px]">...</p>
<p class="font-[1100]">...</p>
```

---

## Beste praksis for Javacript

### Bruk betydningsfulle og uttalbare variabel navn.

Betydnings- og uttalbare variabelnavn er bra.

### ✅ Korrekt

```
js
const currentDate = new Date();
```

### ❌ Ikke Korrekt

```
js
const yyyymmd = new Date();
```

---

## Bruk samme ordforråd for samme type variabel.

Man skal aldri bruke flere variabler for å beskrive noe som bare behøver en.

Et eksempel på dette er å bruke 3 navn for en bruker.

### ✅ Korrekt

```
js
getUser();
```

### ❌ Ikke Korrekt

```
js
getUserInfo();
getPersonData();
getSubscriberRecord();
```

---

## Bruk søkbare navn

Man skal anvende søkbare navn.

Dette utelukker navn som er for korte eller generiske.

Man skal heller ikke ta i bruk av magiske tall, dvs ikke nummer uten egen variabel med beskrivende navn.

### ✅ Korrekt

```
js
const DAY_IN_MILLISECONDS = 86_400_000;
setTimeout(doSomething, DAY_IN_MILLISECONDS);
```

### ❌ Ikke Korrekt

```
js
setTimeout(doSomething, 86400000);
```

---

## Bruk forklarende variabler

<!-- Vi skal lage variabel navn som forklarer hva de inneholder. -->

Man skal navngi variabler med navn som beskriver hva de inneholder for å fremme god oversiktelighet.

### ✅ Eksempel

```
js
const phone = "555-555-1212";
const [areaCode, exchangeCode, lineNumber] = phone.split("-");
```

<!-- Nå vet vi at et telefonnummer kan deles inn i disse numrene. -->

Her ser vi det tydelig at det er et telefonnummer det er snakk om i variablen.

---

## Ingen mental kartlegging

<!-- Vi skal unngå behovet for å kartlegge betydningen av variabelen med tankene våre. -->

Man skal unngå å mentalt kartlegge hva hver variabel betyr.

### ✅ Korrekt

```
js
phoneNumbers.forEach((phoneNumber) => {
  call(phoneNumber);
});
```

### ❌ Ikke Korrekt

```
js
items.forEach(el => {
  ...
});

phoneNumbers.forEach(p => {
  call(p);
});
```

---

## Ingen unødvendig kontekst

Det er fort gjort å legge til for mye informasjon i identifikasjonsnavnene på variabler.

Dette skal unngås.

Vi trenger ikke "car" fremfor hver verdi.

### ✅ Korrekt

```
js
const car = {
  make: "Ford",
  model: "Fiesta",
  color: "Blue",
};
```

### ❌ Ikke Korrekt

```
js
const car = {
  carMake: "Ford",
  carModel: "Fiesta",
  carColor: "Blue",
};
```

---

## Navngi funksjoner etter hva de gjør

<!-- Vi skal navngi funksjoner på en måte som forteller hva de gjør.

Hvis ikke kan det fort bli vanskelig for andre og skjønne meningen bak funksjonen. -->

Funksjoner skal navngis med beskrivende navn, dvs at navnet skal forklare hva den gjør.

Hvis man ikke gjør det på denne måten så vil det være vanskelig for andre å tyde funksjonen.

### ❌ Ikke Korrekt

```
js
const add = (date, years) => {
  // ...
};

const date = new Date();

add(date, 1);
```

### ✅ Korrekt

```
js
const addYearsToDate = (date, years) => {
  // ...
};

const date = new Date();

addYearsToDate(date, 1);
```

<!-- Her slapp jeg sist -->

---

## Funksjons parameter

<!-- Vi skal unngå behovet for å kartlegge betydningen av parametere med tankene våre. -->

Man skal unngå å mentalt kartlegge hva hver parameter betyr.

<!-- En funksjons parameter skal ikke være en singel bokstav. -->

En parameter i en funksjon skal være mer beskrivende enn en eller få bokstaver.

<!-- Prøv og bruke forklarende variabler. Som for eks `forumID` og `userName` osv. -->

Bruk forklarende variabler så ofte som mulig. Et eksempel er 'forumID', eller 'userName' osv.

### ✅ Korrekt

```
js
const handleUsers = (userId) => {
...
}
```

### ❌ Ikke Korrekt

```
js
const handleUsers = (id) => {
...
}
```

---

## Beste praksis for Vue 3

## Axios config i main js

Det er flere grunner til hvorfor det er god praksis i å bruke en Axios-konfigurasjon i main.js-filen i en vue.js-applikasjon.

**Sentralisert Axios-konfigurasjon:**

Ved å definere Axios-innstillingene ett sted, som feks i main.js, for at skal være konsistent i bruk i hele applikasjonen, forenkler vedlikeholdsarbeid og fremmer kodens gjenbrukbarhet.

**Konsistens og Effektivitet:**

Sentralisert konfigurasjon sikrer at alle Axios-forespørslene følger samme standarder og gir en mer effektiv utviklingsprosess.

**Forenklet Feilhåndtering:**

En sentralisert konfigurasjon gjør det mye enklere å endre på Axios-innstillingene, som for eksempel head informasjoen som er felles for alle sidene eller feilhåndtering, på ett sted i koden i stedet for å må gjøre det for hver Axios-forespørsel som måtte forekomme.
Dette forenkler feilsøking og håndtering av errorer.

Nedenfor vil du se ett eksempel på en Axios-config.

```js
axios.defaults.baseURL = import.meta.env.VITE_TALE_BASE_URL;

// Set the 'Content-Type' header for 'POST', 'GET', 'DELETE', and 'PUT' requests to 'application/json'.
axios.defaults.headers.post["Content-Type"] = "application/json";
axios.defaults.headers.get["Content-Type"] = "application/json";
axios.defaults.headers.delete["Content-Type"] = "application/json";
axios.defaults.headers.put["Content-Type"] = "application/json";
axios.defaults.headers.patch["Content-Type"] = "application/json";
```

<!-- Når en Axios config er opprettet kan alle axios kall brukes som eksempelet nedfor. -->

Når man oppretter en Axios config så vil alle instanser av axios kunne kalle på den, som vist i eksemplet nedenfor.

```js
axios.get("user");
axios.post("user");
axios.patch("user");
axios.delete("user");
axios.put("user");
```

Dette skjer pga at vi har oppretted en baseUrl i Axios configen, som da er importert fra en .env fil.

```
js
axios.defaults.baseURL = import.meta.env.VITE_TALE_BASE_URL;
```

### ✅ Korrekt

```
js
// bra url eksempel axios.get('user')

const fetchData = async () => {
  try {
    const response = await axios.get("user");
    console.log(response.data);
  } catch (error) {
    console.error("Feil ved henting av data:", error);
  }
};
```

### ❌ Ikke Korrekt

```
js
// dårlig url eksempel axios.get('https://api.example.com/user')

const fetchData = async () => {
  try {
    const response = await axios.get("https://api.example.com/user");
    console.log(response.data);
  } catch (error) {
    console.error("Feil ved henting av data:", error);
  }
};
```

---

## Async Await med Axios i Vue 3

<!-- I en Vue 3-applikasjon skal vi bruke Axios for å gjøre HTTP-forespørsler til en server. -->

I en Vue 3-applikasjon skal benytte oss av Axios for å begå HTTP-forespørsler til en server.

<!-- Når man arbeider med Axios og ønsker å utføre asynkrone oppgaver, skal det brukes **async/await med try/catch blokker** for å håndtere asynkrone operasjoner som gjør dem mer lesbare og ryddige. -->

Når man skal utføre asynkrone oppgaver i Axios, skal **async/await med try/catch blokk** benyttes for å håndtere asynkrone operasjoner, for å gjøre dem mer lesbare og ryddige.

### ✅ Korrekt

```
js
import axios from "axios";

const fetchData = async () => {
  try {
    const response = await axios.get("user");
    // Håndter dataen som kommer tilbake fra serveren her
    console.log(response.data);
  } catch (error) {
    // Håndter feil her, for eksempel nettverksproblemer eller ugyldige svar
    console.error("Feil ved henting av data:", error);
  }
};
```

<!-- Vi skal ikke bruke .then pga Lesbarhet og struktur, Unngå callback hell og Enklere testing. -->

.then skal ikke benyttes. Det er for å forbedre lesbarhet og struktur i koden, og for å gjøre utprøvning av koden enklere.

<!-- Bedre integrasjon med moderne JavaScript: Mange moderne JavaScript-biblioteker og rammeverk, inkludert Vue 3, støtter og anbefaler bruk av async/await. -->

For bedre integrasjon med moderne Javascript: Mange av de moderne Javascript-biblioteker og rammeverk, som inkluderer Vue 3, både støtter og anbefaler bruken av async/await.

### ❌ Ikke Korrekt

```
js
function fetchData() {
  axios
    .get("https://api.example.com/data")
    .then((response) => {
      // Håndtering av data som blir tatt i mot fra serveren her
      console.log(response.data);
    })
    .catch((error) => {
      // Håndtering av feil her, som for eksempel nettverksproblemer eller ugyldige svar
      console.error("Feil ved henting av data:", error);
    });
}
```

---

## v-for og v-if

<!-- ### Bruk nøkkel med v-for -->

### Bruk av Key sammen med v-for

<!-- Nøkkel med v-for er alltid nødvendig på komponenter for å opprettholde intern komponenttilstand nedover undertrær. Selv for elementer er det en god praksis å opprettholde forutsigbart oppførsel. -->

Det er alltid nødvendig å bruke Key's sammen med v-for for å kunne vedlikeholde den interne komponenttilstanden nedover subtrær. Det er god praksis i å opprettholde forutsigbarhet i koden, selv for elementer.

### ❌ Ikke Korrekt

```
vue
<ul>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ul>
```

### ✅ Korrekt

```
vue
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

### Bruk en unik id som Key i v-for

<!-- En v-for-loop skal bruke en unik id for en nøkkel hvis en er tilgjengelig. -->

Man skal alltid bruke en unik id som en key om det lar seg gjøre.

En v-for-loop bruker unike id-attributter i hvert element for å kunne spore unikheten til hvert listeelement (noe som vanligvis blir forelsått i compilatoren), og for å forbedre DOM-ytelsen.

### ❌ Ikke Korrekt

```

vue

<!-- Kan brukes hvis en unik id ikke er tilgjengelig eller for prototyping -->
<div v-for="(task, taskIndex) in taskStore.favs" :key="taskIndex">
  <div class="card-body">
    <TaskDetails :task="task" />
  </div>
</div>
```

### ✅ Korrekt

```

vue

<div v-for="task in taskStore.favs" :key="task.id">
  <div class="card-body">
    <TaskDetails :task="task" />
  </div>
</div>
```

---

### Unngå bruk av v-if sammen med v-for

Bruk aldri v-if i samme element som allerede har v-for.

<!-- Det er to vanlige tilfeller hvor dette kan være fristende: -->

De to vanligste tilfellene hvor dette kan skje er som følgende:

<!-- - For å filtrere elementer i en liste (f.eks. v-for = "user in users" v-if = "user.isActive"). I disse tilfellene, erstatt users med en ny computed property som returnerer den filtrerte listen (f.eks. activeUsers).
- For å unngå å rendre en liste hvis den skal skjules (f.eks. v-for = "user in unsers" v-if = "shouldShowUsers"). I disse tilfellene flytter du v-if til et container-element (f.eks. ul, ol). -->

- Filtrering av elemeneter i en liste (f.eks. v-for "user in users" v-if ="user.isactive"). I lignende tilfeller burde man i stedet erstatte users med en ny computed property som returnerer den filtrerte listen (f.eks. activeUsers).
- For å unngå en render av en liste som ikke skal være synlig (f.eks. v-for = "user in unsers" v-if = "shouldShowUsers"). I lignende tilfeller flytter du v-if inn i et container-element (f.eks. ul, ol).

### ❌ Ikke Korrekt

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

### ✅ Korrekt

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

## Komponenter

### Komponentnavn skal alltid inneholde flere ord

Komponentnavn skal alltid inneholde flere ord, med unntak av rot-App-komponenter. Dette er for å forhindre konflikter med eksisterende og fremtidige HTML-elementer, siden alle HTML-elementer er bare et enkelt ord.

### ❌ Ikke korrekt

```
vue
<Item />
```

### ✅ Korrekt

```
vue
<TodoItem />
```

---

### Importering av komponenter

<!-- Importering av komponenter skal være i PascalCase. -->

Når man skal importere komponenter, så skal dette gjøres i PascalCase.

<!-- PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template. -->

PascalCase fungerer best i samsvar med autocompletion i code-editors, ettersom at dette vil være konsistent med hvordan komponenter vil bli referert til i JS (X) og templaten.

### ❌ Ikke Korrekt

```
vue
<todo-item><todo-item/>

<toDoItem><toDoItem/>
```

### ✅ Korrekt

```
vue
<TodoItem />
```

---

### Komponentnavn til views

<!-- Navn på views komponenter skal være PascalCase og skal ha et forklarendre navn med en (View) postfiks. -->

Navnene på View-komponenter skal være i PascalCase. Navnene skal være beskrivende, og avlsuttes med en .view postfiks.

<!-- PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template. -->

PascalCase fungerer best i samsvar med autocompletion i code-editors, ettersom at dette vil være konsistent med hvordan komponenter vil bli referert til i JS (X) og templaten.

### ❌ Ikke Korrekt

```
views/
|- myview.vue

views/
|- myView.vue
```

### ✅ Korrekt

```
views/
|- HomeView.vue

views/
|- LoginView.vue
```

---

### Komponentfilnavn for enkel-filkomponenter

<!-- Filnavnene til Single-File komponenter skal være PascalCase. -->

Navnene på enkelt-fil komponenter skal være i PascalCase.

<!-- PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template. -->

PascalCase fungerer best i samsvar med autocompletion i code-editors, ettersom at dette vil være konsistent med hvordan komponenter vil bli referert til i JS (X) og templaten.

### ❌ Ikke Korrekt

```
components/
|- mycomponent.vue

components/
|- myComponent.vue
```

### ✅ Korrekt

```
components/
|- MyComponent.vue
```

---

<!-- ### Tett sammenkoblede komponentnavn -->

### Tett-koblede komponentnavn

<!-- Child komponenter som er tett koblet til deres parent komponent, bør inkludere navnet på den overordnede komponenten som et prefiks. -->

Child-komponenter som er tett-koblet til sitt eget parent-komponent skal inneholde navnet på sin parent-komponent som et prefiks.

<!-- Hvis en komponent bare gir mening i sammenheng med en enslig parent komponent, bør forholdet være tydelig i navnet. Siden editoren vanligvis organiserer filer alfabetisk, holder dette også disse relaterte filene ved siden av hverandre. -->

Om et komponent bare gir mening i sammenheng med et enkelt parent-komponent, så skal relasjonen mellom de være tydeliggjort i navnet. Ettersom at editorer vanligvis organiserer filer alfabetisk vil dette forsikre at filene blir legt ved siden av hverandre.

### ❌ Ikke Korrekt

```
components/
|- TodoList.vue
|- TodoItem.vue
|- TodoButton.vue

components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue
```

### ✅ Korrekt

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

<!-- Komponentnavn skal ha hele ord fremfor forkortelser. -->

Komponentnavn skal ikke inneholde forkortelser, men være fullstendige ord.

<!-- Autofullføringen i editoren gjør kostnadene ved å skrive lengre navn svært lave, mens klarheten de gir er uvurderlig. Spesielt uvanlige forkortelser bør alltid unngås. -->

Autokorrekt i editoren vil kunne gjøre lengre navn mindre krevende å føre inn, og lange navn er verdifulle i sin tydelighet. Uvanlige forkortelser skal ved hver anledning unngås.

### ❌ Ikke Korrekt

```
components/
|- SdSettings.vue
|- UProfOpts.vue
```

### ✅ Korrekt

```
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```

---

<!-- ### Enkeltfilkomponent på toppnivå elementrekkefølge -->

### Korrekt rekkefølge på Enkeltfilkomponenter

<!-- Enkeltfilkomponenter bør alltid være i denne rekkefølgen `<template> <script> <style>` tagger konsekvent, med <style> sist, fordi minst en av de to andre alltid er nødvendig. -->

Den korrekte rekkefølgen på Enkeltfilkomponenter er `<template> <script> <style>`, med `<style>` til slutt, ettersom de to tidligere typene er mer vesentlig.

### ❌ Ikke Korrekt

```
vue
<style>
/* ... */
</style>
<script>
/* ... */
</script>
<template>...</template>

<script>
/* ... */
</script>
<template>...</template>
<style>
/* ... */
</style>
```

### ✅ Korrekt

```
vue
<template>...</template>
<script>
/* ... */
</script>
<style>
/* ... */
</style>
```

---

## Props

<!-- ### Bruk detaljerte prop-definisjoner -->

### Bruk godt detaljerte definisjoner på props

<!-- I kode som er commited bør prop-definisjoner alltid være så detaljerte som mulig, med å angi minst type(r). -->

I koder som blir committed så skal prop-definisjoner være så tydelig detaljerte som det lar seg gjøres, med i det minste tydelig definerte typer.

### ❌ Ikke korrekt

```
js
// Dette er bare OK når man prototyper
const props = defineProps(["status"]);
```

### ✅ Korrekt

```
js
const props = defineProps({
  status: String,
  required: true,
});
```

---

<!-- ### Prop navn casing -->

### Korrekt navngivning på Props

<!-- Propnavn skal alltid bruke camelCase under deklarering, men kebab-case i templates og JSX. -->

Navn på props skal alltid bli skrevet med camelCase når det blir deklarert, mens i templates og JSX skal det skrives i kebab-case.

<!-- Vi følger ganske enkelt konvensjonene for hvert språk. Innen JavaScript er camelCase mer naturlig. Innen HTML er kebab-case. -->

Man skal følge vanlige konvensjoner i hvert språk. I JavaScript er camelCase mest vanlig, mens i HTML er kebab-case mest vanlig.

### ❌ Ikke Korrekt

```
js
<!-- Javascript -->
props: {
  'greeting-text': String
}
```

```
vue
<!-- template / HTML -->
<WelcomeMessage greetingText="hi" />
```

### ✅ Korrekt

```
js
<!-- Javascript -->
props: {
  greetingText: String
}
```

```
vue
<!-- template / HTML -->
<WelcomeMessage greeting-text="hi" />
```

---

<!-- ## Best praksis for Pinia -->

## Beste praksis for bruk av Pinia

<!-- ### Definer en Pinia store -->

### Definering av en Pinia store

<!-- - Du kan navngi returverdien til `defineStore()` alt du vil,
- men det er best å bruke navnet på Pinia store og omgi den med `use`
- og `Store` (f.eks. `useUserStore`, `useCartStore`, `useProductStore`)
- det første argumentet er en unik ID for store på tvers av applikasjonen din -->

- Man kan navngi returverdien til `defineStore` hva man vil, men det er best å bruke navnet på Pinia store for å så omgi navnet med `use` og `Store` (f.eks. `useUserStore`, `useCartStore` , `useProductStore` osv).

[Flere detaljer om Pinia define store](https://pinia.vuejs.org/core-concepts/)

### ❌ Ikke Korrekt

```
js
import { defineStore } from "pinia";

export const taskStore = defineStore("useTaskStore", {
  state: () => ({}),
});

import { defineStore } from "pinia";

export const taskStore = defineStore("TaskStore", {
  state: () => ({}),
});
```

### ✅ Korrekt

```
js
import { defineStore } from "pinia";

export const useTaskStore = defineStore("taskStore", {
  state: () => ({}),
});
```

---

<!-- ### Navngivning på Pinia store filer -->

### Navngivning av Pinia store filer

<!-- Filnavnene til Pinia store skal være PascalCase. -->

Navnene på Pinia Store filer skal være i Pascalcase.

PascalCase fungerer best med autocompletion i kodeeditorer, siden det er konsistent med hvordan vi refererer til komponenter i JS (X) og template.

### ❌ Ikke Korrekt

```
stores/
|- myuserstore.js

stores/
|- myUserStore.js
```

### ✅ Korrekt

```
stores/
|- MyUserStore.js
```

---

<!-- ### Pinia store importering eksempel -->

### Eksempel på importering av Pinia Store

```
vue
<script setup>
import { useTaskStore } from "../stores/TaskStore";

const taskStore = useTaskStore();
</script>
```

---

<!-- ### Basic eksempel på en Pinia store -->

### Vanlig eksempel på en Pinia Store

```
js
import { defineStore } from "pinia";

export const useTaskStore = defineStore("taskStore", {
  state: () => ({
    // store state(s)
    tasks: [
      { id: 1, title: "buy some milk", isFav: false },
      { id: 2, title: "play Gloomhaven", isFav: true },
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
