<template>
  <div id="app">
    <Dollar></Dollar>
    <euro></euro>
    <bitcoin></bitcoin>
  </div>
</template>

<script>
    import Dollar from './Dollar.vue'
    import Euro from './Euro.vue'
    import Bitcoin from './Bitcoin.vue'
    export default {
        components: {
            Dollar, Euro, Bitcoin
        }
    }
</script>
<style>
  body {
    margin-top: 50px
  }
</style>