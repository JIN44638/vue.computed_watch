<template>
  <div>
    <h2>장바구니</h2>
    <p>상품가격 : {{ formatNumber(price) }}</p>
    <p>할인금액(20%) : {{ formatNumber(discount) }}</p>
    <p>세금(10%) : {{ formatNumber(tax) }}</p>
    <hr />
    <p>
      <strong>최종 결제금액 : {{ formatNumber(total) }}</strong>
    </p>
  </div>
</template>
<script setup>
import { ref, computed } from "vue";
// 천단위 콤마 함수
const formatNumber = (num) => {
  return num.toLocaleString();
};
// 원래 가격
const price = ref(10000);
// 할인금액(20%)
const discount = computed(() => {
  return price.value * 0.2;
});
// 세금(10%)
const tax = computed(() => {
  // 세금= 원래가격 - 할인금액의 10%
  return (price.value - discount.value) * 0.1;
});
// 최종결제금액
// 최종금액 = 원래가격 - 할인금액 + 세금
const total = computed(() => {
  return price.value - discount.value + tax.value;
});
</script>

<style scoped></style>
