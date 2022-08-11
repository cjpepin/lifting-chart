<template>
    <div class="nav">
        <span>Lift Estimator Chart</span>
        <button @click="toMyPage()">About</button>
    </div>
</template>

<script>

export default {
    setup() {
        
    },
    methods:{
        toMyPage(){
            window.location.href = "https://www.connorjpepin.com/"
        }
    },
}
</script>

<style scoped>
.nav{
    position: fixed;
    margin-top: -0.5rem;
    margin-left: -0.5rem;
    min-width: calc(100% - 2rem);
    min-height: 4rem;
    background-color: purple;
    padding: 1rem;

    display: flex;
    justify-content: space-between;
}
span{
    font-size: 2.5rem;
    color: white;
}
button{
    all: unset;
    background-color: orange;
    color: black;
    font-size: 1.25rem;
    padding: 0.25rem;
    margin-top: 0.5rem;
    box-shadow: 1px 1px 1px 1px rgba(0,0,0,0.6);
    border-radius: 0.2rem;
    max-height: 2.25rem;
    min-width: 4rem;

    display: flex;
    align-items: center;
    justify-content: center;

    cursor: pointer;
}
button:active{
    background-color: rgba(160,71,0,0.7);
}
</style>