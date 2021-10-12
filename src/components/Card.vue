<template>
    <div id="card">
        <div class="img_cont">
            <img :src="crd.poster" alt="">
        </div>
        <div class="txt_cont">
            <h1>{{crd.title}}</h1>
            <p>{{crd.author}}</p>
            <p>{{crd.year}}</p>
        </div>        
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: {
        crd: Object
    },
}
</script>

<style scoped lang="scss">

@import '@/styles/vars.scss';

    #card {
        width: 180px;
        margin-bottom: 50px;
        padding: 20px;
        height: 300px;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        flex-direction: column;
        background-color: $custom_grey;

        .img_cont {
            width: 140px;

            img {
                width: 100%;
            }
        }

        .txt_cont{
            text-align: center;
                        
            h1 {
                font-size: 18px;
                margin-bottom: 15px ;
            }

            p {
                color: grey;
            }
        }
    }
    

</style>