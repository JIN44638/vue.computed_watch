<template>
  <div>
    <p>가격 : {{ formatNumber(price) }}</p>
    <p>세금 : {{ formatNumber(tax) }}</p>
    <p>총합 : {{ formatNumber(total) }}</p>
  </div>
</template>
<script setup>
import { computed, ref } from "vue";
// computed() - 계산된 값을 담아놓는 함수
// 다른 데이터에 따라 자동으로 값이 바뀌는 계산 전용 변수
const price = ref(2500);
// 결과값은 return 적어서 반환해야한다
const tax = computed(() => {
  return price.value * 0.1;
});
// console.log(tax.value);
const total = computed(() => {
  return price.value + tax.value;
});
// 천단위 콤마(,) 함수
const formatNumber = (num) => {
  return num.toLocaleString();
};
</script>

<style scoped></style>
