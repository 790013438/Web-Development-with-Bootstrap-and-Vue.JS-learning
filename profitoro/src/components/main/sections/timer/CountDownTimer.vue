<template>
  <div class="container text-center">
    <div class="row justify-content-center">
      <svg-circle-sector class="col-sm-12 col-md-8 col-lg-6 col-xl-4"
        :angle="angle"
        :text="'Hello'"></svg-circle-sector>
    </div>
    <div class="controls">
      <div class="btn-group" role="group">
        <button @click="start" type="button" class="btn btn-link">Start</button>
        <button @click="pause" type="button" class="btn btn-link">Pause</button>
        <button @click="stop" type="button" class="btn btn-link">Stop</button>
      </div>
    </div>
  </div>
</template>

<script>
import SvgCircleSector from './SvgCircleSector'

export default {
  props: ['time'],
  data () {
    return {
      timestamp: this.time
    }
  },
  computed: {
    angle () {
      return 360 - (360 / this.time * this.timestamp)
    }
  },
  components: {
    SvgCircleSector
  },
  methods: {
    start () {},
    pause () {},
    stop () {}
  }
}
</script>

<style scoped lang="scss">

</style>
