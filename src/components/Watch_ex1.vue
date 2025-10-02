<template>
  <div>
    <button @click="score++">점수 올리기</button>
    <button @click="score--">점수 내리기</button>
    <hr />
    <p>현재 점수 : {{ score }}</p>
    <p>이전 점수 : {{ oldScore }}</p>
    <p>새 점수 : {{ newScore }}</p>
  </div>
</template>
<script setup>
import { ref, watch } from "vue";
// 1.감시할 값(현재점수)
const score = ref(0);
// 이전점수
const oldScore = ref("");
// 새로운 점수
const newScore = ref("");
// 2. watch()로 점수를 감시하기
watch(score, (newVal, oldVal) => {
  console.log("점수가 바뀌었어요");
  console.log(`이전점수 : ${oldVal} => 새점수 : ${newVal}`);
  oldScore.value = oldVal; //화면에 보이도록 ref에 저장
  newScore.value = newVal;
  if (newVal >= 5) {
    alert("우와! 점수가 5점 이상입니다.");
  }
});
</script>
<style scoped></style>
