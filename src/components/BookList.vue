<template>
  <div id="table">
    <table class="table table-hover">
      <thead>
        <tr>
          <th scope="col">Titulo</th>
          <th scope="col">Editorial</th>
          <th scope="col">Categoria</th>
          <th scope="col">ISBN</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="book in books" :key="book.id">
          <th scope="row" @click="getBook(book.isbn)">{{book.title}}</th>
          <td @click="getBook(book.isbn)">{{book.publisher}}</td>
          <td @click="getBook(book.isbn)">{{book.category}}</td>
          <td @click="getBook(book.isbn)">{{book.isbn}}</td>
          <td>
            <button class="btn btn-default" @click="getBook(book.isbn)"><i class="far fa-eye"></i></button>
            <button class="btn btn-default" @click="deleteBook(book.id)"><i class="fas fa-trash"></i></button>
          </td>
        </tr>
      </tbody>
    </table>
    <ModalBook
      :book = "this.book"
    ></ModalBook>
  </div>  
</template>

<script>
import axios from "axios";
import ModalBook from "./ModalBook.vue";
import config from './../Config/config';

export default {
  name: 'BookList',
  components:{
    ModalBook
  },
  props:{
    books: Array
  },
  data(){
    return{
      book: Object,
    }
  },
  methods:{
    getBook: function(id){    
      axios.get(config.URL + 'api/book/' + id).then(response =>{
        this.book = response.data;
        })
        .catch(e => console.log(e));
    },
    deleteBook: function(id){
      this.$emit("delete-book", id);
    }
  }
}
</script>

<style scoped>
#table tr:hover{
  cursor: pointer;
}
</style>