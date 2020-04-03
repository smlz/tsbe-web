<template>
<div>
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
    {{collectionId}}
</div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      excercises: [],
    }
  },
  computed: {
    numExcercises () {
      return this.excercises.length
    },
    collectionId () {
      if (this.$route.params.id) {
        return parseInt(this.$route.params.id)
      } else {
        return ''
      }
    }
  },
  methods: {
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
    console.log('in Edit')
    const excercises = JSON.parse(localStorage.getItem('excercises'))
    if (excercises !== null) {
      for (const ex of excercises) {
        this.excercises.push(ex)
      }
    }
    console.log(this.$route.params)
  }
}
</script>
