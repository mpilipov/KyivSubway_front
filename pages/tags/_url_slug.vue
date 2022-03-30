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
                    >Подробнее</nuxt-link>
                </div>
                <small class="text-muted">{{ post.created }}</small>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header";
export default {
  components: { Header },
  layout: "post_detail",
  async asyncData({ params }) {
    // Сначала получаем весь список тегов
    const tags = await axios.get(`http://127.0.0.1:8000/api/tags/`);
    var t;
    console.log(tags.data.length);
    // Затем определяем, какому Tags.name соответствует params.url_slug
    // Необходимо, чтобы Сериалайзер тегов в бекенде возвращал fields = ("name", "slug", )
    for (var i = 0; i < tags.data.length; i += 1) {
      if (tags.data[i].name == params.url_slug) {
        t = tags.data[i].slug;
      }
    }
    const { data } = await axios.get(`http://127.0.0.1:8000/api/tags/${t}/`);
    return {
      posts: data.results,
      title: `#${params.url_slug}`,
      tags: tags.data,
    };
  },
};
</script>

<style scoped></style>
