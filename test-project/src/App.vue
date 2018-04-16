<template>
  <div id="app">
    <app-header @show-msg="fnn"></app-header>
    <app-sidebar :msg="value"></app-sidebar>
    <app-main @show-products="fnn2" @show-block="show = !show"></app-main>
    <app-products :prods="prodForShow" :block="show"></app-products>
  </div>
</template>

<script>
import header from './components/header.vue';
import sidebar from './components/sidebar.vue';
import main from './components/main.vue';
import products from './components/products.vue';

export default {
  name: 'app',
  data () {
    return {
      value: '',
      prodForShow: [],
      show: false
    }
  },
  methods: {
    fnn(val) {
      this.value = val;
    },
    fnn2(productsForShow) {
      this.prodForShow = productsForShow;
    }
  },
  components: {
    'app-header': header,
    'app-sidebar': sidebar,
    'app-main': main,
    'app-products': products
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
