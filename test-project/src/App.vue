<template>
  <div id="app">
    <app-header @show-msg="fnn"></app-header>
    <app-sidebar :msg="value"></app-sidebar>
  </div>
</template>

<script>
import header from './components/header.vue';
import sidebar from './components/sidebar.vue';

export default {
  name: 'app',
  data () {
    return {
      value: ''
    }
  },
  methods: {
    fnn(val) {
      this.value = val;
    }
  },
  components: {
    'app-header': header,
    'app-sidebar': sidebar
  }
}
</script>

<style lang="scss">
* {
	margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
