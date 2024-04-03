<template>
  <!-- v-if 1 :
    vue에서 쓰는 조건문
    v-else, v-else-if 도 사용할 수 있다.
  -->

  <!-- component 4 : 컴포넌트를 너무 남발하면 데이터 바인딩 한게 꼬일 수 있으니 자제하자. 
    props를 사용하면 데이터 바인딩이 가능하긴 하지만, 코드가 복잡해질 수 있으니 신중하게 사용하자
   -->
  <!-- props 1 : 부모에서 자식에게 데이터를 전달하는 방식
      v-bind:작명 or :작명 으로 props를 전송한다. (변수 선언과 흡사함)
      단순한 값도 전송 가능 - :작명="데이터" or 작명="데이터" 꼴로 전송 가능
    -->
  <ModalDetail
    v-bind:products="products"
    :currentIdx="currentIdx"
    :modal="modal"
    @closeModal="closeModal"
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
    <!-- props 4 : props로 함수를 전달하면 함수의 원형을 전달한다. (매개변수 사용해줄 필요 X) ***수정 안됨 -->
    <!-- custom event 2 :
      @자식이보낸편지 형태의 이벤트로 실행해준다.
      만약 자식이 값과 함께 편지를 쓴다면?
      $event를 값으로 사용한다.
    -->
    <CardProduct
      v-for="(products, i) in products"
      :key="i"
      :products="products"
      @openModal="openModal($event)"
      @increase="increase($event)"
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
      /* props 5: 
        object형식의 데이터를 따로따로 보내려면?
        :작명="object.name" :작명="object.age"
        한번에 보내려면?
        v-bind="object"
      */
      object: { name: "kim", age: 20 },
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
      선언 한 컴포넌트 명과 변수명이 같다면 한 번만 써서 축약해 사용할 수 있다.
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
</style>
