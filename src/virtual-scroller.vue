<template>
  <div class="demo">
    <!--
      items = list of items to display in scroller
      itemHeight = display height of items in px used to calc scroll height and position
      renderers = map of component definitions objects/names for each item type
        if not defined, scroller will use scoped slots
    -->
    <virtual-scroller
      class="scroller"
      :items="items"
      :renderers="renderers" 
      item-height="40"
      type-field="type"
      page-mode
    >
    </virtual-scroller>
  </div>
</template>

<script>
import Vue from 'vue';

import VueVirtualScroller from 'vue-virtual-scroller/dist/vue-virtual-scroller';
Vue.use(VueVirtualScroller);

// import { VirtualScroller } from 'vue-virtual-scroller/dist/vue-virtual-scroller';
// Vue.component('virtual-scroller', VirtualScroller);

// Data w/ type field
const items = new Array(10000).fill({
  type: 'letter',
  value: 'Derek is awesome'
});
// const items = [
//   { type: 'letter', value: 'A' },
//   { type: 'person', value: { name: 'Alan' } },
//   { type: 'person', value: { name: 'Alice' } },
// ];

import Letter from './Letter.vue';
import Item from './Item.vue';

// bind components to item type
const renderers = Object.freeze({
  letter: Letter,
  person: Item,
});

export default {
  data: () => ({
    items,
    renderers,
  }),
}
</script>

<style>
.scroller {
  margin: 0;
  padding: 0;
}

.scroller .item {
  height: 40px;
}
</style>