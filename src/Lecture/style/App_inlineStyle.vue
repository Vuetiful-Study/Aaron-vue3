<template>
  <div>
    <div :style="styleObject">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempora optio
      eligendi ratione neque voluptatum. Esse maiores unde dignissimos
      voluptatem, sunt, cupiditate, consequuntur tempore quam nobis obcaecati
      sint debitis! Sed, eum!
    </div>
    <button v-on:click="fontSize--">-</button>
    <button v-on:click="fontSize++">+</button>
  </div>
</template>
<script>
import { computed, ref } from 'vue';
export default {
  setup() {
    // 인라인 스타일 적용할 때는 css 속성 명을 camelCase로 일반적으로 적용
    // const styleObject = reactive({
    //   color: 'red',
    //   fontSize: '13px',
    // });
    const fontSize = ref(13);
    const styleObject = computed(() => {
      return {
        color: 'red',
        fontSize: fontSize.value + 'px',
      };
    });
    return { styleObject, fontSize };
  },
};
</script>
<style lang="scss" scoped></style>
