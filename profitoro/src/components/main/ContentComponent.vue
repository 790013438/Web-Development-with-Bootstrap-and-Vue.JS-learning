<template>
  <div class="container">
    <settings></settings>
    <pomodoro-timer></pomodoro-timer>
  </div>
</template>

<script>
import {PomodoroTimer, Settings} from './sections'
export default {
  components: {
    PomodoroTimer,
    Settings
  }
}
</script>

<style scoped lang="sass">

</style>
