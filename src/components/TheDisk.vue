<template>
    <div>
            <img :src="info.poster" alt="">
            <h1>{{info.title}}</h1>
            <h2>{{info.author}}</h2>
            <h3>{{info.year}}</h3>

    </div>
</template>

<script>
    export default {
        name : "TheDisk",
        props : {
            info : Object,
        }
    }
</script>

<style lang="scss" scoped>

div {
    height: 350px;
    background: #2E3A46;
    padding: 0.5rem;
    text-align: center;


img {
    aspect-ratio: 1/1;
    height: 180px;
    max-width: 100%;
    margin-bottom: 0.9rem;
}

h1 {
    font-size: 1.4rem;
    text-align: center;
    color: #fff;
    font-weight: bold;
    text-transform: uppercase;
}

h2 , h3{
    font-size: 1.2rem;
    color: #6D6B6B;
}

}
</style>