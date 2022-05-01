<template>
    <div class="generalInfo" v-if="this.generalInfo">
        <div class="firstRow">
            <p class="name">{{ this.generalInfo.name }} </p>
            <p class="viewAllCards" @click="$router.push('/')" >View all cards</p>
        </div>
        <div class="infoRow">
                <div class="column" id="first">
                <p class="infoTitle" >Club</p>
                <p class="info">{{ this.generalInfo.club }}</p>
                </div>
                <div class="column">
                <p class="infoTitle">League</p>
                <p class="info">{{ this.generalInfo.league }} </p>
                </div>
                <div class="column">
                <p class="infoTitle">Nation</p>
                <p class="info">{{ this.generalInfo.nation}}</p>
                </div>
                <div class="column">
                <p class="infoTitle">Strong Foot</p>
                <p class="info">{{ this.generalInfo.strongFoot }}</p>
                </div>
                <div class="column">
                <p class="infoTitle">Age</p>
                <p class="info">{{ this.generalInfo.age.substring(0,2) }} </p>
                </div>
                <div class="column">
                <p class="infoTitle">Height</p>
                <p class="info">{{ this.generalInfo.height }}</p>
                </div>
                <div class="column" style="border: none">
                <p class="infoTitle">Workrates</p>
                <p class="info">{{ this.generalInfo.workRatesAttacking }}</p>
                </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "GeneralInfo",
    props: ["generalInfo"]
}
</script>

<style scoped>
.generalInfo{
    margin-top: 30px;
    width: 105%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.firstRow{
    width: 100%;
    align-self: flex-start;
    display: flex;
    flex-direction: row;
    align-items: flex-end;
    justify-content: flex-start;
}

.name {
   margin: 0 20px 0 0;
   font-size: 40px;
}

.viewAllCards{
    margin: 0 0 10px 0;
    font-size: 12px;
    color: #848282;
    border-bottom: 1px dashed #848282;
    cursor: pointer;
}

.infoRow{
    margin-top: 15px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    height: auto;
    align-items: center;
}

.column{
    border-right: 1px solid #848282;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-start;
    height: 50px;
    padding: 0 40px 0px 0;
}

.infoTitle{
    font-size: 12px;
    color: #848282;
    margin: 0;
}  

.info{
    font-size: 14px;
    font-weight: 300;
    margin: 0;
}

#first {
    padding: 0 15px 0 0;
}

#last {
    border: none;
}

@media only screen and (max-width: 600px) {
.generalInfo{
    width: 85%;
}

.name {
   margin: 0 12px 0 0;
   font-size: 26px;
}

.viewAllCards{
    font-size: 10px;
    margin: 0 0 5px 0;
}

.firstRow{
    width: 100%;
}

.infoRow{
    flex-wrap: wrap;
    align-items: center;
    width: 100%;
}

.column{
    width: 100%;
    border-right: none;
    border-bottom: 1px solid #848282;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    height: 70px;
    padding: 0;
}

.infoTitle{
    font-size: 12px;
    color: white;
}  

.info{
    font-size: 14px;
    font-weight: 300;
    margin: 0;
}

#first {
    padding: 0;
}


}
</style>