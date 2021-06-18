<template>
  <Titulo texto="Titulo del articulo" />
  <h2>Parámetro: {{ $route.params.id }}</h2>
  <p>
    <strong>Titulo: </strong>
    {{ post.title }}
  </p>
  <p>
    <strong>Contenido: </strong>
    {{ post.body }}
  </p>
</template>

<script>
import Titulo from "@/components/Titulo.vue";
export default {
  name: "Articulo",
  components: {
    Titulo,
  },
  data() {
    return {
      post: {},
    };
  },
  methods: {
    async getSinglePost(id) {
      const resp = await fetch(
        `https://jsonplaceholder.typicode.com/posts/${id}`
      );
      const data = await resp.json();
      this.post = data;
    },
  },
  created() {
    this.getSinglePost(this.$route.params.id);
  },
};
</script>

<style>
</style>