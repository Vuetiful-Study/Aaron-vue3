<template>
  <div></div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
  setup() {
    const count = ref(0);
    const state = reactive({
      count,
    });
    count.value++;
    count.value++;
    console.log(count.value);
    console.log('state.count: ', state.count);

    const msg = ref('hello');
    const arr = reactive([msg]);
    console.log('state.count:', arr[0].value);
    return {
      count,
      state,
    };
  },
};
</script>

<style lang="scss" scoped></style>
