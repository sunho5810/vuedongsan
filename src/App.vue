<template>
  <!-- v-if 1 :
    vue에서 쓰는 조건문
    v-else, v-else-if 도 사용할 수 있다.
  -->

  <!-- component 4 : 컴포넌트를 너무 남발하면 데이터 바인딩 한게 꼬일 수 있으니 자제하자. 
    props를 사용하면 데이터 바인딩이 가능하긴 하지만, 코드가 복잡해질 수 있으니 신중하게 사용하자
   -->
  <!-- props 1 : 부모에서 자식에게 데이터를 전달하는 방식
     v-bind:작명 or :작명 으로 props를 전송한다. -->
  <ModalDetail
    v-bind:products="products"
    :currentIdx="currentIdx"
    :modal="modal"
    :closeModal="closeModal"
  />

  <!-- v-for 2 : 사용 시 key값은 필수 -->
  <div class="menu">
    <a href="javascript:void(0);" v-for="menu in menuList" :key="menu">{{
      menu
    }}</a>
  </div>

  <!-- component 3 : 사용 -->
  <BannerDiscount />

  <!-- v-for 1 : vue에서 쓰는 반복문
    사용 시 밑에 i처럼 인덱스를 받아올 수 있음 
  -->
  <div class="product-list">
    <!-- props 4 : props로 함수를 전달하면 함수의 원형을 전달한다. (매개변수 사용해줄 필요 X) -->
    <CardProduct
      :products="products"
      :openModal="openModal"
      :increase="increase"
    />
  </div>
</template>

<script>
/*
  import 1 :
  가져온 데이터를 원하는 변수명으로 가져오고 경로를 적어준다.
  export했던 형태 그대로 받아와야 한다.
*/
import data from "./assets/oneroom";

/* component 1 : import */
import BannerDiscount from "./components/BannerDiscount.vue";
import ModalDetail from "./components/ModalDetail.vue";
import CardProduct from "./components/CardProduct.vue";

export default {
  name: "App",
  /* data생성 : 
    데이터는 부모도 쓰는 데이터라면 되도록 최상위 부모 컴포넌트에 만들어둔다.
  */
  data() {
    return {
      currentIdx: 0,
      menuList: ["Home", "Shop", "About"],
      products: data,
      modal: false,
    };
  },
  /* 함수 만드는 공간 */
  methods: {
    increase(i) {
      /* data안에 있는 데이터를 사용하고 싶으면 this로 불러올 수 있음. */
      this.products[i].report++;
    },
    openModal(idx) {
      this.modal = true;
      this.currentIdx = idx;
    },
    closeModal() {
      this.modal = false;
    },
  },
  components: {
    /* 
      component 2 : 등록
      선언 한 컴포넌트 명과 변수명이 같다면 BannerDiscount로 축약해서 사용할 수 있다.
    */
    BannerDiscount: BannerDiscount,
    ModalDetail,
    CardProduct,
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
}

div {
  box-sizing: border-box;
  text-align: center;
}

a {
  text-decoration: none;
}

.menu {
  background-color: darkslateblue;
  margin-bottom: 40px;
  padding: 15px;
  border-radius: 5px;

  a {
    color: white;
    padding: 10px;
  }
}

button {
  cursor: pointer;
}

.modal {
  position: fixed;
  padding: 20px;
  width: 100%;
  height: 100%;
  background-color: rgba(black, 0.5);
  &-container {
    width: 100%;
    padding: 20px;
    background-color: white;
    border-radius: 8px;
  }
}

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
