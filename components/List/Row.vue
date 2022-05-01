<template>
    <div class="row" @click="moreInfo(player.name)">
        <div class="nameDiv">{{player.name}}</div>
            <div class="stateContainer">
                    <div class="stat white">{{player.description.substring(player.description.indexOf(")") - 2).substring(0, 2)}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat black" >{{player.position}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat black" v-bind:style=" player.cardType.length >= 6 ? 'fontSize: 8px;' : 'fontSize: 12;' ">{{player.cardType}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat outline" >{{player.statistics.pace.average}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat outline">{{player.statistics.shooting.average}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat outline">{{player.statistics.passing.average}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat outline">{{player.statistics.dribbling.average}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat outline">{{player.statistics.defense.average}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat outline" >{{player.statistics.physical.average}}</div>
            </div>
            <div class="stateContainer">
                <div class="stat black">{{player.workRatesAttacking[0]}}</div>
            </div> 
    </div>


</template>


<script>
export default {
    name: "Row",
    props: ["player"],
     methods: {
        moreInfo(name){
            this.$router.push(`/${name}`)
        }
    }
}
</script>



<style scoped>
.row {
    cursor: pointer;
    border-bottom: 3px solid black;
    background-color: #101010;
    font-size: 11px;
    width: 100%;
    padding: 5px 70px;
    height: 45px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}

.nameDiv {
    font-size: 12px;
    margin: 0;
    width: 130px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
}

.stateContainer {
    width: 50px;
    height: 70%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
}

.stat {
    text-align: center;
    align-items: center;
    width: 90%;
    height: 100%;
    border-radius: 5px;
    display: flex;
    justify-content: center;
    
}

.white {
    color: black;
    background-color: white;
}

.black {
    color: white;
    background-color: black;
}

.outline {
    color: white;
    background-color: black;
    border: 1px solid white;
}




@media only screen and (max-width: 600px) {
  .row {
      width: 95%;
      padding-left: 5%;
  }
}
</style>