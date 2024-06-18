## These rules help to prevent errors, so learn and follow them at all times. Exceptions may exist but should be very rare.

Table of Contents:

- [Prettier Code Formatting](#Prettier-Code-Formatting)
- [HTML Semantics and Accessibility](#HTML-Semantics-and-Accessibility)
  - [aria-label](#aria-label)
  - [Max Width for Paragraphs](#Max-Width-for-Paragraphs)
- [Tailwind](#Tailwind)
  - [Tailwind Extension](#Tailwind-Extension)
  - [Tailwind Apply](#Tailwind-Apply)
  - [Tailwind Custom Fonts](#Tailwind-Custom-Fonts)
  - [One-off Custom Value in Tailwind](#One-off-Custom-Value-in-Tailwind)
- [Best Practices for JavaScript](#Best-Practices-for-JavaScript)
  - [Use the Same Vocabulary for the Same Type of Variable](#Use-the-Same-Vocabulary-for-the-Same-Type-of-Variable)
  - [Use Searchable Names](#Use-Searchable-Names)
  - [Use Variables to Explain](#Use-Variables-to-Explain)
  - [No Mental Mapping](#No-Mental-Mapping)
  - [No Unnecessary Context](#No-Unnecessary-Context)
  - [Name Functions After What They Do](#Name-Functions-After-What-They-Do)
  - [Function Parameters](#Function-Parameters)
- [Best Practices for Vue 3](#Best-Practices-for-Vue-3)
  - [Axios Config in Main JS](#Axios-Config-in-Main-JS)
  - [Async Await with Axios in Vue 3](#Async-Await-with-Axios-in-Vue-3)
  - [v-for and v-if](#v-for-and-v-if)
    - [Use Key with v-for](#Use-Key-with-v-for)
    - [Use a Unique ID on Key in v-for](#Use-a-Unique-ID-on-Key-in-v-for)
    - [Avoid v-if with v-for](#Avoid-v-if-with-v-for)
  - [Components](#Components)
    - [Component Names Should Always Be Multi-word](#Component-Names-Should-Always-Be-Multi-word)
    - [Importing Components](#Importing-Components)
    - [Component Names on Views](#Component-Names-on-Views)
    - [Component File Names for Single-File Components](#Component-File-Names-for-Single-File-Components)
    - [Closely Related Component Names](#Closely-Related-Component-Names)
    - [Full Word Component Names](#Full-Word-Component-Names)
    - [Single-File Component Top-Level Element Order](#Single-File-Component-Top-Level-Element-Order)
  - [Props](#Props)
    - [Use Detailed Prop Definitions](#Use-Detailed-Prop-Definitions)
    - [Prop Name Casing](#Prop-Name-Casing)
- [Best Practices for Pinia](#Best-Practices-for-Pinia)
  - [Define a Pinia Store](#Define-a-Pinia-Store)
  - [Naming Pinia Store Files](#Naming-Pinia-Store-Files)
  - [Pinia Store Import Example](#Pinia-Store-Import-Example)
  - [Basic Example of a Pinia Store](#Basic-Example-of-a-Pinia-Store)

---

## Prettier Code Formatting

:bangbang: These Prettier rules are mandatory for everyone. :bangbang:

:bangbang: There will be a `.prettierrc` file in all Vue 3 projects. This file contains Prettier rules that everyone must follow. :bangbang:

### Contents of the .prettierrc File

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

The Prettier extension must be installed in VS Code for all projects using Vue 3.

This is the correct extension to install.

![Prettier](https://user-images.githubusercontent.com/61709493/213147526-92ad0894-6ca2-4a2e-9d10-e0fa87b30459.png)

Make sure Prettier is selected as the default formatter in VS Code settings.

![Prettier setting](https://user-images.githubusercontent.com/61709493/213150743-73e72f53-0286-4ddf-a560-cf8e82486d81.png)

Also, ensure that Prettier: Use Editor Config is enabled.

![Prettier Editor Config](https://user-images.githubusercontent.com/61709493/213149028-3a95b2ae-126b-40e8-9fb3-8683e4bb3415.png)

---

## HTML Semantics and Accessibility

:bangbang: Everyone must write proper HTML semantics and implement good accessibility practices. Improving accessibility also enhances SEO, making your website more searchable. :bangbang:

- Building accessible websites benefits everyone.
- Caring about accessibility demonstrates good ethics and morals, enhancing your/your company's public image.
- Other good practices that improve accessibility also make your site more usable for other groups, such as mobile users, visually impaired users, etc., or those with low network speed. Many such improvements can benefit everyone.
- Quote from The Web Accessibility Directive: "The 15-page directive requires all public sector websites and applications in EU member states to implement, enforce, and maintain a uniform set of accessibility standards."

For example, you should not use `<div></div>` for navigation. Instead, use the proper HTML semantics for navigation, which is `<nav></nav>`.

If you're unsure about the correct semantics for what you're creating, you can refer to the links below.

[Learn more about accessibility](https://developer.mozilla.org/en-US/docs/Learn/Accessibility)

[Learn more about HTML semantics](https://developer.mozilla.org/en-US/docs/Glossary/Semantics)

[Learn more about HTML elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

### ❌ Bad

```html
<!-- Navigation example -->
<div>
  <li>
    <a href="#">Home</a>
  </li>
  <li>
    <a href="#">Blog</a>
  </li>
</div>
```

### ✅ Good

```html
<!-- Navigation example -->
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

:bangbang: aria-label must be used if there is no standard accessible name for an element, or if the content is not described accurately, and there is no visible content in the DOM that can be associated with the object to give it meaning. :bangbang:

- Most content has an accessible name generated from the text content in the immediate wrapping element. Accessible names can also be created by certain attributes or associated elements.

- By default, a button's accessible name is the content between the opening and closing `<button>` tags, an image's accessible name is the content in the alt attribute, and a form's accessible name is the content in the associated `<label>` element.

- If none of these options are available, or if the default accessible name is not appropriate, use the aria-label attribute to define the accessible name of an element.

A common example is a button that contains an SVG.

The aria-label attribute can be used to define a string that labels the interactive element it is set on. This gives the element its accessible name.

If in doubt, you can find more information about aria-label at the link below

[Learn more about aria-label](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Attributes/aria-label)

### ✅ Example

```html
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

## Max Width for Paragraphs

Paragraphs should have a max-width.

This ensures that text on websites is easier to read.

Paragraphs can become very difficult to read if they stretch across the entire screen.

Fortunately, Tailwind has this built-in with classes, as shown below.

The max-w-prose class gives an element a maximum width optimized for readability and adapts based on the font size.

### ✅ Example 1

```html
<div class="text-sm max-w-prose ...">
  <p>
    Oh yeah. It's the best part. It's crunchy, it's explosive, it's where the muffin breaks free of
    the pan and sort of does it's own thing. I'll tell you. That's a million dollar idea right
    there. Just sell the tops.
  </p>
</div>

<div class="text-base max-w-prose ...">
  <p>
    Oh yeah. It's the best part. It's crunchy, it's explosive, it's where the muffin breaks free of
    the pan and sort of does it's own thing. I'll tell you. That's a million dollar idea right
    there. Just sell the tops.
  </p>
</div>

<div class="text-xl max-w-prose ...">
  <p>
    Oh yeah. It's the best part. It's crunchy, it's explosive, it's where the muffin breaks free of
    the pan and sort of does it's own thing. I'll tell you. That's a million dollar idea right
    there. Just sell the tops.
  </p>
</div>
```

[Learn more about max-w-prose for text in Tailwind](https://tailwindcss.com/docs/max-width#reading-width)

---

## Tailwind

## Tailwind Extension

Everyone is recommended to download the Tailwind CSS IntelliSense extension. This provides IntelliSense for all Tailwind classes.

It also allows you to hover over a Tailwind class to see its CSS.

The correct extension to install is shown in the image below.

![Tailwind IntelliSense](https://user-images.githubusercontent.com/61709493/213677701-5c5b4d48-62aa-4774-9e96-c813f69d0296.png)

## Tailwind Apply

Tailwind CSS is utility-first and uses a class-based system. Therefore, it can often result in many classes on HTML elements.

:bangbang: It is highly recommended to watch the YouTube video in the link below to better understand @apply and how to get the most out of Tailwind CSS :bangbang:

[YouTube video Composing Utilities with @apply](https://www.youtube.com/watch?v=TrftauE2Vyk&ab_channel=TailwindLabs)

[Learn more about extracting classes with apply](https://tailwindcss.com/docs/reusing-styles#extracting-classes-with-apply)

```html
<!-- example of many classes on an HTML element -->
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

If you find yourself in a similar situation as the example above, you can use @apply.

With @apply, you can take all the classes from an HTML element and create a new custom class with the selected classes.

This will be done in the CSS file where Tailwind is imported.

```css
<!-- Tailwind CSS file -->
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer components {
  .custom-button {
    @apply inline-block px-5 py-3 rounde-lg shadow-lg bg-indigo-500 hover:bg-indigo-400 hover:-translate-y-0.5 focus:outline-none focus:ring focus:ring-  offset-2 focus:ring-indigo-500 focus:ring-opacity-50 active:bg-indigo-600 transform transition text-white uppercase tracking-wider font-semibold text-sm sm:text-base;
  }
}
```

The reason for using `@layer components` is that these classes must come before Tailwind's utility classes. If placed after utilities or if `@apply utilities` is used, all the classes in this custom class will be overridden by the utility classes.

```html
<!-- example of HTML after moving classes -->
<a href="#" class="custom-button"> Book your escape </a>

<a href="#" class="custom-button"> Traveling </a>
```

More great resources to learn more about Tailwind CSS are in the links below.

- [Tailwind CSS YouTube channel](https://www.youtube.com/@TailwindLabs/videos)
- [Tailwind documentation](https://tailwindcss.com/)
- [Weather App Build (Vue 3 & Tailwind) - The Net Ninja](https://www.youtube.com/watch?v=gUsBaB5ViAo&list=PL4cUxeGkcC9hfoy8vFQ5tbXO3vY0xhhUZ&ab_channel=TheNetNinja)

---

## Tailwind Custom Fonts

To use custom fonts/add additional fonts like Google Fonts in Tailwind CSS, you need to extend Tailwind CSS's font family.

This is done in the `tailwind.config.js` file.

[Learn more about Tailwind CSS font family](https://tailwindcss.com/docs/font-family)

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

The reason for doing it this way is that you then get all the utilities from Tailwind CSS for this font family. For example, `lg:font-sora` will only display the Sora font on large screens and above.

This will apply to all variants in Tailwind CSS `hover:font-sora`, `lg:font-sora`, `md:font-sora`, etc.

```html
<!-- example -->
<h1 class="lg:font-sora">Example heading</h1>
```

Importing fonts will be done in the usual way by importing them in the `index.html` file in Vue.

```html
<!-- Example of importing fonts -->
<head>
  <meta charset="utf-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width,initial-scale=1.0" />
  <link rel="icon" href="<%= BASE_URL %>favicon.ico" />
  <title><%= htmlWebpackPlugin.options.title %></title>
  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link
    href="https://fonts.googleapis.com/css2?family=Raleway:wght@300;500;700&family=Sora:wght@300;400;600;700;800&display=swap"
    rel="stylesheet"
  />
</head>
```

---

## One-off Custom Value in Tailwind

If you need a height value of `60px` which doesn't exist in Tailwind, you can use a one-off custom value.

The closest to `60px` in Tailwind is `64px`, which we would use the class `h-16` for.

To use an arbitrary value, we use a postfix with square brackets as shown in the example below.

```html
<nav class="h-[60px]">
  <ul>
    <li>
      <a href="#">Home</a>
    </li>
  </ul>
</nav>
```

More examples.

```html
<button class="bg-[#1da1f2]">...</button>
<div class="ease-[cubic-bezier(0.95,0.05,0.795,0.035)]">...</div>
<p class="underline-offset-[3px]">...</p>
<p class="font-[1100]">...</p>
```

---

## Best Practices for JavaScript

### Use Meaningful and Pronounceable Variable Names

Meaningful and pronounceable variable names are good.

### ❌ Bad

```js
const yyyymmd = new Date();
```

### ✅ Good

```js
const currentDate = new Date();
```

---

## Use the Same Vocabulary for the Same Type of Variable

We should use the same vocabulary for the same type of variable.

For example, we should not have 3 different names for a user.

### ❌ Bad

```js
getUserInfo();
getPersonData();
getSubscriberRecord();
```

### ✅ Good

```js
getUser();
```

---

## Use Searchable Names

We should use searchable names.

This excludes names that are too short or too generic.

Also, we should not have magic numbers.

### ❌ Bad

```js
setTimeout(doSomething, 86400000);
```

### ✅ Good

```js
const DAY_IN_MILLISECONDS = 86_400_000;
setTimeout(doSomething, DAY_IN_MILLISECONDS);
```

---

## Use Variables to Explain

We should create variable names that explain what they contain.

### ✅ Example

```js
const phone = '555-555-1212';
const [areaCode, exchangeCode, lineNumber] = phone.split('-');
```

Now we know that a phone number can be divided into these numbers.

---

## No Mental Mapping

We should avoid the need to map the meaning of the variable with our minds.

### ❌ Bad

```js
items.forEach(el => {
  ...
});

phoneNumbers.forEach(p => {
  call(p);
});
```

### ✅ Good

```js
phoneNumbers.forEach((phoneNumber) => {
  call(phoneNumber);
});
```

---

## No Unnecessary Context

It is easy to add too much information to our identification names.

We should avoid doing this.

We don't need

`car` in front of all property names.

### ❌ Bad

```js
const car = {
  carMake: 'Ford',
  carModel: 'Fiesta',
  carColor: 'Blue',
};
```

### ✅ Good

```js
const car = {
  make: 'Ford',
  model: 'Fiesta',
  color: 'Blue',
};
```

---

## Name Functions After What They Do

We should name functions in a way that tells what they do.

If not, it can quickly become difficult for others to understand the meaning behind the function.

### ❌ Bad

```js
const add = (date, years) => {
  // ...
};

const date = new Date();

add(date, 1);
```

### ✅ Good

```js
const addYearsToDate = (date, years) => {
  // ...
};

const date = new Date();

addYearsToDate(date, 1);
```

---

## Function Parameters

We should avoid the need to map the meaning of parameters with our minds.

A function parameter should not be a single letter.

Try to use descriptive variables, such as `forumID` and `userName`, etc.

### ❌ Bad

```js
const handleUsers = (id) => {
...
}
```

### ✅ Good

```js
const handleUsers = (userId) => {
...
}
```

---

## Best Practices for Vue 3

## Axios Config in Main JS

We use an Axios configuration in the main.js file in a Vue.js application since it is good practice for several reasons:

**Centralized Axios Configuration:** Define Axios settings in one place, such as in main.js, for consistent use throughout the application, simplifies maintenance, and increases code reusability.

**Consistency and Efficiency:** Centralized configuration ensures that all Axios requests follow the same standards and provides a more efficient development process.

**Simpler Error Handling:** Centralized configuration makes it easy to change Axios settings, such as common headers or error handling, in one place instead of doing it for each Axios request. This simplifies debugging and handling.

An Axios config will look like the example below

```js
axios.defaults.baseURL = import.meta.env.VITE_TALE_BASE_URL;

// Set the 'Content-Type' header for 'POST', 'GET', 'DELETE', and 'PUT' requests to 'application/json'.
axios.defaults.headers.post['Content-Type'] = 'application/json';
axios.defaults.headers.get['Content-Type'] = 'application/json';
axios.defaults.headers.delete['Content-Type'] = 'application/json';
axios.defaults.headers.put['Content-Type'] = 'application/json';
axios.defaults.headers.patch['Content-Type'] = 'application/json';
```

Once an Axios config is created, all axios calls can be used as shown below.

```js
axios.get('user');
axios.post('user');
axios.patch('user');
axios.delete('user');
axios.put('user');
```

This is because we have created a baseUrl in the Axios config.
Which is imported from an .env file

```js
axios.defaults.baseURL = import.meta.env.VITE_TALE_BASE_URL;
```

### ✅ Good

```js
// good URL example axios.get('user')

const fetchData = async () => {
  try {
    const response = await axios.get('user');
    console.log(response.data);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};
```

### ❌ Bad

```js
// bad URL example axios.get('https://api.example.com/user')

const fetchData = async () => {
  try {
    const response = await axios.get('https://api.example.com/user');
    console.log(response.data);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};
```

---

## Async Await with Axios in Vue 3

In a Vue 3 application, we should use Axios to make HTTP requests to a server.
When working with Axios and wanting to perform asynchronous tasks, we should use **async/await with try/catch blocks** to handle asynchronous operations, making them more readable and clean.

### ✅ Good

```js
npm install axios
import axios from 'axios';

const fetchData = async () => {
  try {
    const response = await axios.get('user');
    // Handle the data returned from the server here
    console.log(response.data);
  } catch (error) {
    // Handle errors here, such as network issues or invalid responses
    console.error('Error fetching data:', error);
  }
}
}
```

We should not use .then because of readability and structure, avoiding callback hell, and easier testing.

Better integration with modern JavaScript: Many modern JavaScript libraries and frameworks, including Vue 3, support and recommend using async/await.

### ❌ Bad

```js
function fetchData() {
  axios
    .get('https://api.example.com/data')
    .then((response) => {
      // Handle the data returned from the server here
      console.log(response.data);
    })
    .catch((error) => {
      // Handle errors here, such as network issues or invalid responses
      console.error('Error fetching data:', error);
    });
}
```

---

## v-for and v-if

### Use Key with v-for

A key with v-for is always required on components to maintain internal component state across the subtrees. Even for elements, it is a good practice to ensure predictable behavior.

### ❌ Bad

```vue
<ul>
  <li v-for="todo in todos">
    {{ todo.text }}
  </li>
</ul>
```

### ✅ Good

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

### Use a Unique ID on Key in v-for

A v-for loop should use a unique id for a key if one is available.

A v-for loop that uses the unique id property of each item as a way to track the uniqueness of each list item - as usually suggested by the compiler, and to increase DOM performance.

### ❌ Bad

```vue
<!-- Can be used if a unique id is not available or for prototyping -->
<div v-for="(task, taskIndex) in taskStore.favs" :key="taskIndex">
  <div class="card-body">
    <TaskDetails :task="task" />
  </div>
</div>
```

### ✅ Good

```vue
<div v-for="task in taskStore.favs" :key="task.id">
  <div class="card-body">
    <TaskDetails :task="task" />
  </div>
</div>
```

---

### Avoid v-if with v-for

Never use v-if on the same element as v-for.

There are two common cases where this might be tempting:

- To filter items in a list (e.g., v-for = "user in users" v-if = "user.isActive"). In these cases, replace users with a new computed property that returns the filtered list (e.g., activeUsers).
- To avoid rendering a list if it should be hidden (e.g., v-for = "user in users" v-if = "shouldShowUsers"). In these cases, move the v-if to a container element (e.g., ul, ol).

### ❌ Bad

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

### ✅ Good

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

## Components

### Component Names Should Always Be Multi-word

Component names should always be multi-word, except for root `App` components. This prevents conflicts with existing and future HTML elements, as all HTML elements are a single word.

### ❌ Bad

```vue
<Item />
```

### ✅ Good

```vue
<TodoItem />
```

---

### Importing Components

Importing components should be in PascalCase.

PascalCase works best with auto-completion in code editors, as it is consistent with how we refer to components in JS(X) and templates.

### ❌ Bad

```vue
<todo-item><todo-item/>

<toDoItem><toDoItem/>
```

### ✅ Good

```vue
<TodoItem />
```

---

### Component Names on Views

Names of view components should be in PascalCase and should have a descriptive name with a `(View)` postfix.

PascalCase works best with auto-completion in code editors, as it is consistent with how we refer to components in JS(X) and templates.

### ❌ Bad

```
views/
|- myview.vue

views/
|- myView.vue
```

### ✅ Good

```
views/
|- HomeView.vue

views/
|- LoginView.vue
```

---

### Component File Names for Single-File Components

The file names of Single-File components should be in PascalCase.

PascalCase works best with auto-completion in code editors, as it is consistent with how we refer to components in JS(X) and templates.

### ❌ Bad

```
components/
|- mycomponent.vue

components/
|- myComponent.vue
```

### ✅ Good

```
components/
|- MyComponent.vue
```

---

### Closely Related Component Names

Child components that are tightly coupled to their parent component

should include the name of the parent component as a prefix.

If a component only makes sense in the context of a single parent component, the relationship should be evident in its name. Since editors typically organize files alphabetically, this also keeps these related files next to each other.

### ❌ Bad

```
components/
|- TodoList.vue
|- TodoItem.vue
|- TodoButton.vue

components/
|- SearchSidebar.vue
|- NavigationForSearchSidebar.vue
```

### ✅ Good

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

### Full Word Component Names

Component names should use full words rather than abbreviations.

Auto-completion in editors makes the cost of typing longer names very low, while the clarity they provide is invaluable. Unusual abbreviations should especially always be avoided.

### ❌ Bad

```
components/
|- SdSettings.vue
|- UProfOpts.vue
```

### ✅ Good

```
components/
|- StudentDashboardSettings.vue
|- UserProfileOptions.vue
```

---

### Single-File Component Top-Level Element Order

Single-File components should always be in this order: `<template> <script> <style>` tags consistently, with `<style>` last, because at least one of the other two is always required.

### ❌ Bad

```vue
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

### ✅ Good

```vue
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

### Use Detailed Prop Definitions

In committed code, prop definitions should always be as detailed as possible, specifying at least type(s).

### ❌ Bad

```js
// This is only okay when prototyping
const props = defineProps(['status']);
```

### ✅ Good

```js
const props = defineProps({
  status: String,
  required: true,
});
```

---

### Prop Name Casing

Prop names should always use camelCase during declaration, but kebab-case in templates and JSX.

We simply follow the conventions of each language. Within JavaScript, camelCase is more natural. Within HTML, kebab-case.

### ❌ Bad

```js
<!-- JavaScript -->
props: {
  'greeting-text': String
}
```

```vue
<!-- template / HTML -->
<WelcomeMessage greetingText="hi" />
```

### ✅ Good

```js
<!-- JavaScript -->
props: {
  greetingText: String
}
```

```vue
<!-- template / HTML -->
<WelcomeMessage greeting-text="hi" />
```

---

## Best Practices for Pinia

### Define a Pinia Store

- You can name the return value of `defineStore()` whatever you want,
- but it is best to use the name of the Pinia store and wrap it with `use`
- and `Store` (e.g., `useUserStore`, `useCartStore`, `useProductStore`)
- the first argument is a unique ID for the store across your application

[More details about Pinia define store](https://pinia.vuejs.org/core-concepts/)

### ❌ Bad

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

### ✅ Good

```js
import { defineStore } from 'pinia';

export const useTaskStore = defineStore('taskStore', {
  state: () => ({}),
});
```

---

### Naming Pinia Store Files

The file names of Pinia stores should be in PascalCase.

PascalCase works best with auto-completion in code editors, as it is consistent with how we refer to components in JS(X) and templates.

### ❌ Bad

```
stores/
|- myuserstore.js

stores/
|- myUserStore.js
```

### ✅ Good

```
stores/
|- MyUserStore.js
```

---

### Pinia Store Import Example

```vue
<script setup>
import { useTaskStore } from '../stores/TaskStore';

const taskStore = useTaskStore();
</script>
```

---

### Basic Example of a Pinia Store

```js
import { defineStore } from 'pinia';

export const useTaskStore = defineStore('taskStore', {
  state: () => ({
    // store state(s)
    tasks: [
      { id: 1, title: 'buy some milk', isFav: false },
      { id: 2, title: 'play Gloomhaven', isFav: true },
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
