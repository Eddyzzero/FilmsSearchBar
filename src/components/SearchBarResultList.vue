<template>
    <ul>
        <SearchBarResultItem
        v-for="(item, index) in items"
        :key="index"
        :content="item"
        />
    </ul>
</template>

<script>
import SearchBarResultItem from './SearchBarResultItem.vue';

export default {
    props: {
        items: {
            type: Array, 
            required: true,
        },
    },
    components: {
        SearchBarResultItem,
    }
}
</script>