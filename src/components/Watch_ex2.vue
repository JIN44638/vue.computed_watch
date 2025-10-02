<template>
  <div>
    <label> <input type="checkbox" v-model="agree"/>약관에 동의합니다. </label>
    <hr>
    <!-- agree ?  "동의함✅" : "동의 안함" = if문과 같다
     = agree가 있으면(참) 동의함 아니면 동의안함으로  -->
    <p>현재 상태: {{ agree ?  "동의함✅" : "동의 안함❌"}}</p>
    <p>이전 상태: {{ oldAgree }}</p>
    <p>새 상태: {{ newAgree }}</p>
  </div>
</template>
<script setup>
import { ref ,watch } from 'vue';
// 체크박스 값(true / false) 
// ref(true)로 해놓으면 체크박스에 체크가 되어있는상태가 된다.그래서 false로 입력함
const agree = ref(false)
// 이전 상태, 새 상태
const oldAgree = ref("")
const newAgree = ref("")
// watch( ) 감시
watch(agree , (newVal , oldVal)=>{
oldAgree.value = oldVal ? "동의함✅" : "동의 안함❌"
newAgree.value = newVal ? "동의함✅" : "동의 안함❌"
})
</script>
<style scoped></style>
