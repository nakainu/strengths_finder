<template>
  <div>
    <b-container>
        <b-table striped hover :items="items" :fields="fields" primary-key="items.id"></b-table>
    </b-container>
  </div>
</template>

<script>
export default {
    data() {
        return {
            fields: ['id', 'team', 'name', 'strength1', 'strength2', 'strength3' , 'strength4', 'strength5'],
            items: [],
        }
    },
    created() {
        this.axios.get('https://sheetdb.io/api/v1/3snlhppfxzhqj')
        .then( response => {
            this.items = response.data;
        });
    },
}
</script>
