<template lang="pug">
    //h1(v-for="item in user"){{item}}
    div
        title Header appCalculator
        span(v-html="myhtml")
        div(v-for="item in user" v-text="item")
</template>


<script>
    export default {
        data(){
            return {
                user : ['Carlos','Eduardo','Arguello','Amaya'],
                myhtml : '<h1>Titulo</h1>'
            }
        }
    }
</script>


<style lang="scss">
 
</style>

