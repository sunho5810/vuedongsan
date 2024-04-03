<template>
  <div class="item">
    <!-- data binding 1 : 속성을 데이터 바인딩 하고 싶으면 :속성 형식으로 사용한다. -->
    <img :src="products.image" alt="" />
    <h4>
        <!-- custom event 1 :
            자식이 부모의 값을 함부로 수정하거나 할 수 없다.
            그래서 자식은 부모에게 편지를 써야 하는데
            $emit()을 사용하여 편지를 쓴다
            ** $로 시작하는건 vue에서 사용하는 변수(함수)이다.
            $emit('작명', 값) - 값은 필수X
         -->
      <a href="javascript:void(0);" @click="send">{{
        products.title
      }}</a>
    </h4>
    <!-- data binding 2 : 요소를 데이터 바인딩 하고 싶으면 {{  }}를 사용한다. -->
    <p>{{ products.price }} 원</p>
    <p>{{ products.content }}</p>

    <!-- event 1 :  v-on은 @로 축약 가능 -->
    <button type="button" v-on:click="$emit('increase', products.id)">허위매물신고</button
    ><span>신고수 : {{ products.report }}</span>
  </div>
</template>

<script>
export default {
  name: "CardProduct",
  props: {
    products: Array,
  },
  methods: {
      /* custom event 3 : 
        함수로 부모에게 편지를 쓰고싶다?
        함수명(){
            **this는 필수!
            this.$emit('작명', 값 or this.props값)의 형태로 편지를 써준다.
        }
      */
    send(){
        this.$emit('openModal', this.products.id)
    }
  }
};
</script>

<style lang="scss">
.product-list {
  .item {
    margin-bottom: 30px;
    img {
      width: 400px;
    }
  }
  h4 {
    a {
      color: black;
    }
  }
}
</style>
