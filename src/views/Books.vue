<template>
  <div class="books-container">
    <h1>My Books</h1>
    <div v-if="myBooks.length">
      <book
        :book="book"
        v-for="book in myBooks"
        :key="book.id" />
    </div>
  </div>
</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  import IBook from '@/types/Book';
  import BookService from '@/services/book-service';
  import Book from '@/components/Book.vue';

  const bookService = new BookService();

  @Component({
    name: 'MyBooks',
    components: { Book }
  })
  export default class MyBooks extends Vue {
    myBooks: IBook[] = [];

    get bookCount() {
      return this.myBooks.length;
    }

    created() {
      bookService.getAllBooks()
        .then(res => this.myBooks = res)
        .catch(err => console.error(err)); 
    }
  }
</script>
