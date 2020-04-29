<template>
  <div class="search">
    <b-container>
      <SearchItem/>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchItem from '@/components/SearchItem.vue'

export default {
  name: 'Search',
  components: {
    SearchItem
  }
}
</script>