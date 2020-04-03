<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <p v-for="id of [1,2,3]" :key="id">
      <router-link  :to="{name: 'Edit', params: {id: id}}">
        Edit collection {{id}}
      </router-link>
    </p>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
  }
}
</script>
