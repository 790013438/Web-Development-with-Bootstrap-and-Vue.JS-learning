<template>
  <div>
    <header-component></header-component>
    <content-component></content-component>
    <footer-component></footer-component>
  </div>
</template>

<script>
import {ContentComponent, FooterComponent, HeaderComponent} from './main'
export default {
  components: {
    ContentComponent,
    FooterComponent,
    HeaderComponent
  }
}
</script>

<style scoped lang="sass">

</style>
