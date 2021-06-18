<template>
  <Titulo texto="Titulo del blog" />
  <button @click="obtenerArticulos" disabled>Consumir API</button>
  <div v-for="item in arrayBlog" :key="item.id">
    <router-link :to="`/blog/${item.id}`">{{ item.title }}</router-link>
  </div>
</template>

<script>
import Titulo from "../components/Titulo.vue";
export default {
  name: "Blog",
  components: {
    Titulo,
  },
  data() {
    return {
      arrayBlog: [],
    };
  },
  methods: {
    async obtenerArticulos() {
      try {
        const resp = await fetch("https://jsonplaceholder.typicode.com/posts");
        const data = await resp.json();
        console.log(data);
        this.arrayBlog = data;
      } catch (error) {
        console.log("Error");
      }
    },
  },
  created() {
    this.obtenerArticulos();
  },
};
</script>

<style>
</style>