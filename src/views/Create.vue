<template>
  <div class="create">
    <b-container>
      <Form/>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import Form from '@/components/Form.vue'

export default {
  name: 'Create',
  components: {
    Form
  }
}
</script>