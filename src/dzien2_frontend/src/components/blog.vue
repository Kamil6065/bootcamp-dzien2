<template>
    <div>
        <h2 class="text-blue-600">Wpisy na bloga</h2>
        <div class="w-100 flex flex-row-reverse">
        <button @click="pobierzWpisy" class="bg-blue-600 rounded text-white p-4">odśwież</button>
    </div>
    <div class="grid mx-6 gap-4 my-4">
        <div v-for="wpis in wpisy" class="drop-shadow-xl bg-stone-300 p-4">
            <p>{{ wpis }}</p>
        </div>
    </div>

        <input v-model="nowyBlog" type="text" class="border-2 border-blue-600 p-4">
        <button @click="dodajWpisy" class="g-blue-600 rounded text-white p-4">dodaj</button>
    </div>
</template>

<script>
import { dzien2_backend } from 'declarations/dzien2_backend/index';
export default {
data(){
    return {
            wpisy: [],
            nowyBlog: ""
        }
    },
    methods: {
       async pobierzWpisy(){
            this.wpisy = await dzien2_backend.odczytaj_wpisy();
        },
        async dodajWpisy(){
            this.wpisy = await dzien2_backend.dodaj_wpis(this.nowyBlog);
        }
    },
    async mounted(){
        this.pobierzWpisy()
    }
}

</script>