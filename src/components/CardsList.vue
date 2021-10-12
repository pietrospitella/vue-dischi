<template>
    <div id="main_cont">
        <div id="cards_cont">
            <div id="card" v-for="(card, index) in filteredCards" :key="index">
                <Card :crd="card" />
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue';

export default {
    name: 'CardsList',
    components: {
        Card,
    },
    props: {
        selectedGenre: String
    },
    computed: {
        filteredCards(){
            if (this.selectedGenre === ""){
                return this.cards;
            }
            else {
                return this.cards.filter((item)=> item.genre === this.selectedGenre);
            }
        }
    },
    data() {
        return{
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        cards: [],
        genres: []
        }
    },
    created() {
        this.getCards();
    },
    methods: {
        getCards(){
        axios
            .get(this.apiUrl)
            .then((res) => {
                this.cards = res.data.response;

                this.cards.forEach((crd) => {
                    if (!this.genres.includes(crd.genre)) {
                        this.genres.push(crd.genre);
                    }
                });
                this.$emit("genresReady", this.genres);
            })
        },

    }
}
</script>

<style scoped lang="scss">

#main_cont{
    width: 100%;
    height: calc(100vh - 80px);
    display: flex;
    justify-content: center;
    align-items: center;


    #cards_cont{
        width: 80%;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;        
    }
}
    


</style>