# KyivSubway_front
This is frontend of Kyiv Subway project

Бэкенд сайта написан на Django Rest Framework
Фронтенд сайта написан на фреймворке NuxtJS - реализован принцип SPA - приложения

Реализован следующий функционал:

1) Главная страница, со всеми постами и слайдером с ссылками на 3 поста

2) Страница самого поста, с комментариями, облаком тегов и ссылками на пять последних постов

3) Страницы Входа на сайт и Регистрации на сайте - после чего можно оставлять комментарии под постами (доп. исправление - после успешной регистрации/входа пользователя
 перекидывает на ту страницу, где он находился до регистрации/входа)

4) Страница Контакты - можно связаться с автором сайта, отправив сообщение ему на электронную почту

5) Страница поиска по сайту

6) Страница тегов - быстрое нахождение нужного поста по тегу

7) На главной странице сайта, на страницах тегов и поиска реализована пагинация

Бэкенд и фронтенд сайта расположены на разных серверах - при работе сайта сервер фронтенда обращается к серверу бэкенда и взаимодействует с ним через GET/POST

Сайт развёрнут и размещён на двух серверах Яндекс.Облако - использовался веб-сервер nginx на машине с ОС Ubuntu

Ссылка на сайт:

http://51.250.84.31

# first_jsapp

## Build Setup

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

For detailed explanation on how things work, check out the [documentation](https://nuxtjs.org).

## Special Directories

You can create the following extra directories, some of which have special behaviors. Only `pages` is required; you can delete them if you don't want to use their functionality.

### `assets`

The assets directory contains your uncompiled assets such as Stylus or Sass files, images, or fonts.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/assets).

### `components`

The components directory contains your Vue.js components. Components make up the different parts of your page and can be reused and imported into your pages, layouts and even other components.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/components).

### `layouts`

Layouts are a great help when you want to change the look and feel of your Nuxt app, whether you want to include a sidebar or have distinct layouts for mobile and desktop.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/layouts).


### `pages`

This directory contains your application views and routes. Nuxt will read all the `*.vue` files inside this directory and setup Vue Router automatically.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/get-started/routing).

### `plugins`

The plugins directory contains JavaScript plugins that you want to run before instantiating the root Vue.js Application. This is the place to add Vue plugins and to inject functions or constants. Every time you need to use `Vue.use()`, you should create a file in `plugins/` and add its path to plugins in `nuxt.config.js`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/plugins).

### `static`

This directory contains your static files. Each file inside this directory is mapped to `/`.

Example: `/static/robots.txt` is mapped as `/robots.txt`.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/static).

### `store`

This directory contains your Vuex store files. Creating a file in this directory automatically activates Vuex.

More information about the usage of this directory in [the documentation](https://nuxtjs.org/docs/2.x/directory-structure/store).
