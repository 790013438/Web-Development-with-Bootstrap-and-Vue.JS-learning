<template>
  <div id="app">
    <h1>Welcome to Profitoro</h1>
    <landing-page></landing-page>
    <main-content></main-content>
    <div class="row">
      <div class="col-6">Column 1</div>
      <div class="col-3">Column 2</div>
      <div class="col-2">Column 3</div>
      <div class="col-1">Column 4</div>
    </div>
    <div class="row">
      <div class="col-6">Column 1</div>
      <div class="col-2 offset-4">Column 2</div>
    </div>
    <div class="row">
      <div class="col-3 push-9">Column 1</div>
      <div class="col-9 pull-3">Column 2</div>
    </div>
    <div class="row">
      <div class="col-sm-12 col-md-8">Column 1</div>
      <div class="col-sm-12 col-md-4">Column 2</div>
    </div>
  </div>
</template>

<script>
import LandingPage from './components/LandingPage'
import MainContent from './components/MainContent'
export default {
  name: 'App',
  components: {
    LandingPage,
    MainContent
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
