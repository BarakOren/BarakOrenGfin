<template>
    <div>
        <Header />

        <nuxt />
    </div>
</template>

<script>
import Header from "@/components/Header"

export default {
    components: {
        Header
    }
}

</script>

<style>
html {
    font-family: 'Manrope', sans-serif;
}

body {
    font-family: 'Manrope', sans-serif;
    font-weight: 700;
    margin: 0;
    background-color: #37373D;
    color: white;
}

@media only screen and (max-width: 600px) {
  body {
    background-color: black;
  }
}

</style>