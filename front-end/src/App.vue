<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <div v-if="isLoggedIn">
      Sie sind eingelogt <button v-on:click="logout">Ausloggen</button>
    </div>
    <div v-else>
      <input type="text" v-model="username" placeholder="Username"><br>
      <input type="password" v-model="password" placeholder="Password" @keyup.enter="login"><br>
      <button @click="login">Login</button>
    </div>
    <hr>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      message: 'Hello Vue!',
      isLoggedIn: true,
      username: '',
      password: '',
    }
  },
  computed: {},
  methods: {
    login () {
      if (this.username === 'admin' && this.password === 'admin') {
        this.isLoggedIn = true
        this.username = ''
        this.password = ''
        console.log('Wir sind eingeloggt')
      } else {
        alert('Username/Passwort falsch')
        this.password = ''
      }
    },
    logout () {
      this.isLoggedIn = false
      console.log('Wir sind ausgeloggt')
    },
  },
  created () {}
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
