<template>
  <div id="app">
    <Header :genres="genresList" @changedGenre="startSearch"/>
    <CardsList :selectedGenre="genreToSearch" @genresReady="getGenresList"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import CardsList from './components/CardsList.vue';

export default {
  name: 'App',
  components: {
    Header,
    CardsList
  },
  data(){
    return{
      genresList: [],
      genreToSearch: "",
    }
  },
  methods: {
    getGenresList(allGenres){
      this.genresList = allGenres;
    },
    startSearch(genreToSearch){
      this.genreToSearch = genreToSearch;
    }
  }
  
}
</script>

<style lang="scss">
@import 'styles/generals.scss';
@import 'styles/vars.scss';


</style>
