<template>
  <div id="app">

    <div>
      <b-navbar toggleable="lg" type="dark" variant="info">
        <b-navbar-brand href="#">Handslab Strengths Finder</b-navbar-brand>
      </b-navbar>
    </div>

    <div id="nav">
      <router-link to="/">リスト</router-link> |
      <router-link to="/create">新規追加</router-link> | 
      <router-link to="/search">検索</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  text-align: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
