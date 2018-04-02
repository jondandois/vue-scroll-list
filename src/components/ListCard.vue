<template>
  <div class="list-card" v-bind:style="styleObject" v-on:click="cardClick">
    <span class="label">{{thing.size}}</span>
  </div>
</template>

<script>
  export default {
    name: 'list-card',
    components: {},
    props: ['thing', 'selected_thing'],
    data () {
      return {
        selectedThing: this.selected_thing,
        styleObject: {
          fontSize: '20px',
          background: this.thing.color,
          height: ((this.thing.size / 2.) <= 5 ? (this.thing.size / 2.) : 5) + 'em'
        }
      }
    },
    methods: {
      cardClick: function () {
        if (this.selectedThing.id == this.thing.id) {
          this.selectedThing.id = null;
        } else {
          this.selectedThing.id = this.thing.id
        }
      }
    }
  }
</script>

<style>
  .list-card {
    background: #eaeaea;
    max-width: 90%;
    border-radius: 5px;
    margin: 1em;
    padding: 1em;
  }
  .label {
    background: white;
    border-radius: 10px;
    opacity: 0.75;
  }
</style>
