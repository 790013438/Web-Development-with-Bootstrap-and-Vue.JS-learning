<template>
  <li>
    <span class="animal" v-html="animal" @click="toggleDescription"></span>
    <span v-show="showDescription">{{description}}</span>
  </li>
</template>

<script>
export default {
  props: ['animal', 'description'],
  data () {
    return {
      showDescription: false
    }
  },
  methods: {
    toggleDescription () {
      this.showDescription = !this.showDescription
    }
  }
}
</script>

<style>
.animal {
  font-size: 4em;
  cursor: pointer
}
</style>
