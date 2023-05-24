<script>
import { store } from '../data/store';
export default {
    name: 'BaseMain',
        
    props: ["negozio"]
    ,
    data() {
        return {
            store
        }
    },
    mounted() {
        // console.log("ooooo",this.store.carte)
    }
}
</script>

<template>

<main>
    <div v-if="store.loading == false" class="container my_bg mt-5">
        <div class="row p-3">
            <div v-for="mostri in store.carte" class="my_card mb-3">
                <img :src="mostri.card_images[0].image_url" alt="">
                <p class="text-light">{{mostri.name}}</p>
                <p class="text-light">{{mostri.race}}</p>
            </div>
            <!-- <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>nome</span>
                <span>razza</span>
            </div>
            <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>lollo</span>
                <span>razza</span>
            </div>
            <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>lollo</span>
                <span>razza</span>
            </div>
            <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>lollo</span>
                <span>razza</span>
            </div>
            <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>lollo</span>
                <span>razza</span>
            </div>
            <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>lollo</span>
                <span>razza</span>
            </div>
            <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>lollo</span>
                <span>razza</span>
            </div>
            <div class="my_card">
                <img src="https://images.ygoprodeck.com/images/cards/6983839.jpg" alt="">
                <span>lollo</span>
                <span>razza</span>
            </div> -->
        </div>
    </div>

    <div v-else class="container mt-5">
        <div class="row text-light justify-content-center fs-2">
            <div class="col text-center">
                loading
                <i class="my_icon fas fa-circle-notch"></i>
            </div>
        </div>
    </div>

</main>

</template>

<style lang="scss" scoped>
@use "../styles/partials/mixins" as *;

.my_bg{
    background-color: white;
}
.my_h1000{
    height: 1000px;
}
.my_card {
    background-color: $black;
    display: flex;
    flex-direction: column;
    text-align: center;
    width: calc(20% - 2rem);
    padding: 0;
    margin: 0 1rem;
    img{
        width: 100%;
    }
}
.my_icon{
    animation: rotation10 1s infinite linear;
}
@keyframes rotation10 {
    from {
        transform: rotate(0deg);
    }
    to {
        transform: rotate(360deg);
    }
}

</style>
