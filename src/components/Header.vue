<template>
  <header>
    <div id="top_bar">
      <img src="https://www.freepnglogos.com/uploads/spotify-logo-png/spotify-icon-marilyn-scott-0.png"/>
      <select v-model="genreFilter" @change="$emit('changedGenre', genreFilter)">
        <option value="">Choose a genre</option>
        <option v-for="(genre, index) in genres" :key="index" :value="genre">{{genre}}</option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: {
      genres: Array
    },
    data(){
      return{
        genreFilter: "",
      }
    }
}
</script>

<style lang="scss" scoped>

@import '@/styles/vars.scss';

header {
    height: 80px;
    width: 100%;
    background-color: $custom_grey;

    #top_bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 0 10px;

      img {
        height: 80px;
        padding: 10px;
      }

      select{
        height: 40px;
        border: none;
        border-radius: 50px;
        background-color: $custom_blue;
        color: white;
      }
    }

}

</style>
