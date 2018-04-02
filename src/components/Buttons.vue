<template>
  <div class="bordered grid">
    <ButtonCard v-for="thing in things"
      :key="thing.id" :thing="thing"
      :selected_thing="selected_thing"
      v-bind:class="{ selected: thing.id == selected_thing.id }"
    />
  </div>
</template>

<script>
  import ButtonCard from '@/components/ButtonCard.vue';

  export default {
    name: 'buttons',
    components: { ButtonCard },
    props: ['things', "selected_thing"],
    data () {
      return {
        selectedThing: this.selected_thing
      }
    }
  }
</script>

<style>
  .grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr;
    grid-gap: 1em;
  }
  .selected {
    box-shadow:inset -0.25em -0.25em red;
  }
</style>
