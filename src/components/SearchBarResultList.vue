<template>
  <div class="flex flex-wrap gap-4">

    <SearchBarResultitem 
      v-for="(item, index) in items" 
      :key="index"
      @mouseover="showImage(index)"
      @mouseleave="hideIndex">
      
      <template #default>
        <div class="relative w-48 h-72 border border-gray-200 text-blue-400 flex justify-center items-center text-center">
          <p class="text-lg font-semibold">{{ item.title }}</p>
        </div>
        <!-- Affichage de l'image lors du survol -->
        <div v-if="hoveredIndex === index" class="absolute top-0 left-0 right-0 bottom-0 rounded-md  bg-opacity-60 flex justify-center items-center">
          <img :src="'/public/images/' + item.image"  class=" max-w-[250px] h-[300px] rounded-md transition-transform" />
        </div>
      </template>
      
    </SearchBarResultitem>

  </div>
</template>

<script>
import SearchBarResultitem from './SearchBarResultItem.vue';

export default {
  components: { SearchBarResultitem, },
  
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  
  data() {
    return {
      hoveredIndex: null, // Indicateur du film survolé
    };
  },
  methods: {
    showImage(index) {
      this.hoveredIndex = index; // Afficher l'image du film survolé
    },
    hideIndex() {
      this.hoveredIndex = null; // Cacher l'image lorsqu'on quitte le survol
    },
    getImagePath(item) {
      return new URL(`../assets/images/${item.image}`, import.meta.url).href;
    },
  },
};
</script>