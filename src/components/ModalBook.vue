<template>       
  <div class="modal fade" id="bookModal" tabindex="-1">
    <div class="modal-dialog" role="document">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">{{book.title}}</h5>
          <button type="button" class="close" data-dismiss="modal" aria-label="Close">
            <span aria-hidden="true">&times;</span>
          </button>
        </div>
        <div class="modal-body text-left ">
          <p>
            <span class="font-weight-bold">Título:</span> 
            {{book.title}} - {{book.subtitle}}
          </p>
          <p>
            <span class="font-weight-bold">Autor:</span> 
            {{book.author}}
          </p>
          <p>
            <span class="font-weight-bold">Descripción:</span> 
            {{book.description}}
          </p>
          <p>
            <span class="font-weight-bold">Editorial:</span> 
            {{book.publisher}}
          </p>
          <p>
            <span class="font-weight-bold">Fecha de publicación: </span> 
            {{book.published | formatDate}}</p>
          <p>
            <span class="font-weight-bold">ISBN:</span> 
            {{book.isbn}}
          </p>
          <p>
            <span class="font-weight-bold">Número de páginas:</span> 
            {{book.pages}}
          </p>
          <p>
            <span class="font-weight-bold">Categoria:</span> 
            {{book.category}}
          </p>
          <p>
            <span class="text-left font-weight-bold">Web:</span> 
            {{book.website}}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import moment from "moment";

  export default {
      name: 'ModalBook',
      props:{
        book: Object
      },
      filters:{
        formatDate: function(value){
          if(value){
            return moment(value.date).format('DD-MM-YYYY');
          }
          return '';
        }
      },
      watch: {
        book: function(){        
            window.$('#bookModal').modal('toggle');
        }
      }
  }
</script>

<style scoped>

</style>