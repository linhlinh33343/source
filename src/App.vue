<template>
  <div id="app">
    <div class="d-flex sp flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-white  justify-content-between">
      <router-link to="Home" class="" >Vue Mini Project</router-link>
      <nav>
        <router-link to="/product" >Project management</router-link>
        <router-link to="/user">User management</router-link>
      </nav>
      <a class="btn btn-outline-primary" routerlink="cart">Administrator</a>
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

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
  padding: 10px 20px;
}

</style>
