<template>
  <img alt="Vue logo" src="./assets/geodelogo-white.png">
  <div id = title>Create User  </div>
  <CreateUser />
</template>

<script>
import CreateUser from './components/CreateUser.vue'

export default {
  name: 'App',
  components: {
    CreateUser
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
