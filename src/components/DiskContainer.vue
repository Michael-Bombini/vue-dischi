<template>
    <main class="flex-grow-1">
        <div class="container">
            <div class="row row-cols-5 g-4">
                <div class="col" v-for="disk in diskList" :key="disk.title" :class="{'d-block' : currentGenre==='all' , 'd-none' : currentGenre!==disk.genre&&currentGenre!=='all' }">
                    <TheDisk :info="disk"/>
                </div>
           </div>
        </div>
        <select name="" id="" v-model="currentGenre">
            <option :value="genre" v-for="genre in genreList" :key="genre.genre">{{genre}}</option>
        </select>
    </main>
</template>

<script>
import axios from "axios";
import TheDisk from "./TheDisk.vue";


    export default {
    name: "DiskContainer",
    data() {
        return {
            diskList: [],
            genreList: [],
            currentGenre : 'all',
        };
    },
    methods: {
        fetchDisk() {
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
                .then((response) => {
                this.diskList = response.data.response;
                this.diskList.forEach(element => {
                    if(!this.genreList.includes(element.genre)){
                        this.genreList.push(element.genre);
                    }
                });
                
            });
        },
        
     
            
        },

    mounted() {
        this.fetchDisk();
     
    },
    components: { TheDisk }
}
</script>

<style lang="scss" scoped>
main {
    background-color: #1E2D3B;
    height: 90vh;
    padding: 7rem 0;
    position: relative;


    select {
        position: absolute;
        top: 0;
        right: 0;
        padding: 0.3rem 1.2rem;
    }
}
</style>