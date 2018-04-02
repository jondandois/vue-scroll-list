<template>
  <div class="button-card" v-bind:style="styleObject" v-on:click="buttonClick">
    <span class="label">{{thing.size}}</span>
  </div>
</template>

<script>
  export default {
    name: 'button-card',
    components: {},
    props: ['thing', 'selected_thing'],
    data () {
      return {
        selectedThing: this.selected_thing,
        styleObject: {
          fontSize: '20px',
          background: this.thing.color
        }
      }
    },
    methods: {
      buttonClick: function () {
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
  .button-card {
    cursor: pointer;
    background: #eaeaea;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100px;
    width: 100px;
    border-radius: 15px;
  }
  .label {
    background: white;
    border-radius: 10px;
    opacity: 0.75;
  }
</style>
