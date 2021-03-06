# ๐ฅ vuevie
TMDb api๋ฅผ ์ด์ฉํ ์ํ์ฌ์ดํธ!

## Deployment / ๋ฐฐํฌ
[https://vuevie.netlify.app/#/<br>
![FireShot Capture 046 - VUEVIE - vuevie netlify app](https://user-images.githubusercontent.com/59958929/128485863-1d1ea959-5be5-4cde-a453-8d130233cc3f.png)](https://vuevie.netlify.app/#/)
 
### webpack์ผ๋ก ์์!

```
$ cd git
$ npx degit Lee-ye-ji/vue3-webpack-template vuevie
$ cd vuevie
$ npm i
$ code . -r
```

- <style></style> ํ๊ทธ ์ฌ์ฉ์ message ์ฌ๋ผ์ง โ `style-loader` ๋ฒ์  ๋ค์ด ๊ทธ๋ ์ด๋

```
npm i -D style-loader@2.0.0
```

### **`ํ์ด์ง๋ฅผ ๊ตฌ๋ถํ  ๋ ์ฌ์ฉํ๋ ๊ธฐ์  โ Router ๊ธฐ์ `**

### vue-router next

next๋ฅผ ์ด ์ด์ ๋ ์๋ ๊ธฐ์กด ๋ฒ์ ์ 2๋ฒ์ ์ธ๋ฐ ์ฐ๋ฆฌ๋ 3๋ฒ์ ์ ์ฌ์ฉํ๋ฏ๋ก ๋์๋๊ธฐ ์ํด์ 

[Installation | Vue Router](https://next.router.vuejs.org/installation.html)

```
npm install vue-router@4
```

**createRouter**

export default โ ๊ธฐ๋ณธ ๋ด๋ณด๋ด๊ธฐ / ์ด๊ฒ์ main.js์์ ๋ฐ์์ ์ฌ์ฉํจ

**`index.js`**

```jsx
// ํ์ด์ง๋ฅผ ๊ตฌ์ฑํ๋ ๊ตฌ์ฑํ์ผ
import { createRouter, createWebHashHistory } from 'vue-router';

export default createRouter({
    // history : hash, history ๋ ๊ฐ์ง๋ก ๊ตฌ๋ถ
    // hash๋ชจ๋ ์ฌ์ฉ
    // https://google.com/#/search
    history : createWebHashHistory(),
    // routes: page๋ค์ ๊ตฌ๋ถ
    routes: []
})
```

hash๋ชจ๋๋ฅผ ์ฌ์ฉํด์ผ์ง๋ง ๊ธฐ๋ณธ์ ์ผ๋ก ํน์ ํ์ด์ง์์ ์๋ก๊ณ ์นจ์ ํ์ ๋ ํ์ด์ง๋ฅผ ์ฐพ์ ์ ์๋ค๋ ๋ฉ์์ง๋ฅผ ๋ฐฉ์งํ  ์ ์์

history๋ชจ๋ โ ์๋ฒ์๋ค๊ฐ ์ธํ ์์์ ํด์ผ๊ธฐ ๋๋ฌธ์ hash๋ชจ๋๋ฅผ ์ฌ์ฉํจ

**`<RouterView />` โ ์ปดํฌ๋ํธ ์ฌ์ฉ Home, Router, about ํ์ด์ง๋ฅผ ์ถ๋ ฅํ๋ ๊ฐ๋์**

๊ฐ๊ฐ์ ํ์ด์ง๋ router๋ผ๋ ๊ฐ๋์ ๊ฐ๊ฐ์ ์์ญ์์ ์ถ๋ ฅ์ด ๋๋ค๊ณ  ๋ณด๋ฉด ๋จ

### ๋ถํธ์คํธ๋ฉ(Bootstrap)

```
$ npm i bootstrap@next -- 5๋ฒ์  ์ค์น
```

Bootstrap ์ค๋ฅ

353 โ $container-padding-x: $grid-gutter-width / 2 !default;
โ                       ^^^^^^^^^^^^^^^^^^^^^^

```
$ npm i sass@1.32.13
```

**downgrading sass to 1.32.***

๐ ์์ด์ฝ

```
$ npm i bootstrap-icons
```

### Vuex

โ ํจ์จ์ ์ธ ๋ฐฉ๋ฒ์ผ๋ก ๊ด๋ฆฌํด์ค ์ ์๋ ์ค์์ง์คํ๋ ์ํ๊ด๋ฆฌ ํจํด์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ 

โ ๋จ์ํ๊ฒ ๋ฐ์ดํฐ๋ฅผ ๋ชฐ์์ ๊ด๋ฆฌํด์ฃผ๋ ๊ณต์ ๋ผ์ด๋ธ๋ฌ๋ฆฌ

```
$ npm i vuex@next
```

**`mapState`**

```jsx
computed: {
    theMovie() {
      return this.$store.state.movie.theMovie;
    },
    video() {
      return this.$store.state.movie.video;
    },
    loading(){
      return this.$store.state.movie.loading;
    }
  },
```

โ ๋ฐ๋ณต์ ์ผ๋ก ์ฝ๋๊ฐ ์์ฑ๋๊ณ  ์๊ธฐ ๋๋ฌธ์ ์ฝ๊ฒ ๊ด๋ฆฌํ๊ธฐ ์ํด์ vuex์ Helper๋ฅผ ์ฌ์ฉํจ!

```jsx
import { mapState } from 'vuex'

computed: {
    ...mapState('movie',[
      'theMovie',
      'video',
      'loading'
    ])
 },
```

โ movie๋ผ๋ ๋ชจ๋์ ์ด๋ฆ์ ๋ช์, ๋๋ฒ์งธ ์ธ์๋ก๋ ๋ฐฐ์ด์ ์ถ๊ฐํด์ ๊ฐ๊ฐ์ ์์ดํ๋ถ๋ถ์๋ค๊ฐ ๋ฌธ์ ๋ฐ์ดํฐ๋ก ๊ฐ์ง๊ณ  ์ฌ state ์ฆ, ์ํ๋ค์ ์ด๋ฆ์ ๋ช์ํด์ฃผ๋ฉด ๋๋ค!

matState๊ฐ ์คํ๋  ๊ฒฐ๊ณผ๋ฅผ ํตํด์ ๋ช์ํ ๋ด์ฉ๋ค์ด ๊ฐ์ฒด ๋ฐ์ดํฐ๋ก ๋ฐํ โ ๊ฐ์ฒด ๋ฐ์ดํฐ๋ฅผ ์ ๊ฐ ์ฐ์ฐ์๋ก ์ ๊ฐํด์ computed๋ผ๋ ๊ณ์ฐ๋ ๋ฐ์ดํฐ์ ๋ฑ๋ก์ ํ๋ ๊ฒ์ด๋ค.

**`mapActions`**

โ **store์ Action์ ๊ฐ์ง๊ณ  ์ค๋ ๋ฐฉ๋ฒ**

```jsx
created() {
    this.$store.dispatch("movie/searchMovieWithId", {
      id: this.$route.params.id,
    });
  },
```

```jsx
import { mapState, mapActions } from 'vuex'

created() {
    // this.$store.dispatch("movie/searchMovieWithId", {
      this.searchMovieWithId({
      id: this.$route.params.id,
    });
  },
  methods: {
    ...mapActions('movie',[
      'searchMovieWithId'
    ])
}
```

โ ํ์ฉ๋๊ฐ ์ ์ผ ๋์ ๊ฒ์! **`mapState`** ์ด๋ค!

### Vuex์ ํต์ฌ์ ๋ฆฌ

App.vueํ์ผ์ ๊ธฐ์ค์ผ๋ก ์ฌ๋ฌ๊ฐ์ง ์ปดํฌ๋ํธ๋ฅผ ํ์ฉํ๊ฒ ๋๋ค.

๋ถ๋ชจํ์ ๊ฐ ์๋ ํน์ ํ ๊ด๊ณ๊ฐ ๋จ์ด์ง์ง ์๋ ์ฌ๋ฌ๊ฐ์ง ์ปดํฌ๋ํธ๋ค์์ ๊ฐ์ ๋ฐ์ดํฐ๋ฅผ ํ์ฉํ  ๋๋ **Store ๋ผ๋ ๊ฐ๋!**

โ ์ฆ, vuex๋ผ๋ ํจํค์ง๋ฅผ ๊ฐ์ง๊ณ  ์์ ํ๋ฌ๊ทธ์ธ์ผ๋ก ์ฐ๊ฒฐํด์ ํ์ฉํ  ์ ์์!

store๋ด๋ถ์์ ๊ด๋ฆฌํ๊ณ , ๊ทธ๊ฒ์ ๊ฐ๊ฐ์ ์ปดํฌ๋ํธ๋ก ๊ฐ์ง๊ณ  ์์ ํ์ฉํ  ์ ์๋ ๊ฒ์ผ๋ก ๋ง๋ฌ!

Store์ movie๋ผ๋ ๋ชจ๋์ด๋ผ๋ ๊ฐ๋์ผ๋ก ์ฐ๊ฒฐํด์ค! ๋ชจ๋๋ค์ ๊ธฐ๋ณธ์ ์ธ ๊ธฐ๋ฅ์ผ๋ก ๊ด๋ฆฌํ๋ ์ฉ๋!

**`Store`**

namespaced๋ผ๋ ์ต์์ ์ ์ธํ๊ณ , ๋๋จธ์ง state, getters, mutations, actions ๊ฐ๊ฐ์ ์ต์๋ค๋ก ๋๋์ด์ง๊ฒ ๋๋ค!

* **state**(data) โ vue.js ์ปดํฌ๋ํธ์์ ์๊ณ  ์๋ ํ๋์ ๋ฐ์ดํฐ

* **getters**(computed) โ ๊ณ์ฐ๋ ๋ฐ์ดํฐ computed์ ์ ์ฌํจ. ๋ฐ์ดํฐ๋ผ๊ณ  ๋ณผ ์ ์๋ ๊ณ์ฐ๋ ํํ๋ก ํ์ฉํ  ์ ์๋๋ก getters๋ฅผ ์ฌ์ฉํ  ์ ์์

* **mutations**(methods) โ vue์ปดํฌ๋ํธ์ method์ ์ ์ฌํจ state๋ฅผ ๋ณ๊ฒฝํ  ์ ์๋ ๊ถํ์ ๊ฐ์ง๊ณ  ์์ด์ state๋ฅผ ๋ณ๊ฒฝํ๋ ๋ก์ง๋ง ์ผ๊ด์ ์ผ๋ก ์์ฑํ๊ฒ ๋จ

* **actions**(methods, ๋น๋๊ธฐ) โ vue์ปดํฌ๋ํธ์ method์ ์ ์ฌํจ  ๋๋จธ์ง ๋ถ๋ถ๋ค์  actions์๋ค๊ฐ ์์ฑ์ ํด ๋น๋๊ธฐ๋ ๊ฐ๋ฅ ํ  ์ ์๋๋ก ์์ฑํ๋ ๊ฒ์ด ์ผ๋ฐ์ ์!

```
context.state
context.getters
context.commit -> mutations
context.dispatch -> actions(๋ค๋ฅธ ์ก์์ ์คํํ๋ ์ฉ๋)
```

### Axios

```
$ npm i axios
```

์๋ฐ์คํฌ๋ฆฝํธ ๋ด๋ถ์์ ๋น๋๊ธฐ๋ก ๋์์ด ๋์ด์ผํ๊ธฐ ๋๋ฌธ์ โ async

๊ทธ ์ฒ๋ฆฌ๋ ๊ฒฐ๊ณผ๊ฐ ๋์ฌ ๋๊น์ง ๊ธฐ๋ค๋ฆฌ๊ธฐ ์ํด์ โ await

### Carousel

```
$ npm i swiper
```

### ์ํธํค ์จ๊ธฐ๊ธฐ

```
$ npm i -D dotenv-webpack
```

**webpack.config.js**

```jsx
const Dotenv = require('dotenv-webpack')

plugins: [
        ...
        new Dotenv
    ],
```

**.env ํ์ผ ์์ฑ**

TMDB_API_KEY=์ํธํค

axios.js

```jsx
const TMDB_API_KEY = process.env.TMDB_API_KEY
// ๊ตฌ์กฐ ๋ถํด
const { TMDB_API_KEY } = process.env
```

netlify์ ์ฌ๋ฆฌ๊ธฐ โ **netlify.toml** ๋ง๋  ํ ์์ฑํด์ผ ํจ!

package.json

```json
"dev:netlify" : "netlify dev",
```

```
$ npm i -D netlify-cli
```

### ๋ฐ๋ณต๋๋ import ๊ท์น

**`additionalData`**

```jsx
module.exports = {
  module: {
    rules: [
      {
        test: /\.s?css$/,
        use: [
          "style-loader",
          "css-loader",
         {
              loader: 'sass-loader',
              options: {
                  additionalData: '@import "~/scss/main";'
              }
            },
          },
        ],
      },
    ],
  },
};
```

๋ฌธ์ ๋ฐ์ดํฐ๋ฅผ โ ๊ฐ์ฒด ๋ฐ์ดํฐ๋ก ๋ณ๊ฒฝ
