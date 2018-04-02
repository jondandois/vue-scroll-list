<template>
  <div id="app" class="wrapper">
    <Tools class="full-width"/>
    <ScrollList :things="things" :selected_thing="selected_thing"/>
    <Buttons :things="things" :selected_thing="selected_thing"/>
  </div>
</template>

<script>
  import Tools from '@/components/Tools.vue'
  import Buttons from '@/components/Buttons.vue'
  import ScrollList from '@/components/ScrollList.vue'

  export default {
    name: 'app',
    components: {
      Tools,
      Buttons,
      ScrollList
    },
    data () {
      return {
        things: this.makeThings(),
        selected_thing: {
          id: null
        }
      }
    },
    methods: {
      makeThings: function () {
        let n_things = 16;
        let things = [];
        for (var i = 0; i < n_things; i++) {
          let thing = { id: i }
          thing.color = this.randomColor();
          thing.size = this.randomVal(50);
          things.push(thing)
        }
        return things;
      },
      randomVal: function (max) {
        return Math.floor(Math.random()*max);
      },
      randomColor: function () {
        return `rgb(${this.randomVal(255)}, ${this.randomVal(255)}, ${this.randomVal(255)})`;
      }
    }
  }
</script>

<style>
  .wrapper {
    display: grid;
    grid-template-rows: 2em 30em;
    grid-template-columns: 1fr 1fr;
  }

  .full-width {
    grid-column-start: 1;
    grid-column-end: 3;
  }

  .bordered {
    border: 1px solid gray;
  }
</style>
