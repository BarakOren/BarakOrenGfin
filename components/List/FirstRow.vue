<template>
    <div class="row">
        <div class="nameDiv">Name 
            <div class="arrowDiv" @click="order('name')" >
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">OVR
            <div class="arrowDiv" @click="order('description')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">POS
            <div class="arrowDiv" @click="order('position')"> 
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">Type
            <div class="arrowDiv" @click="order('cardType')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">PAC
            <div class="arrowDiv" @click="orderStat('pace')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">SHO
            <div class="arrowDiv" @click="orderStat('shooting')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">PAS
            <div class="arrowDiv" @click="orderStat('passing')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">DRI
            <div class="arrowDiv" @click="orderStat('dribbling')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">DEF
            <div class="arrowDiv" @click="orderStat('defense')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat">PHY
            <div class="arrowDiv" @click="orderStat('physical')">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
        <div class="stat" id="last">WR
            <div class="arrowDiv">
                <img class="arrow" id="up" src="../../assets/arrow.png">
                <img class="arrow" src="../../assets/arrow.png">
            </div>
        </div>
    </div>
</template>


<script scoped>
export default {
    name: "FirstRow",
    props: ["orderStat", "order"]
}
</script>

<style scoped>
.row {
    font-size: 11px;
    background-color: black;
    width: 100%;
    padding: 5px 70px;
    height: 45px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
}

.nameDiv {
    margin: 0;
    width: 130px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
}

.arrowDiv {
    display: flex;
    flex-direction: column;
    align-items:center;
    justify-content: center;
    margin-left: 3px;
}

.arrow{
    width: 12px;
    height: auto;
    cursor: pointer;
}

#up{
    transform: rotate(180deg);
}

.stat {
    height: 70%;
    text-align: center;
    margin: 0;
    width: 50px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    border-right: 1px solid #606060;
}

#last {
    border-right: none;
}

@media only screen and (max-width: 600px) {
  .row {
    width: 95%;
    padding-left: 5%;
  }
}

</style>