<template lang="pug">
  .container
    title lista de tareas
    .row
      .col-10
            .jumbotron.mt-4
                //-Lista de tareas
                div
                    h1.text-center.mb-3 Lista de tareas

                    .form-group
                        input.form-control(v-model="content" @keyup.enter="agregarTarea")
                        ul.list-group
                            li(v-for="(item, index) in nuevaTarea" style="height:45px").list-group-item.d-flex.justify-content-between.px-5.d-flex.align-items-center
                                span.form-inline
                                    p(v-if="!item.editar",:class="item.estado?'activo':''") {{item.nombre}}
                                    template(v-else)
                                        input(v-model="editarT" autofocus @keyup.enter="guardarEditarTarea(index)").form-control
                                        button.btn.btn-primary.btn-md(@click="guardarEditarTarea(index)").material-icons save
                                        button.btn.btn-danger(@click="cancelarEditarTarea(index)").material-icons block
                                span.material-icons
                                    button.btn.btn-success.text-white.mr-2.btn-sm(@click="item.estado=!item.estado") done
                                    button.btn.btn-warning.mr-2.btn-sm(@click="editarTarea(index)") create
                                    button.btn.btn-danger.text-white.btn-sm(@click="eliminarTarea(index)") delete
                                

                    .d-flex.justify-content-center
                        button.btn.btn-primary.col-6(style="height:45px;" @click="agregarTarea") Agregar

</template>


<script>
    export default{
        data(){
            return{
                block : false,
                numIndex : '',
                editarT : ''            }
        },
        props:['nuevaTarea'],
        methods : {
            agregarTarea(){
                if(this.content){
                    this.nuevaTarea.push({nombre : this.content,estado : false});
                    this.content = '';
                }else{
                   alert("Ingresa datos")
                }
            },
            eliminarTarea(indice){this.nuevaTarea.splice(indice,1)},
            editarTarea(indice){

                if(this.block && !this.numIndex==indice){
                    alert("block")
                }else{
                    this.nuevaTarea[indice].editar = !this.nuevaTarea[indice].editar;
                    this.editarT = this.nuevaTarea[indice].nombre;
                    this.block = !this.block
                }
                for(var i=0;0<=this.nuevaTarea.lenght;i++){
                    if(!this.nuevaTarea[i].editar){
                        this.block = false;
                        this.numIndex = i;
                    }else{
                        this.block = true;
                    }
                }

                //this.numIndex = indice;
            },
            cancelarEditarTarea(indice){this.nuevaTarea[indice].editar = false;this.block=false},
            guardarEditarTarea(indice){
                if(!this.editarT==""){
                    this.nuevaTarea[indice].nombre = this.editarT;
                }else{
                    this.editarT = this.nuevaTarea[indice].nombre;
                }
                    this.cancelarEditarTarea(indice)
            }
        }
    }

</script>

<style lang="scss">
    .activo{
        color : #ccc;
        text-decoration:line-through; 
    }
</style>
