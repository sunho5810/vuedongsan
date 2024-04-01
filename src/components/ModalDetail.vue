<template>
  <div class="modal" v-if="modal === true">
    <div class="modal-container">
      <img :src="products[currentIdx].image" alt="" />
      <h4>{{ products[currentIdx].title }}</h4>
      <p>{{ products[currentIdx].price }} 만원</p>
      <p>{{ products[currentIdx].content }}</p>
      <p>신고수 : {{ products[currentIdx].report }}</p>
      <button type="button" @click="closeModal">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalDetail",
};
</script>

<style></style>
