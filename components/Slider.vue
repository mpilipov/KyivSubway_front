<template>
  <div class="container-fluid home-slider">
    <div id="carouselExampleCaptions" class="carousel slide" data-ride="carousel">
      <ol class="carousel-indicators">
        <li data-target="#carouselExampleCaptions" data-slide-to="0" class="active"></li>
        <li data-target="#carouselExampleCaptions" data-slide-to="1"></li>
        <li data-target="#carouselExampleCaptions" data-slide-to="2"></li>
      </ol>
      <div class="carousel-inner">
        <div class="carousel-item active">
          <nuxt-link :to="`/posts/osokorki`">
            <img src="/img/c13_1.jpg" class="d-block w-100" alt="Первая картинка">
          </nuxt-link>
          <div class="carousel-caption d-none d-md-block p-1">
            <h5 >Осокорки</h5>
            <p>Сырецко-Печерской линии</p>
          </div>
        </div>
        <div class="carousel-item">
          <nuxt-link :to="`/posts/dnipro`">
          <img src="/img/a13.jpg" class="d-block w-100" alt="Вторая картинка">
          </nuxt-link>
          <div class="carousel-caption d-none d-md-block">
            <h5 >Днепр</h5>
            <p>Святошинско-Броварской линии</p>
          </div>
        </div>
        <div class="carousel-item">
          <nuxt-link :to="`/posts/palac-ukrayina`">
            <img src="/img/b11.jpg" class="d-block w-100" alt="Третья картинка">
          </nuxt-link>
          <div class="carousel-caption d-none d-md-block">
            <h5 >Дворец Украина</h5>
            <p>Оболонско-Теремковской линии</p>
          </div>
        </div>
      </div>
      <a class="carousel-control-prev" href="#carouselExampleCaptions" role="button" data-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="sr-only">Previous</span>
      </a>
      <a class="carousel-control-next" href="#carouselExampleCaptions" role="button" data-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="sr-only">Next</span>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Slider"
}
</script>

<style scoped>

</style>