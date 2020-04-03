<template>
  <div id="app">
    <div v-if="isLoggedIn">
      Sie sind eingelogt <button v-on:click="logout">Ausloggen</button>
    </div>
    <div v-else>
      <input type="text" v-model="username" placeholder="Username"><br>
      <input type="password" v-model="password" placeholder="Password" @keyup.enter="login"><br>
      <button @click="login">Login</button>
    </div>

    <h2>Fragen ({{numExcercises}}):</h2>
    <ul>
      <li v-for="(ex, index) of excercises" :key="index">
        <span v-if="ex.editing">
          <input
            v-model="ex.tempText"
            @keyup.enter="saveExcercise(ex)"
            @keyup.esc="cancelEditingExcercise(ex)"
          >
          <button @click="saveExcercise(ex)">save</button>
          <button @click="cancelEditingExcercise(ex)">cancel</button>
        </span>
        <span v-else>
          <strong>{{ex.text}}</strong>
          <button @click="editExcercise(ex)">edit</button>
          <button @click="deleteExcercise(ex)">delete</button>
        </span>
      </li>
      <li><button @click="addExcercise">+</button></li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      message: 'Hello Vue!',
      isLoggedIn: true,
      excercises: [],
      username: '',
      password: '',
    }
  },
  computed: {
    numExcercises () {
      return this.excercises.length
    },
  },
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
    addExcercise () {
      this.excercises.push({ text: '', editing: true, tempText: '' })
    },
    editExcercise (ex) {
      ex.editing = true
      ex.tempText = ex.text
    },
    saveExcercise (ex) {
      ex.editing = false
      ex.text = ex.tempText
      // Änderungen im localStorage abspeichern
      localStorage.setItem('excercises', JSON.stringify(this.excercises))
    },
    cancelEditingExcercise (ex) {
      ex.editing = false
    },
    deleteExcercise (ex) {
      const index = this.excercises.indexOf(ex)
      this.excercises.splice(index, 1)
      localStorage.setItem('excercises', JSON.stringify(this.excercises))
    },
  },
  created () {
    const excercises = JSON.parse(localStorage.getItem('excercises'))
    if (excercises !== null) {
      for (const ex of excercises) {
        console.log(ex)
        this.excercises.push(ex)
      }
    }
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
