<template>
    <div class="header">
        <div class="container">
            <img class="menu" src="../assets/menu.png">
            <img @click="home" class="logo" src="../assets/logo.png">
        </div>
    </div>
</template>

<script>
export default {
    name: "Header",
    methods:{
        home(){
           this.$router.push(`/`) 
        }
    }
}
</script>

<style scoped>
.header{
    width: 100%;
    height: 64px;
    background-color: black;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.container {
    width: 840px;
    height: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}

.logo {
    width: auto;
    margin-right: 5px;
    height: 25px;
    cursor: pointer;
}

.menu{
    width: 25px;
    height: 25px;
    background-color: #161616;
    padding: 19.5px;
}

@media only screen and (max-width: 600px) {
.header{
position: fixed;
top: 0;
left: 0;
padding: 0;
width: 100vw;
}



}

</style>