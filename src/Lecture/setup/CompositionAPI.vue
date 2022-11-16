<template>
  <div>
    <h2>반응형 메세지</h2>
    <p>{{ reactiveMsg }}</p>
    <button v-on:click="onChangeBtn">Add Mes Btn</button>
    <h2>일반 메세지</h2>
    <p>{{ nomalMsg }}</p>
    <button v-on:click="onChangeNomalMsgBtn">Add Nomal Mes Btn</button>
  </div>
</template>

<script>
import { onBeforeMount, onMounted, ref } from 'vue';
export default {
  setup() {
    console.log('setup');
    const reactiveMsg = ref('Hello reactive Msg');
    let nomalMsg = 'nomal Msg';
    const onChangeBtn = () => {
      reactiveMsg.value = reactiveMsg.value + '!';
    };
    // console.log(isRef(reactiveMsg));

    const onChangeNomalMsgBtn = () => {
      nomalMsg.value = nomalMsg.value + '!';
    };
    // console.log(isRef(nomalMsg));

    onMounted(() => {
      console.log('onMounted');
    });

    onBeforeMount(() => {
      console.log('onBefore Mounted');
    });

    return {
      reactiveMsg,
      nomalMsg,
      onChangeBtn,
      onChangeNomalMsgBtn,
    };
  },
};
</script>

<style lang="scss" scoped></style>
