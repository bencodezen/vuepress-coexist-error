# VuePress Coexist Error

This repo is created to demonstrate an issue discovered in an attempt to integrate a Vue CLI app with VuePress under the same `package.json` file.

## Suspicion

My guess is that the way we're calling a dependency is conflicting with pre-existing libraries inside of `node_modules`.

## How to Reproduce Error

1. Install dependencies via `yarn`
1. Run `yarn docs` to start VuePress instance
1. Open http://localhost:8080
1. See the following error in JavaScript Console

```
[Vue warn]: Failed to resolve async component: function Layout() {
    return __webpack_require__.e(/*! import() */ 0).then(__webpack_require__.bind(null, /*! ./node_modules/@vuepress/theme-default/layouts/Layout.vue */ "./node_modules/@vuepress/theme-default/layouts/Layout.vue"));
  }
Reason: TypeError: Cannot assign to read only property 'exports' of object '#<Object>'
warn @ webpack-internal:///./node_modules/vue/dist/vue.runtime.esm.js:620
```

## How to See Success State

1. Change directory to `/docs`
1. Install dependencies via `yarn`
1. Run `yarn docs` to start VuePress instance
1. Open http://localhost:8080
1. Everything looks great!
