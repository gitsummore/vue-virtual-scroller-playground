<template>
  <div id="app">
    <button @click="show = !show">Toggle</button>
    <label>
      <input type="checkbox" v-model="isVisible" disabled/> Is visible?
    </label>
    <div ref="test" v-show="show" v-observe-visibility="visibilityChanged">Hello world!</div>
  </div>
</template>

<script>
import Vue from 'vue';

import VueObserveVisibility from 'vue-observe-visibility/dist/vue-observe-visibility';
Vue.use(VueObserveVisibility);

// import { ObserveVisibility } from 'vue-observe-visibility/dist/vue-observe-visibility';
// Vue.directive('observe-visibility', ObserveVisibility);

export default {
  name: 'app',
  data () {
    return {
      show: true,
      isVisible: true
    }
  },
  methods: {
    visibilityChanged: function (isVisible, entry) {
      this.isVisible = isVisible
      console.log(entry)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
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
