<template>
  <div id="app">
    <h1>Hello, {{name}}! Let's learn Vue.js </h1>
    <img width="100%"
      :src="name ? gladSrc : sadSrc">
    <hr />
    <introduction @nameChanged="onNameChanged"
      :initialName="name"></introduction>
    <hr />
    <h2>{{name}}! Select your animals</h2>
    <select v-model="animalsForZoo" multiple="multiple" name="animals" id="animals">
      <option v-for="animal in animals"
              :value="animal"
              :key="animal.id">{{animal}}</option>
    </select>
    <hr />
    <zoo
      :animals="animalsForZoo"></zoo>
  </div>
</template>

<script>
import Zoo from './components/Zoo'
import Introduction from './components/Introduction'
export default {
  name: 'app',
  components: {
    Zoo,
    Introduction
  },
  data () {
    return {
      animalsForZoo: []
    }
  },
  computed: {
    name () {
      return this.$store.state.name
    },
    animals () {
      return this.$store.state.animals
    },
    animalsCodes () {
      return this.$store.state.animalsCodes
    },
    sadSrc () {
      return this.$store.state.sadSrc
    },
    gladSrc () {
      return this.$store.state.gladSrc
    }
  },
  methods: {
    onNameChanged (newName) {
      this.name = newName
    }
  }
}
</script>

<style>
#app {
  margin-top: 60px;
  width: 60%;
  margin: 20px auto auto auto;
}
input {
  padding-left: 10px;
}
.animal {
  font-size: 4em;
}
.red {
  color: red;
}
.green {
  color: green;
}
</style>
