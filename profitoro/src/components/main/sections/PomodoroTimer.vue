<template>
  <div>
    <count-down-timer
      :time="time"></count-down-timer>
  </div>
</template>

<script>
import CountDownTimer from './timer/CountDownTimer'
export default {
  computed: {
    time () {
      return 14 * 60
    }
  },
  components: {
    CountDownTimer
  }
}
</script>

<style scoped lang="sass">

</style>
