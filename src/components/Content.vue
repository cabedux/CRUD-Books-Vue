<template>
    <div id="content">
        <BookList v-if="!showForm"
                :books = "bookList"
                @delete-book = "deleteBook"
        ></BookList>
        <BookForm v-if="showForm"
                @new-book = "addBook"
        ></BookForm>
    </div>    
</template>

<script>
    import config from './../Config/config';
    import BookList from './BookList.vue'
    import BookForm from './BookForm.vue'
    import axios from "axios";

    export default {
        name: 'Content',
        components:{
            BookList,
            BookForm
        },
        props:{
            showForm : {
                type: Boolean,
                default: false
            },
        },
        data(){
            return{
                newBook:{},          
                bookList : Array,
            }
        },
        mounted(){
            this.getBooks();
        },
        methods:{
            getBooks: function(){
                axios.get(config.URL + 'api/books').then(response =>{
                this.bookList = response.data;
                }).catch(e => console.log(e));
            },
            addBook: function(book){
                console.log(book);
                axios.post(config.URL + 'api/book', book).then(response =>{
                    if(response.status == 200){
                        alert('Libro añadido correctamente');
                    }
                    this.getBooks();
                    this.$emit('add-book', false);
                    }).catch(e => console.log(e));
            },
            deleteBook: function(id){
                axios.delete(config.URL + 'api/book/' + id).then(response =>{
                    this.getBooks();
                    if(response.status == 200){
                        alert('Libro eliminado correctamente');
                    }
                    }).catch(e => {  
                    console.log(e); 
                    alert('El libro no se ha podido eliminar');
                    }); 
        },
        }
    }
</script>

<style scoped>

</style>