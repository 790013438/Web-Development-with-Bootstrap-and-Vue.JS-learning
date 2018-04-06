<template>
  <div v-if="animals.length > 0">
    <h2><span v-if="name">{{name}}! </span>Here's your Zoo</h2>
    <ol>
      <li v-for="animal in animals"
        :key="animal.id"><span class="animal" v-html="animalsCodes[animal]"></span></li>
    </ol>
  </div>
</template>

<script>
export default {
  props: ['animals', 'animalsCodes', 'name']
}
</script>
