<template>
<div 
id="app"
class="bg-gradient-to-r from-gray-800 via-blue-700 to-gray-900 text-cyan-800 flex-col justify-items-center p-20 space-y-3">
    <h1 class=" text-white text-4xl font-bold uppercase">Application</h1>
    <h2 class=" pb-5 text-lg font-semibold text-zinc-100">Films à regarder une fois dans la vie</h2>
    <SearchBar  v-model="searchQuery" />
    <hr class=" h-1 w-full">
    <SearchBarResultList :items="filtereditems" />
</div>
<hr class=" h-1 w-full">
<div class="flex flex-col text-center justify-center p-4 text-zinc-100">
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
            searchQuery: "",
            items: [
            "Oppenheimer (2023)",
            "Barbie (2023)",
            "Everything Everywhere All at Once (2022)",
            "Spider-Man: Across the Spider-Verse (2023)",
            "The Power of the Dog (2021)",
            "Dune (2021)",
            "Nomadland (2020)",
            "Parasite (2019)",
            "The Irishman (2019)",
            "Roma (2018)",
            "Black Panther (2018)",
            "Get Out (2017)",
            "La La Land (2016)",
            "Mad Max: Fury Road (2015)",
            "Spider-Man: No Way Home (2021)",
            "Joker (2019)",
            "1917 (2019)",
            "Coda (2021)",
            "The Green Knight (2021)",
            "Licorice Pizza (2021)",
            "Drive My Car (2021)",
            "The French Dispatch (2021)",
            "The Lost Daughter (2021)",
            "A Star Is Born (2018)",
            "Moonlight (2016)",
            "Arrival (2016)",
            "Whiplash (2014)",
            "The Grand Budapest Hotel (2014)",
            "Poor Things (2023)",
            "The Whale (2022)",
            "Top Gun: Maverick (2022)",
            "Belfast (2021)",
            "The Father (2020)",
            "Soul (2020)",
            "Once Upon a Time in Hollywood (2019)",
            "The Favourite (2018)",
            "Three Billboards Outside Ebbing, Missouri (2017)",
            "Dunkirk (2017)",
            "Manchester by the Sea (2016)",
            "Birdman (2014)",
            "All Quiet on the Western Front (2022)",
            "The Banshees of Inisherin (2022)",
            "Don't Look Up (2021)",
            "Minari (2020)",
            "Marriage Story (2019)",
            "A Quiet Place (2018)",
            "Lady Bird (2017)",
            "Moonlight (2016)",
            "Spotlight (2015)",
            "Boyhood (2014)",
            "The Menu (2022)",
            "Elvis (2022)",
            "King Richard (2021)",
            "Sound of Metal (2020)",
            "Jojo Rabbit (2019)",
            "BlacKkKlansman (2018)",
            "The Shape of Water (2017)",
            "Hidden Figures (2016)",
            "Room (2015)",
            "The Theory of Everything (2014)",
            "Killers of the Flower Moon (2023)",
            "The Batman (2022)",
            "West Side Story (2021)",
            "Tenet (2020)",
            "Ford v Ferrari (2019)",
            "Bohemian Rhapsody (2018)",
            "Blade Runner 2049 (2017)",
            "Hell or High Water (2016)",
            "Inside Out (2015)",
            "Interstellar (2014)",
            "The Zone of Interest (2023)",
            "Tar (2022)",
            "The Tragedy of Macbeth (2021)",
            "Mank (2020)",
            "Little Women (2019)",
            "First Reformed (2018)",
            "Phantom Thread (2017)",
            "Silence (2016)",
            "Bridge of Spies (2015)",
            "Selma (2014)",
            "Anatomy of a Fall (2023)",
            "The Fabelmans (2022)",
            "Nightmare Alley (2021)",
            "Promising Young Woman (2020)",
            "The Two Popes (2019)",
            "First Man (2018)",
            "Call Me by Your Name (2017)",
            "Hacksaw Ridge (2016)",
            "Carol (2015)",
            "Gone Girl (2014)",
            "Past Lives (2023)",
            "Women Talking (2022)",
            "Being the Ricardos (2021)",
            "One Night in Miami (2020)",
            "The Lighthouse (2019)",
            "If Beale Street Could Talk (2018)",
            "The Florida Project (2017)",
            "Nocturnal Animals (2016)",
            "Ex Machina (2015)",
            "Nightcrawler (2014)",
            "Saltburn (2023)",
            "Triangle of Sadness (2022)",
            "C'mon C'mon (2021)",
            "Da 5 Bloods (2020)",
            "Knives Out (2019)",
            "Hereditary (2018)",
            "The Big Sick (2017)",
            "The Witch (2015)",
            "Wild (2014)",
            "The Wolf of Wall Street (2014)"
            ]
        }
    }, 
    computed: {
        filtereditems() {
            return this.items.filter((item) => 
            item.toLowerCase().includes(this.searchQuery.toLowerCase())
        );
        }
    }
}
</script>