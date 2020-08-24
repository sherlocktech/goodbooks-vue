<template>
  <div class="book-wrapper">
    <div class="book-title">
      {{ book.title }}
    </div>
    <div class="book-author">
      {{ book.author }}
    </div>
    <div class="book-created">
      {{ book.createdOn | humanize }}
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import IBook from '@/types/Book';

@Component({
  name: "Book",
  components: {}
})
export default class Book extends Vue {
  @Prop({ required: true })
  book!: IBook;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.book-wrapper {
  margin: 0.8rem;
  padding: 0.4rem;
  background-color: #fafafa;
  border-radius: 1rem;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
  transition: all 0.3s cubic-bezier(.25,.8,.25,1);
}

.book-wrapper:hover {
  box-shadow: 0 14px 28px rgba(0,0,0,0.25), 0 10px 10px rgba(0,0,0,0.22);
}

.book-title {
  font-size: 1.2rem;
  font-weight: bold;
}

.book-author {
  color: #333;
}

.book-created {
  font-size: 0.9rem;
  color: #333;
}
</style>
