<template>
  <div id="app" class="h-full w-full bg-blue-100">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link :to="{ name: 'conditional-rendering' }">
        Conditional Rendering
      </router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
