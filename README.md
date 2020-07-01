# recruitment-frontend

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

## Documentation

This is custom vue project.

This is not a single page application.
This is webpack for styles, javascripts and vue components.

### Modules

Modules are folders in `src`
Module is a separated functionality. It can be css reset style, vue component, global BEM css.
Module source code that goes to production must be placed in module `src` directory eg. `src/ArticleList/src`.

### Main.js mechanisms

The src/main.js file is main endpoint and handles diffrents mechanism.

#### Style

Mechanism to add style to project. 
Global css using BEM methodology. 
To register styles add imports to: `src/style.scss`

#### Components

Basic vue components.
To register compoennt add it  `src/components.js`

#### Sandbox

Machanism to test modules in development environment.
Module sandbox code must be placed in module `sandbox` direcotry eg. `src/ArticleList/sandbox`
To register sanbox component add new route to `sandbox.js`. The route is na VueRouter route.
Sanboxes are not compiled for production.
