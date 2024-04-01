<template>
  <!-- 
    modal의 값이 true일때 모달창을 노출해주는 조건문 
    v-else, v-else-if 도 사용할 수 있다.
  -->

  <!-- component 4 : 컴포넌트를 너무 남발하면 데이터 바인딩 한게 꼬일 수 있으니 자제하자. -->
  <ModalDetail/>

  <!-- v-for 사용 시 key값은 필수 -->
  <div class="menu">
    <a href="javascript:void(0);" v-for="menu in menuList" :key="menu">{{
      menu
    }}</a>
  </div>

  <!-- component 3 : 사용 -->
  <BannerDiscount/>

  <!-- v-for 사용 시 밑에 i처럼 인덱스를 받아올 수 있음 -->
  <div class="product-list">
    <div class="item" v-for="(item, i) in products" :key="i">
      <!-- 속성을 데이터 바인딩 하고 싶으면 :를 사용한다. -->
      <img :src="item.image" alt="" />
      <h4>
        <a href="javascript:void(0);" @click="openModal(i)">{{ item.title }}</a>
      </h4>
      <!-- 요소를 데이터 바인딩 하고 싶으면 {{  }}를 사용한다. -->
      <p>{{ item.price }} 원</p>
      <p>{{ item.content }}</p>
      <!-- v-on은 @로 축약 가능 -->
      <button type="button" v-on:click="increase(i)">허위매물신고</button
      ><span>신고수 : {{ item.report }}</span>
    </div>
  </div>
</template>

<script>
/*
  가져온 데이터를 원하는 변수명으로 가져오고 경로를 적어준다.
  export했던 형태 그대로 받아와야 한다.
*/
import data from "./assets/oneroom";

/* component 1 : import */
import BannerDiscount from "./components/BannerDiscount.vue";
import ModalDetail from "./components/ModalDetail.vue";

export default {
  name: "App",
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
