<template>
  <div>
    <button v-on:click="increament">Click {{ state.count }}</button>
    <button v-on:click="deepClick">Click {{ state.deep.count }}</button>
  </div>
</template>

<script>
import { reactive } from 'vue';

export default {
  setup() {
    const state = reactive({
      count: 0,
      deep: {
        count: 0,
      },
    });
    const increament = () => {
      state.count++;
    };
    const deepClick = () => {
      state.deep.count++;
    };
    return {
      state,
      increament,
      deepClick,
    };
  },
};
</script>

<style lang="scss" scoped></style>
