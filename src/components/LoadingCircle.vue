<template>
<div class="loader-page">

    <div class="spinning">
        <span>Loading...</span>
    </div>

</div>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>
.loader-page {
    height: 90vh;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 100;
    background: #1E2D3B;
    display: flex;
    align-items: center ;
    justify-content: center;
}

div.spinning {
    width: 130px;
    height: 130px;
    border: 10px dashed #fff;
    border-radius: 50%;
    animation: loadingCircle 3.5s infinite;
    position: relative;
    
}

span {
    position: absolute;
    font-size: 20px;
    color: #fff;
    top: 50%;
    left: 50%;
    transform: translate(-50% , -50%);
}

@keyframes loadingCircle{
    0%{ transform: rotate(0deg);}
    12.5%{ transform: rotate(45deg);}
    25%{ transform: rotate(90deg);}
    37.5%{ transform: rotate(135deg);}
    50%{ transform: rotate(180deg);}
    62.5%{ transform: rotate(225deg);}
    75%{ transform: rotate(270deg);}
    87.5%{ transform: rotate(315deg);}
    100%{ transform: rotate(360deg);}

}

</style>