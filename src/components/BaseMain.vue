<script>
import { store } from '../data/store';
import axios from 'axios';

export default {
    name: 'BaseMain',

    data() {
        return {
            store,
            carte: null,
            // opzioniSelezionabili: [
            //     "Effect Monster",
            //     "Flip Effect Monster",
            //     "Flip Tuner Effect Monster",
            //     "Gemini Monster",
            //     "Normal Monster",
            //     "Normal Tuner Monster",
            //     "Pendulum Effect Monster",
            //     "Pendulum Effect Ritual Monster",
            //     "Pendulum Flip Effect Monster",
            //     "Pendulum Normal Monster",
            //     "Pendulum Tuner Effect Monster",
            //     "Ritual Effect Monster",
            //     "Ritual Monster",
            //     "Spell Card",
            //     "Spirit Monster",
            //     "Toon Monster",
            //     "Trap Card",
            //     "Tuner Monster",
            //     "Union Effect Monster",
            // ],
        }
    },
    methods: {
        recuperaNuoviDati() {
            console.log(this.carte);

            // let indirizzo = this.store.apiUrl;

            let indirizzo = this.store.apiUrl + "&archetype=" + this.carte;

            console.log(indirizzo);

            this.getCards(indirizzo);

        },
        getCards(indirizzo) {

            this.store.loading = true

            axios.get(indirizzo).then(result => {
                console.log("risultato:", result);
                this.store.carte = result.data.data;
                this.store.loading = false;
            });
        }
    },
    mounted() {

    

    // console.log("Store:",this.store)

    axios.get(this.store.selectUrl).then(result => {
        this.store.archetipi = result.data
        console.log("archetipi:", this.store.archetipi)
    });

    },
    computed: {
        
    }
}
</script>

<template>

<main>


    <!-- <div class="container">
        <button @click="getType">DEBUG</button>
    </div> -->
    <div class="container p-0 mt-4">
        <select @change="recuperaNuoviDati()" v-model="carte">
            <option v-for="opzioni in this.store.archetipi" >{{ opzioni.archetype_name }}</option>
        </select>
    </div>

    <div v-if="store.loading == false" class="container p-0 mt-5">



        <div class="row p-3 my_bg">
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
