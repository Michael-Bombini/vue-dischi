<template>
    <main class="flex-grow-1">
        <div class="container">
    
        </div>
    </main>
</template>

<script>
import axios from "axios";


    export default {
        name : "DiskContainer",

    data(){
        return{
            diskList : [],
        }
    },

    methods : {
        fetchDisk(){
            axios.get("https://flynn.boolean.careers/exercises/api/array/music")
            .then((response)=>{
                this.diskList = response.data.response;
            })
        }
    },


    mounted() {
        this.fetchDisk();
    }





    }
</script>

<style lang="scss" scoped>
main {
    background-color: #1E2D3B;
    height: 90vh;
}
</style>