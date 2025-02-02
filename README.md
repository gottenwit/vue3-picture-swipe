# Vue 3 Picture Swipe Gallery

[![npm download](https://img.shields.io/npm/dt/vue3-picture-swipe.svg)](https://www.npmjs.com/package/vue3-picture-swipe)
[![npm version](https://img.shields.io/npm/v/vue3-picture-swipe.svg)](https://www.npmjs.com/package/vue3-picture-swipe)
[![Package Quality](http://npm.packagequality.com/shield/vue3-picture-swipe.svg)](http://packagequality.com/#?package=vue3-picture-swipe)
[![vue3](https://img.shields.io/badge/vue-3.x-brightgreen.svg)](https://vuejs.org/)
[![MIT License](https://img.shields.io/github/license/sitronik/vue3-picture-swipe.svg)](https://github.com/sitronik/vue3-picture-swipe/blob/master/LICENSE)

This component is a simple wrapper for the awesome [Photoswipe](http://photoswipe.com/).
It's a [Vue 3](https://vuejs.org/) plugin that displays a gallery of image with swipe function (and more). 
Includes lazy (smart) loading (mobile friendly) and thumbnails.


## Demo

<img src="https://media.giphy.com/media/F0scu9nmMJQIoJLXdF/giphy.gif">

## Install

```bash
npm install --save vue3-picture-swipe
```

## Usage

You can use it as you want. Here are some examples if you want to use it inline, or in a `.vue` file component or even with Laravel. 

### Inline usage

You can using it inline:

```html
<vue-picture-swipe :items="[
    {src: 'http://example.org/xl.jpg',thumbnail: 'http://example.org/sm1.jpg',w: 600,h: 400, title: 'Will be used for caption'},
    {src: 'http://example.org/xxl.jpg',thumbnail: 'http://example.org/sm2.jpg',w: 1200,h: 900}
  ]"></vue-picture-swipe>
```

Just remember to register the component:

```javascript
import VuePictureSwipe from 'vue3-picture-swipe';
Vue.component('vue-picture-swipe', VuePictureSwipe);

new Vue({
  el: '#app'
})
```

### Usage in another component

Create a component `Example.vue`. Then paste this:

```vue
<template>
  <vue-picture-swipe :items="items"></vue-picture-swipe>
</template>
<script>
  import VuePictureSwipe from 'vue3-picture-swipe';
  export default {
    data() {
      return {
        items: [{
          src: 'http://via.placeholder.com/600x400',
          thumbnail: 'http://via.placeholder.com/64x64',
          w: 600,
          h: 400,
          alt: 'some numbers on a grey background' // optional alt attribute for thumbnail image
        },
        {
          src: 'http://via.placeholder.com/1200x900',
          thumbnail: 'http://via.placeholder.com/64x64',
          w: 1200,
          h: 900,
          htmlAfterThumbnail: '<span class="photos-date">29.12.2021</span>' // optional, insert your html after tag <a> if you need it
        }
      ]};
    }
  }
</script>
```

### Usage with Laravel

Edit `resources/assets/js/app.js` and add this just before the `new Vue` lines.

```javascript
import VuePictureSwipe from 'vue3-picture-swipe';
Vue.component('vue-picture-swipe', VuePictureSwipe);
```
### PhotoSwipe options

Use `options` for [Photoswipe options](http://photoswipe.com/documentation/options.html).

```html
<!-- Disable "share" buttons. -->
<vue-picture-swipe :options="{shareEl: false}"></vue-picture-swipe>
```

### PhotoSwipe instance

You can access the PhotoSwipe instance via setting a ref, the instance object is exposed as `pswp`.

```html
<vue-picture-swipe ref="pictureSwipe"></vue-picture-swipe>
```
```js
this.$refs.pictureSwipe.pswp
```

### Events

| open           | Attributes    | Listen to       | Description |
| ---            | ---     | ---           | ---         |
| Open           | none  | @open        | Emitted after gallery opens |
| Close  | none  | @close | Emitted after gallery closes |

# 🤝 Contributing

1. Fork this repository.
2. Create new branch with feature name.
3. Run `npm install` and `npm run dev`.
4. Create your feature.
5. Commit and set commit message with feature name.
6. Push your code to your fork repository.
7. Create pull request. 🙂

# ⭐️ Support

If you like this project, You can support me with starring ⭐ this repository.

# 📄 License

[MIT](LICENSE)

Developed with ❤️ and ☕️
