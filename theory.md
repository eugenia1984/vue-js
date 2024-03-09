# <img width="32" height="32" src="https://img.icons8.com/fluency/28/vuejs.png" alt="vue.js"/>  How to start a project with Vue and Vite?

1. Create the project...

...using just VUE.js:

NPM: `npm create vue@latest`

PNPM: ```pnpm create vue@latest```

YARN: ```yarn create vue@latest```

This command will install and execute create-vue, the official Vue project scaffolding tool. You will be presented with prompts for several optional features such as TypeScript and testing support:

```
✔ Project name: … <your-project-name>
✔ Add TypeScript? … No / Yes
✔ Add JSX Support? … No / Yes
✔ Add Vue Router for Single Page Application development? … No / Yes
✔ Add Pinia for state management? … No / Yes
✔ Add Vitest for Unit testing? … No / Yes
✔ Add an End-to-End Testing Solution? … No / Cypress / Playwright
✔ Add ESLint for code quality? … No / Yes
✔ Add Prettier for code formatting? … No / Yes

Scaffolding project in ./<your-project-name>...
Done.
```

... with VUE.js and Vite : ```npm create vite@latest```

2. Install dependencies:

```BASH
cd <your-project-name>
npm install
```

3. Run the project: ```npm run dev```. And see the project in the browser at: [ http://localhost:5173/](http://localhost:5173/)

---

# <img width="32" height="32" src="https://img.icons8.com/fluency/28/vuejs.png" alt="vue.js"/>  TailwindCSS

1. Follow this steps: [vue-tailwind.css-config](https://guillaumeduhan.medium.com/vue-tailwindcss-config-4c02236ca89c)

- Install Tailwind.css, post.css and auto-prefixer: `npm install -D tailwindcss@latest postcss@latest autoprefixer@latest`

- Create your configuration files: ``npx tailwindcss init -p``, and two nes files will be created: `tailwind.config.js` and `postcss.config.js`

- Configure Tailwind to remove unused styles in production, at ``tailwind.config.js``:

```JavaScript
module.exports = {
    purge: ['./index.html', './src/**/*.{vue,js,ts,jsx,tsx}'],
    darkMode: false, // or 'media' or 'class'
    theme: {
      extend: {},
    },
    variants: {
      extend: {},
    },
    plugins: [],
  }
```

- Include Tailwind in your CSS, create: `./src/index.css` file with:

```CSS
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- Import your CSS in ``src/main.js``:

```JavaScript
import { createApp } from 'vue'
import App from './App.vue'
import './index.css'

createApp(App).mount('#app')
```

---

# <img width="32" height="32" src="https://img.icons8.com/fluency/28/vuejs.png" alt="vue.js"/> Architecture

```
> .vscode
> node_modules
> public
> src
  > assets
  > components
  > views
  App.vue
  index.css
  main.js
  style.css
  .gitignore
  index.html
  package.json
  package-lock.json
  postcss.config.js
  tailwind.config.js
  vite.config.js
```
---

## <img width="32" height="32" src="https://img.icons8.com/fluency/28/vuejs.png" alt="vue.js"/>  Component

- Between the `<template></template>` tags you will see all the **HTML5** code.

- Between de `<script setup></script>` tags you will see all the **JavaScript** code.

- The style would be between the `<style></style>` tags, but in some project it can be using some library (like **TailwindCSS**) and can be using a separate **.css** file with the attribute **class** inside the corresponding tag. 

### Reusable component

Has **props**, there is two ways...

...in VUE.js version 2:

```Vue
<template>
  <div>
    <Presentation v-for="obj, objIndex in presentations" :key="objIndex" :content="obj" />
  </div>
</template>

<script>
import { Presentation} from "../components";
import { reactive, toRefs} from 'vue'
import ModelSInterior from '../assets/model-s-interior.jpg'


export default {
  components: {
    MainHeader, 
    Nav, 
    Presentation, 
    Stats, 
    Tabs, 
    Footer
  },
  setup() {
    let data = reactive({
      presentations: [
        {
          left: true,
          coll1: {
            title: 'Model S',
            subtitle: 'Beyond Ludicrous',
            description: "Model S Plaid has the quickest acceleration of any vehicle in production. Updated battery architecture for all Model S trims enables back-to-back track runs without performance degradation. Chat with a Tesla Advisor to learn more about Model S or schedule a demo drive today.",
          },
          col2: {
            imgSrc: ModelSInterior
          }
        }
      ]
    })

    return {
      ...toRefs(data)
    }
  }
}
</script>
```

Presentation.vue
```Vue
<template>
  <div>{{ content  }}</div>
</template>

<script>
export default {
  props: {
    content: {
      default: () => {},
      type: Object
    }
  }
}
</script>
```

... in VUE.js version 3:


```Vue
<template>
  <div class="presentation flex flex-row" :class="{'flex-row-reverse': !content.left}">
    <div v-for="col, colIndex in content.columns" :key="colIndex" class="flex-1">{{ col }}</div>
  </div>
</template>

<script>
export default {
  props: {
    content: {
      default: () => {},
      type: Object
    }
  },
  setup(props) {
    console.log("props.content: ",props.content)
  }
}
</script>
```

-> Conditional class example: `:class="{'flex-row-reverse': !content.left}"`

-> Conditional render: using **v-if**:

```VUE
<div v-if="col.imgSrc">
  <img :src="col.imgSrc" alt="Tesla car" />
</div>
```

-> Class generated with the props: `:class="`bg-${col.backgroundColor}`"`

```VUE
<template>
  <section class="presentation flex flex-col md:flex-row" :class="{'md:flex-row-reverse': !content.left}">
    <div v-for="col, colIndex in content.columns" :key="colIndex" class="flex-1">
      <div v-if="col.imgSrc">
        <img :src="col.imgSrc" alt="Tesla car" />
      </div>
      <div v-else class="p-8 md:p-24" :class="`bg-${col.backgroundColor}`">
        <h2>{{ col.title}}</h2>
      </div>
    </div>
  </section>
</template>
```
---
