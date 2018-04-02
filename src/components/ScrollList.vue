<template>
  <div class="bordered scroll-vert">
    <ListCard
      v-for="thing in shuffled_things"
      :key="thing.id"
      :thing="thing"
      :selected_thing="selected_thing"
      v-bind:class="{ selected_list_card: thing.id == selected_thing.id }"
    />
  </div>
</template>

<script>
  import ListCard from '@/components/ListCard.vue'

  export default {
    name: 'scroll-list',
    components: { ListCard },
    props: ['things', 'selected_thing'],
    data () {
      return {
        shuffled_things: this.shuffleThings(this.things)
      }
    },
    methods: {
      shuffleThings: function (things) {
        let shuffled_things = [];
        things.map( (t) => {
          let colors = t.color.match(/\d{1,3}/g);
          let l2 = Math.sqrt(colors[0]**2, colors[1]**2, colors[2]**2)
          t.order = l2 * Math.random();
          shuffled_things.push(t)
        });
        return shuffled_things.sort( (a,b) => a.order - b.order );
      }
    }
  }
</script>

<style>

  .scroll-vert {
    overflow-y: auto;
    box-sizing: border-box;
  }

  .selected_list_card {
    box-shadow:inset 0em 0.75em red;
  }

</style>
