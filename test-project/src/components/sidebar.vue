<template>
  <div id="sidebar">
    {{ msg }}
  </div>
</template>

<script>
  export default {
    props: {
      msg: {
        type: String,
        default: ''
      }
    },
    data () {
      return {

      }
    }
  }
</script>

<style lang="scss">

</style>