<template>
  <div>
    <!-- 속성 v-model 입력함 -->
    <input v-model="message" @input="updateMessage" type="text" placeholder="메세지 입력" />
    <p>입력한 내용 :{{ message }}</p>
    <input v-model="name" @input="updateName" type="text" placeholder="이름입력" />
    <p>이름 : {{ name }}</p>
  </div>
</template>
<script setup>
import { ref, nextTick } from "vue";
// 빈문자열로 만들겠다(input입력된 값넣어야되서)
const message = ref("");
const name = ref("");
// 한글 이슈
const updateMessage = (event) => {
  nextTick(() => {
    // 메세지에 입력되는 값
    message.value = event.target.value;
  });
};
const updateName = (event) => {
  nextTick(() => {
    // 메세지에 입력되는 값
    name.value = event.target.value;
  });
};
</script>
<style scoped></style>
