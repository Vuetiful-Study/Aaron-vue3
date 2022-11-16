<template>
  <div>
    <button v-on:click="increament">Counter: {{ counter }}</button>
  </div>
</template>

<script>
import { onMounted, ref } from 'vue';
export default {
  setup() {
    const counter = ref(0);
    const increament = () => counter.value++;
    onMounted(() => {
      console.log('컴포넌트가 마운트 되었습니다.');
    });
    return {
      counter,
      increament,
    };
  },
  // setup 함수의 첫 번째 매개변수는 props 두 번째 매개변수는 context
  // context.attrs 속성 $attrs와 동일한 비반응형 객체
  // context.slots 속성 $slot에 해당하는 비반응형 객체
  // 이벤트 발생 $emit에 해당하는 함수
  // Public한 속성, 함수를 외부에 노출 시에 사용
};
</script>

<style lang="scss" scoped></style>