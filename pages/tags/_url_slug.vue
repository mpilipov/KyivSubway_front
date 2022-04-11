<template>
  <div>
    <div class="container">
      <p class="my-3">
        Другие теги:
        <nuxt-link
          :to="`/tags/${tag.name}`"
          class="badge badge-success mr-1"
          v-for="tag in tags"
          :key="name"
          >#{{ tag.name }}
        </nuxt-link>
      </p>
      <div class="row">
        <div v-for="post in posts" :key="post.slug" class="col-md-4">
          <div class="card mb-4 shadow-sm">
            <img :src="post.image" alt="" class="card-img-top" />
            <div class="card-body">
              <h4 class="card-title">{{ post.h1 }}</h4>
              <div v-html="post.descr"></div>
              <div class="mb-2">
                <span v-for="t in post.tag">
                  <nuxt-link :to="`/tags/${t}`" class="mr-1 badge badge-info"
                    >#{{ t }}</nuxt-link
                  >
                </span>
              </div>
              <div class="d-flex justify-content-between align-items-center">
                <div class="btn-group">
                  <nuxt-link
                    :to="`/posts/${post.url_slug}`"
                    class="btn btn-sm btn-outline-secondary"
                    >Подробнее</nuxt-link
                  >
                </div>
                <small class="text-muted">{{ post.created }}</small>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Пагинация -->
      <nav aria-label="Paginate me">
        <ul class="pagination justify-content-center">
          <nuxt-link
            v-if="previous != null"
            class="page-link"
            :to="previous"
            tabindex="-1"
            >Предыдущая</nuxt-link
          >
          <li v-else class="page-item disabled">
            <a class="page-link disabled" href="#" tabindex="-1">Предыдущая</a>
          </li>

          <span v-for="i in total">
            <li
              v-if="current_page === i || ($route.query.page === '/' && i === 1)"
              class="page-item active"
            >
              <nuxt-link class="page-link" :to="`?page=${i}`">{{ i }}</nuxt-link>
            </li>
            <li v-else class="page-item">
              <nuxt-link class="page-link" :to="`?page=${i}`">{{ i }}</nuxt-link>
            </li>
          </span>

          <nuxt-link v-if="next != null" class="page-link" :to="next"
            >Следующая</nuxt-link
          >
          <li v-else class="page-item disabled">
            <a class="page-link" href="#">Следующая</a>
          </li>
        </ul>
      </nav>





    </div>
    <div v-if="posts.length <= 3">
      <br />
      <br />
      <br />
      <br />
    </div>
    
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header";
import Footer from "@/components/Footer";
export default {
  components: { Header, Footer },
  layout: "post_detail",
  watchQuery: ['page'],
  data() {
    return {
      posts: [],
      tags: [],
      total: [],
      next: [],
      title: [],
      previous: [],
      current_page: 0,
    };
  },

  async asyncData({ params, route }) {
    // Сначала получаем весь список тегов
console.log('1');

    const tags = await axios.get(`http://51.250.71.220/api/tags/`);
console.log('2');

    var t;
    console.log(tags);
    // Затем определяем, какому Tags.name соответствует params.url_slug
    // Необходимо, чтобы Сериалайзер тегов в бекенде возвращал fields = ("name", "slug", )
    for (var i = 0; i < tags.data.length; i += 1) {
      if (tags.data[i].name == params.url_slug) {
        t = tags.data[i].slug;
      }
    }
    let mypage = route.query.page !== undefined ? `?page=${route.query.page}` : ``;
    console.log(mypage);
    const { data } = await axios.get(`http://127.0.0.1:8000/api/tags/${t}/${mypage}`);
    let next = data.next != null ? data.next.split("/")[5] : data.next;
    let previous = data.previous != null ? data.previous.split("/")[5] : data.previous;
    let current_page = route.query.page;
    return {
      posts: data.results,
      total: Math.ceil(data.count / 6),
      next: next,
      previous: previous,
      current_page: Number(current_page),
      title: `#${params.url_slug}`,
      tags: tags.data,
    };
  },
};
</script>

<style scoped></style>
