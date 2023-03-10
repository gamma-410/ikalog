<template>
  <div>
    <nav class="navbar navbar-light bg-light mb-5">
      <div class="container">
        <span class="navbar-brand mb-0 h1">
          <router-link to="/">
            <img alt="Vue logo" width="100" src="./assets/logo.svg" />
          </router-link>
        </span>
        <div>
          <router-link to="/index">Index</router-link>
        </div>
      </div>
    </nav>
    <div class="container">
      <router-view />
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

a {
  font-weight: bold;
  color: #2c3e50;
}

a.router-link-exact-active {
  color: #000000;
}

img {
  max-width: 100%;
}
</style>
