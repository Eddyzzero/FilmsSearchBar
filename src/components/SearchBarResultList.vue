<template>
    <div class=" mt-10">
    <SearchBarResultitem 
    class=" text-zinc-400"
    v-for="(item, index) in items" :key="index">
      <template
      class=" bg-gray-900 shadow-lg border-2 border-blue-950" 
      #default>{{ item }}
    </template>
    </SearchBarResultitem>
  </div>
</template>

<script>
import SearchBarResultitem from './SearchBarResultitem.vue';

export default {
  components: { SearchBarResultitem },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>