<template>
  <div>
    <b-container>
        <b-table striped hover :items="items"></b-table>
    </b-container>
  </div>
</template>

<script>
export default {
    data() {
        return {
            items: [],
        }
    },
    created() {
        this.axios.get('https://sheetdb.io/api/v1/org6l4fy7fwm9')
        .then( response => {
            this.items = response.data;
        });
    },
}
</script>
