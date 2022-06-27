<template>
    <main class="flex-grow-1">
        <div class="container"  v-if="loading">
            <div class="row row-cols-5 g-4">
                <div class="col" v-for="disk in diskList" :key="disk.title" :class="{'d-none' : currentGenre!==disk.genre&&currentGenre!=='all' || currentAuthor!==disk.author&&currentAuthor!=='all'  }">
                    <TheDisk :info="disk"/>
                </div>
           </div>
        <select class="genre" name="" id="" v-model="currentGenre">
            <option :value="genre" v-for="genre in genreList" :key="genre">{{genre}}</option>
        </select>

         <select class="author" name="" id="" v-model="currentAuthor">
            <option :value="author" v-for="author in authorList" :key="author">{{author}}</option>
        </select>
        </div>
        <LoadingCircle v-else/>
    </main>
</template>

<script>
import axios from "axios";
import TheDisk from "./TheDisk.vue";
import { state } from '../store.js';
import LoadingCircle from "./LoadingCircle.vue";

    export default {
    name: "DiskContainer",
    data() {
        return {
            diskList: [],
            genreList: [],
            currentGenre : 'all',
            authorList : [],
            currentAuthor : 'all',
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
                      if(!this.authorList.includes(element.author)){
                        this.authorList.push(element.author);
                    }
                });
                
                setTimeout(function(){
                    state.isLoading = true;
                },4000);

            });
        },
        

        
     
            
        },
        
computed : {
    loading() {
        return state.isLoading;
        }
    },


    mounted() {
        this.fetchDisk();
     
    },
    components: { TheDisk, LoadingCircle }
}
</script>

<style lang="scss" scoped>
main {
    background-color: #1E2D3B;
    height: 90vh;
    padding: 7rem 0;
    position: relative;


    select{
        position: absolute;
        top: 0;
        padding: 0.3rem 1.2rem;
    

    &.genre{
        right: 0;
    }

    &.author {
        left: 0;
    }

    }
    
}
</style>