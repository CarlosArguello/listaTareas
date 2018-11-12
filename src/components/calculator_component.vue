<template lang="pug">
    div
        title Calculator app
        .computed
            input(v-model="valor1")
            br
            input(v-model="valor2")
            p {{Sumar}}
        br
        .props
            p {{mensaje}}
</template>

<script>
    export default {
        data(){
            return {
                valor1 : 0,
                valor2 : 0
            }
        },
        //COMPUTED AUTOINVOCA LA FUNCION
        computed : {
            Sumar(){
                if(!this.valor1)
                    this.valor1=0;
                
                if(!this.valor2)
                    this.valor2=0;

                return parseInt(this.valor1)+parseInt(this.valor2)
            }
        },props : {
            mensaje: {
                type: String,
                default: "No se ha enviado ningun mensaje."
            }
        }
    }

</script>


<style lang="scss">

</style>