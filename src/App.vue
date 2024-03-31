<template>
  <!-- modal의 값이 true일때 모달창을 노출해주는 조건문 -->
  <div class="modal" v-if="modal === true">
    <div class="modal-container">
      <h3>상세페이지</h3>
      <img :src="products[itemIdx].imgSrc" alt="">
      <h4>{{ products[itemIdx].name }}</h4>
      <p>{{ products[itemIdx].price }} 만원</p>
      <p>신고수 : {{ products[itemIdx].report }}</p>
      <button type="button" @click="closeModal">닫기</button>
    </div>
  </div>

  <!-- v-for 사용 시 key값은 필수 -->
  <div class="menu">
    <a href="javascript:void(0);" v-for="menu in menuList" :key="menu">{{menu}}</a>
  </div>

  <!-- v-for 사용 시 밑에 i처럼 인덱스를 받아올 수 있음 -->
  <div class="product-list">
    <div class="item" v-for="(item, i) in products" :key="i">
      <img :src="item.imgSrc" alt="">
      <h4><a href="javascript:void(0);" @click="openModal(i)">{{ item.name }}</a></h4>
      <p>{{ item.price }} 만원</p>
      <!-- v-on은 @로 축약 가능 -->
      <button type="button" v-on:click="increase(i)">허위매물신고</button><span>신고수 : {{ item.report }}</span>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      itemIdx: 0,
      menuList: ["Home", "Shop", "About"],
      products: [
        {
          id: 0,
          name: "성동구원룸",
          price: 50,
          report: 0,
          imgSrc: "https://dimg.donga.com/wps/NEWS/IMAGE/2016/09/17/80313265.2.jpg",
        },
        {
          id: 1,
          name: "일산동구원룸",
          price: 60,
          report: 0,
          imgSrc: "https://dimg.donga.com/wps/NEWS/IMAGE/2015/01/27/69300957.2.jpg",
        },
        {
          id: 2,
          name: "팔달구원룸",
          price: 70,
          report: 0,
          imgSrc: "https://images.homify.com/v1472840207/p/photo/image/1640320/nachher04.jpg",
        },
      ],
      modal: false,
    }
  },
  /* 함수 만드는 공간 */
  methods: {
    increase(i){
      /* data안에 있는 데이터를 사용하고 싶으면 this로 불러올 수 있음. */
      this.products[i].report++;
    },
    openModal(idx){
      this.modal = true;
      this.itemIdx = idx;
    },
    closeModal(){
      this.modal = false;
    }
  },
  components: {
  }
}
</script>

<style lang="scss">
body{
  margin: 0;
}

div{
  box-sizing: border-box;
  text-align: center;
}

.menu{
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;

  a{
    color: white;
    padding: 10px;
  }
}

button{
  cursor: pointer;
}

img{
  width: 400px;
}

.modal{
  position: fixed;
  padding: 20px;
  width: 100%;
  height: 100%;
  background-color: rgba(black, .5);
  &-container{
    width: 100%;
    padding: 20px;
    background-color: white;
    border-radius: 8px;
  }
}

.product-list{
  margin-top: 40px;
  .item{
    margin-top: 30px;
  }
  h4{
    a{
      color: black;
    }
  }
}

</style>
