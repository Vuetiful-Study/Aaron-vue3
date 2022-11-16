<template>
  <div>
    <p>{{ msg }}</p>
    <hr />
    <p>{{ msg2 }}</p>
    <button v-on:click="addMsg">add click</button>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
  setup() {
    let msg = reactive('hello vue');
    const addMsg = () => {
      msg = msg + '!';
      msg2.value = msg2.value + '!';
    };
    let msg2 = ref('hello vue');
    console.log('msg: ', msg);
    console.log('msg: ', typeof msg);
    console.log(msg2);
    return {
      msg,
      addMsg,
      msg2,
    };
  },
};
</script>

<style lang="scss" scoped></style>
