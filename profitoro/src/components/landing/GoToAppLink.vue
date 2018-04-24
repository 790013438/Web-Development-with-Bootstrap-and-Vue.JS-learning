<template>
  <div>
    <button
      @click="authenticateAnonymous">
      START WITHOUT REGISTRATION
    </button>
  </div>
</template>

<script>
import {mapActions} from 'vuex'

export default {
  methods: {
    ...mapActions(['authenticateAnonymous'])
  }
}
</script>

<style scoped lang="sass">

</style>
