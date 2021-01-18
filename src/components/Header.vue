<template>
    <div id="header">
        <nav class="navbar navbar-light bg-light">
            <h2>Listado de libros</h2>     
            <button class="btn btn-default" @click="showForm">
                <span v-if="show">Listado</span>
                <span v-else>Nuevo libro</span>
            </button>
        </nav>
    </div>    
</template>

<script>
export default {
    name: 'Header',
    props:{
        changeText: Boolean
    },
    data(){
        return{
            show : false,
        }
    },
    methods:{
        showForm: function(){
            this.show = !this.show;
            this.$emit('show-form', this.show);
      },
    },
    watch:{
        changeText: function(){
            this.show = this.changeText;
        }
    }
}
</script>

<style scoped>

</style>