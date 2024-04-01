<template>
  <div class="item" v-for="(item, i) in products" :key="i">
    <!-- data binding 1 : 속성을 데이터 바인딩 하고 싶으면 :속성 형식으로 사용한다. -->
    <img :src="item.image" alt="" />
    <h4>
      <a href="javascript:void(0);" @click="openModal(i)">{{
        item.title
      }}</a>
    </h4>
    <!-- data binding 2 : 요소를 데이터 바인딩 하고 싶으면 {{  }}를 사용한다. -->
    <p>{{ item.price }} 원</p>
    <p>{{ item.content }}</p>
    <!-- event 1 :  v-on은 @로 축약 가능 -->
    <button type="button" v-on:click="increase(i)">허위매물신고</button
    ><span>신고수 : {{ item.report }}</span>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: {
    products: Array,
    openModal: Function,
    increase: Function,
  },
};
</script>

<style></style>
