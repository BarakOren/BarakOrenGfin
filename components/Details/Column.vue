<template>
    <div v-if="this.playerInfo" class="column">
        <div class="row first">
        <!-- main skill (DEF, DRI etc) -->
        <h1 class="title">{{ mainSkill.substring(0,3) }}</h1> 
        <h1 class="title">{{ mainSkillNumber }}</h1>
        </div>
        
        <!-- mapping info (average, balance etc..)  -->
        <div v-for="(obj, index) in infoArray" class="row">
        <!-- turning Kabab case to all lowCase and adding space between words -->
        <p>{{ Object.keys(obj)[0].replace(/([a-z])([A-Z])/g, '$1 $2').toLowerCase() }}</p>
        <p>{{ Object.values(obj)[0] }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: "Column",
    data(){
        return {
            mainSkill: "", // name of the skill (defense, shooting, etc)
            mainSkillNumber: "", // skill number
            infoArray: [] 
        }
    },
    props: [
        "playerInfo"
    ],
    mounted(){
        this.mainSkill = Object.keys(this.playerInfo)[0] // string
        var mainSkill = this.mainSkill
        this.mainSkillNumber = this.playerInfo[mainSkill].average // string
        var mainSkillNumber = this.mainSkillNumber
        var object = (JSON.parse(JSON.stringify(this.playerInfo[mainSkill])))
        var array = []
        //turning object to an array so i can map it
          for(let key in object) {              
              var obj = {}
              obj = {[key]: object[key]} 
              array.push(obj)
          }
        this.infoArray = array
    } 

}
    
</script>

<style scoped>
.column {
    font-size: 12px;
    width: 100px;
    margin: 30px 5px 0 5px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
}

.row{
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 17px;
}

.first {
    border-top: 2px solid white;
    border-bottom: 2px solid white;
}

.title {
    margin: 3px 0;
    font-size: 15px;
}

p{
    font-weight: 500;
    font-size: 9px;
    margin: 0;
}

@media only screen and (max-width: 600px) {
.title{
    font-size: 16px;
}

p{
    font-size: 10px;
}

}
   
</style>