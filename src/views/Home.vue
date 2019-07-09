<template>
  <div class="home">
    <ToDos/>
  </div>
</template>

<script>
import ToDos from '@/components/ToDos.vue'

export default {
  name: 'home',
  components: {
    ToDos
  }
}
</script>
