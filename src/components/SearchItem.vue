<template>
  <div>
    <b-form-input class="form" v-model="text" @keydown.enter="filterStrength" placeholder="ストレングスのキーワードを入力してください"></b-form-input>
    <b-container class="container">
      <b-table striped hover :items="filter_items"></b-table>
    </b-container>
  </div>
</template>

<script>
export default {
    data() {
        return {
            text: '',
            items: [],
            filter_items: [],
        }
    },
    methods: {
        filterStrength() {
            this.filter_items = this.items.filter(items => {
            return items.strength1 == this.text ||
                   items.strength2 == this.text ||
                   items.strength3 == this.text ||
                   items.strength4 == this.text ||
                   items.strength5 == this.text;
            });
        },
    },
    created() {
        this.axios.get('https://sheetdb.io/api/v1/3snlhppfxzhqj')
        .then( response => {
            this.items = response.data;
        });
    },
}
</script>

<style scoped>
.form {
    margin: 10px auto;
    width: 50%;
}
.container {
    padding: 5% 0;
}
</style>