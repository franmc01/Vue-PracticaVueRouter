<template>
  <div class="home">
    <Titulo texto="Titulo de Inicio" />
  </div>
</template>

<script>
// @ is an alias to /src
import Titulo from '@/components/Titulo.vue'

export default {
  name: 'Home',
  components: {
    Titulo
  }
}
</script>
