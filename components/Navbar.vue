<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark sticky-top">

    <nuxt-link class="navbar-brand" to="/">
      <img src="/img/Kyiv_Metro_logo.svg" width="30" height="30" alt="logo">
    </nuxt-link>
            <ul class="navbar-nav mr-auto">
            <li class="nav-item active">
                <a href="/" class="nav-link" style="font-size: 20px">Киевский Метрополитен</a>
            </li>
            </ul>
    <button class="navbar-toggler" type="button" data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse " id="navbarSupportedContent">

      <ul class="navbar-nav ml-auto ">
        <li class="nav-item active ">
          <a class="btn btn-outline-light  " style="font-size: 18px" href="/contact">Контакты</a>
        </li>
      </ul>

      <form class="form-inline ">
        <input name="q" v-model="q" type="text" class="form-control mr-sm-2 ml-2" placeholder="Поиск" aria-label="Поиск">
        <button class="btn btn-outline-success my-2 my-sm-0 mr-2" type="submit" @click.stop.prevent="submit()">Поиск</button>
      </form>
      <span class="navbar-text mr-2" v-if="user">{{user.username}}</span>
      <span v-if="loggedIn"><nuxt-link class="btn btn-outline-light mr-2" to="/signout">Выход</nuxt-link></span>
      <span v-else>
        <nuxt-link class="btn btn-outline-light mr-2" to="/signin">Вход</nuxt-link>
        <nuxt-link class="btn btn-outline-light mr-2" to="/signup">Регистрация</nuxt-link>
      </span>

    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data(){
    return {
      q : null
    }
  },
  methods: {
    submit(){
      this.$router.push("/search?q="+this.q);
    }
  },
  computed: {
    loggedIn() { // проверка авторизован юзер или нет
      return this.$auth.loggedIn
    },
    user() {  // возвращает данные залогиненного пользователя, сохраняет в перемпнную user
      return this.$auth.user
    }
  }
}
</script>

<style scoped>

</style>