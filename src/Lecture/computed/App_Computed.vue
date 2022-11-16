<template>
  <div>
    <h2>{{ teacher.name }}</h2>
    <h3>강의가 있나요?</h3>
    <!-- <p>{{ teacher.lectures.length > 0 ? '있음 :)' : '없음 :)' }}</p> -->
    <p>{{ hasLecture }}</p>
    <p>{{ hasLecture }}</p>
    <p>{{ existLecture() }}</p>
    <p>{{ existLecture() }}</p>
    <button v-on:click="counter++">Counter: {{ counter }}</button>
    <hr />
    <h2>이름</h2>
    <p>{{ fullName }}</p>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
  setup() {
    const teacher = reactive({
      name: '경훈',
      lectures: ['html/css', 'javascript', 'vue3'],
    });

    // method와 computed의 차이점 computed가 성능면에서 더 좋음 왜냐?
    // computed는 한번 계산된 결과를 캐쉬해서 보관하고 있어서 캐쉬된 데이터를 돌려줌
    // 하지만 method는 계산될 때 마다 돌려줌 계산될 때 마다 돌려주는 시점은 반응형 데이터가 변경되는 시점이다.
    const hasLecture = computed(() => {
      console.log('computed');
      return teacher.lectures.length > 0 ? '있음 :)' : '없음 :)';
    });
    // computed는 기본적으로 getter 전용. 계싼된 속성에 새 값을 할당하려고 하면 런타임 경고가 표시
    // 새로운 계산된 속성이 필요한 경우 geter와 setter 모두 제공하는 속성 제작 가능
    const existLecture = () => {
      console.log('method');
      return teacher.lectures.length > 0 ? '있음 :)' : '없음 :)';
    };

    const counter = ref(0);
    const firstName = ref('홍');
    const lastName = ref('길동');

    const fullName = computed({
      get() {
        return firstName.value + lastName.value;
      },
      set(value) {
        console.log('value: ', value);
        console.log(value.split(' '));
        [firstName.value, lastName.value] = value.split(' ');
        // console.log('first: ', first);
        // console.log('last: ', last);
      },
    });

    // const fullName = computed(() => firstName.value + lastName.value);
    console.log('Console 출력 : ', fullName.value);
    // computed에 set하려면 경고표시 출력
    fullName.value = '추 경훈';

    return { teacher, hasLecture, existLecture, counter, fullName };
  },
};
</script>

<style lang="scss" scoped></style>
