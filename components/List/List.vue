<template>
    <div class="main">
        <FirstRow :orderStat="orderStat" :order="order" />
        <Row v-for="player in players" 
        :player="player"
        :key="player.id"
        >
        </Row>
        </div>
    </div>
</template>


<script>
import FirstRow from "@/components/List/FirstRow"
import Row from "@/components/List/Row"


const sanityClient = require("@sanity/client")
const client = sanityClient({
  projectId: "21fy9g0s",
  dataset: "production",
  apiVersion: '2021-03-25',
  useCdn: true,
})

var order = true

export default {
    name: "List",
    components: {FirstRow, Row},
    data() {
      return {players: []}
    },
    async fetch(){this.players = await client.fetch('*[_type == "fifaCard"]')},
    methods: {
      order(type){ 
        client.fetch(`*[_type == "fifaCard"] | order(${type} ${order ? "desc" : "asc"})`) 
        .then(data => {this.players = data; order = !order;})
        //cardType - some of strings comes with a space before the first charecter, that kills the order.
        //desctription/OVR comes as a string (""Pablo Sarabia (OVR 80) - check out the stats of the Sporting CP RW and how he can fit into your Ultimate Team on FIFA 22.")
      },
      orderStat(type){
        client.fetch(`*[_type == "fifaCard"] | order(statistics.${type}.average ${order ? "desc" : "asc"})`) // up on top
        .then(data => {this.players = data; order = !order;})
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
    padding: 30px 70px 4vh 70px;
    width: 700px;
    background-color: black;
}

@media only screen and (max-width: 600px) {
  .main {
    width: 100%;
    padding: 10vh 0 4vh;
    min-height: auto;
  }
}
</style>