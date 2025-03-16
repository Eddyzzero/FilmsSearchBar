<template>
  <div
    id="app"
    class="bg-gradient-to-r from-gray-800 via-blue-700 to-gray-900 text-cyan-800 flex-col justify-items-center p-20 space-y-3"
  >
    <h1 class="text-white text-4xl font-bold uppercase">Application</h1>
    <h2 class="pb-5 text-lg font-semibold text-zinc-100">
      Films à regarder une fois dans la vie
    </h2>
    <SearchBar v-model="searchQuery" />
    <hr class="h-1 w-full" />
    <SearchBarResultList :items="filteredItems" />
  </div>
  <hr class="h-1 w-full" />
  <div
    class="flex flex-col text-center justify-center p-4 text-zinc-100 opacity-50"
  >
    <p>
      Inspired by :
      <a
        target="_blank"
        class="hover:text-gray-500"
        href="https://01streaming.tv/"
      >
        1streaming</a
      >
    </p>
    <p>Jhon Florez 2025</p>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar.vue";
import SearchBarResultitem from "./components/SearchBarResultItem.vue";
import SearchBarResultList from "./components/SearchBarResultList.vue";

export default {
  components: {
    SearchBar,
    SearchBarResultitem,
    SearchBarResultList,
  },
  data() {
    return {
      hoveredIndex: null, // pour savoir quel élément est survolé
      searchQuery: "",
      items: [
        { title: "Oppenheimer (2023)", image: "Oppenheimer (2023).jpg" },
        { title: "Barbie (2023)", image: "barbie 2023.jpg" },
        {
          title: "Everything Everywhere All at Once (2022)",
          image: "Everything Everywhere All at Once (2022).jpg",
        },
        {
          title: "Spider-Man: Across the Spider-Verse (2023)",
          image: "spiderman.jpg",
        },
        { title: "The Northman (2022)", image: "The Northman (2022).jpg" },
        {
          title: "The Unbearable Weight of Massive Talent (2022)",
          image: "The Unbearable Weight of Massive Talent (2022).jpg",
        },
        { title: "The Whale (2022)", image: "The Whale (2022).jpg" },
        {
          title: "Top Gun: Maverick (2022)",
          image: "Top Gun Maverick (2022).jpg",
        },
        {
          title: "Where the Crawdads Sing (2022)",
          image: "Where the Crawdads Sing (2022).jpg",
        },
        {
          title: "The Banshees of Inisherin (2022)",
          image: "The Banshees of Inisherin (2022).jpg",
        },
        { title: "The Batman (2022)", image: "The Batman (2022).jpg" },
        {
          title: "The Black Phone (2022)",
          image: "The Black Phone (2022).jpg",
        },
        { title: "The Bubble (2022)", image: "The Bubble (2022).jpg" },
        { title: "The Contractor (2022)", image: "The Contractor (2022).jpg" },
        { title: "The Flash (2023)", image: "The Flash (2022).jpg" },
        { title: "Dune: Part One (2021)", image: "dunePartieUne.jpg" },
        {
          title: "John Wick: Chapter 4 (2023)",
          image: "johnWick4.jpg",
        },
        { title: "Parasite (2019)", image: "Parasite (2019).jpg" },
        { title: "Joker (2019)", image: "Joker (2019).jpg" },
        { title: "Interstellar (2014)", image: "Interstellar (2014).jpg" },
        { title: "Inception (2010)", image: "Inception (2010).jpg" },
        {
          title: "The Dark Knight (2008)",
          image: "The Dark Knight (2008).jpg",
        },
        {
          title: "The Lord of the Rings: The Fellowship of the Ring (2001)",
          image: "LOTR Fellowship (2001).jpg",
        },
        {
          title: "The Lord of the Rings: The Two Towers (2002)",
          image: "LOTR Two Towers (2002).jpg",
        },
        {
          title: "The Lord of the Rings: The Return of the King (2003)",
          image: "LOTR Return (2003).jpg",
        },
        { title: "The Matrix (1999)", image: "The Matrix (1999).jpg" },
        { title: "Pulp Fiction (1994)", image: "Pulp Fiction (1994).jpg" },
        { title: "Forrest Gump (1994)", image: "Forrest Gump (1994).jpg" },
        { title: "Fight Club (1999)", image: "Fight Club (1999).jpg" },
        {
          title: "The Shawshank Redemption (1994)",
          image: "The Shawshank Redemption (1994).jpg",
        },
        { title: "The Godfather (1972)", image: "The Godfather (1972).jpg" },
        {
          title: "The Godfather Part II (1974)",
          image: "The Godfather Part II (1974).jpg",
        },
        {
          title: "Schindler's List (1993)",
          image: "Schindler's List (1993).jpg",
        },
        { title: "Goodfellas (1990)", image: "Goodfellas (1990).jpg" },
        {
          title: "The Silence of the Lambs (1991)",
          image: "The Silence of the Lambs (1991).jpg",
        },
        { title: "Se7en (1995)", image: "Se7en (1995).jpg" },
        {
          title: "Saving Private Ryan (1998)",
          image: "Saving Private Ryan (1998).jpg",
        },
        { title: "Titanic (1997)", image: "Titanic (1997).jpg" },
        { title: "The Green Mile (1999)", image: "The Green Mile (1999).jpg" },
        { title: "The Pianist (2002)", image: "The Pianist (2002).jpg" },
        { title: "Gladiator (2000)", image: "Gladiator (2000).jpg" },
        { title: "The Departed (2006)", image: "The Departed (2006).jpg" },
        {
          title: "No Country for Old Men (2007)",
          image: "No Country for Old Men (2007).jpg",
        },
        {
          title: "Django Unchained (2012)",
          image: "Django Unchained (2012).jpg",
        },
        { title: "Whiplash (2014)", image: "Whiplash (2014).jpg" },
        {
          title: "Mad Max: Fury Road (2015)",
          image: "Mad Max Fury Road (2015).jpg",
        },
        { title: "La La Land (2016)", image: "La La Land (2016).jpg" },
        { title: "Get Out (2017)", image: "Get Out (2017).jpg" },
        {
          title: "Blade Runner 2049 (2017)",
          image: "Blade Runner 2049 (2017).jpg",
        },
        { title: "Coco (2017)", image: "Coco (2017).jpg" },
        {
          title: "Avengers: Endgame (2019)",
          image: "Avengers Endgame (2019).jpg",
        },
        { title: "The Revenant (2015)", image: "The Revenant (2015).jpg" },
        { title: "Logan (2017)", image: "Logan (2017).jpg" },
        { title: "Jaws (1975)", image: "Jaws (1975).jpg" },
        { title: "The Shining (1980)", image: "The Shining (1980).jpg" },
        {
          title: "A Clockwork Orange (1971)",
          image: "A Clockwork Orange (1971).jpg",
        },
        { title: "The Exorcist (1973)", image: "The Exorcist (1973).jpg" },
        { title: "E.T. the Extra-Terrestrial (1982)", image: "ET (1982).jpg" },
        {
          title: "Indiana Jones: Raiders of the Lost Ark (1981)",
          image: "Indiana Jones (1981).jpg",
        },
        {
          title: "Back to the Future (1985)",
          image: "Back to the Future (1985).jpg",
        },
        {
          title: "The Grand Budapest Hotel (2014)",
          image: "The Grand Budapest Hotel (2014).jpg",
        },
      ],
    };
  },

  methods: {
    showImage(index) {
      this.hoveredIndex = index; ///affiche l'image survolée
    },

    hideIndex() {
      this.hoveredIndex = null; //cache l'image survolée
    },
  },
  computed: {
    filteredItems() {
      return this.items.filter((item) =>
        item.title.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
};
</script>
