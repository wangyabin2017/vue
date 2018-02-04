<template>
  <div class="dom">
      {{ hello }}
  </div>
</template>
<script>
export default {
  data () {
    return {
      hello: 'i am component a'
    }
  }
}
</script>

<style>
.dom {
    color: blue
}
</style>
