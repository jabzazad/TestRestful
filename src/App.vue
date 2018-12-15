<template>
  <div id="app">
  <nav class="navbar navbar-light bg-light">
        <a class="navbar-brand">
            <img src="./image/iconplaystore.png" width="30" height="30" class="d-inline-block align-top" alt=""> Google
            Play
        </a>
        <router-link to="/" class="nav-item nav-link active">Home</router-link> 
        <router-link to="/product" class="nav-item nav-link active">Product</router-link>
        <router-link to="/about" class="nav-item nav-link active">about</router-link>  
        <form class="form-inline">
            <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
            <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
        </form>
    </nav>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
