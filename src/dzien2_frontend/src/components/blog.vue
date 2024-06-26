<template>
    <div>
        <h2 class="text-blue-600">Wpisy na bloga:</h2>
        <div class="w-100 flex flex-row-reverse">
            <button @click="pobierzWpisy">refresh</button>
        </div>
        <div v-for="wpis in wpisy">
            <p>{{ wpis }}</p>
        </div>
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpisy">dodaj</button>
    </div>
</template>

<script>
import { dzien2_backend } from 'declarations/dzien2_backend/index';

export default{
    data(){
        return{
            wpisy:[],
            nowyBlog: ""
        }
    },
    methods:{
        async dodajWpisy(){
            this.wpisy = await dzien2_backend.dodaj_wpis(this.nowyBlog);
        },
        async pobierzWpisy(){
            this.wpisy = await dzien2_backend.odczytaj_wpisy();
        }
    },
    async mounted(){
        this.pobierzWpisy()
    }
}
</script>