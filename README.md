# svelte-bulma-lib
---

The purpose of this library is to provide Svelte versions of common Bulma components.

In order to use the library you'll want to do something like this:

```
npm install svelteBulmaLib
```

In your project, you'll also want to include Bulma (and probably FontAwesome) in your index.html. To do so, just include this in the header:

```
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.8.0/css/bulma.min.css">
    <script defer src="https://use.fontawesome.com/releases/v5.3.1/js/all.js"></script>
```

## Referencing components
Currently, this feels a bit clumsy. To reference the Input component, for example, include the following in your Svelte component:

```
import Input from 'svelte-bulma-lib/src/Input.svelte';
```