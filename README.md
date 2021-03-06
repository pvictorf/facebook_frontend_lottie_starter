# facebook_frontend_lottie_starter
Projeto do curso da Cataline https://station.cataline.io/bootcamp.
Esse projeto se trata apenas do stater onde foi adicionado a biblioteca do vue-lottie para trabalhar com Nuxt.


# Instalando Vue Lottie
https://www.npmjs.com/package/vue-lottie#configuration

npm install --save vue-lottie


# Configurando e Entendendo
### 1) Assets
No diretório *assets* tem uma pasta *animations* que estão as animações em json baixadas no site: https://lottiefiles.com/search?q=emojis&category=animations



### 2) nuxt.config.ts
É necessário configurar o Nuxt para importar automáticamente o componente do lottie
```js
//nuxt.config.ts
components: [{ path: '@/components/', pathPrefix: false }, { path: 'vue-lottie/src/lottie.vue', pathPrefix: false }],
```

### 3) LottieAnimation.vue
Na pasta atoms temos a abstração da lib com o componente LottieAnimation.vue para uso das animações.json é necessário fazer o require() e 
existem duas formas de importar o arquivo, sendo elas:
```js
const animationData = require(`@/assets/animations/${this.animation}.json`)
options {
  animationData: animationData
}

import * as animationData from '@/assets/animations/emojis-like.json'
options {
  animationData: animationData.default // nesse caso os dados da animação ficarão dentro da propriedade 'default'
}
```

### 4) Minha animação está com fundo branco, como corrigir?
```bash
Acesse o arquivo da animção espeficia em json, busque pelo parâmetro "sc" (ou código da cor), 
em seguida, altere cor para transparent, por exemplo, 
# "sc":"#ffffff" para "sc":"transparent"
```


### 5) Solucionando o problema: Cannot find module consider using '--resolveJsonModule' to import module with '.json' extension.
```bash
No tsconfig.json adicione o parâmetro resolveJsonModule: true em "compilerOptions"

// tsconfig.js
"compilerOptions": {
  ...
  "resolveJsonModule": true,
  /* "esModuleInterop": true, */
  "allowJs": true,
  ...
}
```


## Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```
