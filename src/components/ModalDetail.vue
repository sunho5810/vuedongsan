<template>
  <div class="modal" v-if="modal === true">
    <div class="modal-container">
      <img :src="products[currentIdx].image" alt="" />
      <h4>{{ products[currentIdx].title }}</h4>
      <p>{{ products[currentIdx].price }} 만원</p>
      <p>{{ products[currentIdx].content }}</p>
      <p>신고수 : {{ products[currentIdx].report }}</p>
      <button type="button" @click="closeModal">닫기</button>
      <!-- ex) props 3 : props는 read-only
        closeModal함수 형식 말고 modal = false 이런식으로 값의 재할당을 금지한다. -->
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalDetail",
  /* props 2 : 부모에게서 받은 데이터를 저장한다. 
    data명: 자료형(굳이굳이 사용할 필요는 없지만 적어주는게 좋다.)
  */
  props: {
    products: Array,
    currentIdx: Number,
    modal: Boolean,
    closeModal: Function,
  }
};
</script>

<style></style>
