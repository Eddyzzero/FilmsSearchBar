<template>
    <div id="app"
        class="bg-gradient-to-r from-gray-800 via-blue-700 to-gray-900 text-cyan-800 flex-col justify-items-center p-20 space-y-3">
        <h1 class=" text-white text-4xl font-bold uppercase">Application</h1>
        <h2 class=" pb-5 text-lg font-semibold text-zinc-100">Films à regarder une fois dans la vie</h2>
        <SearchBar v-model="searchQuery" />
        <hr class=" h-1 w-full">
        <SearchBarResultList :items="filteredItems"/>
    </div>
    <hr class=" h-1 w-full">
    <div class="flex flex-col text-center justify-center p-4 text-zinc-100 opacity-50">
        <p> Inspired by :
            <a target="_blank" class=" hover:text-gray-500" href="https://01streaming.tv/"> 1streaming</a>
        </p>
        <p> Jhon Florez 2025</p>
    </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue"
import SearchBarResultitem from "./components/SearchBarResultItem.vue"
import SearchBarResultList from "./components/SearchBarResultList.vue"

export default {
    components: {
        SearchBar,
        SearchBarResultitem,
        SearchBarResultList,
    },
    data() {
        return {
            hoveredIndex:null, // pour savoir quel élément est survolé
            searchQuery: "",
            items: [ 
                { title:"Oppenheimer (2023)", image: "Oppenheimer (2023).jpg" },
                { title:"Barbie (2023)", image: "barbie 2023.jpg" },
                { title:"Everything Everywhere All at Once (2022)", image: "Everything Everywhere All at Once (2022).jpg" },
                { title:"Spider-Man: Across the Spider-Verse (2023)", image: "spiderman.jpg" },
                { title:"The Northman (2022)", image: "The Northman (2022).jpg" },
                { title:"The Unbearable Weight of Massive Talent (2022)", image: "The Unbearable Weight of Massive Talent (2022).jpg" },
                { title:"The Whale (2022)", image: "The Whale (2022).jpg" },
                { title:"Top Gun: Maverick (2022)", image: "Top Gun Maverick (2022).jpg" },
                { title:"Where the Crawdads Sing (2022)", image: "Where the Crawdads Sing (2022).jpg" },
                { title:"The Banshees of Inisherin (2022)", image: "The Banshees of Inisherin (2022).jpg" },
                { title:"The Batman (2022)", image: "The Batman (2022).jpg" },
                { title:"The Black Phone (2022)", image: "The Black Phone (2022).jpg" },
                { title:"The Bubble (2022)", image: "The Bubble (2022).jpg" },
                { title:"The Contractor (2022)", image: "The Contractor (2022).jpg" },
                { title:"The Flash (2022)", image: "The Flash (2022).jpg" },
            ]
        }
    },

    methods: {
        showImage(index) {
            this.hoveredIndex = index; ///affiche l'image survolée
        },

        hideIndex() {
            this.hoveredIndex = null; //cache l'image survolée
        }
    },
    computed: {
        filteredItems() {
            return this.items.filter((item) =>
                item.title.toLowerCase().includes(this.searchQuery.toLowerCase()),
            );
        }
    }
}
</script>