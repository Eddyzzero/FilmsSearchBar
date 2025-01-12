<template>
    <div class="flex flex-wrap space-x-4">
    <SearchBarResultitem 
    v-for="(item, index) in items" :key="index">
      <template
      #default>{{ item }}
    </template>
    </SearchBarResultitem>
  </div>
</template>

<script>
import SearchBarResultitem from './SearchBarResultItem.vue';

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