<template>
  <div>
    <svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
      <circle r="100" cx="100" cy="100" fill="gray"></circle>
      <circle r="90" cx="100" cy="100" fill="lightgray"></circle>
      <path id="sector" fill="darkgray" opacity="0.6" d="M100,100 V0 L100,0 A100,100 0 0, 0 0, 100 z"></path>
    </svg>
  </div>
</template>

<script>
export default {
  props: ['angle', 'text']
}
</script>

<style scoped lang="scss">
</style>
