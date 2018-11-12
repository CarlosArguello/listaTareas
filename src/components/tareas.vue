<template lang="pug">
    vista-tareas(:nuevaTarea="nuevaTarea")
</template>


<script>
    import vistaTareas from './subComponents/vistaTareas.vue';
    
    export default {
        data(){
            return{
                nuevaTarea : [
                    {nombre : 'Aprender Vue', estado : false, editar:false,bloqueado:false},
                    {nombre : 'Hacer el aseo', estado : false, editar:false,bloqueado:false},
                    {nombre : 'Hacer ejercicio', estado : false, editar:false,bloqueado:false},
                    {nombre : 'Buscar Trabajo', estado : false, editar:false,bloqueado:false}
                ]
            }
        },
        components : {vistaTareas}
    }
</script>
