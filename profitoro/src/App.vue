<template>
  <div id="app">
    <landing-page v-if="!user"></landing-page>
    <main-content v-if="user"></main-content>
  </div>
</template>

<script>
import LandingPage from './components/LandingPage'
import MainContent from './components/MainContent'
import {mapActions, mapState} from 'vuex'
export default {
  name: 'App',
  components: {
    LandingPage,
    MainContent
  },
  computed: {
    ...mapState(['user'])
  },
  methods: {
    ...mapActions(['bindStatistics', 'bindConfig', 'bindAuth'])
  },
  created () {
    this.bindAuth()
    this.bindConfig()
    this.bindStatistics()
  }
}
</script>

<style lang="scss" scoped>
.col- {
  &1,&2,&3,&4,&6,&9 {
    border: 1px solid gray;
  }
}
.row {
  margin: 1em;
  border: 1px solid black;
  padding: 6px 4px;
}
</style>
