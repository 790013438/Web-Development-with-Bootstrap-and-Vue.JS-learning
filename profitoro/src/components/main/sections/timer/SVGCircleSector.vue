<template>
  <div>
    <svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
      <circle r="100" cx="100" cy="100" fill="gray"></circle>
      <circle r="90" cx="100" cy="100" fill="lightgray"></circle>
      <path id="sector" fill="darkgray" opacity="0.6"
        :d="path"></path>
    </svg>
  </div>
</template>

<script>
function calcEndPoint (angle) {
  let x, y
  x = 100 - 100 * Math.sin(Math.PI * angle / 180)
  y = 100 - 100 * Math.cos(Math.PI * angle / 180)

  return {
    x, y
  }
}
function calcPath (angle) {
  let d
  let {x, y} = calcEndPoint(angle)
  if (angle <= 180) {
    d = `M100,100 L100, 0 A100,100 0 0,0 ${x}, ${y} z`
  } else {
    d = `M100,100 L100, 0 A100,100 0 0,0 100, 200 A100,100 0 0,0 ${x}, ${y} z`
  }
  return d
}

export default {
  props: ['angle', 'text'],
  computed: {
    path () {
      return calcPath(this.angle)
    }
  }
}
</script>

<style scoped lang="scss">
</style>
