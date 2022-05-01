<template>
  <div class="mainPage">
    <List />
      </div>
  </div>
</template>

<script>



import List from "@/components/List/List";



export default {
  components: {
    List
  }
}


</script>



<style>
.mainPage{
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

@media only screen and (max-width: 600px) {
.mainPage{
  width: 230%;
  justify-content: flex-start;
}
}
</style>