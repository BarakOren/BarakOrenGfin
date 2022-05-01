<template>
    <div class="listPage">
        <Details 
        :info="this.info.statistics"
        :generalInfo="this.info"
        :image="this.info.cardImage"
        />
    </div>

</template>

<script>
import Details from "@/components/Details/Details"
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
    components: {Details},
    data() {
      return { info: {}, image: {} }
    },
    methods: {
      getData(){
          //getting information from the params, which will be the selected player.
          client.fetch(`*[_type == "fifaCard"][name == "${this.$route.params.details}"][0]`)
          .then(data => {
            this.info = data
            this.image = data.cardImage
            })
      }
    },
    created(){
      this.getData();
    }
}


</script>


<style>
.listPage{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

@media only screen and (max-width: 600px) {
.listPage{
  width: 100vw;
  justify-content: flex-start;
}
}
</style>