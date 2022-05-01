<template>
    <div class="main">
        <div class="firstDiv">
          <div class="firstDivData" v-if="this.info">
              <div class="imageContainer">
                <img :src="urlFor(image).width(180)"/>
              </div>
          <Column
          v-for="(column, index) in infoArray" 
          :playerInfo="column"
          :key="index"
          />
          </div>
          </div>
          <GeneralInfo v-if="this.info"
          :generalInfo="generalInfo"
          />
    </div>
</template>


<script>
import Column from "@/components/Details/Column"
import GeneralInfo from "@/components/Details/GeneralInfo"
import imageUrlBuilder from '@sanity/image-url'

const sanityClient = require("@sanity/client")
const client = sanityClient({
  projectId: "21fy9g0s",
  dataset: "production",
  apiVersion: '2021-03-25',
  useCdn: true,
})
const builder = imageUrlBuilder(client)

export default {
    name: "Details",
    components: {Column, GeneralInfo},
    data(){
      return{infoArray: []}
    },
    props:["info", "generalInfo", "image"],
    watch: {
      info: function(){ //when info changes starting function
          // turning object to array so i can map it.
          var array = []
            for(let key in this.info) {
                var obj = {}
                obj = {[key]: this.info[key]} 
                array.push(obj)
            }
          this.infoArray = array
      }
    },
    methods: {
      // sanity image builder
      urlFor(source) {
        return builder.image(source)
      }
    }
}

</script>

<style scoped>
.main {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    min-height: 86vh;
    padding: 3vh 70px 4vh 70px;
    width: 700px;
    background-color: black;
}

.firstDiv{
    padding: 0 30px;
    background: linear-gradient(180deg, #0A0A0A 0%, #161616 52.33%, #0D0D0D 100%);
    border-radius: 12px;
    width: 100%;
    height: 350px;

}

.firstDivData {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: space-evenly;
  
}

.imageContainer{
  margin-top: 15px;
  width: 180px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

@media only screen and (max-width: 600px) {
  .main {
    width: 100vw;
    padding: 10vh 0 4vh;
    min-height: auto; 
  }

  .firstDiv {
    width: 90%;
    padding: 10px 0;
    height: auto;
    flex-wrap: wrap;
  }

  .firstDivData {
    width: 95%;
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    justify-content: space-evenly;
    flex-wrap: wrap;
}

  .imageContainer{
      margin-top: 20px;
      width: 100%;
  }
}
</style>