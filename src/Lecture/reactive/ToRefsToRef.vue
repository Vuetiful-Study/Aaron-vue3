<template>
  <div>
    <p>author: {{ author }}</p>
    <p>title: {{ title }}</p>
  </div>
</template>

<script>
import { reactive, toRef } from 'vue';

export default {
  setup() {
    const book = reactive({
      author: 'Vue Team',
      year: '2022',
      title: 'Vue 3 Guide',
      description: '당신은 지금 바로 이 책을 읽습니다.',
      price: '무료',
    });

    // const { author, title } = toRefs(book);
    const author = toRef(book, 'author');
    const year = toRef(book, 'year');

    return { book, author, year };
  },
};
</script>

<style lang="scss" scoped></style>
