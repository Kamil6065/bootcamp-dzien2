<template>
    <div>
        <button>@Click="pobierzWpisy"refresh</button>
        Siema blog!
        {{ wpisy }}
        <input v-model="nowyBlog" type="text">
    </div>
</template>
<script>
import { dzien2_backend } from 'declarations/dzien2_backend/index';
export default {
    data() {
        return {
            wpisy: []
            nowyBlog: ""
        }
    },
    methods: {
        async pobierzWpisy() {
            this.wpisy = await dzien2_backend.odczytaj_wpisy();
        }
    },
}
</script>