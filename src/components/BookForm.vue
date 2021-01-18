<template>
    <div class="container">
        <div id="form-new-book" class="row">
          <form class="form-row">
            <div class="form-group col-12">
              <label for="title">Título</label>
              <input type="text" class="form-control" id="title" placeholder="Título del libro" v-model="newBook.title">
            </div>
            <div class="form-group col-12">
              <label for="subtitle">Subtitulo</label>
              <input type="text" class="form-control" id="subtitle" placeholder="Subtitulo" v-model="newBook.subtitle">
            </div>
            <div class="form-group col-12">
              <label for="author">Autor</label>
              <input type="text" class="form-control" id="author" placeholder="Autor" v-model="newBook.author">
            </div>
            <div class="form-group col-12">
              <label for="publisher">Editorial</label>
              <input type="text" class="form-control" id="publisher" placeholder="Editorial" v-model="newBook.publisher">
            </div>
            <div class="form-group col-6">
              <label for="isbn">ISBN</label>
              <input type="text" class="form-control" id="isbn" placeholder="ISBN" v-model="newBook.isbn">
            </div>
            <div class="form-group col-6">
              <label for="published">Fecha</label>
              <input type="date" class="form-control" id="published" placeholder="Fecha de publicación" v-model="newBook.published">
            </div>
            <div class="form-group col-6">
              <label for="page">Páginas</label>
              <input type="number" class="form-control" id="page" placeholder="Número de paginas" v-model="newBook.pagesnpo">
            </div>
            <div class="form-group col-6">
              <label for="category">Categoría</label>
              <input type="text" class="form-control" id="category" placeholder="Categoría" v-model="newBook.category">
            </div>
            <div class="form-group col-12">
              <label for="description">Descripcion</label>
              <textarea type="text" class="form-control" id="description" placeholder="Descripción" v-model="newBook.description" rows="5"/>
            </div>
            <div class="form-group col-12">
              <label for="website">Web</label>
              <input type="text" class="form-control" id="website" placeholder="Página web" v-model="newBook.website">
            </div>
            <button type="button" class="btn btn-primary" @click="addBook(newBook)">Añadir</button>
          </form>  
        </div>
    </div>  
</template>

<script>

export default {
    name: 'BookForm',
    data(){
      return{
        newBook: {
 /*         "isbn": "9781449337711",
          "title": "Designing Evolvable Web APIs with ASP.NET",
          "subtitle": "Harnessing the Power of the Web",
          "author": "Glenn Block, et al.",
          "published": "2014-04-07",
          "publisher": "O'Reilly Media",
          "pages": 538,
          "description": "Design and build Web APIs for a broad range of clients—including browsers and mobile devices—that can adapt to change over time. This practical, hands-on guide takes you through the theory and tools you need to build evolvable HTTP services with Microsoft’s ASP.NET Web API framework. In the process, you’ll learn how design and implement a real-world Web API.",
          "website": "http://chimera.labs.oreilly.com/books/1234000001708/index.html",
          "category": "Suspense" */
        }
      }
    },
   methods:{
    addBook: function(book){
       this.$emit('new-book', book);
      },    
    }
}
</script>

<style scoped>
label{
  font-weight:bolder;
}
</style>