<template>
  <div class="home">
    <b-container>
      <List/>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import List from '@/components/List.vue'

export default {
  name: 'Home',
  components: {
    List
  }
}
</script>